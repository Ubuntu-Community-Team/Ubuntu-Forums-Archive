---
title: "Making a serial mouse work"
date: 2005-04-04
forum: Outdated Tutorials &amp; Tips
---

### Post by aggiechemist on 2005-04-04
I'm a noob who just installed Ubuntu, and I had issues getting my serial mouse to respond. First, let me thank the forum community. I found some great answers out there and I really appreciate that. 

Ive borrowed some stuff from this post, so I want to give them credit  =D> :
[http://www.ubuntuforums.org/showthread.php?t=2945&highlight=serial+mouse](http://www.ubuntuforums.org/showthread.php?t=2945&highlight=serial+mouse)

This post is to add a little to what was out there, as well as to note a couple of changes in Hoary (as most of the posts I used were for Warty).

If you install with a serial mouse,  and you get no response, you need to alter one of you config files. The file you need to edit is either

Warty: /etc/X11/XF86Config-4
Hoary: /etc/X11/xorg.conf

In order to get there and do that, do the following:

Get to the login window for Ubuntu. Press Ctrl+Alt+F1 to get to the console.
To get to the text editor, type
sudo nano /etc/X11/###

where you write your file name there at the end.

Scroll down through the file until you find the section for the mouse. 
Change the line area that says
/dev/mouse/generic

to read /dev/ttys0

Note: that 0 is a zero, not a big letter O. I messed that up, and it took me hours to figure out why. 

I've also found that you should change to protocol setion to read "Microsoft." I've only found this in some help guides, so I'm not sure how neccesary it is.

All you do now is hit ctrl+x to leave the editor, and y to say you want to save, and press enter to save the new file over the old one.

To finish up, you can do the following (I copied it from that forum I referenced earlier)

[I]
Hit alt-F7 to get back to the mouseless X window.
Hit ctrl-alt-backspace to exit X.
In the console that X exits to, start X again by typing startx&
Serial mouse should now be working.[/I]

That was kind of complicated for me, so I just rebooted after saving the file. It worked for me. :) 

Also, to be on the safe side you might want to back up the files before you mess with them. To create a bkup, type the following in the console before starting:

sudo cp /etc/X11/### /etc/X11/###.bkup



So I hope that brings all the needed info together to help my fellow newbies in one descriptive location. It worked for me at least.  Thanks so much to those who came before me, especially DaveB who replied to the forum I mentioned. 


Adam

---

### Post by Fireblade on 2005-05-13
Hey dude this article is a great help but there is a typo mistake...

"/dev/tts0" should be actually "/dev/ttys0"

This small mistake actually messed up my Xserver setup but then I learnt from this and I want others to be careful. Thanks a lot dude

---

### Post by Syngin on 2005-05-14
Hehe.  I wish I had read this 4 hours ago.  I spent 3 hours trying to solve this then decided the reinstall since I just figured I missed the mouse setup screen.

Thanks for posting ths. Very helpful.

---

### Post by Syngin on 2005-05-14
[QUOTE=Fireblade]Hey dude this article is a great help but there is a typo mistake...

"/dev/tts0" should be actually "/dev/ttys0"

This small mistake actually messed up my Xserver setup but then I learnt from this and I want others to be careful. Thanks a lot dude[/QUOTE]

Oh yeah, um, could a moderator make the above spelling correction to the first post as X locks up when it comes across that hehe.  Required reinstall #2.

Ahh the joy.  :razz:

Note: **"/dev/ttyS0"** (capital 'S')

Additional help (although a little old): [Here](http://www.faqs.org/docs/Linux-mini/3-Button-Mouse.html)

---

### Post by Hellsteeth on 2006-05-25
I was struggling to get a serial to mouse work under Dapper Drake and googled up this thread which gave me the right clues despite being for 4.10. As others for Dapper may also arrive here this way this is what I had to do to make it work.

Do all of the above but when editing etc/X11/xorg.conf alter it to read as follows
....................
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/ttyS0"
        Option          "Protocol"              "microsoft"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
...................

Worked for me.

---

### Post by goatjuggler on 2006-09-21
Thanks all.  Serial mouse working within 15 minutes of OEM install of Dapper Drake 6.06 LTS.  Just make sure you use capital S in /dev/ttyS0 and you should be ok.  In my case, having a lowercase s also exposed another problem when restarting X.  It griped about Wacom inputs, of which I have none, so I commented out all 3 wacom sections and the corresponding entries in the ServerLayout for the Wacom.  Like so:

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
#	InputDevice     "stylus" "SendCoreEvents"
#	InputDevice     "cursor" "SendCoreEvents"
#	InputDevice     "eraser" "SendCoreEvents"
EndSection

Hope this helps someone.  Relative *nix noob here, but ubuntu is damn sexy.   This is on a Frankensteined Gateway Select 366 FWIW.

---

### Post by Shadow Warrior on 2011-03-25
Is there a straight forward utility to force Ubuntu to detect a serial mouse? Do I need to do a clean install with only the serial mouse attached to the system? Currently, I have both a PS/2 Mouse and a serial mouse. I do have a Windows / DOS Driver for the mouse. Is there a way I can use that instead?

Unfortunately, currently, I cannot afford another mouse.:confused:

---

