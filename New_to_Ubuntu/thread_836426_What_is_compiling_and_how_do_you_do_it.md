---
title: "What is compiling and how do you do it?"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by Redrazor39 on 2008-06-21
Topic?

---

### Post by drs305 on 2008-06-21
Here is the link to the Ubuntu Documentation section on compiling:
[https://help.ubuntu.com/community/CompilingEasyHowTo]("https://help.ubuntu.com/community/CompilingEasyHowTo")

---

### Post by the_doc on 2008-06-21
Compilling is the process of turning source code (readable by humans) into object code (readable by the CPU).

You do compilaton with a compiler (sorry!), these include gcc, cc, ones that are built into IDE's etc.

---

### Post by ibuclaw on 2008-06-21
Compiling is making executable binaries out of sourcecode.

Although if you are compiling a program you downloaded, most of the time you don't need to remember the nitty-gritty things about gcc/g++ and other compilers.

Nine times out of ten it will be a simple
```

./configure
make
sudo make install

```
Which is
[LIST]
[*]Configure the compiling flags to suit your computer (architechture/libs/etc).
In configure, you can also add your own custom configurations. For example, "**--prefix=/path/to/dir**", which is the directory that the program will be installed into.
[*]Make the binaries (compile).
[*]Install the binaries and config files into your system.
[/LIST]

Regards
Iain

[EDIT]
Here is a minature overview of what goes on:
[IMG]http://www.aboutdebian.com/compile.gif[/IMG]

Although there is a lot more that goes into the complete compiling process (such as syntax checking/etc/etc) before the binaries are even attempted to be made.

---

### Post by drs305 on 2008-06-21
If you are getting the urge to compile something, here are some general observations:

1. Look to see if the app is in the repositories. The packages in the main repositories have been tested and should work well. That may not be the case with an app you compile yourself.

2. If you compile a package, instead of "make install" use "checkinstall". This will register the installation in your system and allow for easier uninstalls. You will have to install "checkinstall", but it's in the repositories.

3. Compiled packages don't update themselves. If you compile your own package, it won't receive updates as do the packages in the repositories. Additionally, you will often have to recompile the package when your system files change significantly (new kernels, etc).

4. If you compile a package, make sure to save the installation folder. It usually has a 'postinst' or another folder which contains the uninstall files. If you delete the folder, you may be deleting the best method to uninstall the package at a later date.

This is not to discourage you from compiling. It is not something to be afraid of. I compiled audacity from source because it was the only way I could get it to run with an particular feature that I wanted. That's the beauty of linux - freedom to choose.

Best of luck.

---

### Post by Redrazor39 on 2008-06-21
I see, thanks.

I was trying to install raptor-menu in kubuntu with KDE4 until I found out kubuntu does KDE badly and openSUSE does it much better (I agree).

I'll try it in that but I'll come back here for more help if necessary.

[www.raptor-menu.org](www.raptor-menu.org)

check out the download page.

---

### Post by nowshining on 2008-06-22
u can upgreade to a newer/natural version of kubuntu thru kde.org. I did for gutsy. Yes it's usually as easy as adding a repository and doing an upgrade.

---

