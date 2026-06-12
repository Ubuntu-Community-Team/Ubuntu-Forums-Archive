---
title: "An emacs that you might want to lick!"
date: 2006-09-14
forum: Outdated Tutorials &amp; Tips
---

### Post by nurv on 2006-09-14
Hi there!

Do you like this ?

[IMG]http://static.flickr.com/92/243028848_d29bddaeb8_o.png[/IMG]

Just download this zip file, extract him, and run:
```
sudo sh emacs-install.sh
```

It might throw some erros. If so say something and I will correct it.

To change the font, you have to edit ~/.Xdefaults file, and then run:
```
xrdb ~/.Xdefaults
```

(Emacs Color Theme provided by [color-theme.el]("http://www.emacswiki.org/cgi-bin/wiki?ColorTheme") [Dark Laptop], Instructions for ruby on rails suport within emacs available at [Ruby on Rails wiki]("http://wiki.rubyonrails.com"). My font is "Luxi Mono-10". Luxi fonts are Fedora standard, but are available for Ubuntu with packages *ttf-xfree86-nonfree*, *t1-xfree86-nonfree*, and *xfonts-scalable*)

Namaste!

---

### Post by thelocust on 2006-09-14
this doesnt work for me i get  
```
emacs-install.sh: line 3: cvs: command not found
emacs-install.sh: line 4: cd: emacs: No such file or directory
emacs-install.sh: line 6: ./configure: No such file or directory
emacs-install.sh: line 7: make: command not found emacs-install.sh:
line 8: cd: lisp: No such file or directory emacs-install.sh: line 9: make:
command not found emacs-install.sh: line 10: make: command not
found emacs-install.sh: line 12: make: command not found
emacs-install.sh: line 13: make: command not found emacs-install.sh:
line 14: cd: etc/images/: No such file or directory tar:
../../../emacs-tango.tgz: Cannot open: No such file or directory tar:
Error is not recoverable: exiting now tar: Child returned status 2 tar:
Error exit delayed from previous errors emacs-install.sh: line 17: make:
command not found xrdb:  "Emacs.font" on line 2 overrides entry on
line 1 Done! To run emacs you must run it with
'--enable-font-backend'
```

---

### Post by nurv on 2006-09-14
You must, at least have build-essencial and cvs installed to compile emacs. However I would say that you may need more packages. Try installing *build-essencial* and *cvs*. If throws something at you, say something.

---

### Post by pufuwozu on 2006-09-15
> **nurv said:**
> You must, at least have build-essencial and cvs installed to compile emacs. However I would say that you may need more packages. Try installing *build-essencial* and *cvs*. If throws something at you, say something.

It's actually spelt '*build-essential*'.

---

### Post by Eigenwert on 2006-09-15
I'm having a problems with this. None of the lisp functions that I installed seem to work with this (like html-helper-mode or php-mode, etc.) After poking around a bit, I think this is an issure with load-path. I followed this [http://lists.gnu.org/archive/html/help-gnu-emacs/2003-07/msg00504.html]("http://lists.gnu.org/archive/html/help-gnu-emacs/2003-07/msg00504.html") but it still doesn't want to work. 
Any suggestions?

Thnx,

EW

---

### Post by nurv on 2006-09-15
[QUOTE=Eigenwert]I'm having a problems with this. None of the lisp functions that I installed seem to work with this (like html-helper-mode or php-mode, etc.) After poking around a bit, I think this is an issure with load-path. I followed this [http://lists.gnu.org/archive/html/he.../msg00504.html](http://lists.gnu.org/archive/html/he.../msg00504.html) but it still doesn't want to work. 
Any suggestions?[/QUOTE]

Strange... I have php-mode, slime and a bunch of other elisp thinks being loaded at startup and still runs after I compiled it. Are you loading a .emacs bytecompiled or interperted? It may be because something changed inside emacs VM. It also could be because your .el files are in some folder that older versions of emacs would search. Try creating your own folder of elisp files and inform emacs of its presence.

---

### Post by Eigenwert on 2006-09-15
Thanks for the quick response.

Okay, so I've been messing around with this all day. I've been able to compare with my old hard drive where I just had emacs21 installed, and none of the elisp files are in the same place, and some are even missing. I was thinking of starting over with a clean install. How do I go about wiping this from my system?

EW

---

### Post by Zed on 2006-09-20
I don't think there is any good way to uninstall it -- that's the danger of using 'make install' with things built from source. Unfortunately, [checkinstall](http://ubuntuforums.org/archive/index.php/t-2356.html) didn't work with this for me.

After some wrestling with this, I found it worked with these dependencies installed first:

```

sudo apt-get install build-essential cvs libncurses5-dev libgtk2.0-dev libxt-dev libxaw7-dev

```

(I'm not absolutely positive the last two are necessary.)

This isn't going to play well with the rest of the stuff in the repositories, though, 'cause it's a development version of Emacs 23.0, instead of Emacs 21 in the Ubuntu emacs packages and 22.0.50 in the emacs-snapshot packages. This emacs won't find .el packages installed conventionally.

---

### Post by Zed on 2006-09-20
After much more futzing, I got checkinstall to work, mostly. For reasons unknown, sometimes it bundles the elisp, sometimes it doesn't. And I had to create several directories by hand. And one thing that's really weird: the font size I get is a couple of points smaller than the one I specify.

After more investigation, I realize now it would be possible to build a .deb that played well with the repositories -- emacs in debian is organized around the idea of having multiple flavors, and this could be just one more.

---

### Post by bodhi.zazen on 2006-10-11
This has been added to the Ubuntu wiki:

[Colorize Emacs](http://doc.gwos.org/index.php/ColorizeEmacs)

---

### Post by elektronaut on 2006-11-28
> **Zed said:**
> I don't think there is any good way to uninstall it -- that's the danger of using 'make install' with things built from source.
I think this should be sufficient (supposing you are in the directory with the downloaded install script):
```
$ cd emacs/
$ sudo make uninstall
```
That's the purpose of an uninstall directive in a makefile, or did I get something wrong?

---

### Post by elektronaut on 2006-11-28
Before reinstalling from the repositories, I'd like to get rid of unnecessary emacs files on the disk. I still have these directories with emacs stuff:
```
/var/lib/dpkg/alternatives/emacs
/var/lib/dpkg/info/
/var/lib/emacsen-common/
/var/cache/apt/archives/
/var/cache/dictionaries-common/
/etc/emacs/
/etc/emacs-snapshot/
/etc/emacs21/
/etc/emacs-extra/
/usr/share/doc/
/usr/share/emacs/
/usr/share/mime/text/
/usr/share/app-install/
/usr/share/gtkhtml-3.8/
/usr/share/guile/
/usr/lib/emacsen-common/
/usr/libexec/emacs
/usr/var/games/emacs/
```
Which of these directories can I simply delete?

---

### Post by Jengu on 2006-11-30
My icons are definitely not very lickable, take a look:

[IMG]http://img169.imageshack.us/img169/1065/snapshot1xq5.png[/IMG]

Anybody have any idea how to fix this? The font's look nice and it's using gtk, but no idea why the icons are black and white. Emacs is the only app with this problem. I followed this guide right after upgrading to Edgy (I'm on Kubuntu) so I'm not sure if it's something this guide did or something the upgrade did. In any case, any ideas for a fix?

---

### Post by nereid on 2006-12-02
Did you get a CVS version or did you install the emacs-snapshot-gtk package? I'm also on Kubuntu and everything is fine here using the emacs-snapshot-gtk package.

---

### Post by elektronaut on 2006-12-03
> **nereid said:**
> Did you get a CVS version or did you install the emacs-snapshot-gtk package? I'm also on Kubuntu and everything is fine here using the emacs-snapshot-gtk package.

Jengu must be using the cvs version, looking at the version number and date.
How does your emacs-snapshot-gtk package look like? Mine looks like this on Gnome and XFCE: 

[IMG]http://img377.imageshack.us/img377/4910/ildschirmfotoemacssnapscu4.png[/IMG]

The colors are different, I guess it should be a black background by default, or?

---

### Post by Jengu on 2006-12-03
I'm using the guide from this thread's script -- which downloads and installs the cvs version. emacs-snapshot-gtk doesn't have the nice fonts, which I thought was the whole reason for this thread? :P

---

### Post by Dalipay on 2006-12-06
Hello nurv. I followed the steps you gave in installing pretty-emacs package.
After installation, I tried to launch emacs both from the menu and through the command line...It failed to launch. In the command line, it says:
No fonts match Monospace-10. I edited .Xdefaults and tried Luxi Mono-10. Still no fonts match Luxi Mono, and failed to launch emacs.

Pardon me for the question: What should I do? I don't know what to do. Thanks.

---

### Post by elektronaut on 2006-12-06
> **Dalipay said:**
> Hello nurv. I followed the steps you gave in installing pretty-emacs package.
After installation, I tried to launch emacs both from the menu and through the command line...It failed to launch. In the command line, it says:
No fonts match Monospace-10. I edited .Xdefaults and tried Luxi Mono-10. Still no fonts match Luxi Mono, and failed to launch emacs.

Pardon me for the question: What should I do? I don't know what to do. Thanks.
I'm having the same problems. [Look here for my thread](http://ubuntuforums.org/showthread.php?t=308768) about this.

---

### Post by Dalipay on 2006-12-06
Thanks for the reply. I changed the font. My problem now is that there is no change in the foreground color and background color of emacs. The pretty-emacs package did not take effect? How should I solve this? :-D

---

