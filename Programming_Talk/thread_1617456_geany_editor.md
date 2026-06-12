---
title: "geany editor"
date: 2010-11-09
forum: Programming Talk
---

### Post by elruinnou on 2010-11-09
hai everyone, i have a question about using Geany editor. i'm gonna use it to create PHP file, and G++ file, but i don't understand how to install the library for compiling the PHP and G++ script.

anyone can help??

thx before

---

### Post by jahst on 2010-11-12
Well, not to sure about G++ although I want to learn more, but I use Geany all the time for my web design.

PHP is not compiled, it's just server side scripting.

You can change the highlight language in geany

Document Tab
Set FileType

will give you correct formatting.

Usually if you save it for example as .php it will automatically change correct highlighting for php language.. again. not sure about g++ 

It's on my todo list.

---

### Post by leg on 2010-11-12
Once you have a file loaded that has a cpp file extension you will have access to the build menu. In build >> set includes and arguments you can set the paths required to access the g++ compiler. You probably won't need to on a Ubuntu system as it will be on the path and found anyway but I also use it on Windows in conjunction with mingw and need to set that path. You will need to have build-essentials installed.

---

