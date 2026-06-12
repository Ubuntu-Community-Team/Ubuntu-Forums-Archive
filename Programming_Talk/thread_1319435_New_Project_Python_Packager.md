---
title: "New Project: Python Packager"
date: 2009-11-08
forum: Programming Talk
---

### Post by Jacks0n on 2009-11-08
Hey everyone!

I just want to announce a new project I started: [Python Packager]("http://python-packager.com") ([http://python-packager.com]("http://python-packager.com")).

It's a web service where you upload your Python program (.py/.zip/.tar.gz files) and it'll make various packages for Windows and Linux.

Linux - Single file, portable directory, DEB/RPM packages
Windows - Single exe, portable directory, Windows installer
Source code analysis - Using pylint
Source code documentation - Using pydoc
Source code with license prepended to every file (if you want)

It attempts to make packaging Python programs easy, and in theory, "just work". It's currently in beta/alpha so if your program doesn't properly get packaged, send me an email - [email]jackson@jacksonc.com[/email]. It was started because I would often have to use the existing tools (eg. py2exe, pyinstaller) on each platform for each type of binary. Then I'd have custom scripts to make DEB/RPM packages, and a Windows installer. I wanted something easier, and this attempts to make this process as easy as possible.

Anyway, it's open source (available at [http://launchpad.net/python-packager](http://launchpad.net/python-packager)), and so check it out at [http://python-packager.com](http://python-packager.com). Oh, and it's free to use!


Jackson

---

### Post by Can+~ on 2009-11-08
Sounds impressive. Only one question though:

Why do it on server side instead of downloading an application to do it locally?

---

### Post by Jacks0n on 2009-11-08
> **Can+~ said:**
> Sounds impressive. Only one question though:

Why do it on server side instead of downloading an application to do it locally?

I tried that originally, but each platform's binaries need to be packaged on their own platform. eg. Windows packages on Windows, Linux packaged on Linux. So I figured server side would be easiest. So at least this way Linux users can package their app for Windows users without having to use Windows, and visa-versa. Plus if it gains any interest, and seems to work most of the time a Mac version (.app/.dmg) could also be done too.

I love working with Python, but always wished packaging up a Python program for average people would be easier. So this is an *attempt* to do this.


Jackson

---

### Post by Danielkida on 2009-11-30
This is exactly what i've been looking for!

Normally If wan't to show someone something ive been working on I have to tell them to install python..then install the libraries...and they're usually bored and have given up by this point.

---

### Post by -grubby on 2009-11-30
[s]Please have my children[/s] This is going to be very useful for me.

---

### Post by ahmatti on 2009-12-01
Looks very interesting, I'm going to try it straight away! At least for the Mac version would be very useful :)

---

### Post by Jacks0n on 2009-12-02
Thanks Guys, that's great to hear! Yeah that's the idea, basically you can send someone a single file and they can double click on it and it'll "just work" without having to install Python.

A Mac version would be good, I'm still trying to figure out how to do it. The build server runs on Linux (Ubuntu!), and uses Wine to build the Windows version. So I'd have to have some way to run the Mac Python version on Linux.

Also if there's ever any problems/suggestions, email me! jackson 'at' jacksonc.com. There's still bugs that need ironing out.


Jackson

---

### Post by nvteighen on 2009-12-02
It seems you've found a niche. I'll test your packager and tell you my impressions. But the concept (which is the important thing) is really innovative and has potential.

Congrats and good luck!! :KS

P.S.: You meant [https://launchpad.**net**/python-packager]("https://launchpad.net/python-packager") :p

---

### Post by escapee on 2009-12-02
This is pretty brilliant.  It definitely has a lot of potential and I wish you the best of luck!

---

### Post by Jacks0n on 2009-12-06
Thanks guys, that's great to hear. I just got back from holidays so  the project should start improving a lot more soon. I'm a uni student currently on holidays (summer break). Plus the service should be quicker now (~ 20 minutes) since it isn't being run over dial-up in a hotel room :P.

Jackson

---

