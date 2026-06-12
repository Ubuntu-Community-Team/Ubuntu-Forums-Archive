---
title: "How to (automount) drives at startup"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by smartygoldenfish on 2008-10-15
this is my fstab



# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=94bd1fac-86db-4f7a-baf0-1c7a2d6266ff /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=71873c37-d880-48c0-9508-68f816d24f33 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0



I need to automount my 4 hard-drive partitions at startup.
however i am unable to do so. when i added these 4 lines:
/dev/sda1 /media/Windows VistaSP1 ntfs defaults 0 0
/dev/sda5 /media/MISC ntfs defaults 0 0
/dev/sda8 /media/Softwares ntfs defaults 0 0
/dev/sda9 /media/Documents And Media ntfs defaults 0 0

and also created corresponding folders in /media
i dont seem to getting them mounted. 
If these lines ARE IN fstab, i am even unable to mount them MANUALLy [by terminal or GUI]
it says "bad fstab"

So i removed these lines. 
Please note all parameters in lines are correct.

Secondly,
i thought of creating this script,
sudo mkdir /media/Windows VistaSP1
sudo mount /dev/sda1 /media/Windows VistaSP1 -o force
sudo mkdir /media/MISC
sudo mount /dev/sda5 /media/MISC -o force
sudo mkdir /media/Softwares
sudo mount /dev/sda8 /media/Softwares -o force
sudo mkdir /media/Documents And Media
sudo mount /dev/sda9 /media/Documents And Media -o force

but how save it [with what extension, *.sh or *.txt] and where to put it so that it loads automatically at startup.

please help.

---

### Post by Pro-reason on 2008-10-15
The script for mounting filesystems is /etc/fstab.

You have to make sure that there are no spaces in any name.  Spaces delimit arguments.

---

### Post by Tatty on 2008-10-15
The first thing that springs to mind is that you have a space in the path "/media/Windows VistaSP1".  Try changing the space to an underscore.

If that doesnt solve your problem then try mounting a partition manually to see if that works:

```
sudo mkdir "/media/Windows_VistaSP1"
sudo mount /dev/sda1 /media/Windows_VistaSP1
```

---

### Post by smartygoldenfish on 2008-10-15
> **Pro-reason said:**
> The script for mounting filesystems is /etc/fstab.

You have to make sure that there are no spaces in any name.  Spaces delimit arguments.

> **Tatty said:**
> The first thing that springs to mind is that you have a space in the path "/media/Windows VistaSP1".  Try changing the space to an underscore.

If that doesnt solve your problem then try mounting a partition manually to see if that works:

```
sudo mkdir "/media/Windows_VistaSP1"
sudo mount /dev/sda1 /media/Windows_VistaSP1
```

> **smartygoldenfish said:**
> 
sudo mkdir /media/Windows VistaSP1
sudo mount /dev/sda1 /media/Windows VistaSP1 -o force
sudo mkdir /media/MISC
sudo mount /dev/sda5 /media/MISC -o force
sudo mkdir /media/Softwares
sudo mount /dev/sda8 /media/Softwares -o force
sudo mkdir /media/Documents And Media
sudo mount /dev/sda9 /media/Documents And Media -o force

but how save it [with what extension, *.sh or *.txt] and where to put it so that it loads automatically at startup.

please help.

Thanks both of you for speeeeeedy replies.
But as you see, the partition MISC, Softwares etc MUST be then mounted as <space> problem doesnot exist.
Anyways using "Windows<space>VistaSP1 manually, as Tatty says, WORKS. no underscore necessary.

---

### Post by ilrudie on 2008-10-15
fstab runs essentially as a script.  an error or lockup (when hard mounting NFS for example) causes mount points after it to not run/parse.  

They are correct.  The fields in fstab are space (or tab) delimited.  This line:
/dev/sda1 /media/Windows VistaSP1 ntfs defaults 0 0
means mount /dev/sda1 of type VistaSP1 to /media/Windows with options ntfs and garbage....
Its meaningless.  You can try:
/dev/sda1 '/media/Windows VistaSP1' ntfs defaults 0 0
and it may work but its probably best to just take the spaces out.

also see man fstab if you don't believe us.

---

### Post by Orange_and_Green on 2008-10-15
In fstab, the '\040' sequence is used to escape spaces, '\ ' will not work. Try

```
/dev/sda1 /media/Windows\040VistaSP1 ntfs defaults,uid=1000,gid=46,umask=0047 0 1
```

(I am assuming you are the main user, that is, your uid is 1000). You can find out about your uid by running ```
id
```in a terminal. This syntax has the benefit of making you the owner of the partition so you have full read/write access.

Good luck :KS

---

### Post by smartygoldenfish on 2008-10-15
> **Orange_and_Green said:**
> In fstab, the '\040' sequence is used to escape spaces, '\ ' will not work. Try

```
/dev/sda1 /media/Windows\040VistaSP1 ntfs defaults,uid=1000,gid=46,umask=0047 0 1
```

(I am assuming you are the main user, that is, your uid is 1000). You can find out about your uid by running ```
id
```in a terminal. This syntax has the benefit of making you the owner of the partition so you have full read/write access.

Good luck :KS

really thanks Orange and Green [what a name!]
but i editied my fstab with those \040, however both the drives having \040 [windows vista and documents and medaia] failed to mount at startup.

Main reason i was hell bent on name with spaces is that i have all my 5000 songs in Documents And Media partition, and was monitored by RythmBox, but thanks to spaces and blanks now i have made /media/Documents [simply by removing all spaces]. Now this works. All my drives are mounted at startup.

PS: can i now index my partitions [or folder in them]? i have done this in vista. The search there is awesum! i have 2 gb ram.
since now drives are automounted..they will be autoindexed?
I noticed while writing my system froze. just froze no mistake of me! Why!
i have been using vista for 6 months, it hasnt frozen or a single time [yes exactly 0 times] why Ubuntu???? :((

---

