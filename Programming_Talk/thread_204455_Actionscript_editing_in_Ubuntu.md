---
title: "Actionscript editing in Ubuntu"
date: 2006-06-27
forum: Programming Talk
---

### Post by evil_elman on 2006-06-27
Hello everybody...

I'm a Flash coder and I've just started dual-booting Linux on my laptop. I've still got Flash 8 lingering on the Windows partition but I have hopes to be able to remove it permanently in the near future.

My problem is that I can't find any Actionscript editors compiled and ready for use in Linux that would be able to use MTASC. 

* SE|PY is around and made in Python. However I can't get the source code to work since I'm just to inexperienced in that area.
* Eclipse and some 'Flash developer plugin' seemed promising. Everything is compiled and ready to go except that all instructions I could find apparently referred to old versions and was useless.
* F4L doesn't seem stable enough.
* There are other editors available, yes. But I would like to link it to MTASC for compiling.

Someone would really make my day by packaging SE|PY and adding it to the 
repositories... 

[COLOR="White"]**Search keywords:** Flash, Actionscript, Macromedia, Adobe, SEPY, SE|PY, Eclipse, F4L, MTASC[/COLOR]

---

### Post by DirtDawg on 2006-06-28
I'm sorry I cannot immediatly help with your issue, but I would like to suggest you explain what problems you are having when you attempt to compile SEPY. If inexperience is really the problem, you've come to the right place. Someone will likely be willing and able to help.

---

### Post by DirtDawg on 2006-06-28
I did some digging after posting. I'm not sure I'm on the right track with this, since I don't know what I'm talking about, but it seems you can install MTASC as a [stand alone package]("http://packages.ubuntu.com/edgy/devel/mtasc"). Once installed, I beleive you can run it from the command line which would free you up to use whatever editor is to your liking.

Or you could just try compiling SEPY like I mentioned before. A little time and some help from these fine forum folks will likely cure what ails you.

---

### Post by el_itur on 2007-01-31
I was trying to compile SEPY from source. following the [path of the master]("http://www.sephiroth.it/phpBB/showthread.php?t=8019") 
But I still have some issues:
Edit: I was using python 2.4
now (2.5) it says this :```

gandalf-desktop:~/sepy$ python2.5 setup.py 
Traceback (most recent call last):
  File "setup.py", line 10, in <module>
    import core.ui.dialogs.about as About
  File "/home/gandalf/sepy/core/__init__.py", line 12, in <module>
    import config
  File "/home/gandalf/sepy/core/config/__init__.py", line 5, in <module>
    from apiloader import *
  File "/home/gandalf/sepy/core/config/apiloader.py", line 6, in <module>
    import wx, re
ImportError: No module named wx

```

But I have wxPython installed (2.8)

AGHHH, I will never make it work

Any help is welcome

---

### Post by Vevmesteren on 2007-02-18
first off, I am running Flash8 with Wine. But am having some serious issues in installing a working AS editor as well. SEPY, FDT and ASDT all have failed me thus far. If you should find anything. Please let me know...thanks

V

---

### Post by Vevmesteren on 2007-04-02
Well it looks like I hit Send a bit to fast there. ASDT is back! ASDT is alive, and let me tell you, it is well! I just installed the last [ASDT]("http://aseclipseplugin.sourceforge.net/wordpress/?p=6")  and I am nothing short of amazed. Reading the [WIKI]("http://asdt.relivethefuture.com/wiki/doku.php") exites me even more so. [Check it out...]("http://www.asdt.org")

---

### Post by Vevmesteren on 2007-04-25
> **Vevmesteren said:**
> first off, I am running Flash8 with Wine. But am having some serious issues in installing a working AS editor as well. SEPY, FDT and ASDT all have failed me thus far. If you should find anything. Please let me know...thanks

V

I have now bought FDT and it is running smoothly, abnd with the 2.0 update looming (AS3 included) there great things to come from this editor...as of yet, the current version (1.5) is running smoothly, I am compiling with MTASC no problem. Some AS related issues regarding MTASC, trouble running FuseKit, but I am getting into non-Ubuntu related territory here...

so go run get [FDT]("http://fdt.powerflasher.com")

V

---

### Post by delfick on 2007-08-10
is it possible to give actionscript syntax highlighting to vim or gedit or some text editor like that ?? :D

---

### Post by Vevmesteren on 2007-08-11
have not seen any specific sheet for that. But honestly, Eclipse and ASDT are working perfectly fine, with directly integrated MTASC (or Flex for AS3 apps) you really do not need much else for Flashing ion Ubuntu. Add an Ajax plugin to that (personally I am using Aptana) and you got yourself a one-stop shop for Web Developement

V

---

### Post by RavUn on 2008-10-07
I don't know what else ActionScript could be used for, but does this allow us to create .swf files using AS?  I would like to create a FLV player that's a .swf file and am wondering if this would work.

---

