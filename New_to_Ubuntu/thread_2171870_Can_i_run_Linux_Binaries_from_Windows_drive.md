---
title: "Can i run Linux Binaries from Windows drive ??"
date: 2013-09-02
forum: New to Ubuntu
---

### Post by vamsi_spr on 2013-09-02
Hey there guys, recently i have decided to install ubuntu on my laptop and explore Linux and unravel its mysteries, so i have installed it alongside windows which occupies more disk space, Now i really liked ubuntu and want to dive into it by installing Steam and start gaming, that is moment i realized that i don't have enough space to install games, i tried setting the steam library into the windows drive but it is denying saying it needs a file system with the executable permissions, so i was wondering if  i could install my Linux binaries onto my windows drive and run it ?, Tried doing my homework by googling but found no answer, Help me here guys, Thanks in advance !!

---

### Post by nerdtron on 2013-09-02
wubi is really designed only for testing purposes. A full install of ubuntu is faster since it uses a native filesystem. Also, you'll get better experience with steam on a full install of Ubuntu. So I suggest you dedicate a partition for Ubuntu.

---

### Post by mastablasta on 2013-09-02
windows NTFS file system has limited permissions settings. Linux has a lot more permission settings so that's why it could be problematic installing linux programes on NTFS. while storing data on NTFS is fine.

---

### Post by whitesmith on 2013-09-02
> **vamsi_spr said:**
> ...i tried setting the steam library into the windows drive but it is denying saying it needs a file system with the executable permissions, so i was wondering if  i could install my Linux binaries onto my windows drive and run it.You need the +x (execute) permission to run a *nix executable. No permissions are recognized by drives formatted according to the Windows standard. If this does it for you please mark your answer as solved using thread tools.

---

### Post by vamsi_spr on 2013-09-02
> **nerdtron said:**
> wubi is really designed only for testing purposes. A full install of ubuntu is faster since it uses a native filesystem. Also, you'll get better experience with steam on a full install of Ubuntu. So I suggest you dedicate a partition for Ubuntu.

I did dedicate a partition for ubuntu, it's just that there is not enough space left to install my Steam games.

---

### Post by vamsi_spr on 2013-09-02
> **mastablasta said:**
> windows NTFS file system has limited permissions settings. Linux has a lot more permission settings so that's why it could be problematic installing linux programes on NTFS. while storing data on NTFS is fine.


How do you store data on NTFS ?, i mean can't i set my steam library onto a windows drive ??

---

### Post by vamsi_spr on 2013-09-02
> **whitesmith said:**
> You need the +x (execute) permission to run a *nix executable. No permissions are recognized by drives formatted according to the Windows standard. If this does it for you please mark your answer as solved using thread tools.

Are you telling me that there is no way i could save my Linux files on the windows drive and run it due to the permission standards ?? i tried doing chmod on the drive but it still din't work, please  suggest a solution, Thanks.

---

### Post by vamsi_spr on 2013-09-03
Please help me with this guys :(

---

### Post by blackbird34 on 2013-09-03
The answer to your first question is NO, you can't, you have to find some room on your Ubuntu Linux partition. 

Could you not look through your folders and see what you could move somewhere else to make room? (music, films, etc? )

Or else, for us to be more helpful, please post a screenshot of your partition table, to show us how your partitions are set up. Then, with some luck, we can advise you on how to organize them better and maybe make your Ubuntu partition better. To do this, open a program called GParted (Gnome partition editor - if you haven't got it, its in the software center, or paste  "sudo apt-get install gparted"without quotes in the terminal), and give us a screenshot of what you see.

---

### Post by whitesmith on 2013-09-03
> **vamsi_spr said:**
> Are you telling me that there is no way i could save my Linux files on the windows drive and run it due to the permission standards ?? i tried doing chmod on the drive but it still din't work, please  suggest a solution, Thanks.

No, that's isn't what I said. *nix can (normally) read/write data from a Windows-formatted drive without any problem. The issue is that Windows does not understand *nix permissions, which is why chmod didn't work on your drive. Likewise, the Windows method of setting file attributes by using attrib fails to work in *nix. Different strokes...

---

### Post by vamsi_spr on 2013-09-05
> **blackbird34 said:**
> The answer to your first question is NO, you can't, you have to find some room on your Ubuntu Linux partition. 

Could you not look through your folders and see what you could move somewhere else to make room? (music, films, etc? )

Or else, for us to be more helpful, please post a screenshot of your partition table, to show us how your partitions are set up. Then, with some luck, we can advise you on how to organize them better and maybe make your Ubuntu partition better. To do this, open a program called GParted (Gnome partition editor - if you haven't got it, its in the software center, or paste  "sudo apt-get install gparted"without quotes in the terminal), and give us a screenshot of what you see.

Yes, can i shrink my windows partition and format it so i can make room for my ubuntu ?, please check if the attached screenshot would suffice.

---

### Post by vamsi_spr on 2013-09-05
> **whitesmith said:**
> No, that's isn't what I said. *nix can (normally) read/write data from a Windows-formatted drive without any problem. The issue is that Windows does not understand *nix permissions, which is why chmod didn't work on your drive. Likewise, the Windows method of setting file attributes by using attrib fails to work in *nix. Different strokes...

I understand that, since the filesystem is different, and NTFS does not understand the permissions of *nix we cannot run files from a windows drive but i was just curious if there is any method through which we could achieve this.

---

### Post by QIII on 2013-09-05
Hello!

> **vamsi_spr said:**
> Yes, can i shrink my windows partition and format it so i can make room for my ubuntu ?, please check if the attached screenshot would suffice.

If you intend to shrink your Windows partition(s), please do so with the ***Windows*** tools and not gparted.  Resizing your Windows partition(s) with gparted is a very sure way to turn this into a "significant emotional event.".

Cheers!

---

### Post by 3rdalbum on 2013-09-05
> **QIII said:**
> Hello!



If you intend to shrink your Windows partition(s), please do so with the ***Windows*** tools and not gparted.  Resizing your Windows partition(s) with gparted is a very sure way to turn this into a "significant emotional event.".

Cheers!

It's up to you, but I've found Gparted does a good job and I've never lost data when resizing a Windows partition.

If Steam allows you to store games onto as different disk, you could always format a USB flash drive as ext4, or even create an ext4 filesystem sitting in a file on the Windows hard drive.

But yes, downsizing the Windows drive and upsizing the Ubuntu is a good idea. Just make sure you have a backup before doing any partition resizing because it does carry small risks no matter what tool you use.

---

