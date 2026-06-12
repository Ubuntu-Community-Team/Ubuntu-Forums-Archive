---
title: "Defrag NTFS"
date: 2012-06-30
forum: New to Ubuntu
---

### Post by czgirb on 2012-06-30
Dear all!
Before using Ubuntu, I'm using Windows Vista ... so, my External Drive 500GB is NTFS.
Now I'm using Ubuntu ... and no Windows was installed in my lappie. But since my External Drive is NTFS and NTFS is needs to be defrag.
Yesterday I tried to installed the newest version of Defraggler and UltraDefrag via Wine.
But all display NOTHING.
What should I do?

---

### Post by goldshirt9 on 2012-06-30
can you see the hdd when plugged in.

you dont need to defrag under linux .

---

### Post by Shadius on 2012-06-30
If I understand correctly, your external hard drive is NTFS and you want to defragment it when it is plugged into your Ubuntu laptop?

---

### Post by Shadius on 2012-06-30
You could probably use [this]("http://portableapps.com/apps/utilities/jkdefrag_portable") program from a USB and point it to the external hard disk drive to defragment it. 

Check this [thread]("http://ubuntuforums.org/showthread.php?t=1521138") also.

---

### Post by czgirb on 2012-06-30
> **goldshirt9 said:**
> can you see the hdd when plugged in.
you dont need to defrag under linux .

Even if it was NTFS ... as long as it was works under Ubuntu, it will not need to be defrag?
According to what I know, Ext4 is not need any defrag ... but NTFS is.

> **Shadius said:**
> 
If I understand correctly, your external hard drive is NTFS and you want to defragment it when it is plugged into your Ubuntu laptop?

Yup!

---

### Post by Shadius on 2012-06-30
> **czgirb said:**
> Even if it was NTFS ... as long as it was works under Ubuntu, it will not need to be defrag?
According to what I know, Ext4 is not need any defrag ... but NTFS is.



Yup!

Ubuntu's filestyem of EXT4 doesn't need to be defragmented like how an NTFS filesystem does. I believe you can use that program from a USB to defragment your external NTFS hard disk drive. See my previous post.

---

### Post by Elfy on 2012-06-30
If you are not going to need to use the drive in windows anywhere I would be inclined to copy the data elsewhere - format the drive to ext4 and then copy the data back

---

### Post by Shadius on 2012-06-30
> **Elfy said:**
> If you are not going to need to use the drive in windows anywhere I would be inclined to copy the data elsewhere - format the drive to ext4 and then copy the data back

Agreed. If you no longer use Windows, why not backup the data currently on the hard disk drive and then format it to EXT4, or you could even partition the hard disk drive to have both NTFS and EXT4. That way, if you ever encounter a Windows sytem, you can use the NTFS partition.

---

### Post by afz12 on 2012-06-30
Hi czgirb

If you want to retain NTFS, you may be able to format it using Virtualbox to run either XP, Vista or Win7 as virtual machines. Virtualbox is free and reasonably easy to use - You can then run Ubuntu in parallel with Windows. Alternatively, you can format it through Ubuntus' disk utility to NTFS or Ext4. If you want to retain Windows OS then virtualizing may be worth considering - either Ubuntu virtualized on Win7 or Win7 virtualized on Ubuntu.

---

### Post by rai4shu2 on 2012-06-30
Furthermore, if you only use your drive for making backups, you don't really need to defrag. It's only when you're constantly moving files around on your drive that it gets fragmented in the first place.

---

### Post by Shadius on 2012-06-30
[]("http://www.ehow.com/how_7209024_defragment-ntfs-linux.html")I came across this. It also talks about EXT4 even though the title says EXT3. I might give this a try myself. 
[Defragmenting Linux EXT3 Filesystems]("http://www.webupd8.org/2009/10/defragmenting-linux-ext3-filesystems.html")

This was suggested to me also:
[Defragment NTFS using Linux]("http://www.ehow.com/how_7209024_defragment-ntfs-linux.html")

---

### Post by SuperFreak on 2012-06-30
[http://sourceforge.net/projects/defragfs/](http://sourceforge.net/projects/defragfs/)

[http://defragfs.sourceforge.net/](http://defragfs.sourceforge.net/)

Haven't tried this CLI program but apparently it will work on NTFS partitions on a Linux system

---

### Post by czgirb on 2012-07-01
> **Shadius said:**
> Agreed. If you no longer use Windows, why not backup the data currently on the hard disk drive and then format it to EXT4, or you could even partition the hard disk drive to have both NTFS and EXT4. That way, if you ever encounter a Windows sytem, you can use the NTFS partition.

I would like too.
But please be remind ... I only has 2 computers.
1 runs **Ubuntu 12.04** ... emptied space is **100GB**.
1 runs **Windows XP** ... emptied space is **200GB**.
In order to moved External HDD's file (**285GB**) into **100GB** and **200GB** is easy.
But, after I format the External HDD to **Ext4**, the data, to moved data in **Ext4** to **Ext4** is easy. But the data within **200GB** is placed within **NTFS** partition.
So ... **NTFS** is unable to read **Ext4**, right? How can it be moved back?

---

### Post by nipunshakya on 2012-07-01
Why don't you use your Windows XP to defrag the external drive?
[http://support.microsoft.com/kb/227463](http://support.microsoft.com/kb/227463)

---

### Post by miegiel on 2012-07-01
> **rai4shu2 said:**
> Furthermore, if you only use your drive for making backups, you don't really need to defrag. It's only when you're constantly moving files around on your drive that it gets fragmented in the first place.

Indeed, if there's no windows or programs installed on the disk (partition) then there is no real need to defrag it.

---

### Post by czgirb on 2012-07-02
> **WinuxUser said:**
> Why don't you use your Windows XP to defrag the external drive?
[http://support.microsoft.com/kb/227463](http://support.microsoft.com/kb/227463)

Yup! This is the WORST thing, which will be use only if I unable to defrag from Ubuntu.
If it able, I still wish to defrag directly via Ubuntu.

---

### Post by nipunshakya on 2012-07-02
> **czgirb said:**
> Yup! This is the WORST thing, which will be use only if I unable to defrag from Ubuntu.
If it able, I still wish to defrag directly via Ubuntu.

Well then its worth waiting until someone finds an app that can really defrag NTFS partitions in ubuntu...

---

### Post by dodo3773 on 2012-07-02
> **czgirb said:**
> Yup! This is the WORST thing, which will be use only if I unable to defrag from Ubuntu.
If it able, I still wish to defrag directly via Ubuntu.

No good solution exists at this time to defragment an ntfs drive directly from Ubuntu that I am aware of. If you are not willing to use a virtual machine to do this then you will have to write your own software probably. If you do find some fly by night way of doing this directly from a gnu system then good luck. Make sure to back up your data.

---

### Post by nipunshakya on 2012-07-02
> **dodo3773 said:**
> If you do find some fly by night way of doing this directly from a gnu system then good luck.

I was wanting to say the same thing...:guitar:

---

### Post by anewguy on 2012-07-02
I don't think you'll get it working via Wine since it is a USB drive.  Wine, at least as far as I know, doesn't support USB devices - it hasn't in the past (except for the keyboard, mouse and possibly a printer - but I think they are mapped anyway).

If your laptop can handle it, I'd install virtualbox, set up a Windows virtual machine and then do the defrag (if indeed you don't want it just EXT4).

---

### Post by Paqman on 2012-07-02
> **miegiel said:**
> Indeed, if there's no windows or programs installed on the disk (partition) then there is no real need to defrag it.

+1 to this.

Not having an operating system installed on the drive doing lots of little writes all over the place means it's likely fragmentation is very low. And since it's just data any fragmentation that exists is likely to have very little effect.

If you're worried about it, plug it into someone else's Windows machine once a year and run a defrag.

---

### Post by czgirb on 2012-07-02
> **Paqman said:**
> +1 to this.

Not having an operating system installed on the drive doing lots of little writes all over the place means it's likely fragmentation is very low. And since it's just data any fragmentation that exists is likely to have very little effect.

If you're worried about it, plug it into someone else's Windows machine once a year and run a defrag.

Thank you very much and thank you to anybody, who are willing for spending his/her time here.
Thank you ... Thank you ... Thank you

---

