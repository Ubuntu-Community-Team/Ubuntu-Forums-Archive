---
title: "Command line GUI - university project"
date: 2010-09-28
forum: Programming Talk
---

### Post by sw0rn on 2010-09-28
Ciao!

This semester, for a software engineering class, I have a term project that involves using several software engineering tools, extensive documentation, and a functional end-product. From the available projects (supplied by the professor), I have chosen a "GUI to command line translator for Unix shell."

My plan is to create a .htm page with an image. This image will have an image map implemented so that when the user clicks on a part of the image (ex. "Change Directory") it will push the command out to a terminal. 

That said, I am turning to Ubuntu community with a few questions:

[LIST]
[*]I have seen on several example pages that such a program is feasible and has been done before. However, most of them are designed so that the web page is loaded from a server and then pushed out to the computer. I just want to run mine locally. In HTML, would my command look like this?:
[/LIST]
```
<a href="COMMAND" target="where?"> <!--code for image map, etc ---> </a>
```
[LIST]
[*]Does anybody have suggestions on what functions I should use? Common ones or useful ones? I was thinking that I would do mainly information-based commands, such as printing Operating System details, memory usage, etc etc.
[/LIST]
Thanks in advance to any and all replies!

---

### Post by pricetech on 2010-09-28
Plenty of HTML tutorials on the web.  That's where I'd start.

---

### Post by Barrucadu on 2010-09-28
You'd have to set up a web server locally and probably use a server-side scripting language (such as PHP) for this. It would be *much* simpler to write your project in, say, Python using PyGTK or PyQT.

---

### Post by conundrumx on 2010-09-28
Using HTML for the GUI is a bad idea; I would agree with the previous poster's suggestion to use Python.

---

### Post by worksofcraft on 2010-09-28
Due to security reasons you cannot issue system commands from html documents, not even with Javascript. It is howevere possible to do it with Java (e.g. [see here for details]("http://devdaily.com/java/edu/pj/pj010016/")) Your Java can be embedded in your html, but I suspect you will still have a battle with security constraints.

---

### Post by Bachstelze on 2010-09-28
Or PHP. Horde has a shell thing in its admin interface.

---

### Post by SeijiSensei on 2010-09-28
> **worksofcraft said:**
> Due to security reasons you cannot issue system commands from html documents, not even with Javascript.

That's not strictly true, but you'd need to make Apache run as the root user rather than as the Ubuntu default "www-user".  [Webmin]("http://www.webmin.com/"), for instance, is a full-featured administrative console for Linux with a self-contained web server that is written in perl and runs with root privileges.

OP, I'd suggest you take a look at Webmin just to get some ideas.

Webmin is not in the repositories for reasons given [here]("https://help.ubuntu.com/community/WebMin"). There are a number of articles out there on how to install it from the tarball available at webmin.com.

---

### Post by worksofcraft on 2010-09-28
> **SeijiSensei said:**
> That's not strictly true, but you'd need to make Apache run as the root user rather than as the Ubuntu default "www-user"...

Oh... yes I hadn't thought of that. I was thinking sw0rn wanted to use it as a client-side html page on computers that might not even have Apache installed.

---

### Post by sw0rn on 2010-10-03
Thanks, everyone. With this in mind, I will venture forward and see what I can come up with.

---

