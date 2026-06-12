---
title: "Resizing a partition?"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by thunderwolf333 on 2008-04-26
I'm loving ubuntu, but I still use XP at times.
Problem is when I installed ubuntu as a partition on my system, it made xp the smallest it could be. So now I don't have any space on my xp anymore except like 200 mb and it's giving me the "not enough disk space" popup and constantly trying to run diskspace cleaner.

so i am wondering, **what is the easiest way to resize the partitions, by making xp larger and ubuntu smaller?**
please give me a simple solution because i dont want to mess up my computer lol.
thanks.

---

### Post by krisfrajer on 2008-04-26
gparted seems to work nice and EZ. I do not know if you will have surprises while resizing your partition. I recommend having a full backup of all your files in case it does not work. What size is your HD? Why did you minimize winXP's partition size?

---

### Post by thunderwolf333 on 2008-04-26
i didnt realize that i made it so small lol but thanks for your help i will back up my files first. and then use gparted but 

im not sure how to use it, can you explain?
when i tried to click resize it was greyed out (unselectable)

---

### Post by enigmaniac23 on 2008-04-26
The best way is to do it from a live CD.  So, you just boot from the live CD and then run gparted from there and see if you can resize it then.

---

### Post by thunderwolf333 on 2008-04-26
ok will try and post if it works.

---

### Post by Zralou on 2008-04-26
Make sure you defrag before you start.

Sara Lou

---

### Post by axor1337 on 2008-04-26
first i would defrag all parts  then i would boot to ubd[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)  it has gparted on it and it is very easy to use to resize i run  min of 40 for each of my os parts

---

### Post by thunderwolf333 on 2008-05-01
thank you all for your posts.
however im still having problems!
ok i used a gparted live cd to make ubuntu smaller.
i restarted, and went to the live cd again.
when i try to make windows larger it wont let me! even though there's like 20gb free now.
it will only let me make windows smaller. wth?
help!

---

### Post by sam_delta on 2008-05-01
try moving the ubuntu partition to the right so the 20g of free space are just after the windows partition, so when you try to make windows partition bigger, there will be no partition after it to "block" it from growing

tell us if it works

sam

---

### Post by Tatty on 2008-05-01
>Sorry! i posted this in the wrong thread :) <

---

### Post by iSplicer on 2008-05-01
> **thunderwolf333 said:**
> im not sure how to use it, can you explain?
when i tried to click resize it was greyed out (unselectable)

If you see a "padlock" icon next to the partition you want resized, you need to unmount it. Right click on the drive icon on your desktop/places and select "unmount"

Make sure you are doing this from a livecd

---

### Post by thunderwolf333 on 2008-05-01
thanks to isplicer, above me, but i already got through that problem but now i can't make windows larger.

to sam:
there is windows, then the free space, and then ubuntu.
it's already like you said.
here's some screenshots that might help.
it says the maximum size is what it already is?
[IMG]http://i29.tinypic.com/nezvk6.png[/IMG]
[img]http://i32.tinypic.com/30js3nm.png[/img]

these were taken in ubuntu as you can probably tell, but i resized the ubuntu portion from a gparted live cd.

---

### Post by sam_delta on 2008-05-02
alright, as i can see, that unallocated space is "part of" or "inside" the extended partition sda3, so its not considered as free space, it is considered as an extension of sda3, make the hole sda3 partition smaller or try to delete the "unallocated space" extension from sda3

tell us how it goes
sam

---

### Post by thunderwolf333 on 2008-05-03
Yes! I got it working.
Thanks sam :D

i couldnt delete the space.
so what i did first was make ubuntu into the same space again.
then resized the whole linix part (aqua blue) and then made xp larger.
i had to move around some stuff for it to work though.
it took me a while to figure out that you need to make it smaller and then drag it on the resize/move window. lol
thanks to all.

---

### Post by drsox1899 on 2008-05-03
Try using PartedMagic : [http://partedmagic.com/wiki/PartedMagic.php](http://partedmagic.com/wiki/PartedMagic.php)

It's a clone of Partition Magic (Symantec Windows App) and runs as a live CD.  I have found it to be very good.

Luck

---

### Post by sam_delta on 2008-05-03
> **thunderwolf333 said:**
> Yes! I got it working.
Thanks sam :D

i couldnt delete the space.
so what i did first was make ubuntu into the same space again.
then resized the whole linix part (aqua blue) and then made xp larger.
i had to move around some stuff for it to work though.
it took me a while to figure out that you need to make it smaller and then drag it on the resize/move window. lol
thanks to all.

no problem, glad you made it :)
enjoy ubuntu

sam

---

