---
title: "Reformatting"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by Don Cox on 2008-05-04
If I were doing a clean install of 8.04 from 7.04 Feisty Fawn using the desktop iso I would intend not reformatting the windows and /home partitions. Do I need to reformat the / partition or just install over it?

-- 
Don Cox

---

### Post by macaholic on 2008-05-04
Well, if you intend on keeping your home directory, you should probably back it up since either reformatting or installing over it will erase that data.

---

### Post by Dark Aspect on 2008-05-04
You need to backup your home folder before doing a clean install as noted above.If you have a external hard drive you can move the home folder over to it and then back after you install.Thats what I did when updating to Hardy and no problems yet :)

---

### Post by Don Cox on 2008-05-04
> **Dark Aspect said:**
> You need to backup your home folder before doing a clean install as noted above.If you have a external hard drive you can move the home folder over to it and then back after you install.Thats what I did when updating to Hardy and no problems yet :)

But does / require reformatting? 

-- 
Don Cox

---

### Post by jonaphant on 2008-05-04
you don't have to reformat the windows partition
just install 8.04 over the 7.04 partition but as the others say, make a backup of your home directory

---

### Post by Dark Aspect on 2008-05-04
> **Don Cox said:**
> But does / require reformatting? 

-- 
Don Cox

If you do a clean install,your whole hard drive is going to be reformatted including your root.There is not much reason to backup anything in your root since with Linux the only folder a basic user has access to is your home folder.Any software you had installed in your root can easily be reinstalled via Synaptic or a 3rd party repository.

---

### Post by Don Cox on 2008-05-04
Am I misreading the documentation? I believe it is essential not to reformat the 'windows' partition if I wish to keep XP Home and continue to dual boot. Is the 
back-up of /home (which I do routinely in any case) simply a precaution against things going wrong or is it an absolute essential?

---

### Post by bodhi.zazen on 2008-05-04
> **Don Cox said:**
> If I were doing a clean install of 8.04 from 7.04 Feisty Fawn using the desktop iso I would intend not reformatting the windows and /home partitions. Do I need to reformat the / partition or just install over it?

-- 
Don Cox

If you already have a separate /home partition, you should be fine.

Run the installer, manual partitioning, mount /home at /home and your windows partition where you want it (/media/windows). Just be sure to confirm the installer will NOT Format these partitions (it is a small check box in manual partitioning).

If you do NOT have a separate /home already, either move your old one or move your data to an alternate medium (alternate hard drive, USB device, CDROM/DVD).

[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Last thing to consider, rather then a separate /home use a separate /data partition.

---

### Post by kwacka on 2008-05-04
I agree with the previous post. If you are carrying out a clean install your home **_partition_** does not need to be formatted, set it to keep and your data will be untouched; likewise your Windows partition.

Only those that don't have 'Home' on a separate partition will lose their data (although, of course  its always wise to backup).

Format your '/' partition, ensure that there's no crud left behind.

---

### Post by Don Cox on 2008-05-04
Many thanks to all, especially posters #8 & #9. The original post has been edited as solved.

-- 
Don Cox

---

### Post by Oldsoldier2003 on 2008-05-04
> **bodhi.zazen said:**
> 
Last thing to consider, rather then a separate /home use a separate /data partition.

I agree- for the most part having a separate data partition is way more useful since its only prudent to use different usernames when playing with multiple OS distributions. At first thought it would be cool to use the same username and have your desktop remain consistent... but experience tells me there is enough difference between the different families of Linux that you end up messing your configurations up anyhow.

---

