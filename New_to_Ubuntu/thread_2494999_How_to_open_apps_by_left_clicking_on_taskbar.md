---
title: "How to open apps by left clicking on taskbar ?"
date: 2024-02-03
forum: New to Ubuntu
---

### Post by datraja on 2024-02-03
Hi , i recently decided to make a switch from windows 7 to lubuntu 18.04. I am running it on a virtual machine before making a complete sitch but I am facing some issues with customization already. 

In the integrated application launch and taskbar , I always have right click followed by "Raise" to open it. How can I do so by simply left clicking on the application I want to open ?

---

### Post by ajgreeny on 2024-02-03
Why did you choose Lubuntu 18,04?
It has already lost support unless you have already enabled the ESM support and Ubuntu-Pro.
It would have made a great deal more sense for you to use 22.04 which still has support, though don't forget Lubuntu receives only 3 years of support whereas Ubuntu has 5 years.

Unfortunately I can not recall enough about Lubuntu 18.04 which used the LXDE desktop so I'm unable to tell you much about using that DE and there is little point in doing so as it will no longer be available in newer versions of Lubuntu which started using the Lxqt desktop after 18,04.

As you are using a virtual system at present in order to familiarise yourself with Linux I suggest you look at other DE versions such as Ubuntu itself, Xubuntu, Kubuntu, Ubuntu Mate, etc, etc, and you may find another version with which you are happier; certainly some of these may be more similar to Windows 7.

I also recommend that you use the current Long Term Support (LTS) version, 22.04, of all of them and do not use an old version such as 18.04.

---

### Post by datraja on 2024-02-03
Thank you for your response. 
Update : The issue kind of fixed itself , i don't know how , but I was experimenting with taskbar settings and I don't know how I fixed it .
Well my PC is 32 bit , 2GB of RAM . I heard 18.04 is the last version that supports 32 bit systems so I decided to go along with that . With my fair bit of research before doing this experiment, what I found was that lubuntu is by far the most recommended OS to revive old PCs .

Do you have any other recommendations for Linux Distros which I can run in my machine ? 

Windows 7 SP 1 was not terrible on my PC , it was decent after a recent format of the C drive , but a few applications including ones I used for programming (VS code) were malfunctioning(XHR errors etc). On top of that , I am new to all of this. For the most part , I have seen accomplished developers always coding in the Linux environment which they recommend for a better experience and learning curve.

---

### Post by ajgreeny on 2024-02-03
There are no supported versions of any of the Ubuntu family any more for 32bit hardware so unfortunately you will need to look more widely.
Debian on which Ubuntu is based still does have 32bit OSs available but some people find it much more difficult to use than Ubuntu.  You may have no major difficulties if you try it.
Search more for 32bit Linux systems, and as an example have a look at
[https://www.debugpoint.com/32-bit-linux-distributions/](https://www.debugpoint.com/32-bit-linux-distributions/)
[https://www.makeuseof.com/linux-distros-with-32-bit-support/](https://www.makeuseof.com/linux-distros-with-32-bit-support/)

---

### Post by datraja on 2024-02-04
Thank you for all your efforts , I do want some more advice from you regarding the Linux operating system. Reading the manuals as well as using the terminal seems a bit too overwhelming with all the technical jargon , most of which I cannot understand. Can you suggest some good beginner friendly sources to understand linux from the basics?
For eg , I just tried to install something by sudo apt install , and it threw a bunch of errors regarding archives etc . I have decided to not make the switch from Windows until and unless I am reasonably comfortable with fixing all the errors regarding updates and stuff .

---

### Post by grahammechanical on 2024-02-04
> For eg , I just tried to install something by sudo apt install , and it threw a bunch of errors regarding archives etc .

When a version of Ubuntu (in your case, Lubuntu) reaches the end of its support life the archives/repositories are closed and moved to another address:

[http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/)

But remember two things. To access those repositories you need to edit a file called sources.list. The second thing to remember is that the packages/software in the repositories are not being upgraded any more.

So, that is why you are getting those errors.

Regards

---

### Post by Holger_Gehrke on 2024-02-04
The errors that 'sudo apt install ...' gave were probably due to 18.04 being out of support. The servers holding the packages for installation (the repositories) get cleaned up after a version of Ubuntu goes past end of support, so apt couldn't find what it was looking for.

In most cases you can get by in Ubuntu without using the command line. For example there are graphical tools for software installation (gnome-software, synaptic, discover, muon (on newer versions of Lubuntu)). Forums like this one often give help for fixing things from the command line because it's easier since the command line stays the same no matter what language you're using or what settings you've made to change the GUI to your tastes or what version of Ubuntu you're using.

There are manuals for the various flavours of Ubuntu online.[TABLE="width: 500"]
[TR]
[TD]Ubuntu[/TD]
[TD][https://help.ubuntu.com](https://help.ubuntu.com)[/TD]
[/TR]
[TR]
[TD]Kubuntu[/TD]
[TD][https://kubuntu.org/support/](https://kubuntu.org/support/) (link to pdf manual on github)[/TD]
[/TR]
[TR]
[TD]Xubuntu[/TD]
[TD][https://xubuntu.github.io/xubuntu-docs/user/C/index.html](https://xubuntu.github.io/xubuntu-docs/user/C/index.html)[/TD]
[/TR]
[TR]
[TD]Lubuntu[/TD]
[TD][URL="https://manual.lubuntu.me/stable/index.html"]https://manual.lubuntu.me/stable/index.html
[/URL][/TD]
[/TR]
[/TABLE]

A good resource for the command line is [www.linuxcommand.org]("http://www.linuxcommand.org"). Among a lot of other good stuff you'll find free PDF files of 'The Linux Command Line' by William Shotts and its sequel 'Adventures with the Linux Command Line'. These books are not distribution specific, so things like software installation or changing GUI settings from the CLI are not covered (although it does give an overview of installing programs from source code).

Holger

---

### Post by him610 on 2024-02-06
> Well my PC is 32 bit , 2GB of RAM .
There other distros that still support 32 bit hardware, Debian being one of them. All of the *buntus are based on Debian.

---

