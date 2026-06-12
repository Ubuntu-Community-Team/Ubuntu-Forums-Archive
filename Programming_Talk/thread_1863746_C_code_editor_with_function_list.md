---
title: "C code editor with function list"
date: 2011-10-18
forum: Programming Talk
---

### Post by mbbuntu on 2011-10-18
I have ubuntu linux 11.04.
Gedit is very nice looking editor, but there isn't funciton list. I anstalled two plugins: function browser and symbol broser. In both cases, when I activated plugins I got some error, that there isn't some libraries. I downloaded those libs from other linux and made symbol linking to them. Now I can activate plugins but there isn't any functions in side bar.
So what would be good editor or how I can solve the issue in gedit?

---

### Post by Meghnaad on 2011-10-18
Hi,

use manual pages for the same,

you can get man page of printf by typing
```
man 3 printf
```
just replace name of function with function you want.
in doubt use
```
man -k <function_name>
```
to know which section to refer to

or 

If you want to use something in GUI go for code blocks IDE,
It has a help plugin with which you can see C/C++ help
[http://wiki.codeblocks.org/index.php?title=Help_plugin]("http://wiki.codeblocks.org/index.php?title=Help_plugin")

---

### Post by mbbuntu on 2011-10-20
Maybe you didn't understand my question.

I want similar function list like in ultra edit.

---

### Post by Mordred on 2011-10-20
gedit supports plugins.
This plugin should do the trick.

[https://github.com/Quixotix/gedit-source-code-browser](https://github.com/Quixotix/gedit-source-code-browser)

If you need even more, you could switch to an IDE like Code::Blocks, Anjuta or Eclipse with CDT plugin.

---

### Post by Pithikos on 2011-10-21
Have you tried Geany? I was also very upset with gedit untill I tryied out Geany. It's still clean and has more powerful features. It lists functions/variables by default.

---

### Post by Fallen_Demon on 2011-10-23
I still love NetBeans. Others on here will want to wage a holy war against me for using an Oracle product, but whatever. It's really nice and can automatically create your build files for you (may just be Java... Not sure about C)

---

### Post by mbbuntu on 2011-11-01
> **Pithikos said:**
> Have you tried Geany? I was also very upset with gedit untill I tryied out Geany. It's still clean and has more powerful features. It lists functions/variables by default.
Sorry my late response. This is nice editor and works like I wanted.

---

