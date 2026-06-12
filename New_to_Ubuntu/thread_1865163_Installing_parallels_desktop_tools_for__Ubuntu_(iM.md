---
title: "Installing parallels desktop tools for  Ubuntu (iMac-Intel Lion)"
date: 2011-10-19
forum: New to Ubuntu
---

### Post by Dsoslglece on 2011-10-19
Hi,
I've installed now the last version of Ubuntu on my iMac intel, using parallels desktop, and it is working fine, except for one thing, to be able to pass from one screen to another, from one system to another, and having the mouse free to just do it too (without an extra short key (alt + ctrl), I need to install the parallels desktop tools. On installing XP or Win7, it is done automatically, but it says that for Ubuntu, one has to use Terminal. Well, I did some times used Terminal on Mac for various things including compiling some apps, and I know the commands are almost identical with Linuxes, being sort of close cousins in the Unixes family. but here it doesn't seem to work.
It says:

To install parallels tools, open Terminal, go to the CD/DVD player's directory and execute the following command as root: <sudo ./install>

But, doing so (after having entered my PW) gives me the message : the command install wasn't found.

I also tried to find an install.sh in the installation folder, and from this folder I asked <./install.sh run> but it didn't work either.

One thing maybe was on my way: 
Since I don't know  (and couldn't find) the command to go into the CD/DVD player's directory (BTW the file is a disc image), I copied the folder onto the desktop and continued from there. with the command <cd path to the folder on desktop>, and continued with the other command…

Since it also said that with certain Linux systems (but didn't say which!!) one may have to dismount the install disc and mount it again with the following command: <mount -o exec> and then continue with the sudo command, I also tried it…
But it didn't work either.

I'd be very grateful if someone had a solution for this… Thanks in advance.

---

### Post by arpanaut on 2011-10-19
You might get better help here: [http://ubuntuforums.org/forumdisplay.php?f=328](http://ubuntuforums.org/forumdisplay.php?f=328)

Or maybe here:[http://ubuntuforums.org/forumdisplay.php?f=308](http://ubuntuforums.org/forumdisplay.php?f=308)

Don't make a duplicate post, if you want to have your post moved to one of those forums click on the report abuse button (lower left) on your original post and ask to have your post to be moved to whichever you choose.

hth

---

### Post by Dsoslglece on 2011-10-20
Thanks Arpanaut, 

I went to the places You indicated but unfortunately There was no information concerning that problem.
On iMac, one can install natively any system (Linux , Windows…) with "bootcamp", but one can then only run one at the time, and one needs then to shut the one opened to be able to run one of the others.

With "Parallels desktop", one can run together 2 or more systems at the same time, and since with Snow Leopard and Lion one also has the possibility to have few desktops and choose the one needed, it is then possible to have a particular desktop for Lion or Snow Leopard, another for Ubuntu and another for Win7 (provided the machine has enough RAM and cpu).
This anyway at the moment is fine on my machine and works 100%.

But there are also some special tools available from Parallels Desktop (parallels desktop Tools) that permit to, so to say, be in all systems at once: be in Ubuntu and save a file in Lion, or be in Lion and open a file from Win7, and so on, and also have the mouse passing from one system to the other without neading to use the short keys (alt+ctrl). 
All this is for you to understand what I'm trying to do. 

But finally, since the Parallels desktop tools have to be installed from Ubuntu, I bet it is only a question related to Ubuntu, and mostly also a question concerning Ubuntu's commands in terminal.

They say (in paralles desktop):

Go to the CD/DVD player's directory… But I don't know where this dir is, and when I do <cd path to the disc image at desktop> it says "no such directory".  My only way to turn this around was to first copy the CD's content on the desktop, and then, using <cd> to go to this directory, but I'm not sure it is the same, and anyway, using the next command <sudo ./install> doesn't work.

So, I can only assume that it is a question of using the wrong or the right command, since I know there is some slight differences sometimes betwen Mac and Linux, since some time in the past I've had to search and try for the right command for a specific action.

---

