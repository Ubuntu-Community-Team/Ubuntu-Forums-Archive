---
title: "Really cannot understand mount , fdstab ... any tutorial  or help"
date: 2012-09-27
forum: New to Ubuntu
---

### Post by cp2819 on 2012-09-27
hi
I am a newbie trying to test and learn Linux especially Ubuntu
I have read some documentations but really cannot understand how 
mount ... and all the fdstab stuffs work
If someone can help or give me a good clear tutorial link 

especially I cannot understand why sometimes some distros I can see devices mounted and other time, I don't see anything
secondly, for example if I boot from Ubuntu LIVECD (not rewritable) with the idea to get access to a hard disk with problem trying to save data files for example ...
how can I mount ? and see the partitions of the hard disk when I cannot write on the LIVECD

you see, I admit I am confused about all these things , (sorry because I begin just to discover and have million questions at each step..)
and perhaps I am mixing up everything

thanks

---

### Post by mikewhatever on 2012-09-27
Here you go: [FSTAB]("https://help.ubuntu.com/community/Fstab")

When ruuning from a Live CD, use **sudo fdisk -l** to see partitions on the hdd. To mount a partition, use the **mount** command, for example:

```
sudo mount /dev/sda1 /mnt
```

If all goes well, files on /dev/sda1 should be accesible through /mnt/.

---

### Post by cp2819 on 2012-09-27
thanks a lot for the link

ok, I understand now the mount command does not "wirte" on the Ubuntu system from which I boot (Live CD) but it "write" on the HD to mount .... right ?

In this case, dos it "write" something somewhere ? or just stay in memory ?
then how about when I type the command mount to mount a dvd on the same system with a supposed failed HD ? where does it "write"?


I decide to open a new thread because I need to learn by doing thing and start from the beginning step by step experimenting by myself...

---

### Post by mikewhatever on 2012-09-27
What do you mean by "write"? The mount command doesn't write anything anywhere, it mounts file systems, by may be I didn't quete get your meaning.

---

### Post by cp2819 on 2012-09-27
sorry Mike

It's just me, 
because I thought the command mount "write" something on the HDD, just like a directory in /mount
You see I am mixing up everything

---

### Post by cp2819 on 2012-09-27
mount command

I am getting confused

On my system , when I plug an USB key

it appears as /dev/sdb1

I have to  type 

mkdir /media/usb
and
mount /dev/sdb1 /media/usb

so the command mount have to access a real directory "written" in my partition at the location /media/usb
 right ?

---

### Post by wheeze on 2012-09-27
> **cp2819 said:**
> so the command mount have to access a real directory "written" in my partition at the location /media/usb
 right ?

Yes, the mount command needs a location to mount your partition at. The basic idea of mount goes like this; pretend you're telling your computer the following:

I want to [COLOR=Red]**mount**[/COLOR] one of hard drive [COLOR=Blue]**partition**[/COLOR]s at this [COLOR=Purple]**location**[/COLOR] in the filesystem.

[COLOR=Red]mount[/COLOR]  [COLOR=Blue]/dev/sdb1 [/COLOR] [COLOR=Purple]/media/usb[/COLOR]

---

### Post by cp2819 on 2012-09-27
> **wheeze said:**
> Yes, the mount command needs a location to mount your partition at. The basic idea of mount goes like this; pretend you're telling your computer the following:

I want to [COLOR=Red]**mount**[/COLOR] one of hard drive [COLOR=Blue]**partition**[/COLOR]s at this [COLOR=Purple]**location**[/COLOR] in the filesystem.

[COLOR=Red]mount[/COLOR]  [COLOR=Blue]/dev/sdb1 [/COLOR] [COLOR=Purple]/media/usb[/COLOR]


ok

but what make me confused is this situation exactly :
when you boot on a livecd, to access to a system with a supposed failed hdd, to save data on this hdd.
you cannot "write" on the LiveCD 
mount /dev/sda /media/harddisk
to access to the hard disk
because the cd is not writable

So... where do you "write" the mount command to have access to the hdd ?

---

### Post by deadflowr on 2012-09-27
When you boot a LiveCD, the LiveCd loads itself into your systems RAM, giving you temporary read/write access.
Think of it like this, the LiveCd is like a textbook, immutable(read only), your hard drive is like a personal journal(you can set it to read only{pen} or read/write{pencil}, and the RAM is like a chalk board(you can copy the files from the others to the RAM on a temporary basis, and when it's done, it wipes itself clean).
However, if your running Ubuntu, just open the file manager(Home Folder) and click on the drive you need listed in devices. This will mount the drives you want.
Fstab automounts devices on boot.

---

### Post by cp2819 on 2012-09-27
> **deadflowr said:**
> When you boot a LiveCD, the LiveCd loads itself into your systems RAM, giving you temporary read/write access.
Think of it like this, the LiveCd is like a textbook, immutable(read only), your hard drive is like a personal journal(you can set it to read only{pen} or read/write{pencil}, and the RAM is like a chalk board(you can copy the files from the others to the RAM on a temporary basis, and when it's done, it wipes itself clean).
However, if your running Ubuntu, just open the file manager(Home Folder) and click on the drive you need listed in devices. This will mount the drives you want.
Fstab automounts devices on boot.


thanks for your very clear explanations

I open the home folder and click on the drive as you said, then I check the /media folder.
Effectively, there is a folder corresponding to the drive I clicked on

But ... why the name of the folder is TOO complicated ??? 
something like 482021FA2021EF9C ughh...

when using the terminal to copy files , I have to typed /media/482021FA2021EF9C !!!

---

### Post by lisati on 2012-09-27
You might want to think of "mounting" as placing a book on the table, and telling the person who is going to use it that it's available on that particular table. Then there's permissions: some books you can write in, some you should only read from.

"Unmounting" is the reverse process, it puts out the word that the "book" is no longer available for use. The "Safely remove hardware" option takes the idea a bit further, allowing the system the chance to finish what it's doing, e.g. write data to disk from the cache, before unmounting.

---

### Post by 1clue on 2012-09-27
deadflowr is right, but (s)he did not use the word "ramdisk" which I think would be helpful in understanding what's going on.

The big long string of characters is a UUID.  In theory, the UUID of every individual storage device and/or partition would be unique.  I use that for assembling RAID arrays and such, it's great.

If the disk is already mounted you can use tab completion.  For example:

**cd /media/4<tab>**

The command line has an autocompletion feature.

Of course if you're making an /etc/fstab entry for a filesystem to be mounted regularly and consistently you'll want to use a directory name which makes sense.  For example, you could use that partition as /home if you want.  Don't experiment there, you could cause yourself quite a bit of grief that way.  Try making a directory someplace which is not used and mount there at first.

---

### Post by cp2819 on 2012-09-27
waow 

I have to thank you all
In just one day, I learn really a lot of things from you all
Things are getting more and more clear in my mind now !

the autocompletion ....  I love Linux !!!!

---

### Post by deadflowr on 2012-09-27
I hope your endeavor has been somewhat successful.
The reason why the mount shows up as the UUID is because the drive has not been labelled(named). If you were to give the drive a name, the name would show up in /media/givenname, if no name was created, it default to the device id. I personally name all my drives(Either through disk utility, or other means).
It is nice that you can use graphical, and/or command line means to achieve a goal.

BTW, even though, I'm very effeminate, I am sadly, a boy.

---

### Post by 1clue on 2012-09-27
> **deadflowr said:**
> BTW, even though, I'm very effeminate, I am sadly, a boy.

I didn't mean any disrespect.  I know there are a lot of female Linux people out there, and lots of them choose androgynous(gender-unspecified) handles.  I can't tell from how you type, so I tried to take all possibilities into account.

---

### Post by deadflowr on 2012-09-27
> **1clue said:**
> I didn't mean any disrespect.  I know there are a lot of female Linux people out there, and lots of them choose androgynous(gender-unspecified) handles.  I can't tell from how you type, so I tried to take all possibilities into account.

No offense taken. 
Also I'm not a cartoon character, either.(As my avatar would have you believe).:lolflag:

---

### Post by cp2819 on 2012-09-28
> **deadflowr said:**
> No offense taken. 
Also I'm not a cartoon character, either.(As my avatar would have you believe).:lolflag:


haha LOL
boy, girl, cartoon fan ? 
all I see is the BIG sign in front of the heart of your avatar !!!:D

you are simply a very generous Ubuntu guru

---------------------------------
question :
when I put on an Usb key , it is mounted automatically vy Ubutu
and I can have access to it via nautilus.. ok
Just for testing
can I unmouted  (just for testing and learning)

umount /dev/sdb

and mount it again in /media/usb I created ?

mkdir /media/usb
mount /dev/sdb /media/usb ??

---

