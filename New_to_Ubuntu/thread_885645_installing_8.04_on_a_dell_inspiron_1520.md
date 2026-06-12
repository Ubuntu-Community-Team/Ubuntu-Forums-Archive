---
title: "installing 8.04 on a dell inspiron 1520"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by grungebunny on 2008-08-10
Hello I recently showed off my ubuntu desktop to a friend who was awestruck and had to have a copy for herself.  I made her a copy of the live cd and let her play around with it for a week till she asked me to help her install it.  I said no problem.

Now is where things get tricky. Once in the live cd the only 2 options for installing are the complete wipe of the hard drive and making Ubuntu the only OS but she's wanting to dual boot with XP.
The other option is the manual install. 

I searched several websites and I would like the options to install it simply with the drag bar to set the size of your partition, thats how I installed mine.
Why does ubuntu only give me these 2 options to install?
the complete way thus formatting the whole drive or the manual way which is way too complicated for me to comprehend.
Any help on how to get the easier install with the drag bar to work?

---

### Post by Elfy on 2008-08-10
Have you made sure to defrag the xp a couple of times.

---

### Post by Elfy on 2008-08-10
Have you made sure to defrag xp a couple of times

---

### Post by rampageoberon on 2008-08-10
Also at times due to windows unmovable files you need to do a offline defragment too. (Perfect disk or something similar will do that job)

I usually prefer to then bootup with gparted and create the partitions for the linux system.

Now when installing you only need to go into manual mode and instruct the installer on what partition you want to have linux use.

Hope that helps

---

### Post by Flyingjester on 2008-08-10
Does she have another partition she can use for ubuntu? if not, you need to boot up a liveCD and use GParted (or similar program) and make one for her, then use the manual install option to put the / partition on it, (you should also make a swap partition out of the newly created freespace, makes things run smoother) after that GRUB should auto recognize the windows partition and you would be good to go. [http://psychocats.net/ubuntu/index.php](http://psychocats.net/ubuntu/index.php) this site helped me out immensley.

---

### Post by Elfy on 2008-08-10
> Also at times due to windows unmovable files +1
I have turned off the pagefile, defragged, resized and then turned it back on before with installations.

---

### Post by Mytth on 2008-08-11
Try installing through wubi :[http://en.wikipedia.org/wiki/Wubi_(Ubuntu](http://en.wikipedia.org/wiki/Wubi_(Ubuntu))
If you installl through wubi you can automatically dual boot without loosing your xp files and os,and you dont have to partition your drive.

---

