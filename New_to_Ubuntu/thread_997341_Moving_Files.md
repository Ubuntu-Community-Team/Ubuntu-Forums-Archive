---
title: "Moving Files"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by WillT87 on 2008-11-29
Is it possible to take files from my windows partition which has some virus and put them on a flash drive with ubuntu?

---

### Post by Xiong Chiamiov on 2008-11-29
Yes.  I believe ntfs read-support is built-in to Ubuntu, so you should be able to simply mount the drives and move files between them.  The Windows drive should appear in Disks->Media or something - I'm not quite sure how Gnome-magic works.

---

### Post by WillT87 on 2008-11-29
Where is Disks? 
Under computer all I see is my cd drive and Filesystem

---

### Post by linuxguymarshall on 2008-11-29
You could install a Virus scanner in Ubuntu and scan your Windows partition to remove it. That's why they are there

---

### Post by WillT87 on 2008-11-29
Whats a good virus scanner for ubuntu. The only ones I can find are for windows except for AVG that will only scan my ubuntu partition because I cant find my windows

---

### Post by oldos2er on 2008-11-29
> **WillT87 said:**
> Where is Disks? 
Under computer all I see is my cd drive and Filesystem

 Click "Places" in the top menu, you should see it.

---

### Post by WillT87 on 2008-11-29
under places I see 

Home Folder
Desktop
Documents
Music
Pictures
Videos
-------------
Computer
CD/DVD Creator
CD/DVD Drive
------------
Network
Connect to server..
Search For Files
Recent Documents

---

### Post by Xiong Chiamiov on 2008-11-29
[Here]("http://www.psychocats.net/ubuntu/mountwindows")'s a nice guide.

It should be under the Computer section.  Since it doesn't appear to be there, we'll have to do some trouble shooting.

[In a terminal]("http://www.psychocats.net/ubuntu/terminal"), type
```

sudo fdisk -l

```
and paste the output here.

---

### Post by WillT87 on 2008-11-29
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6fd86fd8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30400   244187968+   7  HPFS/NTFS

```

---

### Post by oldos2er on 2008-11-29
Did you do a Wubi install?

 Edit: and I should also have asked, do you have two or more physical hard disks?

---

### Post by WillT87 on 2008-11-29
What is that?

---

### Post by Xiong Chiamiov on 2008-11-29
[Wubi]("http://wubi-installer.org/") is a method of installing Ubuntu *within* Windows, so that you do not have to deal with GRUB, and can easily remove it using Windows' Add/Remove Programs control panel.

---

### Post by oldos2er on 2008-11-29
> **WillT87 said:**
> What is that?

 If you have to ask, then the answer is most likely no.

---

### Post by WillT87 on 2008-11-29
I have one HDD I had xp pro installed first then I installed ubuntu

---

### Post by WillT87 on 2008-11-29
Bump

---

### Post by Xiong Chiamiov on 2008-11-29
The reason oldos2er asked is because your fdisk output showed only one partition, which was a Windows partition.  It doesn't look like you have Linux installed, from that output at least.

---

### Post by WillT87 on 2008-11-29
I am on it right now. Linux and windows look a little different :)

I installed linux with an exe file though which gave me 30gb for linux and the other 220gb for windows

---

### Post by oldos2er on 2008-11-30
"I installed linux with an exe file"

 Was it wubi.exe? Because you have only one partition, as [Xiong Chiamiov]("http://ubuntuforums.org/member.php?u=440346") said. Anyway, use Synaptic Package Manager to install clamav or whichever antivirus program you prefer.

---

### Post by WillT87 on 2008-11-30
/host is my C:\ drive for windows and it has all of my information

Is it possible to get malwarebytes AV to run I dont know what synaptic package manager is

---

### Post by WillT87 on 2008-11-30
What Avs can I run with ubuntu?

---

### Post by oldos2er on 2008-11-30
System, Administration, Synaptic.

---

### Post by WillT87 on 2008-11-30
Thanks and yes i did do a wubi install

---

