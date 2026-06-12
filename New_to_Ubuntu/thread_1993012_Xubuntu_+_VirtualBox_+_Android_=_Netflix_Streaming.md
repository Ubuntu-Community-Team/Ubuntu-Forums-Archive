---
title: "Xubuntu + VirtualBox + Android = Netflix Streaming?"
date: 2012-06-01
forum: New to Ubuntu
---

### Post by lhb1142 on 2012-06-01
I have a ZaReason Teo Netbook which has an Intel Atom processor. I am running Xubuntu 12.04LTS. With this system I cannot watch Netflix streaming movies.

If I were to install VirtualBox and, within it, install the Android operating system, would I then be able to watch Netflix with this computer?

If anyone **truly** **_knows_** the answer to this question, would he/she please reply?

And, if this is a viable solution, would that person direct me to a site from which I could download and install Android within VirtualBox?

I am not a particularly sophisticated user of Linux. :(

I thank anyone who can be of help in this matter.

Lawrence H. Bulk

P.S. I do not like tablet computers (I own a Dell Streak 7) nor do I like the Android operating system. But if Android could be made to work on my netbook I would use it only for watching Netflix movies.

---

### Post by QIII on 2012-06-01
If google costs you nothing, it is worth a try.  But don't hold your breath.

1.  Your Atom processor will be running your host OS, which will be running both a program (Virtualbox) and another OS on it.  This will tax both your processor and the memory, since some of your memory will be commuted to the guest OS.

2.  Your guest OS will not be running directly on your hardware, but on a hardware abstraction layer.  This generally means performance takes a hit, particularly with graphics.  That said, I have gotten some marginally acceptable streaming performance (not great) using Windows as a guest OS.

Give it a try if it's free.  You might end up being able to answer this definitively for the next person that asks.

---

### Post by forrestcupp on 2012-06-01
[Here is a blog article](http://www.sysprobs.com/download-pre-installed-virtualbox-image-of-android-4-ice-cream-sandwich-run-it-on-intel-windows-7-pc) that explains how to download a preinstalled VirtualBox image of Android ICS and get it working in VirtualBox. The blog is for doing it in Windows 7, but VirtualBox is VirtualBox, and it will work in Xubuntu, too.

I can't verify how well it will work with Netflix, but the only thing you'll be out is your time. I tried watching Netflix in a Windows 7 virtual machine. It was not as smooth as watching it from a real Win7 install, but it did work. I'd say you'd probably get worse performance on a netbook, but maybe Android is light enough that it will work better than Win7 in a VM.

Let us know how well it works, because this could be a good, free solution for people.

---

### Post by TVTrukChik on 2012-06-10
I took a stab at this... the blog article linked above has a link that supposedly goes to a VDI image, but I got a page not found error.  I did find an ISO at [http://www.android-x86.org/]("http://www.android-x86.org/") that I was able to install in VirtualBox.  

It does run, but the screen image is sideways, my mouse doesn't work (have to navigate by keyboard), and I can't make the image fill my monitor.  Maybe someone else can do better.

---

