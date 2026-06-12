---
title: "partition problem. I think I broke it."
date: 2008-04-24
forum: New to Ubuntu
---

### Post by jjremy on 2008-04-24
ok, I hope I'm put this in the right place. Sorry if it's not. I'm just kinda freaking out at the moment.
so I'm running a Dell inspiron 1520 core2 duo t7250. 160gb harddrive. with nvidia 8600m gt. vista home premium. 

I've played around for a few hours with the Gutsy livecd in the past and have been waiting for the Haron release to truely dip my feet into Ubuntu.

after not being able to shrink my windows partition(within windows)to make room for to install haron, I decided to boot up the livecd and tried doing it in Gparted. (the partitions were showing 4 different sections for some reason. OS - 140ishGb Recovery - 10gb and 2 strange small ones. one was 78mb and the other was about 2gb. no idea what those 2 are??)  

It took about 5 hours. but it said it was successful. i managed to shrink the recovery partition down to 5gb and OS down 45gb. so windows still has 90gb and I now have 50gb of unallocated space.

but when I rebooted and tried to load up windows it just gets stuck cycling the bios load. bios loads up. screen goes black. then right back to bios load. 

Now I can't get back into windows! I think I messed up the partion tablet? I don't know what to do. I'd like to try and avoid reinstalling windows if possible.

Can anyone help me out? If anymore info is needed let me know.
thanks in advance.

---

### Post by swoll1980 on 2008-04-24
if you didn't defrag before partitioning you may have messed the windows installation up did you defrag first?

---

### Post by ElTimo on 2008-04-24
That's interesting. One question: does GRUB show up? Basically, does a menu show up that lists the operating systems on your computer? because if not, you may have a problem with your bootloader, which can (probably) be fixed by simply running the install again from the LiveCD. Let me know if that helps.

PS: In Soviet Russia, partition table breaks YOU!!!
(sorry i couldnt resist :-P)

---

### Post by jjremy on 2008-04-24
I did both a scandisc and defrag before I tried.

---

### Post by swoll1980 on 2008-04-24
> **ElTimo said:**
> That's interesting. One question: does GRUB show up? Basically, does a menu show up that lists the operating systems on your computer? because if not, you may have a problem with your bootloader, which can (probably) be fixed by simply running the install again from the LiveCD. Let me know if that helps.

PS: In Soviet Russia, partition table breaks YOU!!!
(sorry i couldnt resist :-P)

He hasn't installed ubuntu yet I don't think anyways did you?

---

### Post by jjremy on 2008-04-24
that's correct. I haven't installed ubuntu yet. I wanted to see if windows still worked beforehand. 
should I try installing it and see if windows shows up in GRUB?

---

### Post by swoll1980 on 2008-04-24
sounds like maybe the master boot record got messed up you can fix that by using the GNU Grub disk or if you install ubuntu

---

### Post by jjremy on 2008-04-24
ok, ill try installing ubuntu now. Ill report back after. 

thank you kindly.

---

### Post by swoll1980 on 2008-04-24
> **jjremy said:**
> that's correct. I haven't installed ubuntu yet. I wanted to see if windows still worked beforehand. 
should I try installing it and see if windows shows up in GRUB?

yes go ahead it will probably fix the problem

---

### Post by Miljet on 2008-04-24
If I understood correctly, the first mistake was shrinking your Windows recovery partition. Now you can't use it to recover Windows. I don't know how to repair the damage. If you have the Windows install disks, just finish clearing the recovery partition, I guess.

---

### Post by ElTimo on 2008-04-24
yup, that sounds like it might solve the problem, or at least get the computer to a usable state. Just out of curiosity, what did you use to partition your drive? Was it gparted (I think it's listed as "Partition Editor" in System->Administration)? Or did you use the LiveCD installer, and just quit after it partitioned?

---

### Post by jjremy on 2008-04-24
Ok, ubuntu is installed. But for some reason GRUB is now showing 2 XPs(neither of which load) and NO vista.
This computers never even had XP on it.
Ubuntu is running just fine. Which is nice.
Windows however is completely missing. Is there any hope of recovering it*

thanks again.

---

### Post by jjremy on 2008-04-24
sorry for the double post.

---

### Post by ElTimo on 2008-04-24
are you able to see the windows partition from ubuntu? if so, you may be able to copy all of your important files (assuming that they fit onto your ubuntu partition or you have an external drive), and reinstall windows. This is probably not the only way though, but if you can, you should still back up any files from windows you can access just in case.

---

### Post by jjremy on 2008-04-24
hey, look at that. i actually can access it through ubuntu. Now I can atleast get my firefox bookmarks back. 

thanks for the help. now I need to find a way to get my wifi working on ubuntu(no clue on that one either) and then ill be set for now. 

aslo, will i be able to reinstall windows without ruining my ubuntu partition?

---

### Post by ElTimo on 2008-04-24
now that you have a separate partition, yes. you'll just have to reinstall to that partition.

---

