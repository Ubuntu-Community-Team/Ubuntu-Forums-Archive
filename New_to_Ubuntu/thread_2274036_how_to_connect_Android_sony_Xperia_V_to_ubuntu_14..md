---
title: "how to connect Android sony Xperia V to ubuntu 14.04."
date: 2015-04-17
forum: New to Ubuntu
---

### Post by sebastiaan5 on 2015-04-17
So my problem is that I don't know how to connect my phone to ubuntu 14.04.

If I plug in my phone via USB I can see all the folders on my screen but I can't open files like jpg,mp3,mp4's and so on,
I get an error "Could not load image. libmpt error: Unknown error."

The installer I can download via my phone is an .exe and I don't want to use Wine or any other windows-like program.

Is there any program/manner on how I can see photos / play movies from my phone?


regards.

---

### Post by ajgreeny on 2015-04-17
See my post #2 at [http://ubuntuforums.org/showthread.php?t=2274028&p=13266735#post13266735](http://ubuntuforums.org/showthread.php?t=2274028&p=13266735#post13266735) for more info on getting Android phones and tablets to connect to Ubuntu.

---

### Post by sebastiaan5 on 2015-04-17
I did all the steps but I still can't see pictures/movies etc.

this is my lsusb output:

Bus 003 Device 007: ID 0fce:0186 Sony Ericsson Mobile Communications AB 


STEP 4
 	Code:
 	sudo nano /lib/udev/rules.d/69-mtp.rules 
Add the below lines of code with red text transferred from above
 	Code:
 	# Sony Xperia Z2 Tablet
ATTR{idVendor}=="[COLOR=#ff0000]0fce[/COLOR]", ATTR{idProduct}=="[COLOR=#ff0000]01b1[/COLOR]", SYMLINK+="libmtp-%k", ENV{ID_MTP_DEVICE}="1", ENV{ID_MEDIA_PLAYER}="1" 
So i guess i need to change 01b1 with 0186 and what do I need to do then? ctrl X, Ctrl M? how to save? 

and how to use MTP?

---

### Post by ajgreeny on 2015-04-18
> **sebastiaan5 said:**
> I did all the steps but I still can't see pictures/movies etc.

this is my lsusb output:

Bus 003 Device 007: ID 0fce:0186 Sony Ericsson Mobile Communications AB 


STEP 4
     Code:
     sudo nano /lib/udev/rules.d/69-mtp.rules 
Add the below lines of code with red text transferred from above
     Code:
     # Sony Xperia Z2 Tablet
ATTR{idVendor}=="[COLOR=#ff0000]0fce[/COLOR]", ATTR{idProduct}=="[COLOR=#ff0000]01b1[/COLOR]", SYMLINK+="libmtp-%k", ENV{ID_MTP_DEVICE}="1", ENV{ID_MEDIA_PLAYER}="1" 
So i guess i need to change 01b1 with 0186 and what do I need to do then? ctrl X, Ctrl M? how to save? 

and how to use MTP?
Yes, you need to use the [COLOR=#ff0000]0fce[/COLOR] and [COLOR=#ff0000]0186[/COLOR] in your /lib/udev/rules.d/69-mtp.rules file, as you suspected, and then if using nano hit Ctrl+o to save the changes and Ctrl+x to close nano.

Try again to see if that now works for you.

---

