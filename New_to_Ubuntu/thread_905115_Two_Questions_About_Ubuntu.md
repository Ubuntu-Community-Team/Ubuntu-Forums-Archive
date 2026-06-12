---
title: "Two Questions About Ubuntu"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by MHarrison72 on 2008-08-30
Ok, I'm a complete n00b to Linux. First thing I was wondering, if why I cannot dual-boot Ubuntu. I'm a computer geek but I cannot get this to work. I'm running Vista and I have the hard drive partitioned. But when I try to boot from the burned CD, it will not load. So any ideas on how to fix that?
And my second question is, if I decided to only boot Ubuntu, is there a way to keep all of my files that are on Vista without backing them up?

---

### Post by nicedude on 2008-08-30
First question use the alternate CD version.

Second one you would have to post a list of your partitions as you may have recovery partitions for vista but if not then the answer would be no if you didn't setup a dual boot


PS just setup a dual boot with the alternate CD as that might be best until you decide whether you want to switch ( I hope you do though :-) )

Hope that helps

---

### Post by swoll1980 on 2008-08-30
You could make a third partition move your files to that erase the ms one then mount the partition with ubuntu to recover the data, or install ubuntu, and move the data right from the ms partition to the ubuntu one, but I wouldn't do any thing 'till
you back up your data

---

### Post by MHarrison72 on 2008-08-30
I downloaded the alternate CD last night and I need to try that. Also, there are three partitions on my hard drive. There is a 1.46 gig partition, which I don't know what it's for. Then there is 131.96 gig one that is the regular one for Vista. And finally, there is a 15.63 gig one that I have set as the partition for Ubuntu. So I'm guessing there is not a recovery partition.

---

### Post by wolfen69 on 2008-08-30
> **MHarrison72 said:**
>  is there a way to keep all of my files that are on Vista without backing them up?

sure, there is a way. don't lose them in the first place.

---

### Post by wolfen69 on 2008-08-30
the only way you can keep your files is to back them up. and back them up again.

---

### Post by ivikas on 2008-08-30
Hello,
       How did you partitioned your hard disk? Usually this can be done using manage disk from your vista.Make sure you have not deleted or modified recovery partition.If you have done so,it will effect dual booting and your vista will be in trouble.Now you have to change bios setting of your computer to make it boot from CD.If you have a 64 bit machine you have to select the 64 bit version of ubuntu or ortherwise the pc version.Again some devices "may" have problem like you mentioned,to make sure collect your hardware information and check for ubuntu hardware compactibility(just google it).And for the second question,as you said you've partitioned hard disk,one will where your vista resides and other will be used for ubuntu.At a time only one OS will be booted and vista will be perfectly safe if you do not modify your vista partition and it's recovery information.

---

### Post by MHarrison72 on 2008-08-30
I partitioned it though disk managment in Vista. I didn't delete any partitions so I wouldn't screw anything up on accident.

---

### Post by nicedude on 2008-08-30
1.46 gigs is too small for a recovery partition so if you don't know what it is then I would say you can delete it. Then I would also resize Vista down to a much smaller size ( 25-30GB ) Also don't create the Ubuntu partitions before hand you should get Gparted live CD to delete that 1.46 and resize Vista and also have Vistas partition reclaim the 1.46GB space assuming that is at begining of the drive. You could also create your data storage partition at the end of the drive then boot Vista and copy whatever you need to it for safety purposes. Also delete the EXT3 partition you made for Ubuntu as you should do that in the installer when installing Ubuntu. I would also plan to give Ubuntu more than 15GB ( 25-30GB ) and you will need a 2GB SWAP formated partition for Ubuntu ( its seperate from the system partition in linux unlike windows ) so just leave Vista at beggining resized and data at the end after calculating how big your data partition can be and still have  the free space in the middle for your Ubuntu system and swap partitions that you will make when you use the alternate CD to install. After the install you will have a proper dual boot PC with both Vista and Ubuntu and if you ever want to get rid of Vista you can use live gparted disk again to delete its partition and then add the space to Ubuntu if you ever so choose.


You can get a gparted live CD by googling for it and it is free and although it is also a live linux CD I think you will find that it will boot fine on your system unlike the Ubuntu live CD.

---

### Post by lovinglinux on 2008-08-30
> **MHarrison72 said:**
> I'm running Vista and I have the hard drive partitioned. But when I try to boot from the burned CD, it will not load. So any ideas on how to fix that?

I don't know if this is the case, but I tried Vista a while ago. When I decided to roll back to Windows XP I couldn't boot from XP CD. This was due to the way Vista format the hard drive. So I had to use a DOS program that completely  wiped all partitions, then I was able to boot from XP again and re-install it. Don't need to mention that Vista never get close to my computer again.

Anyways, I don't know if Ubuntu Live CD handles Vista partitions the same way, but this could be culprit.

---

### Post by SunnyRabbiera on 2008-08-30
actually it could be something simple as a bad burn.

---

### Post by lovinglinux on 2008-08-30
> **SunnyRabbiera said:**
> actually it could be something simple as a bad burn.

Yeap, if you follow the Occam's razor principle that would be the first choice.

---

### Post by nicedude on 2008-08-30
Live CD will resize and work with Vista partitions just fine, bad burn though is a definite possibility although some systems just won't boot the live CD which is why the alternate one exists ( on top of allowing install with weaker system specs )

---

### Post by ugm6hr on 2008-08-30
Indeed.  Make sure your LiveCD doesn't have errors.

Check md5 etc.  Burn at 4x or 8x speed to minimise errors.

Set BIOS for CD boot.

What happens when you try to boot the CD?

---

### Post by MHarrison72 on 2008-08-30
Bump

---

### Post by MHarrison72 on 2008-08-30
Thanks for all your help. I'll try them and let you know if it works.

---

### Post by MHarrison72 on 2008-08-30
When I try and boot the CD, it just goes to a black screen with some white writing on the top. It's something along the lines of Linux Disturbators.

---

### Post by ugm6hr on 2008-08-31
> **MHarrison72 said:**
> When I try and boot the CD, it just goes to a black screen with some white writing on the top. It's something along the lines of Linux Disturbators.

You say you know about computers, but you haven't given any detail about:
1. Type of CD (CD-R vs CD-RW)
2. How you burnt CD
3. Where you downloaded

You must appreciate it is impossible to help without knowing what you did.

Also - details about your hardware would help.

Try reading the "Start here" thread linked below for various helpful hints.

---

### Post by MHarrison72 on 2008-08-31
1. It's a DVD RW.(Might be the problem but the only CD I had that it would burn on)
2.I burnt the CD with Power ISO
3.I downloaded it from the Ubuntu Site

As for system specs...
AMD Turion(tm)64 X2 TL-58 1.90 GHz
4 Gigs of RAM
32 Bit Operating System
ATI Radon X1200

Everything is stock except for the RAM. I have a Toshiba Satalite A215 Series Laptop.

---

### Post by MHarrison72 on 2008-08-31
bump

---

### Post by MHarrison72 on 2008-09-01
bump

Also, I tried the alternate CD and once I got to the actual install portion, it said something was missing. I'm going to try and burn it again.

---

### Post by ugm6hr on 2008-09-02
Did you check MD5?  Have you tried running the check disc option?

I'd suggest a CD-R.

---

