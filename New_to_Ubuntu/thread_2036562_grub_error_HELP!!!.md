---
title: "grub error HELP!!!"
date: 2012-08-02
forum: New to Ubuntu
---

### Post by jamsebob on 2012-08-02
I have a dell inspiron 6400 and i accidently pressed the MediaDirect button when turning it on whilst not concentrating.

I previously had Ubuntu 12.04 installed after removing windows vista.

When I turn it on I now get just:
error: unknown filesystem.
grub rescue>

I tried using an ubuntu disk to live boot but when i click any of the boot options it returns to the same screen.

I using windows 7 on my other computer so I need to be able to do stuff on there if I'm making any boot discs etc.

---

### Post by NikTh on 2012-08-02
Hi and **welcome to Ubuntu-forums! **
for begin you can try this tool --> [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) 
follow first option and make a bootable CD . 
If this not fix your problem , we will need the info from boot-repair. 

Thanks

---

### Post by jamsebob on 2012-08-02
I did the following and did the recommended repair and the following now comes up when I try and boot ( and I don't use windows):

Windows could not start because the following file is missing or corrupt:
<Windows root>\system32\hal.dll
Please re-install a copy of the above file.

I think i could use a boot disk i just didnt mount the previous one properly

---

### Post by jamsebob on 2012-08-02
I then got opened it again and clicked the other option and got:

[http://paste.ubuntu.com/1125117](http://paste.ubuntu.com/1125117)

---

### Post by NikTh on 2012-08-02
> **jamsebob said:**
> I then got opened it again and clicked the other option and got:

[http://paste.ubuntu.com/1125117](http://paste.ubuntu.com/1125117)

Hi , 
do you have any sensitive data ? 
If yes try to access it with a LiveCD/Usb(usb its better) and copy it on external drive. 
If no then proceed with a Completely format of Everything. 

It is so messed up , I cannot help. 

You can format everything either from Gparted Live CD/Usb --> [http://gparted.sourceforge.net/livecd.php/livecd.php](http://gparted.sourceforge.net/livecd.php/livecd.php)
or from windows DVD. 
Delete all partitions - Unite the disk to One part , and start again from begin.
Sorry

Thanks

---

### Post by jamsebob on 2012-08-02
turns out there's no ubuntu left on the system?

---

### Post by NikTh on 2012-08-02
> **jamsebob said:**
> turns out there's no ubuntu left on the system?

Yes. I cannot see anything that shows Ubuntu there. Only swap is present.
Also I can see an archaic file system Fat32 (maybe there are boot files for windows?) , also I can see overlapped partitions. 
Messed up reports for O.S's  , windows 7 , windows xp embedded , you said on first post for Windows vista... hmm . 

Like I said before , best solution is to Delete everything , and unite all partitions to One. Then you can just start over and if you want any help (with Ubuntu) 
we are here. :) 

Thanks

---

### Post by jamsebob on 2012-08-02
not sure why it has windows xp and windows 7 on it, i bought it with vista installed then installed ubuntu 11.10 with a disk then updated to 12.04

---

### Post by jamsebob on 2012-08-02
is there a way to deactivate the media direct button once/if i reinstall ubuntu or will that get removed when i format the drive

---

### Post by NikTh on 2012-08-02
> **jamsebob said:**
> is there a way to deactivate the media direct button once/if i reinstall ubuntu or will that get removed when i format the drive
Hi ,
I assume has something to do in regard to windows installation but....
.....I don't know what is this  "media direct button" .(I never bought a Desktop or Laptop with windows pre-installed) 
Wait for someone who knows better. 

Thanks

---

### Post by audiomick on 2012-08-02
> **jamsebob said:**
> not sure why it has windows xp and windows 7 on it, i bought it with vista installed then installed ubuntu 11.10 with a disk then updated to 12.04

Don't bother your head too much with that. I have a Vista dual boot and a Win 7 dual boot on two different machines, and neither of them shows the correct name for the windows os that is there. The main thing is whether a Windows os is detected or not.

I have to agree with NikTh. That really does look terminally messed up. It is a bit too late at night for me to look for myself to see where it is, but there was mention of overlapping partitions. This indicates a messed up partition table.i

If it is not absolutely life and death to try and recover the install, I think it would be easier to do a new one.

What does this "media direct" button allegedly do? It sounds like a manufacturer specific function. I don't like your chances of being able to disable it completely

---

