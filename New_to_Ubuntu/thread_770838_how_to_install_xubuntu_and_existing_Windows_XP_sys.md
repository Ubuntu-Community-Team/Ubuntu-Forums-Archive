---
title: "how to install xubuntu and existing Windows XP system"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by zel108 on 2008-04-27
I have Windows XP with 3 partitions.

the first 20GB primary partition is NTFS with windows xp system,and the other 2 FAT32 logical partitions are used for data and can not put anything on it.

I repartitioned the first primary one with 10GB for the XP system,and gain 10GB free space would like to install xubuntu to learning Linux.

The question is there is no "/swap" option during the installation on this free 10GB for Linux the system. 

So,[COLOR="Blue"]**what should i do to install the xubuntu on this free 10GB partition and not affect XP and my data.**[/COLOR]

Thanks in advance!



P.S.  I download Xubuntu 8.04 (Hardy Heron),PC (Intel x86) desktop CD and burn to CD.

---

### Post by tompickles on 2008-04-27
basically, as youve done the hard part, pariting your hadd - then the install is easy. when you get to the partitionisng stage - play it safe and hit manual. there, you can make sure you pick that 10GB partition, and probably set it up as an extended one, with 512mb for swap, and the rest for /. it will ask you to chose a file system, so choose linux swap for the swap, and ext 3 for the prxubuntu partition and mount that one at /. also, you might want to mount the other ones at other places in your install, such as /files/music, or whatever. just, click manual and read properly, and dont touch the other partitions. oh, and back up

---

### Post by zel108 on 2008-04-27
> **tompickles said:**
> basically, as youve done the hard part, ...

thank you for the quick reply.

i really need your help about how to "[COLOR="Blue"]set it up as an extended one, with 512mb for swap, and the rest for /. it will ask you to chose a file system, so choose linux swap for the swap, and ext 3 for the prxubuntu partition and mount that one at /.[/COLOR]"
because there is no such option for xubuntu cd installation.

---

### Post by tompickles on 2008-04-27
just boot into the cd (set your BIOS to boot to cd, then reboot your machine)

EDIT: use the "try without any changes to the computer" option, cos you can install from this earlier.

then, once the live desktop loads (i think its a live cd still) have a play, and when your bored, hit the install button on teh desktop.

eventually (like the 3rd screen i think) you will get to partitioning. it will scan your current ones and suggest tuff to do. safeest to hit manual, and then you can see what is what. create a new partition in that 10GB your wanting to (but it will be an extended one, as you currently have 4 (the MAX) number of partitions. in that partition, you can create a further two. one  512MB will have a filesystem os swap. the rest of it, choose ext 3 and mount point /

i run ubuntu, not xubuntu, and not played with 8.04 xubuntu yet, but i assume the install is very very similar/identical

---

### Post by tompickles on 2008-04-27
just a thought - boot into it now, and get your internte working, then you can still use forums etc while your installing :)

---

### Post by zel108 on 2008-04-27
thank you tompickles,i do it now.

---

### Post by tompickles on 2008-04-27
fab - hope it makes sense... if you get stuck, then post back, and someone;; help you out! we're a friendly bunch

---

### Post by zel108 on 2008-04-27
hi,tompickles,i made it! 

now i need to lean how to setup the wireless network.

thank you again!

---

### Post by tompickles on 2008-04-28
brilliant - glad you did it. does it not work straight away then? have you tried unplugging it and plugging it back in again. if that still doesnt work, then give these forums a search for ndiswrapper. you might have to use your windows drivers to get it to work. this does involve a bit of work in a command line terminal, but there are plenty of people around with tutorial links in their sigs

---

### Post by hyper_ch on 2008-04-28
it would have been simpler to

(1) Resized the existing partitions to the size you want it
(2) The partition for Linux to leave unpartitioned
(3) Select in the installer "Use largest continuous empty space"

That would have picked up the unpartitioned space, made it an extended partition, made a swap and root partition within it.

However, you figured it out :)

Good luck with your wifi.

---

