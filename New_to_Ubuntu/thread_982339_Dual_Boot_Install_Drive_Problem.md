---
title: "Dual Boot Install Drive Problem"
date: 2008-11-14
forum: New to Ubuntu
---

### Post by BoomBoxer on 2008-11-14
Hey guys i am after some help, i found a guide on the net explaining how to install UBUNTU as a dual boot on a system that already has Vista installed and have stumbled at the second hurdle, basically i shrunk my c: partition to give me free space as it says to do in the guide, now i come to install UBUNTU but instead of seeing any of my partitions it just sees 2 x 500gb drives. They are actually in RAID and show in windows as just one disc.

Hope someone can help thnx Lee.

P.S The guide tells me to use the Guided - Use the largest continous disk space to install but i dont even have this option.

---

### Post by Bölvaður on 2008-11-14
Might that second partition actually be empty space?

You should always make the partitions in gparted (Partition Manager). And then go to manual instead of guided.. I doubt that the installer knows better than you what you want.

Lets begin:

Fire up gparted from alt+F2 and type gparted (or System->Administration->Partition Manager)

Make 3 partitions like so:

1. 12 GB   ext3
2. rest*    ext3
3. ram**    linuxswap

*rest is what ever amount you can spare for all your user data. You can make it simple and just not make this partition, but it is wiser and safer than not having one.

**ram = the size of your ram, this is a partition dedicated to what you might know was "page file"


now you got your 3 partitions ready to be used :)
In the installation process, you are asked what part of your hd you want to use, pick manual because you want to do it your self.

Mount the 1. partition to / (you can find it in dropdown list) and have ext3 filesystem on it
Mount the 2. partition to /home (find it in dropdown list) and have ext3 filesystem on it.

Now you are ready to continue :) good luck

---

### Post by mapes12 on 2008-11-14
> They are actually in RAID and show in windows as just one disc.

That may be so but how many physical HDD's do you have? Can you post the output to ```
sudo fdisk -l
``` please.

Bölvaður post is spot on but we need to establish what your HDD configuration is before pressing ahead.

---

### Post by BoomBoxer on 2008-11-14
I run Ubuntu off the CD so i could try the gparted thing but it said something about i dont have root permission or similar. if its any help i do know 100% that my 2 raided drives are partitioned as 

c: vista os and files around 600gb
k: TV Recordings around 200gb
l: 146gb Partition Totally empty

and there is also 10gb of free space that isnt partitioned at all

the problem is the CD installer sees none of this just 2 x 500gb drives.

any ideas what to do now?

Thnx Lee.

---

### Post by fiddler616 on 2008-11-14
Edit: Never mind. People responded while I was writing.

---

### Post by BoomBoxer on 2008-11-14
I have 2 x 500gb Physical Disks

Thnx

---

### Post by fiddler616 on 2008-11-14
> **BoomBoxer said:**
> 
the problem is the CD installer sees none of this just 2 x 500gb drives.

any ideas what to do now?

Thnx Lee.
And you're using "Manual", not "Guided"?

---

### Post by BoomBoxer on 2008-11-14
Yeah its great that this forum is so active but its hard to keep up when people respond as you type lol :) im not complaining though its real nice to find an active forum like this :)

Im sure i will get this sorted with the help here :)

---

### Post by BoomBoxer on 2008-11-14
Yup Manual just "see's" 2 x 500gb drives

---

### Post by fiddler616 on 2008-11-14
> **BoomBoxer said:**
> Yup Manual just "see's" 2 x 500gb drives
And it says each only has one partition on it?
What type? (NTFS, Ext3, etc?)

I'm sorry if I seem kinda inquisitive, I just am finding this kinda incredible...

---

### Post by BoomBoxer on 2008-11-14
Hmm i cant quite remember give me 5min and ill try the install now and write it down brb. Thnx

---

### Post by BoomBoxer on 2008-11-14
Ok this is what it says

It shows 2 drives being SCSI 000 SDA 500.1GB ATA ST350030AS

and the other SDB

When i click manual and next it asks me either /DEV/SDA or /DEV/SDB if i select either it says no root system defined, does this mean anything to you?

---

### Post by BoomBoxer on 2008-11-14
Its as if it just isnt recognising none of the Raid or the partitions on there, strange isnt it?

Cheers Lee

---

### Post by fiddler616 on 2008-11-14
> **BoomBoxer said:**
> Its as if it just isnt recognising none of the Raid or the partitions on there, strange isnt it?

Cheers Lee
Yes, very strange.

I hate to say it, but this is surpassing my knowledge :( (I actually have yet to use a RAID array...) so I leave it up to the rest of the Forum....
Sorry I couldn't be more helpful.

---

### Post by BoomBoxer on 2008-11-14
Its ok mate thnx for trying i appreciate it, i am sure i will get it sorted at some point with everyone on here being so helpfull!

Cheers Lee.

---

### Post by fiddler616 on 2008-11-14
> **BoomBoxer said:**
> Its ok mate thnx for trying i appreciate it, i am sure i will get it sorted at some point with everyone on here being so helpfull!

Cheers Lee.
I'm interested in how this is going to get fixed--let me know when it gets solved.

---

### Post by BoomBoxer on 2008-11-14
Not sure if this helps anyone but now i have cancelled the install and i have droped back into Ubuntu if i click on my computer in places i do not see any hard disk what so ever.

Thnx

Edit - No probs will let you know mate!

---

### Post by fiddler616 on 2008-11-14
> **BoomBoxer said:**
> Not sure if this helps anyone but now i have cancelled the install and i have droped back into Ubuntu if i click on my computer in places i do not see any hard disk what so ever.

Thnx

Edit - No probs will let you know mate!
I believe you have to mount it. Try the Places menu--you should see a list of xxGB media, and you can mount it from there. Although I feel like it should automount....so don't hold me to that. My final 2 cents before I go to bed.

---

### Post by BoomBoxer on 2008-11-14
Yep i looked in the places menu but the drives arnt in there, im going to bed too now hopefully ill work it out tomorrow.

Cheers lee.

---

### Post by caljohnsmith on 2008-11-14
So do you know if you are using software RAID or hardware RAID? It sounds like you might be using a software RAID setup since Ubuntu sees both of the drives as separate. You might want to check out these links at the Ubuntu help site:

[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
[https://help.ubuntu.com/community/Installation/LVMOnRaid](https://help.ubuntu.com/community/Installation/LVMOnRaid)

---

### Post by BoomBoxer on 2008-11-15
Hmmm well Nvidia Mediashield is the very first thing that flashes up when i switch on my machine even before the BIOS screen comes on, i am pretty sure this is a Hardware Raid built into the Motherboard is that correct? If it helps the machine is an Dell XPS 720 I really hope i can get this sorted from what i have seen of Ubuntu so far i like :)

Cheers Lee.

---

### Post by BoomBoxer on 2008-11-16
Hi again guys, after reading those links i am starting to think you are right and i have a fakeRaid, is there any way for me to easily install Ubuntu on one of the partitions i have made without loosing all of my vista install and files? If it ends up getting really complicated i may have to give up on having Ubuntu on my PC :(

Cheers Lee.

---

### Post by fiddler616 on 2008-11-16
> **BoomBoxer said:**
> Hi again guys, after reading those links i am starting to think you are right and i have a fakeRaid, is there any way for me to easily install Ubuntu on one of the partitions i have made without loosing all of my vista install and files? If it ends up getting really complicated i may have to give up on having Ubuntu on my PC :(

Cheers Lee.

Well just making a new partition from gparted (read: partition editor) in the installation should do the trick...

---

