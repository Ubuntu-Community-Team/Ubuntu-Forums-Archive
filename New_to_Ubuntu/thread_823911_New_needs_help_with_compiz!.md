---
title: "New needs help with compiz!"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by ryangates13 on 2008-06-09
Hello all,

I am very new to ubuntu and am working my way around.  

I had compiz up and running and everything was good, I then added fusion and everything has done downhill. I no longer can see my toolbars and I am not able to move any of my windows they are all locked. I tried to remove compiz and start fresh without fusion and I am having no luck

Could anyone give me the code or best way to remove compiz, then reinstall. I am running ubuntu 8.04 hardy

Thanks! :)

---

### Post by Grishka on 2008-06-09
> **ryangates13 said:**
> Hello all,

I am very new to ubuntu and am working my way around.  

I had compiz up and running and everything was good, I then added fusion and everything has done downhill. I no longer can see my toolbars and I am not able to move any of my windows they are all locked. I tried to remove compiz and start fresh without fusion and I am having no luck

Could anyone give me the code or best way to remove compiz, then reinstall. I am running ubuntu 8.04 hardy

Thanks! :)

what do you mean by adding fusion? what exactly did you do? to remove compiz, enter this command in the terminal:
sudo aptitude remove compiz* libcompiz* libdeco* fusion-icon emerald python-compiz*
to reinstall, just change the "remove" bit to "install".

---

### Post by ryangates13 on 2008-06-09
I was going a little to fast yesterday and added a program, I though fusion was enhanced compiz, turns out I now can no longer move my windows or close them, its as if the windows are locked?

---

### Post by ryangates13 on 2008-06-09
I get this when running the following "script" sorry learning the terms.

Couldn't find any package whose name or description matched "compiz-git"
Couldn't find any package whose name or description matched "compiz-git-newest.tar.gz"
Couldn't find package "libcompiz*".  However, the following
packages contain "libcompiz*" in their name:
  libcompizconfig0 libcompizconfig0-dev 
Couldn't find package "libdeco*".  However, the following
packages contain "libdeco*" in their name:
  libdecibel-dev libdecoration0 libdecoration0-dev libdecibel0.6.0 
Couldn't find package "python-compiz*".  However, the following
packages contain "python-compiz*" in their name:
  python-compizconfig 
Couldn't find any package whose name or description matched "compiz-git"
Couldn't find any package whose name or description matched "compiz-git-newest.tar.gz"
Couldn't find package "libcompiz*".  However, the following
packages contain "libcompiz*" in their name:
  libcompizconfig0 libcompizconfig0-dev 
Couldn't find package "libdeco*".  However, the following
packages contain "libdeco*" in their name:
  libdecibel-dev libdecoration0 libdecoration0-dev libdecibel0.6.0 
Couldn't find package "python-compiz*".  However, the following
packages contain "python-compiz*" in their name:
  python-compizconfig 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
ryan@ryan-desktop:~$ sudo aptitude remove compiz* libcompiz* libdeco* fusion-icon emerald python-compiz*

---

### Post by Grishka on 2008-06-09
it looks like you've installed compiz in some non-standard way. pray tell your system version and how did you install compiz and that fusion thing. :) btw, compiz has been merged with beryl some time ago. the resulting project is called compiz-fusion. if that's what you tried to install, please state the exact method you used.

---

### Post by ryangates13 on 2008-06-10
I am so new to Linux and all I only wish I can remember how I installed it. I think I found a link to some code on the interweb and downloaded it.

I wish I could be more helpful to help the veterans work with my problem :)

Any help I could get in removing what I have and intalling a clean version would be greatly appreciated.   If you need to get anything of my system to help let me know.

Thanks!

---

### Post by ryangates13 on 2008-06-10
Anyone, right now I have the basic graphics on and would love some help to work with compiz. 

Thanks! :)

---

### Post by mgmiller on 2008-06-10
You said in your original post that you are running version 8.04.  If that is the case, compiz-fusion is installed by default.  If you have installed other versions and other things "willy nilly" off the "interweb", it may take longer to fix than is worth the time and effort.  If you have nothing of value on the system yet, the easiest way around this might be a clean install. 

After the install is done, make sure you have all the repositories enabled by clicking on System > Administration > Software Sources.

On the Ubuntu Software tab, make sure the first 4 choices are checked under Downloadable From the Internet. They are the choices ending with (main) (universe) (restricted) and (multiverse).

Click close and let it do it's thing.

Once you have done that, install the gui control interface for compiz-fusion by entering the following in a terminal (Applications > Accessories > Terminal)
```

sudo apt-get install simple-ccsm
```

Also add a bunch of codecs and java and flash by doing:
```
sudo apt-get install ubuntu-restricted-extras
```

To start playing with the effects for compiz-fusion, click on System > Preferences > Appearance.

Go to the Visual Effects tab.

By default, Normal is selected.  This has a few simple things turned on.  For lots of fun, click custom and then click the Preferences button next to it.  This will give you lots of choices that are not too confusing.

Once you have explored that for a while, if you really want to go crazy, click on System > Preferences > Advanced Desktop Effects Settings and all of compiz-fusion will be available for tweaking.

Assuming you have compatible hardware, compiz-fusion is enabled by default.  If it isn't, come back to these forums and ask questions before trying to download stuff off the internet.  In general, anything you need will be in all the trusted repositories and can be accessed through Add/Remove programs or Synaptic package manager. 

If you want more stuff enabled, like DVD movies and win32 codecs and etc. come back here and search the forums to get the package names and instructions for adding the multimedia repository at medibuntu.org.  

Remember, start all your software searches within ubuntu itself, not the web, until you really understand what you're doing.

Come back here for help, the price is right.

Welcome to ubuntu.

---

### Post by cardinals_fan on 2008-06-10
It sounds like you installed compiz-git, the development version of Compiz.

---

### Post by ryangates13 on 2008-06-11
Thank you all, a clean install it will be! I will be back with more info once I am done just to give an update.  

Thanks for your help!

---

### Post by ryangates13 on 2008-06-12
A nice new install, followed by the above directions and compiz-fusion is working like a charm.  Thanks again for your help!

---

### Post by mgmiller on 2008-06-12
:guitar:

You're welcome.

---

