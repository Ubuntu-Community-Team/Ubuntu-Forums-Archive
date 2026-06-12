---
title: "what is a installer script?"
date: 2012-10-16
forum: New to Ubuntu
---

### Post by yuanhangliu1 on 2012-10-16
while I am installing a software. The instructions are "Use the installer script to create the correct directory layout by typing", so what is a installer script? is it something like Eric? Please help with this. Thanks!

---

### Post by cortman on 2012-10-16
What software are you trying to install? From where did you download it? Is it a zipped or tarballed file? What are the contents?

---

### Post by yuanhangliu1 on 2012-10-16
genesis-sim.org/userdocs/installation-ubuntu-precise/installation-ubuntu-precise.html
this is the link to the software and some guides.

---

### Post by yuanhangliu1 on 2012-10-16
> **cortman said:**
> What software are you trying to install? From where did you download it? Is it a zipped or tarballed file? What are the contents?


genesis-sim.org/userdocs/installation-ubuntu-precise/installation-ubuntu-precise.html
 this is the link to the software and some guides considering installation

---

### Post by yuanhangliu1 on 2012-10-16
anybody can help me?

---

### Post by lisati on 2012-10-16
From the web page, emphasis added:
> Use the installer script to create the correct directory layout by typing **&#8220;neurospaces_create_directories&#8221;**.

It would seem that the installer script  here (the *thingummy* that helps you install something) is called *neurospaces_create_directories*

---

### Post by SWGraphics291 on 2012-10-16
sudo apt-get (Program)

It gets confusing, depends on what the program is.

You need to find out from the program site.

---

### Post by audiomick on 2012-10-16
Without wanting to be rude, I think starwars might have posted without really reading the thread up to now...

> **yuanhangliu1 said:**
> ..so what is a installer script? 

To be absolutely precise, a script is a text document containing a set of commands that are executed one after the other when the script is run. The same result can be achieved by typing the commands one by one manually. The advantage in having them all contained in a text document that can be run with one command should be fairly obvious.

An installer script is, logically, one of those designed to install something.

In your case, it would seem that the text file that is the script has the name "neurospaces_create_directories”. Typing that in the terminal when you are in the directory it is in will cause it to be run.

---

