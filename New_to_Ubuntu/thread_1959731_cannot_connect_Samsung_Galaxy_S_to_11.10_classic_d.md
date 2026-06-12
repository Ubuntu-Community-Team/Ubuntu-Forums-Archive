---
title: "cannot connect Samsung Galaxy S to 11.10 classic desktop"
date: 2012-04-16
forum: New to Ubuntu
---

### Post by chipppy on 2012-04-16
Good Morning

I am try to get 1 pic out of my phone and I cannot get it to connect 
phone details
Samsung Galaxy S GT-I9000
Firmware 2.2
Baseband Version I9000HVJP3
Kernel 2.6.32.9root@SE-5604 #6
build number FRoyo.hvjp4

I am using ubuntu 10.10 classic desktop fully updated.

I have even tried the Kies software but have a driver issue with Marvell 91xx driver not updated on window & 64bit.  Therefore back to trusty ubuntu

So I go
setting ==> wireless & networks ==> USB settings ==> Mass storage
connect cable (phon charges ok out of interet)

Get USB connected and green andriod.  Button at bottom 'Connect USB Storage.  BLue bar at top USB mass storage

nothing at this point

Drag down notification (grey) bar at top

Tap line with the following on it
'USB connected
Select to copy files to/from your computer'

Back to green android as per above

Tap button and button now says 'turn off' and andriod changes to orange in colour

Still nothing.

Tried using the debug mode, dont allow screen to turn off and debugg mode, and a few other random stabs in the dark but still nothing

Anyone got any ideas on how to get this darn pic of my kids covered in mud of my phone????

Cheers
chipppy

---

### Post by chipppy on 2012-04-22
bump

---

### Post by The Cog on 2012-04-22
I have a GS2 which I guess is very similar. It goes like this:

Settings -> Wireless and networks -> USB Utilities

I see a USB mass storage page with a "Connect storage to PC" button. Press the button.

I get a USB Utilities dialog popup saying "Connect USB cable to use mass storage", and a cancel button. Plug the cable in.

I get a "USB connected" page with a green android. At the botton is a "Connect USB storage" button. If you look at your file manager on Ubuntu at this point, there are no USB drives in the sidebar. Press the Connect button on the phone. 

I see a spinny thing on the phone for a couple of seconds, then I get a "USB storage in use" page with an orange android. Two USB drives appear in my Ubuntu file manager sidebar (I use thunar, not nautilus cos I'm using Xubuntu).

One of the drives is the internal flash, the other is the extra flash SD I installed behind the battery. You can just drag/drop files between PC and phone now.

Hope this helps.

---

