---
title: "If I manually install a package, how do I go the other way?"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by UnWarierMage224 on 2008-05-14
Hi folks, 

i have no problem installing things. The kind folks over at MonkeyBlog have provided a very nice set of instructions for, as they say, how to install anything in ubuntu ([http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/))... My question though is if you download a package file and install it, how do you remove it? If you install a package manually, will synaptic get a handle on it and remove it? (I'm assuming this is the case if you use the sudo checkinstall command, yes?) If, however, you use the sudo install command and you want to remove a package, but don't remember the exact name of the downloaded package what do you do?

EDIT: Case in point, a package which I want to install. The website for that package gives the latest version as a tar.gz file and synaptic has an old version...

Does this make sense, what I'm asking?

Thanks. 

-'Mage

---

### Post by alexandremrj on 2008-05-14
Usually a tar.gz has the source file and usualy you have to compile it and that way synaptic doesnt know the program.
If you use a .deb file and install it even manually synaptic will recognize the package - usually on Origin (lower left button) and then local.

---

### Post by Paqman on 2008-05-14
Unless you used checkinstall, you can't easily remove it. Checkinstall creates a .deb package, which slots into the normal package management system.

In general, compiling software yourself should be avoided, since you get problems like this. Compiling also breaks the complicated dependency management system that the package manager maintains. This introduces instability into your system.

Bottom line, your order of preference should be:
1) The repos
2) A .deb file
3) Compile it yourself and use checkinstall

---

### Post by radamo on 2008-05-14
Is there anyway to go back and determine which packages I have installed from tar.gz files?  I thought that Synaptic would still handle updates on those so I never kept track. 
Thanks,
RA

---

### Post by t0p on 2008-05-14
> **UnWarierMage224 said:**
> 
My question though is if you download a package file and install it, how do you remove it? If you install a package manually, will synaptic get a handle on it and remove it?

I haven't manually installed many packages so I don't know if this is always the case: but Synaptic has got a handle on the few self-installed apps on my computer.  For instance, I installed a MMORPG called Daimonin, and afterwards  I successfully used Synaptic to uninstall it. I've also done this with a few crappy games I found on the web and quickly grew sick of.  So yes, Synaptic should be able to deal with it.

**EDIT:** just to clarify a point, the self-installed apps all came as .debs.  I didn't compile them myself.  So I have no idea if Synaptic can handle self-compiled apps.

---

### Post by kosmic on 2008-05-14
One way to see what programs you have compiled from source is when compiling programs one must define the PATH.

Usualy I define the PATH of the program to be /opt, so everything I compile from Source will be instaled in /opt/etc/files, /opt/bin/exec etc...

This Way I know where is every file of a program manually installed, so I can remove the directory if I dont need that program anymore :)

[offquote]
That is the reason I Love FreeBSD so much when compared to linux, it is a simpler and wonderful world ;)
[/offquote]

---

### Post by Paqman on 2008-05-14
> **radamo said:**
> Is there anyway to go back and determine which packages I have installed from tar.gz files?  I thought that Synaptic would still handle updates on those so I never kept track. 
Thanks,
RA

Nope. I'm afraid Synaptic has no idea what you've installed by compiling those tarballs (unless you use checkinstall, of course). Compiling from source completely bypasses the package management system. Hence, not a good idea in my opinion.

---

### Post by alexandremrj on 2008-05-14
Synaptic only handles updates from those programs thats has repositories to check.

Programs manually that are manually installed synaptic doesn't know which site to check.


Sometimes programs that come with tar.gz have an executable inside them, so you didn't compile them yourself. To compile you have to go thru the command line so perhaps you still got a chance in synaptic

---

### Post by mbarak on 2008-05-14
try running
```
sudo make uninstall
```
in the directory of the source code (i.e. in the same directory as ./configure)
if the developer included a way to uninstall the program, it doesn't matter what you put as your PATH, it will remove the program completely.

if that isn't an option, and you didn't supply a PATH, the default install directory for locally compiled and installed files (i.e. with .tar.gz packages) is /usr/local/
search through each of those folders and remove all folders with the name of the program

this is yet another reason to use the package manager (i.e. - repositories or .deb files)

---

