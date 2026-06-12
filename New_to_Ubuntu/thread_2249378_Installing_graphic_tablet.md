---
title: "Installing graphic tablet"
date: 2014-10-21
forum: New to Ubuntu
---

### Post by Willi_Meyhoff on 2014-10-21
I really need to install my graphics tablet, and dont want to go back to windows just for that, so I wanted to ask if someone could explain to me how to do this?
[http://ubuntuforums.org/showthread.php?t=2216333&p=13131603](http://ubuntuforums.org/showthread.php?t=2216333&p=13131603)

am I supposed to install the kernel first and then the patch? or are they two different things?

I bet it's something really simple haha

---

### Post by ian-weisser on 2014-10-21
Compiling your own kernel is not simple at all.
It's very much an experience that you will learn a lot from.
Builds character. My first time, I learned a few new ways to ...er... express frustration.
You will also become quite experienced at using a terminal.

I recommend building a plain, unpatched kernel first. See [https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel](https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel)
Go through the entire process and make sure you can install the final product, and that it runs.

Then patch the kernel source, ( [http://askubuntu.com/questions/11249/correct-way-to-apply-patches-to-your-kernel](http://askubuntu.com/questions/11249/correct-way-to-apply-patches-to-your-kernel) ) and, build, install, and run the custom kernel.

---

