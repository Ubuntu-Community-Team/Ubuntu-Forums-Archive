---
title: "[SOLVED] On Live CD right now...over-install an existing distro"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by pavan115 on 2008-11-01
Hello everyone,

I have already installed an ubuntu distro but some experiments later, messed up the OS and it lags badly. I am on the live CD as I type this out and was wondering how I should delete and replace the same linux distro from the live CD.

I have heard bad rumours about Grub making the OS haywire when deleting an existing Dual partition - which I have btw.

If you need any system specs please ask. 

Thank you

---

### Post by taurus on 2008-11-01
If you want to reinstall over existing version, just tell the installer to format the partitions.  Then, you would have a clean new install.

---

### Post by pavan115 on 2008-11-01
I'm a bit of a noob, so can you help me with the step by step?

---

### Post by pavan115 on 2008-11-01
Like - once we get to patritioning, do we select Manual? and then click on the Format checkbox for both ext3 and swap files?

---

### Post by taurus on 2008-11-01
Yeah, you can do that.  Make sure you pick a partition to mount it to /.  And don't forget to put a check mark in the format box to format it.  

How many partitions do you have?

---

### Post by pavan115 on 2008-11-01
I guess we need to go to GParted to format?

Format to NTFS? Do we swapoff our swap and format that too?

---

### Post by mkvnmtr on 2008-11-01
I don't remember the number of steps but I can explain I think. When you click on the install icon you go through several steps. Naming the user and computer. Setting the time and you will arrive at the point where it asks you  how you want to install and give you several choices. If you want to go back in the same partitions pick manual install. You will be presented with a list of your partitions. If you remember how much space you gave to Ubuntu you should not have a problem picking it out. If you are dual booting you need to know how much space your other OS had and you can tell which it is. Also you have a grub and a swap partitions. grub is very small and swap is some bigger but small also. You have to make suer the name of these is correct. My Ubuntu partition was named "/" and I had to put that in before it would let me proceed. If you don't change the size of the partitions it won't let you make a mistake when you think you have it right proceed. Then it will ask you if you want to format these 2 partitions. Up to this point you can back out and you have changed nothing. Once you click on format you are past the point of no return and it will just finish the install. Give it a try. Go step by step and when you have a question back out and come to the forum to ask. Go at it again . When you feel sure you have it right  then format and finish. Grub and your Ubuntu should be installed just like it was before.

---

### Post by pavan115 on 2008-11-01
I guess I better give a better info...

I have an XP partition and a Xubuntu partition

I tried to click on the checkmark for Format and it gives me this Edit Partition menu - I'm lost there

Right now it shows that i have a NTFS partition - for my windows, a linux partition for my swap and an ext3 partition that is taking up almost the size that i initially set up for my Xubuntu.

Thank you for all the assistance upto now btw!

---

### Post by louieb on 2008-11-01
> **pavan115 said:**
> Like - once we get to patritioning, do we select Manual? and then click on the Format checkbox for both ext3 and swap files?
You got it right. format the ext3 partition and mount it as / (root). It will probably set up swap without you doing any thing.

---

### Post by pavan115 on 2008-11-01
Hi mkvnmtr,

When I tried to click on the ext3 partition and forward it gives me "No root filesystem is defined"

Also, in my guided install it doesn't recognize anything except a 40 GB HD as a whole XD That wasn't how it was when I first clicked on install :(

---

### Post by taurus on 2008-11-01
> **pavan115 said:**
> I guess I better give a better info...

I have an XP partition and a Xubuntu partition

I tried to click on the checkmark for Format and it gives me this Edit Partition menu - I'm lost there

Right now it shows that i have a NTFS partition - for my windows, a linux partition for my swap and an ext3 partition that is taking up almost the size that i initially set up for my Xubuntu.

Thank you for all the assistance upto now btw!

You don't have to do anything with the swap partition.  However, you want to tell the installer to mount the second partition, ext3, to / and format it as ext3.  That's where you want to reinstall Ubuntu to.  You don't have to reformat it to ntfs first.

---

### Post by pavan115 on 2008-11-01
Hi louieb,

that helped! I got an option to "use as" and i selected Ext3 journaling filesystem since only that seemed faimilar. Is that right? ( I also used it as "/")

And I am unsure what anyone is saying I should do with my swap partition? Format it or leave it as it is?

---

### Post by pavan115 on 2008-11-01
Alright ignore my last post - tauraus made it clear before my reply. 

Thank you all! i will give it a try and see how it works out! ^^

---

### Post by pavan115 on 2008-11-02
Yippe! It works! Thanks a lot everyone!

---

