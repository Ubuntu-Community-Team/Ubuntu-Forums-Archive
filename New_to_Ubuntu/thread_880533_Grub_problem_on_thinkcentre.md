---
title: "Grub problem on thinkcentre"
date: 2008-08-05
forum: New to Ubuntu
---

### Post by jerryduk on 2008-08-05
I need help with what I think is a GRUB problem. 
I am a total UBUNTU/Linux newbie.
I just got a new used computer, an IBM thinkcentre.
I can&#8217;t dump windows because I have some special applications, vinyl cutter things like that.
Eventually I hope to run a few windows apps in a virtual machine envronment but for now I plan to dual boot.

I have found two articles about how to set up the PC to preserve the original rescue and recover partition whilst dual booting Ubuntu but I can&#8217;t get the final stage to work.

References:
[http://gawrysiak.org/corvus/?p=4](http://gawrysiak.org/corvus/?p=4)
[http://www.thinkwiki.org/wiki/Rescue_and_Recovery](http://www.thinkwiki.org/wiki/Rescue_and_Recovery)

I have partitioned my disk as outlined in the articles which recomend a small boot partition (which I formatted FAT32). I loaded ubuntu from the alternate CD and when it comes to install grub loaded it in the small boot partition.
I then copied the first part of the boot partition to a file named ubuntu.img using the command:
dd if=/dev/sda3 of=ubuntu.img bs=512 count=1
I moved ubuntu.img to c:\ (my windows partition)
I then appended boot.ini to include the line:
c:\ubuntu.img="Ubuntu Linux Hardy Heron"
Now when I boot the PC I get first the option to boot windows or Linux as expected but when I choose Linux the machine hangs with the error:
<windows root>\system\hal.dll
File corrupt or not found reinstall this file ??????????

The only strange point is that the boot prompt says &#8220;Linux Hardy Heron&#8221; not &#8220;Ubuntu Linux Hardy Heron&#8221; as typed in boot.ini?

It appears the Linux boot information is not being pickd up.
I guess this could be because:
1) the information was not correctly written to the small boot partition
2) the information did not copy to ubuntu.img correctly
3) something else which is way over my head

I also tried to install GRUB to a USB pen. When I use this method I get an error:
GRUB geom error

Can anyone help ?

[COLOR="Red"]Problem solved. It was just a missing "=" sign in boot.ini that I failed to spot even though I must have looked at it ten times.[/COLOR]

---

### Post by logos34 on 2008-08-05
> **jerryduk said:**
> I loaded ubuntu from the alternate CD and when it comes to install grub loaded it in the small boot partition.


But did you also point the installer to the separate /boot partition?

You should have manually entered these mount points:

**/boot**
/
/swap

Get [fs-driver]("http://www.fs-driver.org/") so you can access your linux files.

Is there anything in sda3?

ADD: you normally don't need a separate /boot, so I'm not sure why you did it that way

---

### Post by jerryduk on 2008-08-05
Thanks for the reply.
Sorry not sure what you mean by mount points?
Linux files appear to be on the Linux Partition.
Linux SWAP partition is set up.
No files in sda3 but when I copied the first block with dd if=/dev/sda3 of=ubuntu.img bs=512 count=1 and look at the ubuntu.img file I see text saying "GRUB  Geom Hard Disk Read  Error" for example so I assume that part of Grub has been installed in the first block of sda3 as expected.

I can access the Linux files by booting the live CD.

---

### Post by logos34 on 2008-08-05
Sounds like what I thought--your kernel images and menu.lst are in /boot **directory** on linux root partition, not sda3 which you intended as a separate /boot.

Do this:

Write grub to the bootsector of the root partition using the 'Restore Grub from the live cd' isntructions in my signature--except do '**setup (hd0[COLOR=Red],?[/COLOR])**' where [COLOR=Red]?[/COLOR] = root partition (remember grub starts counting from 0).

Post your **sudo fdisk -l** if unsure.

Now redo the command:

dd if=/dev/sda2 of=ubuntu.img bs=512 count=1

replace 'sda2' with whatever your / partition # is

Copy the file over to c:\ and try again

---

### Post by jerryduk on 2008-08-05
> **logos34 said:**
> Sounds like what I thought--your kernel images and menu.lst are in /boot **directory** on linux root partition, not sda3 which you intended as a separate /boot.

Do this:

Write grub to the bootsector of the root partition using the 'Restore Grub from the live cd' isntructions in my signature--except do '**setup (hd0[COLOR=Red],?[/COLOR])**' where [COLOR=Red]?[/COLOR] = root partition (remember grub starts counting from 0).

Post your **sudo fdisk -l** if unsure.

Now redo the command:

dd if=/dev/sda2 of=ubuntu.img bs=512 count=1

replace 'sda2' with whatever your / partition # is

Copy the file over to c:\ and try again

I tried setup hd2 I think. But I am not sure I was in the correct place when I did it. Rather than risk messing up my nice partitions and overwriting my MBR here is the fdisk list:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcccdcccd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       22171   178088526    7  HPFS/NTFS
/dev/sda2           29863       30401     4329517+  12  Compaq diagnostics
/dev/sda3           29850       29862      104422+   c  W95 FAT32 (LBA)
/dev/sda4           22172       29849    61673535    5  Extended
/dev/sda5           22172       29673    60259783+  83  Linux
/dev/sda6           29674       29849     1413688+  82  Linux swap / Solaris

Partition table entries are not in disk order
ubuntu@ubuntu:~$

find /boot/grub/stage1    ===> (hd0,4)

thanks

---

### Post by logos34 on 2008-08-05
> **jerryduk said:**
> 
/dev/sda5           22172       29673    60259783+  83  Linux


yep,

do

[B]setup (hd0,4)

[/B]and dd if=/dev/sda**5** of=ubuntu.img bs=512 count=1

---

### Post by jerryduk on 2008-08-05
Many thanks for the help.
This wont re-write the MBR for my Windows partition?

---

### Post by jerryduk on 2008-08-05
Many thanks for your help but still didn't get it to work.

This is what I did:

ubuntu@ubuntu:~$ sudo grub 

       [ Minimal BASH-like line editing is supported.   For 
         the   first   word,  TAB  lists  possible  command 
         completions.  Anywhere else TAB lists the possible 
         completions of a device/filename. ] 

grub> find /boot/grub/stage1 

 (hd0,4) 

grub> root (hd0,4) 

grub> setup (hd0,4) 
 Checking if "/boot/grub/stage1" exists... yes 
 Checking if "/boot/grub/stage2" exists... yes 
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes 
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,4)"... failed (this is not fatal) 
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,4)"... failed (this is not fatal) 
 Running "install /boot/grub/stage1 (hd0,4) /boot/grub/stage2 p /boot/grub/menu 
.lst "... succeeded 
Done. 

grub> quit 

ubuntu@ubuntu:~$ sudo grub 

close terminal

open terminal

ubuntu@ubuntu:~$ sudo -i 
root@ubuntu:~# dd if=/dev/sda5 of=ubuntu.img bs=512 count=1 
1+0 records in 
1+0 records out 
512 bytes (512 B) copied, 0.0179083 s, 28.6 kB/s 
close terminal

copy file root/ubuntu.img > usb stick

copy file usb stick/ubuntu.img > c:

error was the same as before !

---

### Post by logos34 on 2008-08-05
> **jerryduk said:**
>  when I choose Linux the machine hangs with the error:
<windows root>\system\hal.dll
File corrupt or not found reinstall this file ??????????

The only strange point is that the boot prompt says “Linux Hardy Heron” not “Ubuntu Linux Hardy Heron” as typed in boot.ini?

Well, we know one thing: your grub files (stage1 et al) and kernel images are definitely on / in the /boot folder, not on sda3.  But the main problem seems to be on the windows side, because it can't read the .img file (can't even get the title right).  The line in boot.ini is correct as far as I can tell, and it appears to be in c:\.

Not sure what to suggest...maybe boot.ini can be replaced by a fresh copy...try Start>Run>type **msconfig**>BOOT.INI tab>see if there's an checkbox option that can help (been a while since I had XP).  Or run error checking (**chkdsk /r**).

---

### Post by jerryduk on 2008-08-06
Fantasmagorical !!!!!!!

Two days of hair pulling is over.
Your comment about boot.ini prompted me to examine boot.ini more closeley and stupidly I had missed an "=" sign when typing. Now it boots to GRUB and beyond with no problem.

Thanks again for your help.

---

### Post by logos34 on 2008-08-06
> **jerryduk said:**
> 
I then appended boot.ini to include the line:
c:\ubuntu.img="Ubuntu Linux Hardy Heron"

...

[COLOR=Red]Problem solved. It was just a missing "=" sign in boot.ini that I failed to spot even though I must have looked at it ten times.[/COLOR]

Aha, so that was it!

Those little typos can be tough to spot...I've had days like that.  Just wish I'd asked you to post your actual boot.ini--might have saved you a few hours.

Glad it's fixed.  Now you can start enjoying Ubuntu!

---

