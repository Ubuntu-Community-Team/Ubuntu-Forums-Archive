---
title: "problem with external hard drive disc"
date: 2011-10-04
forum: New to Ubuntu
---

### Post by Ymurti on 2011-10-04
I cannot mount my external HDD
I typed the command blkid in a terminal and got this:



/dev/sda1: LABEL="Recovery" UUID="64FAC1EFFAC1BD94" TYPE="ntfs" 
/dev/sda2: LABEL="System Reserved" UUID="227E420C7E41D965" TYPE="ntfs" 
/dev/sda3: UUID="FA9443B094436DE7" TYPE="ntfs" 
/dev/sda5: UUID="6d38953f-4558-4e99-b25e-e988a8de299a" TYPE="ext4" 
/dev/sda6: UUID="f725f4aa-088c-4d26-a0c3-6de90b82cb76" TYPE="swap" 

Please can someone help me?

---

### Post by Paqman on 2011-10-04
What type of external is this? USB? Try opening a terminal and entering:
```
sudo mount -a
```

If the drive is formatted NTFS it might have not unmounted cleanly. It looks like you have Windows, so try booting up into it, mounting your external drive, then unmounting it and rebooting into Ubuntu.

---

### Post by fantab on 2011-10-04
Plug in the External HDD and type following in the terminal and post the result

```
lsusb

OR

sudo lsusb
```

---

### Post by Ymurti on 2011-10-04
> **fantab said:**
> Plug in the External HDD and type following in the terminal and post the result

```
lsusb

OR

sudo lsusb
```


Here it is the result:


Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0c45:6464 Microdia 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by ajsoulmate on 2011-10-04
> **Ymurti said:**
> I cannot mount my external HDD
I typed the command blkid in a terminal and got this:



/dev/sda1: LABEL="Recovery" UUID="64FAC1EFFAC1BD94" TYPE="ntfs" 
/dev/sda2: LABEL="System Reserved" UUID="227E420C7E41D965" TYPE="ntfs" 
/dev/sda3: UUID="FA9443B094436DE7" TYPE="ntfs" 
/dev/sda5: UUID="6d38953f-4558-4e99-b25e-e988a8de299a" TYPE="ext4" 
/dev/sda6: UUID="f725f4aa-088c-4d26-a0c3-6de90b82cb76" TYPE="swap" 

Please can someone help me?

Use another USB Port. It happened with me the other day.

---

### Post by Ymurti on 2011-10-04
Dear ajsoulmate,  I tried in all USB ports ( I have 3 in my Sony Laptop) and did not work. I tried the HDD in another laptop with Windows and it works!

---

### Post by hyper2hottie on 2011-10-04
Post the result of the following
```
sudo fdisk -l
```
note that -l is a small -(small L)

---

### Post by Ymurti on 2011-10-05
> **hyper2hottie said:**
> Post the result of the following
```
sudo fdisk -l
```
note that -l is a small -(small L)

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa7e1f5f4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1681    13494272   27  Unknown
/dev/sda2   *        1681        1693      102400    7  HPFS/NTFS
/dev/sda3            1693       19559   143509971+   7  HPFS/NTFS
/dev/sda4           19560       38914   155462657    5  Extended
/dev/sda5           19560       38123   149110784   83  Linux
/dev/sda6           38123       38914     6350848   82  Linux swap / Solaris

---

### Post by hyper2hottie on 2011-10-05
Well I was hoping that would find your hard drive so we could mount it manually, it does not appear to be showing though.

I must admit my experience with this is pretty minimal, but what happens if you install gparted and open it.  Does it see the external drive?  When you open gparted does the top right drop down list show any options other than /dev/sda?

---

### Post by Ymurti on 2011-10-05
> **hyper2hottie said:**
> Well I was hoping that would find your hard drive so we could mount it manually, it does not appear to be showing though.

I must admit my experience with this is pretty minimal, but what happens if you install gparted and open it.  Does it see the external drive?  When you open gparted does the top right drop down list show any options other than /dev/sda?

I took a screenshot and it is attached. I hope you can see it.

---

### Post by hyper2hottie on 2011-10-05
Ok.  Please click the button in the top right(I uploaded a screenshot with the button circled).  Tell me what is all in that drop down list.

What I am doing is trying to find out if ubuntu is even seeing your external hard drive.  If it sees it then we can mount it.  If it doesn't see it then I'm not sure what to do.

---

### Post by Ymurti on 2011-10-05
There is no other drive. When I clicked came the same /dev/sda  (298.09 Gib)

---

### Post by hyper2hottie on 2011-10-05
Well I am out of ideas I'm afraid.  

I only see two possible issues here.  Either you are missing a driver for the hard drive, or your hard drive has some sort of hardware issue(which I doubt because it works in windows).

I have no idea how you would get a driver for your hard drive if that is the issue. 

I hope that someone else will jump in that has some idea.  Sorry I couldn't help more.

Good luck.

---

### Post by hyper2hottie on 2011-10-05
Ok I have done a little searching.  If you go into your bios does it find your external hard drive?

---

### Post by Ymurti on 2011-10-05
> **hyper2hottie said:**
> Ok I have done a little searching.  If you go into your bios does it find your external hard drive?
Sorry but how I go into the bios?

---

### Post by hyper2hottie on 2011-10-05
That depends on your motherboard.  [http://www.cpucare.net/Hardware/BIOS/Access_BIOS.htm](http://www.cpucare.net/Hardware/BIOS/Access_BIOS.htm) has common keys to use to access the bios.  When your computer is starting(before the bootloader screen and before the login screen) you press the appropriate key.  It will take you into your bios.

---

### Post by Paqman on 2011-10-05
It looks like you have Windows installed. Can you see the drive in Windows?

---

### Post by Ymurti on 2011-10-06
> **Paqman said:**
> It looks like you have Windows installed. Can you see the drive in Windows?

Mystery, No. I have Windows 7 installed in my laptop and I tried to open the HDD and it is not showing in My computer. It is not any problem with the USB port as when I use a pen drive I can open it. There is no problem with the HDD as I can open it in my wife's laptop.
:(

---

### Post by hyper2hottie on 2011-10-06
This makes it seem like a bios issue.  Your motherboard is not finding the hard drive.  If you access your bios there may be a setting to get it to recognize your hard drive.

---

### Post by amjjawad on 2011-10-06
> **Ymurti said:**
> Mystery, No. I have Windows 7 installed in my laptop and I tried to open the HDD and it is not showing in My computer. It is not any problem with the USB port as when I use a pen drive I can open it. There is no problem with the HDD as I can open it in my wife's laptop.
:(

Then please do this:

1- Copy the content of your External HDD to your Wife's machine
2- Format your External HDD (NTFS).
3- Safely Remove it from your Wife's Machine
4- Plug it to your machine
5- Report back.
6- That's all.

---

### Post by amjjawad on 2011-10-06
> **hyper2hottie said:**
> This makes it seem like a bios issue.  Your motherboard is not finding the hard drive.  If you access your bios there may be a setting to get it to recognize your hard drive.

BIOS has nothing to do with that IMHO:

> **Ymurti said:**
> It is not any problem with the USB port as when I use a pen drive I can  open it. There is no problem with the HDD as I can open it in my wife's  laptop.
:sad:

---

### Post by hyper2hottie on 2011-10-06
> BIOS has nothing to do with that IMHO:My reasoning for thinking it was a bios issue is that the other machine running windows can access it.  

EDIT:
I was searching for info to help and came across 
> We assume that the hard drive is physically installed and detected by the BIOS. From [https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

It is very possible that I am wrong though.  Thanks for the correction.

---

### Post by amjjawad on 2011-10-06
> **hyper2hottie said:**
> My reasoning for thinking it was a bios issue is that the other machine running windows can access it.  

It is very possible that I am wrong though.  Thanks for the correction.

I wasn't correcting you, I was sharing my opinion :)

---

### Post by hyper2hottie on 2011-10-06
Well I appreciate it anyway.  

If your interested, you could take a look at my edit in my last post to see what you think.

---

### Post by Ymurti on 2011-10-06
> **amjjawad said:**
> Then please do this:

1- Copy the content of your External HDD to your Wife's machine
2- Format your External HDD (NTFS).
3- Safely Remove it from your Wife's Machine
4- Plug it to your machine
5- Report back.
6- That's all.

Dear amjjawad   I have too many things in the HDD and the laptop of my wife has too little memory. But wonder, my wife's laptop has Ubuntu and it can open the HDD. I took a screenshot of it and here it is:

---

### Post by amjjawad on 2011-10-06
> **Ymurti said:**
> Dear amjjawad   I have too many things in the HDD and the laptop of my wife has too little memory. But wonder, my wife's laptop has Ubuntu and it can open the HDD. I took a screenshot of it and here it is:

Oh, my bad ... I should have thought about that.
Well, there must be another way, so simple that we missed.

By the way, I was wondering, who did that partitioning? you? or it's like that by default? last time I bought my External HDD, it was one partition.

---

### Post by amjjawad on 2011-10-06
> **hyper2hottie said:**
> Well I appreciate it anyway.  

If your interested, you could take a look at my edit in my last post to see what you think.

Thanks for your understanding and I'll definitely do that but later simply because I haven't slept since two days :/

---

### Post by Ymurti on 2011-10-06
> **amjjawad said:**
> Oh, my bad ... I should have thought about that.
Well, there must be another way, so simple that we missed.

By the way, I was wondering, who did that partitioning? you? or it's like that by default? last time I bought my External HDD, it was one partition.

I did it by mistake. When I began to install Ubuntu in my Laptop for the first time, the HDD was connected and Ubuntu began to install on it. I stopped the installation and desconnected the HDD and after installed again Ubuntu in my laptop.

---

### Post by amjjawad on 2011-10-07
> **Ymurti said:**
> I did it by mistake. When I began to install Ubuntu in my Laptop for the first time, the HDD was connected and Ubuntu began to install on it. I stopped the installation and desconnected the HDD and after installed again Ubuntu in my laptop.

Perhaps that is why you can't access your files any more while connecting to "your" laptop.

Why not remove the extra partitions? you can use GParted to remove the extra partitions.

While I'm writing this, it came to my mind another thought.
Do you still have the media you used to install Ubuntu from? a LiveCD or LiveUSB? boot your machine from that media, connect your External HDD and try to access the files. This is the best I could come up with :)

---

### Post by Ymurti on 2011-10-07
Dear hyper2hottie and amjjawad, thank You very much for your endeavour trying to help me. I appreciate it a lot.   Yours Ymurti
:p

---

### Post by amjjawad on 2011-10-07
> **Ymurti said:**
> Dear hyper2hottie and amjjawad, thank You very much for your endeavour trying to help me. I appreciate it a lot.   Yours Ymurti
:p

You welcome but what happened? did you manage to access your files from LiveCD or LiveUSB?

---

### Post by Ymurti on 2011-10-07
> **amjjawad said:**
> You welcome but what happened? did you manage to access your files from LiveCD or LiveUSB?

No, I tried and I could not access my files from my Laptop even using Live USB. I am beggining to think that is some incompatibility between the USB port in my laptop and the HDD.???

---

