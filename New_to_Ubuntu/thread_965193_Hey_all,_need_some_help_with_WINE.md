---
title: "Hey all, need some help with WINE"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by amit.la on 2008-10-31
hey.

i'm kinda new to ubuntu, but so far i'm really glad i preffered it over vista :)

anyway, i've heard of WINE, and installed it successfully, however, no mater what i try to install (using wine-doors) the installation always gets stuck in the "installing desktop icons" phase

I'm using:
- Ubuntu 8.04,
- AMD Athlon64 3000+ (old, i know...)
- ATI radeon 9800 pro
- 1 GB of RAM


I would appreciate any thought about how to solve my problem.
Thanks,


Amit

---

### Post by bodhi.zazen on 2008-10-31
wine doors is spotty.

Your best source of information on wine is wineHQ, search the application data base to get your application working.

[http://www.winehq.org/](http://www.winehq.org/)

Better, use linux native applications :twisted:

---

### Post by lhb1142 on 2008-10-31
> **amit.la said:**
> hey.

i'm kinda new to ubuntu, but so far i'm really glad i preffered it over vista :)

anyway, i've heard of WINE, and installed it successfully, however, no mater what i try to install (using wine-doors) the installation always gets stuck in the "installing desktop icons" phase

I'm using:
- Ubuntu 8.04,
- AMD Athlon64 3000+ (old, i know...)
- ATI radeon 9800 pro
- 1 GB of RAM


I would appreciate any thought about how to solve my problem.
Thanks,


Amit

:) I installed WINE and then installed two Microsoft Windows programs just as I would have if I were using Windows. But I unchecked all the options such as "Make Desktop Icon" and the other such options as these would not work properly in Ubuntu. Try doing that - uncheck any and every option the Windows program offers (other than the basic install itself) - and see if this works.

Also you might want to go to the WINE site and check to see if the Windows program(s) you want to install are in fact compatible. I have found a couple that I would have liked which were not copatible (but subsequently found a Linux equivalent that did the same thing).

I still only use those two Windows programs I originally installed. Ubuntu has equivalents for everything else I want. Just use the Synaptics Package Manager search box (you may have to try several different search terms) and I'll bet you find something that will satisfy you.

From the specifications you show, your computer looks fine to me.

I hope this helps you.  :lolflag:

---

### Post by roger_1960 on 2008-10-31
Hi

I found this guide very clear and useful

[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

---

### Post by amit.la on 2008-10-31
Wow!
That was really quick :) thank you guys!!
All of the tips were great! I'll try all of them!

---

### Post by Kellemora on 2008-10-31
Hi Amit

Here is something I put together the other night that you may find very useful.

As already stated, don't try to install desktop icons!

BUT, you WILL want to be able to access your program from the pull down Applications Menu and NOT go digging through hidden folders to find the program launcher (.exe file) each time.

I'm posting it below!  Sorry none of the formatting comes through here.

TTUL
Gary

Helpful Tips for WINE: 
Ubuntu 8.04 Hardy Heron

From a Noob for fellow Noobs!

Launching Programs From the Applications Menu:

Wine makes it very easy to install programs, by simply going to drive C, creating a folder and pasting it right in.  However, after 9 hours of studying several on-line documents on using Wine, not a single one told how to place a launcher in the Applications/Wine/Programs folder.  Then how to get it to work.
Trying to use the EXAMPLE of Applications/Wine/Programs/Accessories/Notepad is of no use.  Somehow they manage to get it to run from simply the word 'notepad'.

So, for those of you having as much trouble as I have in performing this assumed simple task.  Here is a step by step method to follow.  It may not be the best or the easiest, but it works!

First we will add the Directory 'Games' to Applications/Wine/Programs:  

Right click on Applications, left click on Edit Menus, (a Main Menu will open, in the left column marked Menus) scroll down and left click on the arrow to the left of WINE then highlight the Directory Programs.  On the right side of the Main Menu, select New Menu (a Directory Properties box will open).  In the Name box enter the name for the new Directory, EG: Games.  Then click OK and the name (EG: Games) will appear as a folder in the Items list.  You cannot check mark the box yet because the folder is empty.

To make the Launcher, highlight the name of the Folder you want to place the new executable in, then from the right side select New Item and a Create Launcher box will open.  In the Name box, enter the name of the program you wish to Launch.  EG:  JezzBall.  You can add something under comments as well!  EG:  Old Win95 Game.  Now click on the word Browse and a Choose an Application window will open.  It should be in your USER folder!  Press CTRL-H to show the hidden files if required.  Now scroll down until you find a Folder named .wine (the dot indicates this is a hidden folder) and double click on this .wine folder to open it, you should see a Folder named Drive_C, double click on this folder and things should start looking more familiar to you now.  
If you are like me, you would have installed, for EG: JezzBall in a folder marked Games and possibly within the Games folder may have a folder named JezzBall.  Only you will know where you put the program you copied here!  Just work your way through your Folders until you get to the Executable file that opens the program.  (You may have already opened the program from here and found it worked great.  But after creating the Launcher, you may find Permission Denied when you try to Launch the program, we'll fix that in a moment).  Double click on the Executable and you will find yourself right back at the Create Launcher window with the link in the Command box click OK.  A check mark should automatically appear in the Items list under Show, if not place a check mark here and select Close.  In this Example:  By going to Applications/Wine/Programs/Games you should find JezzBall.

If you get Permission Denied go to Places/Computer/FileSystem/Home/USER(your username).  Again we need to press CTRL-H to see the hidden folders.  Scroll down and select the now visible .wine folder by double clicking on it.  Double click on the Drive_C folder and go to or through your folders to reach the Executable file EG: Jezzball.exe, right click and select Properties.  Click on the Permissions tab and place a check mark in the Executable box and select Close.  That's it, your done!  

If you received a message that you do not have the authority to change Permissions, then go to your root terminal and use nautilus from root, repeating the above directions for changing Permissions.

TTUL
Gary/aka Kellemora
10/26/08 &#8211; rev 10/30/08

---

