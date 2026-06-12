---
title: "Gimp not working"
date: 2012-10-15
forum: New to Ubuntu
---

### Post by alfu on 2012-10-15
I have 2 problems with Gimp under 12.04.  

First, frequently just after saving a image, it folds.

Second, whenever I use a tool, the image editing window becomes deselected, and takes with it the 'show on mouseover' menubar at the top of the screen.  To get the menubar back, I have to click in the top of the image editing window.

Previous editions of Gimp did not have this tiresome behavior.

---

### Post by SWGraphics291 on 2012-10-16
Maybe you should try reinstall it! PM me if it has done this from the time you installed it.

---

### Post by sandyd on 2012-10-16
**Moved to seperate thread in ABT**

---

### Post by neu2buntu on 2012-10-16
yeah i also have had the tiresome behaviour of the top panel menu (12.04 clean install ) losing focus when using any of the option like color, tools etc and the only way of gaining focus is to give focus to the image i was working on, this is perhaps an oversight of the G.I.M.P devs . it could be that gnome3 hasnt thought about multiple floating windows, where there aren't so many ubuntu apps that have this behaviour, so the question i would ask is where to make a bug report gnome or GIMP?  thanks ;)

---

### Post by deadflowr on 2012-10-16
I don't understand your folding problem, but to keep the image window in focus right-click on the image widow title bar, and select always on top. Gimp has a weird way of defaulting to another dock, this method seems to work for me.

---

### Post by neu2buntu on 2012-10-16
the above will work also found a permanent fix which i have just tested found here >>> [http://voices.yahoo.com/ubuntu-hiding-gimp-toolbox-3449370.html](http://voices.yahoo.com/ubuntu-hiding-gimp-toolbox-3449370.html)

also read that GIMP 2.8 will be a single window app so this won't be a problem for long.  can the original poster mark the post as solved if this solves their problem, ( also unsure of the folding problem i think the op maybe means crashing on image save tho ? ) thanks

---

### Post by deadflowr on 2012-10-16
> **neu2buntu said:**
> the above will work also found a permanent fix which i have just tested found here >>> [http://voices.yahoo.com/ubuntu-hiding-gimp-toolbox-3449370.html](http://voices.yahoo.com/ubuntu-hiding-gimp-toolbox-3449370.html)

also read that GIMP 2.8 will be a single window app so this won't be a problem for long.  can the original poster mark the post as solved if this solves their problem, ( also unsure of the folding problem i think the op maybe means crashing on image save tho ? ) thanks

GIMP 2.8 single window mode is optional.
It's in Ubuntu 12.10.
You can switch between the old style and the single window style, if so desired.

---

### Post by alfu on 2012-10-23
Oh, duh.  Yes, 'always on top' might fix that.  Thanks!

---

### Post by alfu on 2012-12-11
Actually, 'Always on top' did NOT fix the behavior.

---

### Post by NM5TF on 2012-12-11
just wondering if you have tried Shotwell that seems to have
replaced GIMP in 12.04???

are there features lacking in Shotwell that require you to
use GIMP???

Tommy

---

### Post by pierceTN on 2012-12-11
> **alfu said:**
> I have 2 problems with Gimp under 12.04.  

First, frequently just after saving a image, it folds.

Second, whenever I use a tool, the image editing window becomes deselected, and takes with it the 'show on mouseover' menubar at the top of the screen.  To get the menubar back, I have to click in the top of the image editing window.

Previous editions of Gimp did not have this tiresome behavior.

for you second problem, if you are on 2.8 go to windows>single window mode.

this will make them all one window.


please explain the first problem a little bit, does it minimize?


Pierce

---

### Post by audiomick on 2012-12-11
> **NM5TF said:**
> just wondering if you have tried Shotwell that seems to have
replaced GIMP in 12.04???

are there features lacking in Shotwell that require you to
use GIMP???

Tommy

Shotwell replaced F-Spot, not Gimp. Shotwell and F-Spot are image organising programs that can do a little bit of image manipulation. GIMP is and image manipulation program, not an image organising program.

---

### Post by alfu on 2012-12-12
No, [pierceTN]("http://ubuntuforums.org/member.php?u=1431401"), I have not tried minimizing Gimp.  Another disturbing behavior is that when it launches, the tools window is mostly down in the lower workspace and I have to do 'Super-S' to grab it and haul it up into the working workspace, because my install of Ubuntu has lost its window borders so resizing and moving windows is problematic.

Someone suggested installing Xubuntu as a fix for some of the other issues I am having with Unity (the two mutually exclusive types of directory views that have to be accessed from the nenubar and no ability to supress partitions mounting from an external drive, among others).

I have tried Xubuntu from the live CD I burned, and it looks like it will address all these issues, because the Gimp window positions are correct, and you don't have to go all the way up to the top of the screen to get menu selections.
_____________________________
Have now installed Xubuntu, and the issues with Gimp have disappeared.  :)

---

### Post by SeijiSensei on 2012-12-12
I use Kubuntu (KDE) and don't experience any of the problems you describe in either 2.6 or 2.8.

---

### Post by Calinou on 2012-12-12
> **NM5TF said:**
> just wondering if you have tried Shotwell that seems to have
replaced GIMP in 12.04???

are there features lacking in Shotwell that require you to
use GIMP???

Tommy

Why do you even bother asking? Shotwell is heavier and lacks much more features than GIMP does.

alfu: try another DE? Maybe that'd work. :P

---

### Post by audiomick on 2012-12-12
> **Calinou said:**
>  Shotwell is heavier and lacks much more features than GIMP does.

Either you haven't really looked at GIMP, or you are comparing apples with pears.

Shotwell is a program for organising your photos that can do a little bit of image manipulation.

Gimp is a very powerful image manipulation program. It can't do any organisation of your photos because it is an image manipulation program and not a program for organising your photos.

---

### Post by alfu on 2012-12-14
Installing Xubuntu 12.04 totally solved the issues I was having with Gimp, but opened a new can of worms: playing flash files (gnash) is now broken.  I have tried everything, and Synaptic won't even let me go back to the old swfdec-mozilla, which did work. 

Flash-Aid did not seem to do anything (except destroy the browser windows I had open, which I will now have to rebuild from scratch).

Yikes, I just tried it and everything works! Here's what I did: wiped all the flash plug-ins, then did an install of swfdec-gnome.  It pulls in 'gnash-common' and 'gnash', but NOT 'mozilla-plugin-gnash' or 'browser-plugin-gnash'.

Update 121216:  That was a little premature.  Now, some youtube videos play, but everything else is prompting me to install a flash plugin.  Still broken.  Installing the gnash suite did not help, either.

Update 121216: No Youtube videos or any other flash files work now at all.  This on a computer that was showing all flash content before switching over to Xubuntu.

Edit 121217: Googled 'Xubuntu flash problems' and found a link to [http://www.youtube.com/watch?v=3HAgUCh5qoM](http://www.youtube.com/watch?v=3HAgUCh5qoM),  installing Adobe Flash on Xubuntu 12.04. Amazingly, the video played! Without the tips presented there, I would have come to a  dead end on Adobe's site. So far, following these instructions looks  like it has enabled Flash content to play. ( I removed all 'gnash' system resources)  :smile:

121218: The fix seems to be persistent, with youtube feed speeds improved over anything I had seen before here.

---

