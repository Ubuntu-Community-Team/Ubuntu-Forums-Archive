---
title: "How to create a system image or backup in 12.04??"
date: 2012-06-25
forum: New to Ubuntu
---

### Post by rafsuntaskin on 2012-06-25
I have **12.04** installed and I have **updated** with many other updates like 300-400 mb of updates **via update manager**. So, I want to **create a backup of my ubuntu system **So that whenever I **reinstall** ubuntu I can **use the backup to get my current updated ubuntu. **

---

### Post by CharlesA on 2012-06-25
remastersys should work.

Otherwise just clone the drive.

---

### Post by rafsuntaskin on 2012-06-25
> **CharlesA said:**
> remastersys should work.

Otherwise just clone the drive.


A little more details would help much more  .....  :p

---

### Post by CharlesA on 2012-06-25
[http://www.remastersys.com/](http://www.remastersys.com/)

---

### Post by mkstallings1 on 2012-06-25
I always use a copy of Clonezilla.  Google it to go to the website, download the .iso, burn a disc or put it on a thumb drive.  Put the disc in the drive or plug in the thumb drive and reboot,  Follow the on screen instructions and backup to an external harddrive.  I've done it a million times and never had a problem.

---

### Post by rafsuntaskin on 2012-06-30
OK, I have setup my system with WUBI.. SO will cloning  the drive is apporpriate??

---

### Post by CharlesA on 2012-06-30
> **rafsuntaskin said:**
> OK, I have setup my system with WUBI.. SO will cloning  the drive is apporpriate??
That will make cloning the "drive" difficult because wubi installs Ubuntu onto a virtual drive on the C drive and uses the Windows boot loader to start it.

If you want to move the Wubi install to a real partition see here:
[https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)

---

### Post by mkstallings1 on 2012-07-02
I could be mistaken, but I would certainly clone the entire drive before you attempt to move your wubi install.  That way, if you mess up, you can at least go back to what you have.

---

### Post by CharlesA on 2012-07-02
> **mkstallings1 said:**
> I could be mistaken, but I would certainly clone the entire drive before you attempt to move your wubi install.  That way, if you mess up, you can at least go back to what you have.
Agreed. That way if the migration goes back, you can restore the whole drive from backups and try again.

---

### Post by O2Blevel on 2012-07-02
You could also copy the ubuntu folder that is on your windows system drive and use that as a backup. If you don't have very much     space available you can compress it.

---

### Post by dvks on 2012-07-03
As CharlesA suggested- use remastersys and you will thank him for taking the time to install it.
 
[http://www.remastersys.com/ubuntu.html](http://www.remastersys.com/ubuntu.html)
Go to the bottom of the page for manual installation and find the following instructions:
 
[COLOR=black][FONT=Verdana][COLOR=black][FONT=Verdana]Download and apply the repository gpg key:[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]wget -O - [[COLOR=#444444]http://www.remastersys.com/ubuntu/remastersys.gpg.key[/COLOR]]("http://www.remastersys.com/ubuntu/remastersys.gpg.key") | apt-key add -[/FONT][/COLOR]
 
[SIZE=3][FONT=Calibri]Add the following line that corresponds to your version of Ubuntu to your /etc/apt/sources.list[/FONT][/SIZE]
[COLOR=black][FONT=Verdana]# Remastersys for UBUNTU Precise[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]deb [[COLOR=#444444]http://www.remastersys.com/ubuntu[/COLOR]]("http://www.remastersys.com/ubuntu") precise main[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Now run the following commands:[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]apt-get update [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]apt-get install remastersys[/FONT][/COLOR]
 
 
[FONT=Calibri][SIZE=3][FONT=Calibri]Test the new Remastersys:[/FONT][/SIZE][/FONT]
[FONT=Calibri][SIZE=3][FONT=Calibri]sudo remastersys clean[/FONT][/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3][FONT=Calibri]To install the new Remastersys GUI [/FONT][/SIZE][/FONT]
[FONT=Calibri][SIZE=3][FONT=Calibri]sudo apt-get install remastersys-gui[/FONT][/SIZE][/FONT]
[FONT=Calibri][SIZE=3][FONT=Calibri]Or[/FONT][/SIZE][/FONT]
[FONT=Calibri][SIZE=3][FONT=Calibri]sudo apt-get install remastersys-gtk[/FONT][/SIZE][/FONT]
 
[FONT=Calibri][FONT=Calibri][SIZE=3]====================================[/SIZE][/FONT][/FONT]
 
[FONT=Calibri][SIZE=3][FONT=Calibri]For creation of a new system backup call: [/FONT][/SIZE][/FONT]
[SIZE=3][FONT=Calibri][FONT=Calibri]sudo remastersys backup filename.iso[/FONT][/FONT][/SIZE]
[FONT=Calibri][SIZE=3][FONT=Calibri]This will create the system backup file under folder /home/remastersys[/FONT][/SIZE][/FONT]
[FONT=Calibri][SIZE=3][FONT=Calibri]Always clean remastersys generated files before creating backup or distribution[/FONT][/SIZE][/FONT]
 
**[FONT=Calibri][FONT=Calibri]Create a new distribution ISO image of you current system:[/FONT][/FONT]**
[SIZE=3][FONT=Calibri][FONT=Calibri]sudo remastersys dist[/FONT][FONT=Calibri] YOU MUST RUN AS ROOT!!![/FONT][/FONT][/SIZE]
[FONT=Calibri][SIZE=3][FONT=Calibri]The new ISO file will be saved under /home/remastersys/remastersys/xxxxxxx.iso[/FONT][/SIZE][/FONT]
 
Enjoy remastersys it is a very good package.[/FONT][/COLOR]

---

