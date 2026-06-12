---
title: "Hard Drive Permission"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by DarkSaga70 on 2008-05-11
I installed a new HD and when i try to create a folder on it  it says i do not have permission to do that. How do I fix this? Thanx

---

### Post by SunnyRabbiera on 2008-05-11
what format is this new HD in?

---

### Post by DarkSaga70 on 2008-05-11
EXT 3
is what i formatted it in was that wrong?

---

### Post by SunnyRabbiera on 2008-05-11
Nono, that should do, what is the make and model of this hard drive and how do you have things set up?

---

### Post by DarkSaga70 on 2008-05-11
Western Digital 160 gig jumper set to slave (onmy because thats the only setting I can have it on to make it read my burn drive wich is set to master on that controler).

---

### Post by Ripfox on 2008-05-11
find out what the drive is called 

Example 

/dev/sda/*

then run > sudo chmod -R 755 /dev/sda on it...that tends to work for me when I have permission problem

/dev/sda/* is just an example

---

### Post by DarkSaga70 on 2008-05-11
ok i understand how to find it. On my PC its either dev/disk  or media/disk. However I m not sure how to run that sudo command on it because I can not figure out how to even get to that in the term. So please explain. Sorry for all this but I have came a long way from windows and I refuse to go back and even though I ask a lot of questions on here I have learned a lot.

---

### Post by Cresho on 2008-05-11
I had the same issues on my hardrive when i Resized my windows xp partition from 500gb to 100 and created a 400gb partition.  I had a problem because it was not automounted and my permissions were not in place.  This is not a problem!  It is if you are not aware on how to modify fstab to automount the drive at boot and if you do not understand how to create folder directories with your permissions.  This is an excellent learning expirience for you.  Once mastered (took me 30 minutes), you wont look back.


It's easy stuff!  first

is your hardrive mounted at startup?  (mines was not)  do a 

sudo fdisk -l  in terminal and post here the result.

if your hardrive mounts automatically at boot, just open terminal and type sudo nautilus.  Navigate to your new hardrive and create a folder and right click on it and go to properties and permission.  change owner to your username and group too.  allow for folder create and delete files on both.  Other groups put none.  close and close nautilus.  Now you have a accessable folder.  so anything in this folder created or files placed will be yours.  If you want to put a link to your home, just ---

example
ln -s /path/to/real/file /path/to/non-existant/file

in my pc I used this

ln -s /media/disk/someguy-stuff/me-High_Definition-Recorded /home/someguy/me-High_Definition-Recorded

so now I have in my home a link to my folder that goes in that hardrive.

If you are having issues with the drive automounting at startup, just post here and we will help you with this.  It is so easy!

---

### Post by Ripfox on 2008-05-11
Ok if it's /dev/disk (example)

open a terminal (applications/accessories/terminal) and type

sudo chmod -R 755 /dev/disk (example)

and it will ask for your password

If I am wrong someone tell me, but I have used this to fix permission problems on a lot of my external/usb hdds

---

### Post by egwest on 2008-05-11
> **DarkSaga70 said:**
> ok i understand how to find it. On my PC its either dev/disk  or media/disk. However I m not sure how to run that sudo command on it because I can not figure out how to even get to that in the term. So please explain. Sorry for all this but I have came a long way from windows and I refuse to go back and even though I ask a lot of questions on here I have learned a lot.


We all have to start somewhere to learn. Go up and click on Applications, then go in to the Accessories menu and down to Terminal and click on that.

Sudo command puts you in temporary Root User control so you can run system commands. Just copy the and paste the command in the quote box '***ripfox***' gave you.

Check out this site, 

[http://paulstamatiou.com/2005/10/24/how-to-ubuntu-linux-for-novices](http://paulstamatiou.com/2005/10/24/how-to-ubuntu-linux-for-novices)

it got me started in the basics, from there I have bought some books to help me further along. Although I am way far from being even remotely experienced enough to feel conformable with passing along information in regards to system commands. I am getting there and learning as I use the system.

Most important thing to remember, if you are ever in doubt of running a command or not sure how it will affect your system, make sure you stop by here first and ask!

---

### Post by DarkSaga70 on 2008-05-11
Hey I got it !!!  Thanks a lot for all the fast replies and help.

---

### Post by Ripfox on 2008-05-11
Did my command do it? Just curious.

---

### Post by DarkSaga70 on 2008-05-11
actualy I tried yours and could not get it to work so I went with the nautalis route but I do appreciate your help :)

---

### Post by Ripfox on 2008-05-11
Cool...probably the syntax (I forget commands, I'm old now) :lolflag:

Don't forget to use "thread tools" and mark it as solved :)

---

