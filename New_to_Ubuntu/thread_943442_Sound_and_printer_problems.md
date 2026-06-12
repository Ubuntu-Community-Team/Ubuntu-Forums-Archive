---
title: "Sound and printer problems"
date: 2008-10-10
forum: New to Ubuntu
---

### Post by poscomp on 2008-10-10
This software installed very nicely but, I have no sound and I can't get the system to see any printer. I have printers attached to Windows and a Samsung networked laser printer. Mandriva 2008 saw both printers and printed. Mandriva 2008 also played sound. Mandriva 2009 would not load. I have a HP TX2000Z tablet computer hooked via a direct network cable because the Broadcom 4321 wireless will not work. Can anyoue help me with these problems?

---

### Post by gali98 on 2008-10-10
Okay..
To get the wireless working plug into the internet with a ethernet cord (which you are already doing...)
Then use the update manager
System->Administration->Update Manager

and click the check button and put in your password then click on the update button. 
(sorry if I sound like I'm talking to a five-year old :) Just want to be clear)

And to fix your sound, you have two options at this point.
The sound on this laptop is a little messed up at this moment.

Go to a terminal

Applications->accesories->terminal

and type

sudo gedit /etc/modprobe.d/alsa-base

this will open a text editor.

on the bottom add one of these lines:

If you want everything to work except the front microphones (the ones by the webcam) then put this line:
options snd-hda-intel model=hp

if you want the front microphones to work (your headphones and the mic jack may not work..)
then use this line:
options snd-hda-intel index=0 model=3stack position_fix=0 single_cmd=0

Cheers, 
Kory

Also if you want the tablet part working (the touchscreen and pen...)
See my tutorial:
[http://ubuntuforums.org/showthread.php?p=5469447#post5469447](http://ubuntuforums.org/showthread.php?p=5469447#post5469447)

I will post again later to try and help you with the printers... I'm short of time now..
:)

---

### Post by gali98 on 2008-10-11
Okay....
First of all what distibution are you on (Fiesty, Gusty, Hardy, Intrepid....)
For the sound:
did you save the file?
check to make sure on of those lines is at the bottom of 
/etc/modprobe.d/alsa-base

finally did you restart?

Now on the wireless:
You are fully updated?
You restarted?
You might need to enable a resticted driver:
Go to System->Administration->Hardware Drivers

and check everything so that it says "enabled"
then restart.
Kory

---

### Post by gali98 on 2008-10-11
Okay on the printers:
Please give me the model (i.e photosmart c3180)
and make (i.e HP)
and for the Windows computer make sure it is shared.
After you give me that info, I can try and help you get your printer installed :)
Kory

---

