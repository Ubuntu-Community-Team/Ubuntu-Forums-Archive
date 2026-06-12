---
title: "Github Installation Instructions"
date: 2014-10-26
forum: New to Ubuntu
---

### Post by darb78 on 2014-10-26
I have downloaded files from a github repository, but being new don't know how to actually install these files so that they work. I'm sure there is a post that provides these instructions but I have not been able to find it. Can someone point me in the right direction? 

I'm trying to install drivers to provide better control of my MacBook Pro trackpad as found [here]("http://ubuntuforums.org/showthread.php?t=1730361&p=10682051#post10682051"). 

Thanks!

---

### Post by TheFu on 2014-10-27
Github is normally a place for source code and almost always the files must be compiled into either program or object or library before they can be used.

In the 30 seconds I spent looking at the source code, I didn't see an easily found set of instructions - normally these would be inside a README or INSTALL file at the head of the directory structure.  The driver files ARE all C code, so you will definitely need to build them with a compiler.  

The github page has an issue tracker. After carefully reading all the text files there, if you cannot figure out how to build the driver, I'd open a issue asking for clearer instructions there. Hopefully they really want to help.  You can also find other projects with kernel drivers to review their installation instructions. Normally, these things are very similar.

---

### Post by Alireza_Zamani on 2014-10-27
> **TheFu said:**
> Github is normally a place for source code and almost always the files must be compiled into either program or object or library before they can be used.

In the 30 seconds I spent looking at the source code, I didn't see an easily found set of instructions - normally these would be inside a README or INSTALL file at the head of the directory structure.  The driver files ARE all C code, so you will definitely need to build them with a compiler.  

The github page has an issue tracker. After carefully reading all the text files there, if you cannot figure out how to build the driver, I'd open a issue asking for clearer instructions there. Hopefully they really want to help.  You can also find other projects with kernel drivers to review their installation instructions. Normally, these things are very similar.

;) yes

---

### Post by darb78 on 2014-10-28
Thanks, I posted a request for installation instructions as per your suggestions.

---

### Post by darb78 on 2014-10-28
This is the response I recieved: 

> The first place to look is your distro's package manager. There are  packages for Arch, Debian, Ubuntu, Gentoo, and Fedora. I maintain the  Gentoo package but the rest are maintained by others.


  And if that doesn't work you can build it from source. It's a standard autoconf/automake package.



I'm not entirely sure what to do with it.

---

### Post by TheFu on 2014-10-28
So the package has been build for Ubuntu - I'd use that either from the Canonical repos or from a known-good PPA.

If you don't know the package name, perhaps searching in **Synaptic** will have it jump out?  Software Center hides lots of the available packages.
Or there is always the Apple-Hardware sub-forum here.

If you need to build it from source, which should be avoided, automake is fairly easy to use for C programmers. I'm certain you can figure it out from the vast number of guides on the internet. This is NOT ubuntu specific. [http://mij.oltrelinux.com/devel/autoconf-automake/](http://mij.oltrelinux.com/devel/autoconf-automake/) was the first result I found - seems fairly complete.

---

### Post by chili555 on 2014-10-28
I suggest you look in Synaptic for:  *xserver-xorg-input-mtrack*.

---

