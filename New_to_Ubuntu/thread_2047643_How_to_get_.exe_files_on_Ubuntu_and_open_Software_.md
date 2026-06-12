---
title: "How to get .exe files on Ubuntu and open Software Sources?"
date: 2012-08-25
forum: New to Ubuntu
---

### Post by confu on 2012-08-25
I am completely new to this system and need some help. I know there is a way to download a program to have the ability to download .exe files, but I don't know how and everywhere I go to find out says I need to open.my Software Sources, andrytime I try to run it, it says that I need to run it with administrative powers and should run it with kdesudo. I REALLY NEED HELP, PLEASE!

---

### Post by Wim Sturkenboom on 2012-08-25
You can download exe files from the web as you used to do under windows. To run them however, you need a program like *wine*, that is in the repositories. Your success rate varies. See [http://appdb.winehq.org/](http://appdb.winehq.org/) for ratings how well certain software works under wine.

To be honest, if you want to run windows applications, use windows.

---

### Post by 2F4U on 2012-08-25
No offense from my side, but you should start by reading some documentation about Ubuntu before doing anything else. Probably avoids some trouble.

[https://help.ubuntu.com/12.04/ubuntu-help/index.html](https://help.ubuntu.com/12.04/ubuntu-help/index.html)

You cannot run .exe files (Windows programs) natively on a Linux system. You can use Wine if you really need a particular program

[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

---

### Post by Bucky Ball on 2012-08-25
Welcome.

You might want to go for a dual-boot. Some Win programs work great with Wine, others not good, others not at all. Check here:

[http://appdb.winehq.org/](http://appdb.winehq.org/)

Ubuntu not a slip-in replacement for Windows. You might find this of interest:

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

;)

---

### Post by Lars Noodén on 2012-08-25
Others have pointed out [wine](https://help.ubuntu.com/community/Wine) which works great for some Windows programs but not all.  The WINE project keeps a [database of how well programs run under WINE](http://appdb.winehq.org/), so you can check there first.

But rather than run Windows programs on your nice Ubuntu system, you can look for native packages.  Nearly all that is worth running can already be found in the package repositories and those are accessible either via Synaptic or the Software Center.  

What is it that you are trying to do?  Chances are there is a good native app already for that.

---

### Post by The Cog on 2012-08-25
Confu: Can you explain exactly what you are trying to do? 

Linux is a different operating system to windows. In general, you run windows programs on windows, and linux programs on linux. Windows programs are generally known as .exe files, but linux programs are not - they are generally referred to as packages.

Are you trying to install linux programs for linux? If so, then the software centre is the place to go to do that.

Are you trying to get windows programs (exes) to run on Linux? If so, there is a package called wine that allows windows programs to run on linux, with varying degrees of success. You can install wine from the software centre, and will then have to download and run whatever windows exe is is you want to run.

Which program do you want to install and run? The more you can tell us, the better the help we can give you.

---

### Post by s1baker on 2012-08-25
I use VirtualBox to run a Windows programs that I need for work. 
Other than that program, I could trashcan Windows.

---

### Post by Mark Phelps on 2012-08-26
Sorry to be the bearer of bad news ... but if you installed Ubuntu primarily to run MS Windows apps, then you're in for a very frustrating experience.

While Wine does run SOME apps well, in many cases, the apps run poorly or not at all.  You were given the website to check to see how well particular apps, and their versions, work with Wine.

IF you're going to rely on MS Windows apps on a daily basis, you're really better off staying with MS Windows.

Remember, Ubuntu is not a free VERSION of MS Windows; it's a free ALTERNATIVE to MS Windows.

---

### Post by Bucky Ball on 2012-08-26
@ MarkPhelps: +1

---

