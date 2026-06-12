---
title: "Mono Problem with Labels and Text in 9.10"
date: 2009-10-30
forum: Programming Talk
---

### Post by weaver4 on 2009-10-30
I wrote a very simple program using Visual Studio (on my WinXP box) that simply had a button on a form that moved text to a textbox when it was pressed.

I moved the exe file to Ubuntu 9.10 and ran it and the Window showed up but the button label was missing.  No text shows up on any control.

I did install libmono-winform* and freetype from synaptic.

This was working with Ubuntu 9.04

Any ideas?

---

### Post by directhex on 2009-10-30
Could it be something as simple as the font?

---

### Post by The Bard sRc on 2009-10-31
I'm having the same problem as well. it had been working fine previously in 9.04, after a reinstall with 9.10 though, blank menus, button labels, and tooltips

---

### Post by weaver4 on 2009-10-31
I tried common fonts, plus you would expect that Mono would give an error if it could not find a font.

---

### Post by directhex on 2009-10-31
Can you post a screenshot? Or, even better, the assembly?

---

### Post by weaver4 on 2009-10-31
Can't figure out how to paste a picture here.  But It is a simple form with a TextBox and two buttons.  The Text in the TextBox  shows up, but the two buttons are completely blank; no text in them.

---

### Post by The Bard sRc on 2009-10-31
here's how one of the things I use looks (ehh [http://castletilemaped.svn.sourceforge.net](http://castletilemaped.svn.sourceforge.net) if you want the code) :

[http://img141.imageshack.us/img141/2238/screenshot1mj.png](http://img141.imageshack.us/img141/2238/screenshot1mj.png)

it's supposed to look like this: [http://img22.imageshack.us/img22/6042/35006732.jpg](http://img22.imageshack.us/img22/6042/35006732.jpg)

but that's only one example, all of the .NET assemblies I've tried do it. had been working just fine in 9.04

---

### Post by Paedie on 2009-10-31
I have the same problem, there are no error message, I just get the program without the text.

---

### Post by directhex on 2009-10-31
Oh. Hrm... that's odd. I don't think it's Mono itself, as the same packages on Jaunty don't have that issue - probably one of the X libraries has changed & Mono doesn't deal with it

---

### Post by weaver4 on 2009-10-31
I believe mono in 9.04 was version 2.0 and mono in 9.10 is 2.5.

So mono has changed.

---

### Post by directhex on 2009-10-31
> **weaver4 said:**
> I believe mono in 9.04 was version 2.0 and mono in 9.10 is 2.5.

So mono has changed.

2.4.2.3

And I was running backports of those packages for months.

---

### Post by weaver4 on 2009-11-01
So you were using mono 2.4.2.3 on Ubuntu 9.04 and did not see this problem?  

Were you running a program that uses the windows forms library.  The reason I ask is that I tried F-Spot.exe under mono in Ubuntu 9.10 and it did not have a problem, but I think it uses GDI for its graphics.

Thanks for correcting my version info.

---

### Post by directhex on 2009-11-01
> **weaver4 said:**
> So you were using mono 2.4.2.3 on Ubuntu 9.04 and did not see this problem?  

Were you running a program that uses the windows forms library.  The reason I ask is that I tried F-Spot.exe under mono in Ubuntu 9.10 and it did not have a problem, but I think it uses GDI for its graphics.

Thanks for correcting my version info.

Yes, I routinely use a winforms app to run comparisons between assembly versions, so winforms was tested (and 2.4.2.3 is fine in Debian)

It's something specific to Ubuntu 9.10, and I don't know what

---

### Post by directhex on 2009-11-02
Not as clear-cut as I thought - works fine on this (Karmic AMD64) PC, but not my (Karmic AMD64) laptop

What graphics driver are you using?

---

### Post by geekabit on 2009-11-02
I made a minimal example to show the problem.

debian squeeze / sid i386 -> no text
ubuntu 9.04 i386 -> text
ubuntu 9.10 i386 -> no text
winxp i386 -> text

---

### Post by geekabit on 2009-11-02
It seems to be a video driver problem. More info on Novell's bugtracker: [https://bugzilla.novell.com/show_bug.cgi?id=549882](https://bugzilla.novell.com/show_bug.cgi?id=549882)

---

### Post by directhex on 2009-11-02
> **geekabit said:**
> It seems to be a video driver problem. More info on Novell's bugtracker: [https://bugzilla.novell.com/show_bug.cgi?id=549882](https://bugzilla.novell.com/show_bug.cgi?id=549882)

Yup yup, the laptop which misbehaves is Intel - My desktops (and the desktop of a Debian guy I asked to test) are NVIDIA

---

### Post by geekabit on 2009-11-02
Same thing here. My desktop has an Intel 82915G/GV/910GL controller, my laptop has an Intel 915GM/GMS/910GML controller. Both have the same problem.
xserver-xorg-video-intel 2:2.6.3-0ubuntu9.3 (Ubuntu 9.04) works, xserver-xorg-video-intel 2:2.9.0-1ubuntu2 (Ubuntu 9.10) does not work.
Hopefully Ubuntu will have an updated driver soon.

---

### Post by weaver4 on 2009-11-02
It is my understanding from Bugzilla that xserver-xorg-video-intel 2:2.9.1 will work and you can download it here:

[http://intellinuxgraphics.org/](http://intellinuxgraphics.org/)

But the installation instructions here do not work:

[http://intellinuxgraphics.org/install.html](http://intellinuxgraphics.org/install.html)

[I]If these packages are available, building should be as simple as:
$ ./autogen
$ make
$ sudo -c "make install"[/I]

In the first step there is no file "autogen" in the package.

Can someone help me figure out how to install this package?

The README found in the package is no help.

Thanks

---

### Post by directhex on 2009-11-02
> **weaver4 said:**
> It is my understanding from Bugzilla that xserver-xorg-video-intel 2:2.9.1 will work and you can download it here:

[http://intellinuxgraphics.org/](http://intellinuxgraphics.org/)

But the installation instructions here do not work:

[http://intellinuxgraphics.org/install.html](http://intellinuxgraphics.org/install.html)

[I]If these packages are available, building should be as simple as:
$ ./autogen
$ make
$ sudo -c "make install"[/I]

In the first step there is no file "autogen" in the package.

Can someone help me figure out how to install this package?

The README found in the package is no help.

Thanks

Anything with "make install" in it is highly likely to hose your system if you don't know exactly what you're doing. I'd wait a little - once the driver is in Lucid, then something can be done about Karmic. The bug relating to this issue is filed against the package

---

### Post by weaver4 on 2009-11-02
This is work related, either I have to get 9.10 working with mono or go back to 9.04.  I thought it would be easier to try this than go back.  I will cost me a full day to reinstall everything on 9.04.

---

### Post by The Bard sRc on 2009-11-02
oh goody, so it's another Intel related problem. this little Eee  is turning out to be a lot more pain than it's worth.

---

### Post by weaver4 on 2009-11-02
I found this very helpful; but I did have to reboot.

[http://www.nanowrimo.org/eng/node/3373197](http://www.nanowrimo.org/eng/node/3373197)

---

### Post by geekabit on 2009-11-03
Works for me. Thanks weaver4!

---

### Post by geekabit on 2009-11-03
I didn't have to reboot. Log out and log in seems to do the trick as well.

---

