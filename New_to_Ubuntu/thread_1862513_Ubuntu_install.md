---
title: "Ubuntu install"
date: 2011-10-16
forum: New to Ubuntu
---

### Post by 40ftcobb on 2011-10-16
Ok so its only been a week or so since I found out about ubuntu,read up rescreached and finaly decided to install,but something went horribly wrong,first instead of 10.04 32bit i got 11.10,now im using hp mini 110,some how ubuntu has erased windows which would be fine if it ran,i boot up chose my os in grub I get the purple screen says ubuntu 11.10 and then nothing just a black screen with a flashing cusor.
As this is my only comp my options are limited is thete away to fix this or did I screw the pouch?
Thanks ahead of time

---

### Post by collisionystm on 2011-10-16
> **40ftcobb said:**
> Ok so its only been a week or so since I found out about ubuntu,read up rescreached and finaly decided to install,but something went horribly wrong,first instead of 10.04 32bit i got 11.10,now im using hp mini 110,some how ubuntu has erased windows which would be fine if it ran,i boot up chose my os in grub I get the purple screen says ubuntu 11.10 and then nothing just a black screen with a flashing cusor.
As this is my only comp my options are limited is thete away to fix this or did I screw the pouch?
Thanks ahead of time

Reboot. When you get the Purple Ubuntu screen hit the UP arrow key on your keyboard. It should show you what its trying to load. What does it stop at?

Do you still have the CD you installed from? Can you run ubuntu from the cd?

---

### Post by overdrank on 2011-10-16
Hi and welcome. Moved to Absolute Beginner Talk

---

### Post by 40ftcobb on 2011-10-16
The last thing it says is stopping system V runlevel compatibility

---

### Post by 40ftcobb on 2011-10-16
I used a 16gig usb,which some also installed ubuntu to it so ya nope lol cant reinstall,i think im screwd

---

### Post by collisionystm on 2011-10-16
try this

reboot your computer

immediately after the bios hold the shift key

you will be at the grub menu

The top line, not the system rescue, hit the letter E on your keyboard to edit it

go to where it says 'boot splash' or something like that. Before that put this, acpi=off nomodeset

Hit F10 to boot

see if that works

---

### Post by 40ftcobb on 2011-10-16
Nope still the same black screen flashing cursor,still stops in the same spot too

---

### Post by collisionystm on 2011-10-16
hit CTRL + ALT + F1

Login

type 

sudo service lightdm start

---

### Post by 40ftcobb on 2011-10-16
Says lightdm unrecognized service

---

### Post by collisionystm on 2011-10-16
okay

sudo apt-get remove lightdm

sudo apt-get install lightdm

reboot


see if that works

---

### Post by 40ftcobb on 2011-10-16
Ok so that worked,kinda im in logged on but its almost as if im missing icons,all my boxes on the left are just white,and in system folder most of the icons are gone,but thank you lol you saved me from the wrath of my wife lol

---

### Post by 40ftcobb on 2011-10-16
No internet browser or anything

---

### Post by 40ftcobb on 2011-10-16
Ok so after 2 days and some wicked help here I finaly got 11.10 working but I have no icons my boxes to the left are just that white boxes,no browser no software center or update manager,any ideas?

---

### Post by thanatos6 on 2011-10-16
Did you install ubuntu from a CD?
It sounds like you have file corruption somewhere.

Try booting off of the install CD, running the check CD for defects.

Also, try running the memory test for at least 30 minutes.

Can you provide details as to how you installed the OS and what made it difficult.

---

### Post by oldgeekster on 2011-10-16
> **thanatos6 said:**
> Did you install ubuntu from a CD?
It sounds like you have file corruption somewhere.

Try booting off of the install CD, running the check CD for defects.

Also, try running the memory test for at least 30 minutes.

Can you provide details as to how you installed the OS and what made it difficult.The OP is duplicating the same complaint in the latter part of his other thread **[[B]Ubuntu install**]("http://ubuntuforums.org/showthread.php?t=1862513")
[/B] 
You pretty well have to read that one to figure out where he is at - I'm no help at all on this one s/he has done too much up to this point already to figure out exactly what has happened other than "borked".:(

---

### Post by mörgæs on 2011-10-17
Threads merged. Please don't create multiple threads on the same topic.

40ft, it would be good if you read this thread thoroughly: [http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)
It is hard to understand exactly what you problem is.

---

### Post by 40ftcobb on 2011-10-17
Ok sorry for the multi threads wont happen again :)
Ok so heres what I did so far
First off im using a hp mini 110 32bit system,now I downloaded and wrote it to a usb
Some how during the install it wiped out windows,and installed ubuntu to the usb as well as my hard drive,now after everything I finally got ubuntu to load but its like I missed something because I have white boxes in the left hand of my desktop if I click system setting more than half of those icons are gone and I have no software center or update manager,no browser or any other apps,it would seem the only thing I do have is the music player lol so ya im not to sure were to go from here

---

### Post by collisionystm on 2011-10-17
> **40ftcobb said:**
> Ok sorry for the multi threads wont happen again :)
Ok so heres what I did so far
First off im using a hp mini 110 32bit system,now I downloaded and wrote it to a usb
Some how during the install it wiped out windows,and installed ubuntu to the usb as well as my hard drive,now after everything I finally got ubuntu to load but its like I missed something because I have white boxes in the left hand of my desktop if I click system setting more than half of those icons are gone and I have no software center or update manager,no browser or any other apps,it would seem the only thing I do have is the music player lol so ya im not to sure were to go from here

open terminal

type

firefox

if web browser comes up, download 10.04 lts

burn it to a cd or copy to your thumb drive

reboot and run the live cd.. install something that works!

---

### Post by 40ftcobb on 2011-10-17
Ok how do I open terminal?nothing working

---

### Post by -kg- on 2011-10-17
Try <ctrl>+<alt>+"t"  That should open a terminal.

[Ubuntu 11.10 (Oneiric Ocelot) Keyboard Shortcuts]("http://blog.sudobits.com/2011/09/04/ubuntu-11-10-oneiric-ocelot-keyboard-shortcuts-for-unity/")

---

### Post by 40ftcobb on 2011-10-17
Nope no good lol

---

### Post by collisionystm on 2011-10-17
> **40ftcobb said:**
> Nope no good lol

Any luck on fixing that computer?

---

### Post by 40ftcobb on 2011-10-17
Not yet

---

### Post by mörgæs on 2011-10-18
Have you thought of a fresh install?

---

### Post by Faudyen on 2011-10-19
My suggestion would be to install gnome 3 and use the gnome classic interface until you can do a fresh install of an Ubuntu version below 11.10.  I would also use a wired connection for the install in case your wireless is not working.


[http://www.computerandyou.net/2011/10/16/how-to-install-gnome-3-in-ubuntu-11-10/](http://www.computerandyou.net/2011/10/16/how-to-install-gnome-3-in-ubuntu-11-10/)

---

### Post by 40ftcobb on 2011-10-21
sorry for the late reply here ive finally got things running,borrowed a friends laptop rewrote the usb with 10.04 lts and installed last night.everything is awesome thisis my first time ever using linux and just the fact alone that it only takes up 3.9gigs of my harddrive is wicked.
ok but i do have to issues
1 no sound from my speakers,headphone jack works for my external speakers
2 will not read my sd card

now are these drivers i need to find to instal or is there patch or something

oh ya and thanks evryone for the help

---

