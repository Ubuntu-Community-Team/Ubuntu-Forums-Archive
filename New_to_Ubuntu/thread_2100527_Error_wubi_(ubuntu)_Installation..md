---
title: "Error wubi (ubuntu) Installation."
date: 2013-01-02
forum: New to Ubuntu
---

### Post by rahulquara20 on 2013-01-02
Hello everyone.
I tried to install ubuntu through wubi as my dvd writer doesn't work.
I get the following message.
 
[COLOR=red]Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {db411ab6-4ee1-11e2-8244-cc828989c139} device partition=D:
>>retval=1
>>stderr=An error has occurred setting the element data.[/COLOR]
[COLOR=red]The request is not supported.[/COLOR]
[COLOR=#ff0000][/COLOR] 
[COLOR=black]Please help as faster.[/COLOR]
 
System Configuration:
 
Maker: Dell
Product : Inspiron 1545
RAM: 3 GB
OS: Windows 7 Ultimate SP1
Processor : Intel Core 2 Duo

---

### Post by NikTh on 2013-01-02
Hi , 

I bet you have set up dynamic volumes on dynamic disk . Am I correct ? 

Open a terminal (CTRL+ALT+T) from Ubuntu Live session and apply the command below
```
sudo fdisk -l
``` 
Post back here the results

_Please click on **"New Reply"** and put the results inside [CODE] tags to be easier to read._ [See here how]("http://i.stack.imgur.com/zADbK.png")

Thanks

---

### Post by newb85 on 2013-01-02
Since your DVD burner doesn't work, you'll probably have to use a Live USB to get to a live session as NikTh described.  There are a few different ways to do this.  I recommend the method prescribed at the Ubuntu download site - [http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows]("http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows").

---

### Post by rahulquara20 on 2013-01-03
Thank You NikTH.
 
I will try and reply as soon as possible.

---

### Post by rahulquara20 on 2013-01-03
Thank You NikTH.
 
  It gives me the following result.
[COLOR=Red]

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb8000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      206847      103392+  42  SFS
/dev/sda2   *      206848   163842047    81817600   42  SFS
/dev/sda3       163842048   625140399   230649176   42  SFS

Disk /dev/sdb: 4048 MB, 4048551936 bytes
128 heads, 9 sectors/track, 6864 cylinders, total 7907328 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        9136     7907327     3949096    c  W95 FAT32 (LBA)

[COLOR=Black]I dont know what to do the next.

Please help.
[/COLOR][/COLOR]

---

### Post by NikTh on 2013-01-03
> **rahulquara20 said:**
> [COLOR=Red]
[COLOR=Black]Disk /dev/sda: 320.1 GB, 320072933376 bytes
/dev/sda1              63      206847      103392+  42  **SFS**
/dev/sda2   *      206848   163842047    81817600   42  **SFS**
/dev/sda3       163842048   625140399   230649176   42  **SFS **[/COLOR]
[/COLOR][COLOR=Red] [COLOR=Black]
Yeap , I won the bet. You've set up a dynamic disk with dynamic volumes. 

[/COLOR][/COLOR][COLOR=Red][COLOR=Black]> **rahulquara20 said:**
> I dont know what to do the next.[/COLOR][/COLOR]
Unfortunately nothing. Dynamic volumes are Microsoft's specific volumes and you cannot install anything there except Windows. Even Windows that are not support dynamic volumes (I think Xp Home edition is one) will not be installed.
This is all  I know (if I'm wrong someone will correct me). 

I see two choices.
1) Convert the dynamic volumes to normal volumes (some tool maybe exists for this or you must to delete them)

2) Install Ubuntu on VirtualBox. 

Thanks

---

