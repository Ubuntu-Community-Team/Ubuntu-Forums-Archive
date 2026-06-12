---
title: "I need help deciding between windows and ubuntu."
date: 2010-08-18
forum: Recurring Discussions
---

### Post by Artemis Fowl on 2010-08-18
Sorry if this is the wrong forum, but I need help deciding between Windows and ubuntu. I'm really fond of ubuntu, and I finally got a live CD working without destroying the disk. I do have some questions though:
1. Am I able to import pictures from windows/my current ubuntu OS?
2. Does Wine run games like Star Wars:Empire at war well, or should I try to avoid windows applications?
3. Is there any program the can simulate batch files well? I know they're not used in ubuntu, but I like experimenting with them.

I bring this up because today Vista stopped working; something wrong with system32, probably courtesy of a batch file antivirus I was trying to make; and it needs it's install disks to repair. I'm almost too lazy to find them, and it almost seems to be a coincidence I finally get a live disk working today, so if someone can convince me to switch I'm going to leave Windows until I finish building my new computer which will be a dual boot.

---

### Post by cgroza on 2010-08-18
All I can tell you is that you should avoid Windows apps if there are alternatives for them.

---

### Post by Artemis Fowl on 2010-08-18
What if there aren't alternatives?

---

### Post by Zorgoth on 2010-08-18
a) Importing photos should be pretty easy, as long as you preserve the data.  Your Ubuntu can read your Windows partition no problem.  If you have a lot of photos in different places organized my some manager, maybe you should try exporting them in Windows to a cross-platform manager like Picasa (I know nothing about what I speak, just guessing - I just keep my photos in ~/Pictures :D)

b) Windows applications will work or not work on a case by case basis.  Wine appdb has a database of which applications work and which don't.  As long as you have a decent graphics card, most but not all modern games will run (if you are willing to spend some time tweaking with winetricks), with performance hits varying from unnoticable to 50% or more (decent graphics cards do not include Intel cards except maybe X4500/Intel HDs that come with core i*s, and as far as Linux is concerned primarily include more recent ATI cards and most nVidia cards, nVidia being best)

The particular game you mentioned looks like it will likely not work based on the page in the wine appdb.  Some versions may work, and the test results are all very old, meaning things likely got better since then, but I would not count on it by any means.

c) If you like Windows batch files, soon you will pity them, because Linux's bash is far, far more powerful, and if you like that kind of scripting, you will fall in love.  Just open a terminal (Applications > Accessories > Terminal or possiblt Control-Alt-T) and start bashing, it is the language of the Linux command line interface.

---

### Post by Dracona on 2010-08-18
> **Artemis Fowl said:**
> Sorry if this is the wrong forum, but I need help deciding between Windows and ubuntu. I'm really fond of ubuntu, and I finally got a live CD working without destroying the disk. I do have some questions though:
1. Am I able to import pictures from windows/my current ubuntu OS?
2. Does Wine run games like Star Wars:Empire at war well, or should I try to avoid windows applications?
3. Is there any program the can simulate batch files well? I know they're not used in ubuntu, but I like experimenting with them.

I bring this up because today Vista stopped working; something wrong with system32, probably courtesy of a batch file antivirus I was trying to make; and it needs it's install disks to repair. I'm almost too lazy to find them, and it almost seems to be a coincidence I finally get a live disk working today, so if someone can convince me to switch I'm going to leave Windows until I finish building my new computer which will be a dual boot.

1. Yes,you will have access to your complete windows partition.
2. Wine 1.2 will run a lot of windows based games/programs. sometimes without any tinkering. ( i am running EQ2 from ubuntu 10.04 
3. dunno

if you have a usb stick, you can install ubuntu onto it, and never have to worry about making a cd again. ( it will work just like the cd, you just have to enable you system to boot from USB)  
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
go to section #2

hope this helps.

---

### Post by Artemis Fowl on 2010-08-18
Thanks for the helpful replies! As for the terminal, I've already started playing around with it and I really like it.

edit: I've decided to say goodbye to Windows. As of my next post, I will be 100% linux.

---

### Post by SoFl W on 2010-08-18
> 1. Am I able to import pictures from windows/my current ubuntu OS?When you install, if you do a dual boot, it should ask you if you want to import/copy your pictures.

> 3. Is there any program the can simulate batch files well? I know they're not used in ubuntu, but I like experimenting with them.There is a batch equivalent in Linux.

> if someone can convince me to switch I'm going to leave Windows until I finish building my new computer which will be a dual boot.I would recommend a dual boot, and soon enough you wont be using the Windows side anymore, but at least you still have it.  Of course, if Windows isn't working then making the switch is that much easier.


*EDIT*:  I guess you made up your mind as I typed this!

---

### Post by Zorgoth on 2010-08-18
> **Artemis Fowl said:**
> What if there aren't alternatives?

There are alternatives for most commonplace apps.  If you use specialized applications for work/hobbies, there may or may not be alternatives - please ask if you have any questions about individual programs. 
 Also, as an example, the Linux alternative to Photoshop, GIMP, while there are people who rely on it exclusively, is considered by most users I've seen to be marginally lower quality, and some plugins in Photoshop do not exist in GIMP.  I cannot state a real personal opinion because I am not any kind of design expert - that is just an example of a common Windows/Linux comparison.

Now, there are also a lot of cases where Linux alternatives are superior (as well as free), and Linux is far more customizable than Windows, and by default you will have compiz (or kwin if you got Kubuntu - this is still probably > Aero but <<< compiz), which is a far more powerful window manager than Windows' Aero (and imo much better looking once you get it set up right).  The main feature that you will notice is that it supports multiple desktops, and there are a plethora of other features under the hood that you can experiment with by getting compizconfig-settings-manager or ccsm (fear not, it's a pretty easy to understand GUI, but with a lot of options).  Also you will immediately notice that once installed on the hard drive (the Live CD is for obvious reasons much slower than a hard drive install) Ubuntu is far, far faster than Windows and uses fewer resources.

For games, you will have to take what you can get.  I am lucky in this regard - all my favorite Windows games are working on my Ubuntu.  You might not be so fortunate, particularly if you play a lot of games.  Also if you have a low-end system you will probably be less satisfied with the performance.  It is important to have a fast processor in particular to handle all the translation of Windows calls into Linux calls that wine has to do.  There are some commercial games for Linux, but probably less than 5% of the games out there have native Linux versions is my guess.

---

### Post by Zorgoth on 2010-08-18
> As for the terminal, I've already started playing around with it and I really like it.

Hint:  try typing man bash - then you will learn the true power of the terminal! (man + any command will give an extensive help file - except that for a few commands that are specific to bash you use help instead of man - the most common of these include commands like bg, fg, export, unset, and jobs)

man bash basically contains a summary of all of the features of bash - variables, loops, conditionals, arrays, command substitution, etc. - it would take a while to get through it all before you have applications for all the tools though.  If you have any questions about bash scripting, just ask in general help or programming talk.

---

### Post by Rumpletumbler on 2010-08-18
> **Artemis Fowl said:**
> What if there aren't alternatives?

When a financial package I was comfortable with wasn't available in Linux I became destitute in order to eliminate that as an objection. 

You can do it.

---

### Post by Artemis Fowl on 2010-08-18
I am now completely linux. Thanks for helping me, and thank you for the person who told me to try man bash, as I have wondered what exactly bash is(I hope it's not something I've been using but not known what it's called, I feel really stupid when it's something like that.) As for gaming, I've already found an alternative to the Civilization games, freeciv. I'm going to try and contribute here more. Thanks again! :D

---

### Post by Zorgoth on 2010-08-18
Just a note about the Civilization games - I have Civ IV working perfectly under wine.  If you don't, get the script called winetricks (google it) and isntall first all the d3dx* packages (like d3dx9 and d3dxof), and also install anything people on the wine appdb talk about with civ IV.

---

