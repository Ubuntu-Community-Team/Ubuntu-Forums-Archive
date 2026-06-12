---
title: "Issue with Wine Shortcut"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by Dragonseer on 2008-11-01
I am having a peculiar issue with a Wine shortcut, when running WinQuake, if I open a terminal and run "wine /home.../winquake.exe -noipx" then I get an error that says quake cannot load gfx.wad.  

However if I first use cd to navigate to the directory and then run "wine winquake.exe -noipx" from the Quake directory then it runs fine. :confused:  

So how would I go about creating a shortcut that runs these two lines in sequence?  Can I do this from the "create Launcher" option on the desktop or would I have to create a small script?

---

### Post by Kellemora on 2008-11-01
Hi Dragon

I'm not familiar with that program, but due to our last XP machine biting the dust I've had to run a lot of things in Wine that at first I didn't think was possible.

But I put together this little document on making a link in applications to open programs.  It doesn't go into the detail you are looking for I don't think, but it's worth a try anyhow.

We have some games that kept trying to install to the z/ drive in Wine which would put it on the ext3 partition and not in the C drive where it belongs.  Games that REQUIRE the CD to be in the drive and booted to play.
A royal Pain to say the least.  None of them have a start.ext or any way I could see to start them up.  
But by making a Link to the CD player under Wine, quite a few of them work just fine now.

Here's my document:

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
10/26/08 – rev 10/30/08

---

### Post by Dragonseer on 2008-11-02
Thanks Gary that CRTL-H shortcut is useful.  I was able to create a launcher using the following template I pinched from another post:

Open a terminal and type

cd Desktop
touch [nameofyourscript]
nano [nameofyourscript]

Then paste this into it:

#!/bin/bash
#[nameofyourscript] {I used Quake Launcher}
cd /home/~/.wine/drive_c/Quake
wine winquake.exe -noipx

Then save and close. 

Next type

sudo chmod +x [nameofyourscript]

I will use this method again (taken from here [http://ubuntuforums.org/showthread.php?t=862257](http://ubuntuforums.org/showthread.php?t=862257)) if I have to create some more complicated launchers.

---

