---
title: "error 13, can't boot Ubuntu"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by Mr Pockets151 on 2008-06-30
I have Mandriva Grub booting my system.  Mandriva boots fine and so does XP.  I installed ubuntu onto the same HDD as Mandriva but in step 7(live cd) I chose to install Ubuntu grub onto the Ubuntu partition.  

I set up my menu.lst as this



```
title WinXP
rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1

title Ubuntu
root (hd0,2)
chainloader +2
```
When I choose Ubunut I get the Ubuntu GRUB loaded but from there I get an error 13. 

my fdisk -l 
```
Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9ebf9ebf

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        8938    71794453+  83  Linux
/dev/hda2            8939       14046    41030010   83  Linux
/dev/hda3   *       14047       14047        8032+  82  Linux swap / Solaris

```where hda2 is Ubuntu

---

### Post by caljohnsmith on 2008-06-30
> **Mr Pockets151 said:**
> I have Mandriva Grub booting my system.  Mandriva boots fine and so does XP.  I installed ubuntu onto the same HDD as Mandriva but in step 7(live cd) I chose to install Ubuntu grub onto the Ubuntu partition.  

I set up my menu.lst as this



```
title WinXP
rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1

title Ubuntu
root (hd0,2)
chainloader +2
```
When I choose Ubunut I get the Ubuntu GRUB loaded but from there I get an error 13. 

my fdisk -l 
```
Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9ebf9ebf

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        8938    71794453+  83  Linux
/dev/hda2            8939       14046    41030010   83  Linux
/dev/hda3   *       14047       14047        8032+  82  Linux swap / Solaris

```where hda2 is Ubuntu
I think you might simply need to change the "chainloader +2" to "chainloader +1". Note that the +1 is the block list offset and so you shouldn't use +2 just because that is your second chainloader entry. For details see: [http://orgs.man.ac.uk/documentation/grub/grub_11.html#SEC36](http://orgs.man.ac.uk/documentation/grub/grub_11.html#SEC36)

---

### Post by maxcarson on 2008-06-30
can't get ubuntu to boot from cd. will not get past the load graphic. freezes at one third load, cd does not move, cd door does not respond? my cd is new out of the package, tried both cd drives, same. hp/compaq sr1120nx windowsxp ati9320 vid. card.,
external hdd, 1320 hp printer, usb. what am i doing wrong? i am
a newbie.

---

### Post by caljohnsmith on 2008-06-30
> **maxcarson said:**
> can't get ubuntu to boot from cd. will not get past the load graphic. freezes at one third load, cd does not move, cd door does not respond? my cd is new out of the package, tried both cd drives, same. hp/compaq sr1120nx windowsxp ati9320 vid. card.,
external hdd, 1320 hp printer, usb. what am i doing wrong? i am
a newbie.

Welcome to the forums, maxcarson. You really should post your question in a thread of your own and not in this thread since your question is unrelated. that's considered "hijacking" the thread and people are not going to be willing to give you a response. Hopefully someone can help you if you start your own thread. :)

---

### Post by sydbat on 2008-06-30
I hope I am not hijacking this thread, but I am just reinstalling Hardy and need to know where to put Grub. As th OP mentioned (sort of) there are choices at step 7. Should I put grub into the Ubuntu partition or let it go to the default (hd0) which has not worked before?

---

### Post by ChameleonDave on 2008-06-30
> **sydbat said:**
> I hope I am not hijacking this thread, but I am just reinstalling Hardy and need to know where to put Grub. As th OP mentioned (sort of) there are choices at step 7. Should I put grub into the Ubuntu partition or let it go to the default (hd0) which has not worked before?

Yes, you are hijacking the thread.  Just put GRUB on the master boot record of (hd0) unless you have some particular reason for wanting to put it on a partition instead.  This is not the thread to discuss this.

---

### Post by ChameleonDave on 2008-06-30
> **Mr Pockets151 said:**
> I have Mandriva Grub booting my system.  Mandriva boots fine and so does XP.  I installed ubuntu onto the same HDD as Mandriva but in step 7(live cd) I chose to install Ubuntu grub onto the Ubuntu partition.  

I set up my menu.lst as this



```
title WinXP
rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1

title Ubuntu
root (hd0,2)
chainloader +2
```
When I choose Ubunut I get the Ubuntu GRUB loaded but from there I get an error 13. 

So, this is the menu.lst from your Mandriva installation.  It hands over the boot process to the grub on your Ubuntu partition, which fails.  (Amd I don't see Mandriva on that list for some reason)  We are going to need to see your Ubuntu menu.lst to investigate that.

Also, I'm not sure that all this chainloading is necessary anyway.  You should be able to have one GRUB installation that directly loads Mandriva or Ubuntu, or chainloads into XP.

---

### Post by sydbat on 2008-06-30
I apologize. It will not happen again. And thank you for the help.

---

