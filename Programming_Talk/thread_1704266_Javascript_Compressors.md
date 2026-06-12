---
title: "Javascript Compressors"
date: 2011-03-10
forum: Programming Talk
---

### Post by nair on 2011-03-10
What javascript compressors have you guys used before? I'm looking for a simple, downloadable/installable javascript compressor that isn't ancient. I've never used one before. A lot of the ones I am finding are several years old, and all of them are web-based, (ex. [http://www.diveintojavascript.com/tools/javascript-minifier-packer-compressor-compiler](http://www.diveintojavascript.com/tools/javascript-minifier-packer-compressor-compiler)).

I really don't know a lot about what I am looking for in terms of features. I just want to develop javascript code that runs fast, which means the compressor has to be able to remove whitespace, newline characters, and comments.  I also don't know much about the evolution of the javascript language itself, if its syntax has changed over the years, and--if so--which compressors work with older javascript code and which compressors work with newer javascript code.

---

### Post by VernonA on 2011-03-10
I was reading the following IBM tutorial on setting up a site using latest ideas ([BoilerPlate HTML5]("http://www.ibm.com/vrm/newsletter_10731_8472_184778_email_DYN_1IN/jrnb138365135")) and downloaded the resources from [http://html5boilerplate.com/]("http://html5boilerplate.com/"). Amongst other things, it has a build directory which contains an ANT script and tools to do things like minify the scripts, the html and the images in the rest of the site just before publishing. Specifically it uses Yahoo's yuicompressor tool for Javascript compression. Mr Irish and his colleagues spend their time looking for the "best-of-the-best" so this is a good endorsement.

---

### Post by myrtle1908 on 2011-03-10
I've used YUI, it's great [http://developer.yahoo.com/yui/compressor/](http://developer.yahoo.com/yui/compressor/)

I've heard good things about Closure Compiler [http://code.google.com/p/closure-compiler/](http://code.google.com/p/closure-compiler/)

For large JS projects consisting of many files one typically does the following

1. On build, combine all JS files into one (many ways to do this eg. Ant or just a basic concat).  Careful, order of files is often important.
2. Compress the single file using YUI or similar
3. Have web server GZip for delivery to client

Apply similar process to CSS files if they are also large.

Good Luck

---

