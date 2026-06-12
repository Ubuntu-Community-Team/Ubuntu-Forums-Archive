---
title: "How do I install .exe files?"
date: 2008-09-06
forum: New to Ubuntu
---

### Post by Dracus124 on 2008-09-06
When I try to install various programs a screen pops up saying i need to choose an application to open it with. :confused:

I just switched to Ubuntu a few days and I like it better than vista and XP. I just need to learn how to install programs

---

### Post by ibizatunes on 2008-09-06
u need to install wines
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)
Only thing some app's dont work, you need to check first before install, because programs may not work as expected

[http://www.winehq.org/](http://www.winehq.org/)
Bottom left had side, there is a app's search function

---

### Post by diablo75 on 2008-09-06
Well, first thing you should know is that EXE files are intended to be run in a Windows environment.  However, if you install WINE, your EXE *might* work for you.

To install WINE (as well as a lot of other programs you may not know about yet) click Applications>Add/Remove Software (at the bottom).

Then search for "wine", check it off and click Apply to install it.

After Wine is installed, you can attempt to run an exe file just by double-clicking on it, but you can't be guaranteed that it will work.  You should consult the [Wine Applications Database]("http://appdb.winehq.org/") to see if the app you're trying to run is yet able to run on WINE.  Otherwise, you'll have to find a free alternative to whatever it is you're trying to run, or have to resort back to Windows on occasion.

---

### Post by cmay on 2008-09-06
you dont install exe files in ubuntu. it is a different system. you should find add remove programs in the menu and there you have acces to many programs that are safe and virus free and gets updated.

---

### Post by Bliepo32 on 2008-09-06
You cannot open exe's in Ubuntu. At least, not directly. You could try it using Wine. To install it, open the terminal, and type:

```
sudo apt-get install wine
```

Not all exe's will work in Wine. There are other programs like Wine, but they are a bit more commercial.

---

### Post by OutOfReach on 2008-09-06
.exe files cannot be executed in Ubuntu (Since .exe files are FOR Windows), natively, you'll need WINE or something similar to run the .exe, but be warned, WINE is not perfect there will be bugs/crashes, etc.

---

### Post by Miljet on 2008-09-06
Bottom line is that .exe programs are written for Windows and will not work on Ubuntu (or any other Linux.) As someone mentioned, some Windows applications can run on Linux, but has to run under a program called Wine.

Almost all Windows applications have an equal or better equivilent for Linux. All the applications that you will need are located in the Ubuntu repositories and are very easy to install.

Please have a look at this link
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by TWO on 2008-09-06
> **Dracus124 said:**
> When I try to install various programs a screen pops up saying i need to choose an application to open it with. :confused:

I just switched to Ubuntu a few days and I like it better than vista and XP. I just need to learn how to install programs

One thing to remember is that Ubuntu is very different to Windows. .exe files don't natively install under a Linux distribution, so as been stated, you will need to install Wine, which is a program that tries to enable .exe files to be installed under Linux. It isn't guaranteed to get your program to work and will often require a lot of tweaking before you get the program you wish to install to function correctly.

Unless these are applications that are essential to say, your field of work, I would suggest that you look for Linux alternatives to the programs that you are used to using under Windows.

Here are a couple of links with lists of such alternatives:
[http://www.linuxalt.com/](http://www.linuxalt.com/)
[http://www.linux.ie/newusers/alternatives.php](http://www.linux.ie/newusers/alternatives.php)
[http://linuxappfinder.com/alternatives](http://linuxappfinder.com/alternatives)

You can use the Synaptic Package Manager, or the Add/Remove Programs option under the Applications menu to search for new programs. The 'Add/Remove Programs' method is the easier option. 

The equivalent to the .exe under Ubuntu is the .deb file. It pretty much functions in the same way; installing a program without you having to do anything but click the file. The following web page is the official source of such files:

[http://www.getdeb.net/](http://www.getdeb.net/)

I must warn you in advance though not to always expect the same functionality as under Windows. Whilst it is indeed possible to perform most of the tasks that you able to do under Windows, do expect for there to be certain discrepancies with certain programs. And don't be put off if you find that some programs are not as aesthetically pleasing as you might expect. They can often still do the same job, but require a different approach to using them.

All in all, I'd say come with an open mind to using Ubuntu. It is the most user-friendly Linux distribution out there after all! :) (Well, in my biased opinion at least!)

TWO

---

### Post by hyper_ch on 2008-09-06
Do you think you can run Playstation3 games on Wii?
If not, why do you think you can run Windows programs on Linux?

---

### Post by cmay on 2008-09-06
and dont worry about missing programs there are 18.000 programs all the linux developers keep updated and functional at all times.
its all in packages at the same place so you dont have to install things from randomly selected places on the internet. so no need to worry about spyware advare or virus in linux. and i forgot to tell you good luck with your linux system. give it a few month and you are used to it by then.

---

### Post by Bölvaður on 2008-09-06
I can give you some help in installing programs and how it works, so you will never get confused in the future again.

First of all, most Macintosh users are used to the idea that they are not supposed to install windows (.exe) files. And also the other way round. This is because the exe files are made form long strings of 0 and 1 that are made only for the platform they are meant to be used on. But in theory it can be solved... like it has... read about it further down here.


**Installing in Ubuntu, the simple way (Add/Remove):**

In Ubuntu you can find a program labeled Add/Remove under Applications on your top left of your screen.
This program is the best tool to install most programs. It gives you a long list of programs you can install. Just mark a tick next to any program you want to install, or take away the tick of the programs you wish to uninstall.

You might want to put the "Show" drop down box to "All available applications", for the biggest list of all the programs you will be able to install.



**Installing in Ubuntu, the simple way (Synaptic Packet Manager):**

Exactly the same as before, but has more than just programs. It is more powerful tool than Add/Remove, and you might need it for installing codecs and stuff like flash and java.
You can find it under System -> Administration


**Installing in Ubuntu, the simple way (apt-get):**

This way is the simple way when getting help from others, from irc or forums like this one. You can just copy and paste the code from others in the terminal which might look like this :  sudo apt-get install flash-nonfree    to install, or   sudo apt-get purge firefox-3.0
It does exactly the same as the above ways, but is easier to tell others to do right over the internet.



**Installing in Ubuntu, the simple way (.deb):**

The ways listed above work the same was downloading the .deb file (install and automatic setup file for ubuntu and debian). You might find them on websites like getdeb.net (many programs can be downloaded from there) or the skype website.
You just save the .deb file onto your desktop and double click it. (Be sure it is from trusted source, add/remove, synaptic and apt-get is 99.9% failprove).



**Installing in Ubuntu, the risky way (Binaryfiles):**

Binaryfiles that either end with .bin or have no ending can be run by double clicking them or write ./ in front of the name of the file in terminal. Some binary files do not have been given permission to run (execute). So you have to right click on the file, go to Permissions and put a tick next to where it says Execute. Or write "chmod u+x filename" in terminal.


Exe files in dos are all binary files like these, but the thing about binary files is that they depend on OS to understand them 100%. And it is amazing if you would be able to run windows compiled binary files in Linux... but you can do it with program that took 15 years of development.


**Installing in Ubuntu, the strange way (Wine):**

You are able to install exe files from windows if you open them with Wine (which you can install from add/remove) but not all programs. You can find list of programs who have been found out that work with Wine [here]("http://appdb.winehq.org/")

This basically works like in windows but no guarantees that this works, because it is not native linux applications.



Then it is compiling from source by yourself, which is easy way to optimize the speed of your program (it is made by your computer, for your computer). But I'm not expecting you to be doing that, websites that let you do that normally have .txt files telling you how to do it any way :P

cheers.

---

### Post by men28 on 2008-09-06
It is right what people say: you have use Ubuntu replacements for windows programs. These programs you can use with another linuxes too.
For the beginning you need those programs:

Instead of Microsoft Office use Open Office. It is installed with Ubuntu. You don't need look for it in the internet and install it. Use OpenOffice.org Writer (may be Word Processor) instead of Microsoft Word. Look for it in Office menu. You can save .doc files with it and send those documents by email to windows users.

Instead of Microsoft Outlook use Evolution. It was installed with ubuntu too.

Instead of Internet Explorer web browser use Firefox.

Instead of Adobe Photoshop use GIMP.

Good luck with ubuntu.

---

### Post by Crafty Kisses on 2008-09-06
A lot of the programs have Linux alternatives, as stated above you can use Wine or the repositories.

---

### Post by zipperback on 2008-09-06
.exe files are executable files for the MS Windows operating system.
If you want to run a .exe file you will need to use WINE which provides a Windows compatibility layer for Linux.

Some applications will work fine with Wine, some applications don't work at all with Wine.

However, it would be best for you if you were to use applications which are native to Linux rather than trying to get a Windows application to run.

Please tell us what application it is that you would like to use, and we can tell you some options for the solutions that will run on the Linux operating system.

Linux is not Windows so it cannot be expected to work in the same way.

- zipperback
:popcorn:

---

### Post by hyper_ch on 2008-09-06
Btw Dracus124:

With your immature response you just made it onto my ignore list.

---

### Post by hd_sheena on 2008-09-06
So, quick question.
I installed what looked like an "edubuntu add on package" for my regular ubuntu linux, but it has exe and inf files in it. Is this not what I wanted?
Anyone have the time to hand-hold me through a few things on my switch to linux? If so, PLEASE pm me!
Courtenay

---

### Post by cmay on 2008-09-06
> So, quick question.
I installed what looked like an "edubuntu add on package" for my regular ubuntu linux, but it has exe and inf files in it. Is this not what I wanted?
Anyone have the time to hand-hold me through a few things on my switch to linux? If so, PLEASE pm me!
Courtenay
it is better that you start a new tread on it so everyone can benefit from reading the posts and the solutions that comes from it. you can post about all subjects that may come up. there is lost of people here to help.

---

