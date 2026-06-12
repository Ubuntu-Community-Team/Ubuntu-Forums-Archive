---
title: "my 500GB is empty today"
date: 2014-06-19
forum: New to Ubuntu
---

### Post by czgirb on 2014-06-19
Currently, I'm using Ubuntu Pangolin
Yesterday, my external HDD **500GB NTFS** is OK and I able to play a video for my child to see.
Today, when I tried to explore it ... i found it's empty.
Why?
I tried to check it via GParted ... but the given information is the same. Emptied. and the available space is 499GB.
Why?
Remembered I do not make any "FORMAT" activities upon it yesterday. But today it's said to be empty, like a new HDD.
Please help me ...

---

### Post by Matthew_Smith on 2014-06-19
Hmm... What DID you do to your Linux yesterday?

---

### Post by Mark Phelps on 2014-06-19
Did you have your external drive plugged into a PC when that PC was running Windows?

---

### Post by czgirb on 2014-06-19
> **Matthew_Smith said:**
> Hmm... What DID you do to your Linux yesterday?
As I remembered, I only open **firefox**, **deadbeef**, and **puddletag**

> **Mark Phelps said:**
> Did you have your external drive plugged into a PC when that PC was running Windows?
There is no windows OS in within my lappie. My **external HDD (X-HDD)** has to be **NTFS**, due to **when I give Ubuntu a try, my X-HDD is 450GB fully occupied**.
and I unable to move elsewhere.
If now, if it really empty, the X-HDD will be formated to **ext4**. :D :D :D

---

### Post by Impavidus on 2014-06-20
Can you access the drive from a Windows pc? Maybe it needs a file system check. Also, if you want to recover something, best to use Windows tools on ntfs drives.

If you don't have Windows systems it's indeed best to avoid ntfs altogether.

---

### Post by kansasnoob on 2014-06-20
I would think that TestDisk may be useful:

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

I don't use it frequently enough to be able to give any advice but I always begin with that page if I'm dealing with NTFS.

---

### Post by czgirb on 2014-06-23
Checked the external HDD in windows XP ... it's empty.
Is the problem was occur due to the **NTFS** ?
Yesterday, I tried to re-fromat the HDD to **ext4** with **GParted**. (All process **much more faster** than NTFS, no more than 5 minute)
But after all finished, I face 2-problems :
* it always requires me to be a root in order to modify the HDD contains. add a new file or a new folder
* and I unable to change the HDD label as I desired
why?

**PS:**
Sorry my Ubuntu knowledge is poor

---

### Post by LastDino on 2014-06-23
You need to change permissions.

**1** - Connect your HD. Go to **Terminal**, copy & paste this command: **```
 gksudo nautilus 
```** that will open nautilus as root

**2** - Navigate to your drive, **Right Click**, select the **Permissions** tab 

**3** - Change the **Owner** drop-down menu to your name, then change **Folder Access** to **Create & Delete Files**, then **File Access** to **Read & Write**, then **Group** to your name, **Folder Access** to **Create & Delete Files**, **File Access** to **Read & Write** then click **Apply Permissions To Enclosed Files**.

**4 **- Close nautilus imdiately after this as this is not recommended practice.

---

### Post by czgirb on 2014-06-23
> **LastDino said:**
> You need to change permissions.

**1** - Connect your HD. Go to **Terminal**, copy & paste this command: **```
 gksudo nautilus 
```** that will open nautilus as root

**2** - Navigate to your drive, **Right Click**, select the **Permissions** tab 

**3** - Change the **Owner** drop-down menu to your name, then change **Folder Access** to **Create & Delete Files**, then **File Access** to **Read & Write**, then **Group** to your name, **Folder Access** to **Create & Delete Files**, **File Access** to **Read & Write** then click **Apply Permissions To Enclosed Files**.

**4 **- Close nautilus imdiately after this as this is not recommended practice.


Thank you for the guidance
but i unable to try it due i have no ubuntu with me now.
tonight will reported to you
thank you

---

### Post by czgirb on 2014-06-23
[SIZE=4][SIZE=3]Checked the external HDD in windows XP ... it's empty.[/SIZE]
Is the problem was occur due to the **NTFS** ?[/SIZE]

---

### Post by LastDino on 2014-06-23
If you checked it after formatting it to ext4, then yeah, Windows can't read that format.

---

### Post by czgirb on 2014-06-23
> **LastDino said:**
> If you checked it after formatting it to ext4, then yeah, Windows can't read that format.

No! No! No! After **ubuntu** say that it's empty, i check the HDD in windows XP.
and used **recuva** to order to see what file able to be rescued. after make a copy of that files.
i re-format it to **ext4**.

i really do not know why all files within the HDD is gone.
so I ask, if the problem was occur due to the NTFS?

---

### Post by LastDino on 2014-06-23
Ubuntu can read NTFS fine, so probably not, I use NTFS external drive too. There is no way to tell what went wrong with yours from here tbh, especially since you've formatted it with ext4.

---

### Post by czgirb on 2014-06-23
> **LastDino said:**
> You need to change permissions.

**1** - Connect your HD. Go to **Terminal**, copy & paste this command: **```
 gksudo nautilus 
```** that will open nautilus as root

**2** - Navigate to your drive, **Right Click**, select the **Permissions** tab 

**3** - Change the **Owner** drop-down menu to your name, then change **Folder Access** to **Create & Delete Files**, then **File Access** to **Read & Write**, then **Group** to your name, **Folder Access** to **Create & Delete Files**, **File Access** to **Read & Write** then click **Apply Permissions To Enclosed Files**.

**4 **- Close nautilus imdiately after this as this is not recommended practice.

Do it as instruction given. And now, I able to create a new folder ... but I still **unable to change the label**.
everytime I click **Apply Permissions To Enclosed Files**, it seems reset all **File Access**, **Owner** and **Group**, to **------ (Empty)**

---

### Post by czgirb on 2014-06-24
please, everybody ...
please help me ...

---

### Post by Impavidus on 2014-06-24
If you want to change partition labels (I'm sure not what you want exactly... Or what your situation is right now.), any decent partition/disk tool can do so. I don't know which one is included by default nowadays, but gparted can change labels.

---

### Post by czgirb on 2014-06-25
> **Impavidus said:**
> If you want to change partition labels (I'm sure not what you want exactly... Or what your situation is right now.), any decent partition/disk tool can do so. I don't know which one is included by default nowadays, but gparted can change labels.

Strange ... before post this problem, I've tried to used **GParted**. But it do not write any label for my HDD.
But today, it's write. Strange ...
But no matter what ... I would like to say thank you for the guidance.

---

### Post by LastDino on 2014-06-26
It probably didn't because those drives were mounted?

---

