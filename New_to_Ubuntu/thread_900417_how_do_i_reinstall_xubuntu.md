---
title: "how do i reinstall xubuntu?"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by mdialogo on 2008-08-25
i accidentally deleted my admin user account and error displays COULD NOT AUTHENTICATE: An unexpected error has occured. now im planning to reinstall xubuntu and start all over again. how do i reinstall xubuntu in the same partition? do i have to manually delete the partition where xubuntu installed or the livecd will automatically format the parition? please help...thanks

---

### Post by halitech on 2008-08-25
when you get to the partitioning stage of the install, select manual and you should see a listing of your partitions. select them based on the sizes and mount them accordingly. You may even be able to mount /home (if it was seperate) and not format it and save your data that was there

---

### Post by mdialogo on 2008-08-25
the first partition is ntfs where my winxp is installed, the second is ext3, and the 3rd is a swap space.  im not yet familiar with linux yet. if i mount the 2nd partition to / does it means that the system will be installed there. what is the meaning of "mount /home". lastly, does my windows installation will not be affected by the reinstallation? thanks

---

### Post by halitech on 2008-08-26
when doing your install, select the ext3 partition for / (root) and the swap space as obviously the swap space. As long as you don't tell it to install in the ntfs partition it won't be touched and GRUB should see it when you install it and allo wyou to dual boot.

/home can be a seperate folder for your personal files. Some people prefer to have it seperate and others just allow it to be inside /

---

### Post by drubin on 2008-08-26
> **halitech said:**
> when doing your install, select the ext3 partition for / (root) and the swap space as obviously the swap space. As long as you don't tell it to install in the ntfs partition it won't be touched and GRUB should see it when you install it and allo wyou to dual boot.

/home can be a seperate folder for your personal files. Some people prefer to have it seperate and others just allow it to be inside /

Swap Space is like Virtual Memory, Similar to Paging files in windows. Dont worry to much about it just that it is there and relatively  between your rams size and twice as much as your ram.

Mounting a separate /home is nice because this way if you choose to re-install your OS you will still have your settings saved.

This is just a fancy way of saying you will be taking that 1 ext3 partion and making it 2 ext3 partions, one's mount point will be /  and other would be /home/

Ie  the folder  /home/ANYTHING/UNDER/HERE will be on the second partion
 /ANY/THING/BUT/home  will be on the first partion. 

As for the sizes it depends how big your ext3 partion is??

---

