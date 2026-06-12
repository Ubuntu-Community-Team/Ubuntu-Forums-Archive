---
title: "Sharing of Drives"
date: 2012-04-22
forum: New to Ubuntu
---

### Post by Shouvik0206 on 2012-04-22
Guys i am not able to access my D and E drives of ma laptop in ubuntu.....i also hv Win 7 installed where i cn easily access all my drives!!

---

### Post by Silent Sam on 2012-04-22
Click on "Dash Home" and type in "disk".
Open the "Disk Utility".
Are your devices viewable there?

---

### Post by Shouvik0206 on 2012-04-22
i can see a icon of my 640GB harddisk....thats it!!yeah n Cd, pd and all!! But cant see the drived D and E

---

### Post by Morbius1 on 2012-04-22
Can Linux see the drives? Post the output of the following command:
```
sudo blkid -c /dev/null
```

---

### Post by JKyleOKC on 2012-04-22
> **Shouvik0206 said:**
> Guys i am not able to access my D and E drives of ma laptop in ubuntu.....i also hv Win 7 installed where i cn easily access all my drives!!The word "drive" has slightly different meanings in Windows and in other systems including Ubuntu. Everywhere except in Windows, a "drive" is a single physical hard disk. That disk may be divided into several "partitions" by software, with each partition being independent of the others but all are part of the same physical drive.

In Windows, if a disk is partitioned into several areas, each partition is called a drive. Thus your C, D, and E "drives" are actually partitions 1, 2, and 3 of your 640 GB disk. The Disk Utility mentioned in another message will show you these partitions.

It appears that only the first of these is being mounted automatically, but it's possible to mount the others and access them. After you post the results of some of the diagnostic actions suggested, we can offer you ways to do so.

Keep in mind, always, that Linux (and so Ubunutu) is not Windows, and quite a few details are going to be different. However if you stick with it you'll probably come to love those differences...

---

### Post by slyspring on 2012-04-28
To preface this, I am using Ubuntu 11.10 64-bit and am actively sharing with my other Win7 computer.

OMG! I just solved this in 15 minutes with just SAMBA and a few Win7 tweaks! Follow these to the letter

1. Using Ubuntu, open Terminal and run **sudo apt-get install samba**

2. Run the command sudoedit **/etc/samba/smb.conf**

3. Under "Global Settings", where it says #Change this to the Workgroup/NT-domain....#, change the workgroup the actual name of your group. Also, add the string directly underneath that called **netbios name = ** and type the EXACT name of your computer.

4. Hit CTRL and the letter X at the same time to exit. When, asked to save, press the letter Y, and hit Enter.

On to Windows 7 (bane of existence)

1. Open Network and Sharing Center.
2. On the left, click "Change Advanced sharing options"
3. Perform the following (make sure your computer is set for Home/Work):
  a: Network Discovery - On
  b: File and Printer Sharing - On
  c: Public Sharing - On
  d: file sharing connection - 128-bit encryption
  e: password protected sharing - off
  f: use user accounts (just as a precaution)
4. In the Control Panel, select User Accounts.
5. Enable the Guest Account. It is not automatically a part of every folder for permissions sake.
6. On the in the folder permissions (or the root of the external drive you want to share), add the Guest account, and I recommend you give it up to MODIFY rights to all folders and subfolders you need. NTFS permissions trump Share permissions.
7. Create the share you want, with me STRONGLY recommending adding the Group user and giving it up to Modify rights. 

All that other crap about winbind and nss... i undid on my Ubuntu, and my fixes persisted forever. take it or leave it.

---

