---
title: "Clonezilla does not see USB HD formatted with linux file system"
date: 2016-01-01
forum: New to Ubuntu
---

### Post by rod52 on 2016-01-01
I am trying to test clonezilla to create an image file of my hard drive.  I want use a USB HD as the repository for that image. I had assumed that because that the external HD was not formatted with a linux file system, clonezilla was not seeing it. So I used GPARTED to wipe the HD then add a GPT table then formatted to ext4. Clonezilla still does not show that drive as an option when it comes time to mount it. Any idea as to why?

---

### Post by leunam12 on 2016-01-02
Can other operating systems see it? Have you tried different USB ports?

---

### Post by greggfowler on 2016-01-02
I have used Clonezilla for imaging Linux, OSX, and Windows Systems. I have never formatted the external drive as ext4, so would be unsure whether Clonezilla would see it or not. I would think Clonezilla Documentation would be a place to look for that specifically. Not sure however why you are using the ext4 format for your drive. Why not use FAT or NTFS? It does not matter what format you use, the image file still retains the characteristics of the system or drive you imaged. Just a though.

---

### Post by stalkingwolf on 2016-01-02
in my experience ext hdd and flash drives must be formatted to fat32 or ntfs to work

---

### Post by sudodus on 2016-01-02
> **rod52 said:**
> I am trying to test clonezilla to create an image file of my hard drive.  I want use a USB HD as the repository for that image. I had assumed that because that the external HD was not formatted with a linux file system, clonezilla was not seeing it. So I used GPARTED to wipe the HD then add a GPT table then formatted to ext4. Clonezilla still does not show that drive as an option when it comes time to mount it. Any idea as to why?

I have been using ***Clonezilla*** for years. I usually download an iso file of the ***stable*** version, and I have not had your problem. This way Clonezilla is running in a linux live session and recognizes most file systems, definitely ext4, FAT32 and NTFS in external as well as internal drives. Something else must be wrong. Have you realized that the first question is asking you about the target drive, where to write the image? (The image is a directory with a number of files.)

Please ***enter the shell (command line) in Clonezilla***, type some commands and give us the output. If you think it is complicated to copy the output to a reply here, you can take pictures of the screen with a camera and attach the picture files to a reply (advanced mode, manage attachments). These commands will show what drives (mass storage devices) that are found by the linux system of Clonezilla.

```
df
```

```
lsblk
```

```
sudo parted -ls
```

```
sudo lsblk -fm
```

***Edit:***

You get more information in one screen if you ***select higher resolution*** in the first [grub] menu, 1024x768.

---

### Post by rod52 on 2016-01-02
Other OS can see it. GPARTED can see it.  I am not sure that Clonezilla does not see it.  It does not appear to give me the choice for the target drive.  When I first get to the screen showing any drives...this is after the screen telling me to connect the HD and wait for 5 s then press enter.  My options are sda1, sda2 and sda3.  No sdb...which should the external drive. I am in the middle of using GPARTED to format that drive to FAT32 and try again.  Then will try other USB ports.  The Clonezilla manual does not appear to cover how target drives should be formatted.  If I still have problems, I will go into the shell.

---

### Post by sudodus on 2016-01-02
Maybe your external drive has some electronics or firmware, that is not recognized by Clonezilla. The 'stable' versions, that I use are basically built from Debian stable. You might have better luck with a version that is built from Ubuntu, an 'alternative stable release' or vice versa.

If you tell us the brand name and model of your external drive, someone might recognize it and help us understand the problem.

---

### Post by rod52 on 2016-01-02
I think I am close to a resolution.  Went into the shell.  From these commands you listed, I can tell Clonezllla does see the drive. That helps.  This time however I tried something different. The cloneizlla prompts tell me to use the space bar to pick options.  For the first few screens, this did work where there is not a separate check box.  I don't know what me do it, but this time in those first few windows, I hit tab. This time the options hi lighted in red hi-lighted to blue etc. This time the HD list included sdb1. So I am trying again.  I will post if this is resolved.  The external HD is Seagate Back Plus Portable Drive, model SRD0SP0.  As for the file system I was trying to use, I did not want to use FAT32 because of the limitations.  I may go back ext4 as formatting etc seemed to be much faster.

---

### Post by sudodus on 2016-01-03
I'm glad that you make progress and can see the external drive as /dev/sdb now in Clonezilla.

I think Clonezilla will see an ext4 partition as easily as a FAT32 partition, and I agree, ext4 is better.

There might be problems for Clonezilla to see directories (or partitions) with a space or other non-standard character in the name (or label).

---

### Post by rod52 on 2016-01-03
Wow, it is still creating the image file. 16 hours into it. Thought it would be faster.  I may repeat this after formatting to ext4 just to see.  Even GPARTED took a lot longer to format to FAT32 and re-scan devices when done formatting.

---

### Post by sudodus on 2016-01-03
USB 2 is very slow. If you want faster data transfer you should save your image via SATA or externally via eSATA or USB 3.

Compression of the image is also slow, particularly if the processor is slow.

Which version of Clonezilla are you running (the full description of it: including the architecture i586, i686-pae or amd64)? i586 is slower than the other architectures in computers with more than one core.

---

