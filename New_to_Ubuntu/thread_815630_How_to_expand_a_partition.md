---
title: "How to expand a partition"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by adobrakic on 2008-06-01
Is there anyway, without reinstalling, that I can make my Ubuntu partition larger? I just deleted like 15gb off of my Windows partition, and would like to make my Ubuntu one larger.

---

### Post by ALex! on 2008-06-01
> **adobrakic said:**
> Is there anyway, without reinstalling, that I can make my Ubuntu partition larger? I just deleted like 15gb off of my Windows partition, and would like to make my Ubuntu one larger.

yes, there is!!! boot into a live cd and click System->Administration->Partion Editor (gparted)

But it will take a looooooong long time to finish... so please be patient and never ever ever cancel it!

[http://ubuntuforums.org/showthread.php?p=5095574#post5095574](http://ubuntuforums.org/showthread.php?p=5095574#post5095574)

---

### Post by ibuclaw on 2008-06-01
Yes, there is.

Grab your Ubuntu LiveCD, insert it into your disc tray, reboot and boot into it.

Once the LiveCD environment has loaded, open up GParted (It should be in "**System>Administration**" in the Gnome menu).

And you can stretch the size of the partition in there.

Also, don't mount any partitions when the LiveCD starts up. As you can only alter your partition when it is unmounted.

Regards
Iain

---

### Post by ALex! on 2008-06-01
> **tinivole said:**
> Yes, there is.

Grab your Ubuntu LiveCD, insert it into your disc tray, reboot and boot into it.

Once the LiveCD environment has loaded, open up GParted (It should be in "**System>Administration**" in the Gnome menu).

And you can stretch the size of the partition in there.

Also, don't mount any partitions when the LiveCD starts up. As you can only alter your partition when it is unmounted.

Regards
Iain

:mrgreen:

---

### Post by adobrakic on 2008-06-01
okay thanks a lot guys. :]

---

### Post by ALex! on 2008-06-01
> **adobrakic said:**
> okay thanks a lot guys. :]

you're welcome! :mrgreen:

---

### Post by adobrakic on 2008-06-01
[IMG]http://img260.imageshack.us/img260/8242/screenshotdevsdagpartedva3.png[/IMG]

I got to here. The 'unallocated' is the space i just freed from the windows partition and wanna add to the linux partition, but idk how to do that. if i click on dev/sdaS, and go to resize/move, it doesnt let me make it any bigger.

---

### Post by IHATEDLINK on 2008-06-01
> **adobrakic said:**
> [IMG]http://img260.imageshack.us/img260/8242/screenshotdevsdagpartedva3.png[/IMG]

I got to here. The 'unallocated' is the space i just freed from the windows partition and wanna add to the linux partition, but idk how to do that. if i click on dev/sdaS, and go to resize/move, it doesnt let me make it any bigger.

Yes it does. :P.
Click n' drag the border of the partition you want to expand onto the unallocated space when pressing after pressing "resize/move"

**DON`T FORGET TO CLICK "APPLY" WHEN YOU FINISH.**

---

### Post by adobrakic on 2008-06-01
I'm trying, lol. I right-click on /dev/sda5 and go to 'resize/move', this is what I get. I can't make it bigger, only smaller.

[IMG]http://img299.imageshack.us/img299/129/screenshotresizemovedevmz7.png[/IMG]

---

### Post by adobrakic on 2008-06-01
I right-clicked on the 'unallocated' and went to paste, and it opened the /dev/sda5 for me, and then I could make it bigger. So i think it's good now. Is this how it's supposed to look? 
                                                 

[IMG]http://img528.imageshack.us/img528/6711/screenshotdevsdagpartedve2.png[/IMG]

---

### Post by adobrakic on 2008-06-01
Sorry, i know i should wait 24 hours to bump a topic, but i really don't wanna be running on the live cd for 24 hours.

---

### Post by ibuclaw on 2008-06-02
> **adobrakic said:**
> Sorry, i know i should wait 24 hours to bump a topic, but i really don't wanna be running on the live cd for 24 hours.

Have you solved this yet?

The answer to your previous question is, no. That should not look like that at all.

Try increasing that amount of space that precedes the partition to see if that makes any difference.

Regards
Iain

---

### Post by IHATEDLINK on 2008-06-02
> **adobrakic said:**
> Sorry, i know i should wait 24 hours to bump a topic, but i really don't wanna be running on the live cd for 24 hours.

I really don't know what to say...
Defragmenting the disk may help. Aldo try using the [gPareted live CD]("http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779"), sometimes the one included in the Ubuntu live CD mounts and unmount the disk, this can cause issues during the process. The file you have to download is an .iso so you just burn it with brasero or nero like you did with Ubuntu's.
That's all I can think of... so you go and try it! :D

---

