---
title: "Ubuntu just won't boot"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by Flobuntu on 2008-05-31
Hi all.  Have been searching the forum for a while, but can't quite find a fix for my issue.

I put a new hard drive into my laptop and tried to install Gutsy Gibbon.  The install went okay, but when I try to boot up the computer I get the Dell splash screen and then a black screen with a blinking cursor that just sits there.  The Bios recognizes the hard drive, and it is in the boot sequence.  Also, no jumpers on the hard drive, which is the correct setting for master.

When I boot off my live cd and go into terminal here is what I get for fdisk -l:
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00019d14

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9352    75119908+  83  Linux
/dev/sda2            9353        9729     3028252+   5  Extended
/dev/sda5            9353        9729     3028221   82  Linux swap / Solaris

   
I can get the grub prompt, but I can't seem to get much accomplished from there.

Any thoughts?

---

### Post by Tatty on 2008-05-31
what do you mean by grub prompt?  If you mean you can get to the grub menu, then go highlight your OS and press e, highlight the big long line, press e again, then remove "quiet" and "splash" from it, press enter then b to boot

Hopefully it might give you some output as to what might be wrong.

Im afraid i cant really help much more than this :(

---

### Post by meierfra. on 2008-05-31
At the grub prompt type

```
 find /boot/grub/menu.lst
```
(l is a lowercase L)


and 

```
find  /boot/grub/stage1
```
(last symbol is the number one)

Post the output


You might also try SuperGrub (see my signature)

---

### Post by Flobuntu on 2008-05-31
> **Tatty said:**
> what do you mean by grub prompt?  If you mean you can get to the grub menu, then go highlight your OS and press e, highlight the big long line, press e again, then remove "quiet" and "splash" from it, press enter then b to boot

Hopefully it might give you some output as to what might be wrong.

Im afraid i cant really help much more than this :(


Sorry, when I said "grub prompt" I meant in the terminal window I type in GRUB and get to the grub> prompt.  I do not have the Grub menu you are describing.

---

### Post by meierfra. on 2008-05-31
Try this at the grub prompt:


```
root (hd0,0)
setup (hd0)
quit
```

Reboot and hope for the best.

---

### Post by Flobuntu on 2008-05-31
> **meierfra. said:**
> At the grub prompt type

```
 find /boot/grub/menu.lst
```
(l is a lowercase L)


and 

```
find  /boot/grub/stage1
```
(last symbol is the number one)

Post the output


You might also try SuperGrub (see my signature)

Aftering entering te text you posted, I get "Error 15:  File not found"

have tired a few iterations of find commands in grub but am getting the "file not found" message each time.  Where from here, boss?

---

### Post by meierfra. on 2008-05-31
> text you posted, I get "Error 15: File not found"


Did you start grub with 



```
sudo grub
```

---

### Post by Flobuntu on 2008-05-31
> **meierfra. said:**
> Try this at the grub prompt:


```
root (hd0,0)
setup (hd0)
quit
```

Reboot and hope for the best.
 Meierfra, I did sudo grub and at tried your text:

grub>
      root (hd0,0)

grub>
      setup (hd0)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 15: File not found

Does this mean that something went wrong in my install, maybe?

---

### Post by meierfra. on 2008-05-31
It seems grub did not get installed at all. Lets do one more check:


```

sudo mkdir /ubuntu 
sudo mount -t ext3 /dev/sda1 /ubuntu
cd /ubuntu/boot/grub
ls
```

Post the output. (It is probably blank)

In the mean time I'll write up instruction how to install grub from scratch.

---

### Post by Flobuntu on 2008-05-31
> **meierfra. said:**
> It seems grub did not get installed at all. Lets do one more check:


```
sudo mount -t ext3 /dev/sda1 /ubuntu
cd /ubuntu/boot/grub
ls
```

Post the output. (It is probably blank)

In the mean time I'll write up instruction how to install grub from scratch.

Well, this can't be good:
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sda1 /ubuntu
mount: mount point /ubuntu does not exist

from my original post I thought that showed that it was correctly mounted...maybe not.  Or may an MBR issue?

---

### Post by meierfra. on 2008-05-31
My bad. A forget  the first step:


```
 sudo mkdir /ubuntu  
```

if "ls" really returns nothing 


(do the first two steps only if you rebooted since the last time you did it)
```

sudo mkdir /ubuntu 
sudo mount -t ext3 /dev/sda1 /ubuntu  
sudo mkdir /ubuntu/boot/grub
sudo mount -t proc none /ubuntu/proc
sudo mount -o bind /dev /ubuntu/dev
sudo chroot /ubuntu
grub-install /dev/sda 
update-grub

```

---

### Post by Flobuntu on 2008-05-31
little by little.....
I got the mount command to work, but:
cd /ubuntu/boot/grub
bash: cd: /ubuntu/boot/grub: No such file or directory

so maybe instlling grub is the next step?

much appreciate the help so far.

---

### Post by meierfra. on 2008-05-31
Yes, but add this step at the beginning

```
sudo mkdir /ubuntu/boot/grub
```

and in case that you rebooted since the last time to this again to start with 

sudo mkdir /ubuntu 
sudo mount -t ext3 /dev/sda1 /ubuntu

(I'll add this to me earlier post, so that you have it all in one place.

---

### Post by Flobuntu on 2008-05-31
> **meierfra. said:**
> My bad. A forget  the first step:


```
 sudo mkdir /ubuntu  
```

if "ls" really returns nothing 



```

sudo mount -t proc none /ubuntu/proc
sudo mount -o bind /dev /ubuntu/dev
sudo chroot /ubuntu
grub-install /dev/sda 
update-grub

```

Even though I could not get through the code you previously posted (I got the error at cd /ubuntu/boot/grub) I went ahead and tried the above commands. seems to have made some progress:

ubuntu@ubuntu:~$ sudo mount -o bind /dev /ubuntu/dev
ubuntu@ubuntu:~$ sudo chroot /ubuntu
root@ubuntu:/# grub-install /dev/sda
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.
root@ubuntu:/# update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... Generating /boot/grub/default file and setting the default boot entry to 0
Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.lst file ... 

Could not find /boot/grub/menu.lst file. Would you like /boot/grub/menu.lst generated for you? (y/N) y
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.22-14-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

---

### Post by meierfra. on 2008-05-31
It sound like that you have a grub folder by now with all the files in it. But grub did not  get installed yet. You might try 

```
sudo grub
root (hd0,0)
setup (hd0)
quit
```

again,  and see what happens.

---

### Post by Flobuntu on 2008-05-31
I thought we were making some progress, but looks like it's back to where we were:
grub> root (hd0,0)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 15: File not found

---

### Post by meierfra. on 2008-05-31
> Searching for GRUB installation directory ... found: /boot/grub

Sorry, I had concluded from this line that "grub-install" had created the grub folder, and I assumed it also put the stage files in where.

I'm pretty much at the end of my wisdom and don't think there is any quick solutions. How about giving Hardy Heron a try?

---

### Post by Flobuntu on 2008-05-31
Well, I tried Hardy Heron on another system before I undertook this install--liked it okay, but my wireless connection got much worse reception than I had with GG; that's why when it came time to install on this new hard disk I went back to GG.  That said, if it fixes this issue, I could live with it.

BTW, at this point when I type ls in terminal I get the following:
ubuntu@ubuntu:~$ ls
Desktop  Documents  Music  Pictures  Public  Templates  Videos

so it is seeing the disk.

thanks for your help.

---

### Post by meierfra. on 2008-05-31
Well, you could also  try reinstalling Gutsy. Make sure that you Gusty CD is o.k.

---

### Post by Flobuntu on 2008-05-31
I've reinstalled a few times, but same problem persists each time...maybe trying something other than GG will be the ticket.

---

### Post by ugm6hr on 2008-05-31
> **Flobuntu said:**
> I've reinstalled a few times, but same problem persists each time...maybe trying something other than GG will be the ticket.

Just skimmed the thread.  Pick a version - I'd recommend 8.04LTS.

Boot, then select the check CD for errors.

If GRUB is not loading, you either have a HD problem (you can check with diagnostic software from HD manufacturer, or ultimatebootdisk), or there is a problem with the Ubuntu CD.

---

### Post by Flobuntu on 2008-05-31
> **ugm6hr said:**
> Just skimmed the thread.  Pick a version - I'd recommend 8.04LTS.

Boot, then select the check CD for errors.

If GRUB is not loading, you either have a HD problem (you can check with diagnostic software from HD manufacturer, or ultimatebootdisk), or there is a problem with the Ubuntu CD.

Will give 8.04 a try.  When I checked the GG cd for errors it said it was fine.  Maybe this is a hard drive problem--It's brand new, but that probably does not mean much.

Am flying off on a trip today will let you know how it goes next week.  Thank you for the help.

---

### Post by ugm6hr on 2008-06-01
> **Flobuntu said:**
> Will give 8.04 a try.  When I checked the GG cd for errors it said it was fine.  Maybe this is a hard drive problem--It's brand new, but that probably does not mean much.

Am flying off on a trip today will let you know how it goes next week.  Thank you for the help.

Make sure you check the md5 before burning the 8.04 CD.  The beginners sticky has links.

---

### Post by Flobuntu on 2008-06-23
Just to update, I just installed a new hard drive and it booted up the first time.  I'm going to keep the old drive and use it in an enclosure--it works fine as long as I don't need to boot.

thanks for all the ideas.

---

### Post by ugm6hr on 2008-06-23
> **Flobuntu said:**
> Just to update, I just installed a new hard drive and it booted up the first time.  I'm going to keep the old drive and use it in an enclosure--it works fine as long as I don't need to boot.

thanks for all the ideas.

Great.

Beware trusting data to a flawed HD though.

---

