---
title: "i think ive broke it"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by colcol on 2008-11-01
Hi i tried ubuntu some time ago on my last pc,live cd and dual boot with xp but was confused. After getting new pc with vista on it its an hp pc and windows and restore are built in to hard drive, i decided ive had enough of vista and to try ubuntu again i d/l ubuntu 8.10 and ran as live cd no problems but when i took disc out and went into my computer my 250 gig hard drive now said it was 110 gig,i restarted pc and thought lets install ubuntu as dual boot again did what i did in the past but now when i start pc there is no option for logging into vista and once loaded ubuntu i can not find icon for hard drive to see how much storage is assinged to it please help how do i get vista back i still need it for a few progs and wheres my hard drive info on ubuntu ive looked in my placeshome etc etc oh and when i start pc f11 is supposed to kick in system recovery but now does nothing whats happened to my pc

---

### Post by lisati on 2008-11-01
Safely navigating around partitions has its traps to avoid.

Does your Vista partition show up when you enter the following command at the terminal?
```
sudo fdisk -l
```

---

### Post by colcol on 2008-11-01
opened terminal and typed it in all i got command not found

---

### Post by colcol on 2008-11-01
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xee748692

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29646   238131463+  83  Linux
/dev/sda2           29647       30401     6064537+   5  Extended
/dev/sda5           29647       30401     6064506   82  Linux swap / Solaris
colcol@colcol-desktop:~$ 



this is what ive managed to get as you see my 250 hd is showing but where is windows

---

### Post by akiratheoni on 2008-11-01
> **colcol said:**
> Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xee748692

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29646   238131463+  83  Linux
/dev/sda2           29647       30401     6064537+   5  Extended
/dev/sda5           29647       30401     6064506   82  Linux swap / Solaris
colcol@colcol-desktop:~$ 



this is what ive managed to get as you see my 250 hd is showing but where is windows


It doesn't look like Windows is on there... if there was, there would be an NTFS partition and there is only Linux and swap.

---

### Post by colcol on 2008-11-01
so does this mean ubuntu has wiped vista from my system if so i have stuff i need to use and now can not

---

### Post by ugm6hr on 2008-11-01
> **colcol said:**
> so does this mean ubuntu has wiped vista from my system if so i have stuff i need to use and now can not

You sure you didn't use the "auto" install option to use entire disk?

It looks like Ubuntu has been installed on entire HD, wiping Vista and your restore partition.  The way the partitions are set up are the default auto install for Ubuntu.

Unfortunately, if you didn't have backups, it will be very difficult (without expensive commercial services) to retrieve that data.

---

### Post by colcol on 2008-11-01
oh well i wanted to be rid off windows one day,guess ill have to learn to grasp ubuntu quicker than i thought, but if i bought a windows disc i could reinstall it yes

---

### Post by 3rdalbum on 2008-11-01
You've learnt the hard way. For anyone looking up this topic in future: Always make backups before doing anything with partitions! Even if you think everything will go alright, make a backup.

---

### Post by roger_1960 on 2008-11-01
Hi

If you bought it from HP, presumably with a vista licence, you could try asking them for an installation disk?

---

### Post by colcol on 2008-11-01
Yes it came with vista preinstalled and license was built in unfortunately i did not write it down but if i give them the serial no etc they should be able to trace it i think ill give that a try many thanks to all, and ive just found out how to open some of my works spreadsheets in open office ive started learning already one day good bye mr gates

---

### Post by colcol on 2008-11-01
many thanks for all advice.can i ask another question how do i back up using ubuntu, i can not seem to locate any software to do it i think im using gnome if that any use im not sure what all this gnome and kde is as yet but getting there

---

### Post by mdpalow on 2008-11-01
> **colcol said:**
> ... Can i ask another question how do i back up using ubuntu, i can not seem to locate any software to do it i think im using gnome if that any use im not sure what all this gnome and kde is as yet but getting there

Hi Colcol,

You can try QuickStart for your back-up needs. See my signature below for the link.

Good Luck

---

### Post by roger_1960 on 2008-11-01
Hi

pybackpack in the repositories - use synaptic to get it - is really easy and simple if thats what you need.

---

### Post by ugm6hr on 2008-11-01
I use **grsync** to backup just my /home folder.

Install it from Synaptic.

---

### Post by bruce2000 on 2008-11-01
Edit: Nevermind sorry :)

Hi Colcol, Im also from the north of england with a hp laptop running vista. Id be happy to mail you the recovery disks, mine is a hp 530 i dont know whether they would work on other models. PM me if youre interested

---

### Post by colcol on 2008-11-03
Thanks Roger have been in touch wit HP and ordered a recovery disc cost £25:90 so not to bad but a lesson learnt, having said that ubuntu 8.10 seems to doing just fine i just have to work out copying/making cd;s and dvd,d,s gonna try audacity for cd but havent a clue how to do dvd colcol

---

### Post by Barrucadu on 2008-11-03
k3b is a very good program for burning/copying/whatevering discs, but if you're using GNOME it'll look a bit out of place as it is a KDE program.
You said you don't know the difference between GNOME and KDE well, the simplest way to put it is, they both have different, ways of drawing the interface of applications, so they look different.
GNOME and KDE are both desktop environments, they give you a wallpaper, panels, menus, et cetera.

---

### Post by colcol on 2008-11-03
so how would i change from gnome to kde and would it affect anything ive already done under gnome ie put music into folder etc

---

### Post by spider_dijon on 2008-11-03
Partitions can be a real hassle lol. I just installed ubuntu 8.04 onto a new studio 15 using paragon hard disc managing software.. sorted out all the partitions and went ahead with the instalation, when i had both up and running i was pretty happy, but for some reason ubuntu wasnt letting me install any updates or plugins. So i thought i would go ahead and install 8.10.. didnt adjust my partitions and i have ended up with a couple of extra partitions that i didnt want because ubuntu changed them! lol all in all though im loving ubuntu!

---

### Post by colcol on 2008-11-03
the only thing is im now getting paranoid as there is no pop ups saying someone tried to connect to my pc etc from firewalls, anti virus etc and wonder when do you settle down and just trust all is ok

---

### Post by nothingspecial on 2008-11-03
> **colcol said:**
> so how would i change from gnome to kde and would it affect anything ive already done under gnome ie put music into folder etc
```

sudo apt-get install kubuntu-desktop
``` Then you can select kubuntu or ubuntu at boot. It makes everything a bit messy though. It won`t affecy anything you`ve done already.
If like me you don`t like having gnome and kde see this -

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

It`s useful to try both though.

Infact read that whole website, bookmark it. It`s great for new ubuntu users.

:)

---

### Post by itisbasi on 2008-11-03
> **colcol said:**
> the only thing is im now getting paranoid as there is no pop ups saying someone tried to connect to my pc etc from firewalls, anti virus etc and wonder when do you settle down and just trust all is ok
Lol....you've got withdrawal symptoms, as you've been used to windows for so long...Happened to me too...don't worry, you'll get used to ubuntu very soon and realize that it's pretty secure..

---

