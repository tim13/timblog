---
layout: post
title: 用jekyll写博客
category: infotech
---
第一篇博客。写下用博客的感受，再介绍用<a href="http://jekyllrb.com/">jekyll</a>写博客theme。

我所了解的博客，主要是3种：

* 博客服务提供商，比如新浪、qq空间，还有blogger不过国内被墙。用过一年新浪的，后来没写荒废了。现在登陆看，很多广告和弹窗。
* 使用wordpress博客程序+买vps+买域名。个人博客一般采用wordpress，搭建难度不大，插件多，theme多，和windows安装软件差不多，有些配置google下就可以解决。曾申请过个免费空间试，域名也是搜了个免费的用。后来没写，也荒废了。（如果用免费空间和免费域名，有风险，你苦心经营的博客可能随时崩，如果连数据都拿不回就惨极了）
* 最后是github pages，<a href="https://www.github.com">github</a>提供的项目展示功能。这个免去买空间的费用，如果不愿意用github的域名就自己买个。博客程序默认使用jekyll。

用jekyll写博客，其实网上很多教程。但定制自己博客theme（就是自己写页面和根据jekyll文档说明定制自己要的功能）时，感觉有步骤提及的软件版本旧。下文给教程的link，然后说过时的地方。还有一点是觉得没有说全面。

做好的准备：

1. html+css（二者去<a href="http://www.w3school.com.cn/h.asp">w3school</a>看看基本知识（了解div元素和css排版和盒模型(box model)后，边做边学可以了）+javascript（如果想做丰富的动态效果的话,要费一些时日）。

2. git知识，因为要提交文件到github。<a href="http://try.github.io/levels/1/challenges/1">这里</a>是github提供的试用git的页面。中文教程的，google到<a href="http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000">这个</a>。windows下安装git和安装常用软件没区别。了解后，申请一个github账号，并在github新建一个项目。如果需要帮助，可以看<a href="https://help.github.com/">这个</a>.

3. 找一个编辑器。比如notepad。没用过的话安装后用着就会了。

（注：更详尽的html、css和git资料分别在<a href="http://www.w3schools.com/">这</a>和<a href="http://git-scm.com/docs">这</a>)

定制theme步骤有4：

1.配置jekyll环境（windows下）。方便调试。（这一步你忽略也可以，因为可以git提交到github然后看效果。不过这样很痛苦）。教程点击<a href="http://huangxc.com/jekyll/">这里</a>。过时的地方在于编码问题，教程里提及如下：
<div style="border:solid 1px #000000">
<pre>
<p>之前本地调试一直不成功，提示如下错误：</p>
<code> Error:invalid byte sequence in GB2312</code>
<p>这是中文编码的错误，如果是写英文博客就不会出错，这似乎是 Jekyll 的一个 bug，解决方法是将 Ruby 安装文件路径下的 <code>.\lib\ruby\gems\1.9.1\gems\jekyll-1.1.2\lib\jekyll\convertible.rb</code> 文件第 31 行：</p>
<code>self.content = File.read(File.join(base, name))
</code>
<p>修改为：</p>
<code>self.content = File.read(File.join(base, name), :encoding =&gt; "utf-8")</code>
</pre>
</div>
我用的jekyll版本是jekyll-1.4.2。修改如下：
<div style="border:solid 1px #000000">
<pre>
文件的38行<code>self.content = File.read_with_options(File.join(base, name),merged_file_read_opts(opts))</code>改为
<code>self.content = File.read(File.join(base, name), :encoding =&gt; "utf-8")</code>
</pre>
</div>
意思是在jekyll读取文件时使用utf-8编码。

2.看<a href="http://jekyllrb.com/docs/home/">jekyll</a>文档，jekyll中文文档在<a href="http://jekyllcn.com/">这里</a>，写页面。要使用github pages 功能，创建分支有要求，github给出的说明在<a href="https://help.github.com/articles/creating-project-pages-manually">这里</a>。

3.写好页面，调试。做好后，提交到github。你定制的theme就好了。（2和3步骤一般是循环反复的）

4.用markdown写博客文章。写好博文文件提交到github就可以了，或者你在步骤3先写好一篇一并提交也可以。markdown可以边学习边写，写多后就快了。教程在<a href="http://wowubuntu.com/markdown/#code">这里</a>。
