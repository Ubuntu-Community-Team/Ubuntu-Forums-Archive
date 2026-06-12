---
title: "wow i messed up my partiton table"
date: 2008-09-27
forum: New to Ubuntu
---

### Post by RogerKorby on 2008-09-27
ok so what i was doing was trying to get more space to my linux partition this is what i did

in windows i used the shrink in the disk manager to shrink the windows partition

then i was using gparted to give the space to my ext3 partition
and thats when the power went out  and now i have nothing at all

i have tried to use the windows repair from the install cd and that didnt work because the partition table is corrupt  


where should i start looking for ways to repair the damage



any help will be great thanks

---

### Post by bumanie on 2008-09-27
Power interruptions are when disk patitioning mucks up and mucks up badly. I don't think there is a repair. You could try testdisk to recover things as they were before the partitioning - if you are lucky it might work. Otherwise try a program like photorec to try to recover any important data. They are both available form [here]("http://www.cgsecurity.org/wiki/TestDisk").

---

### Post by RogerKorby on 2008-09-27
i mean my power went out at my appartment at the same time i was running gparted :( after the power came back i couldent boot to ubuntu and my ntfs partition had a ! next to it saying its 


thanks ill try test disk first 

right now i just put back in the ubuntu cd is there a way i can fix ubuntu to boot without formating the partition

---

### Post by gastly on 2008-09-27
Hiya RogerKorby,

The same thing has happened to me lots of times, and like bumanie said, you cannot do anything but try and recover any useful data.

In my case, [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") worked wonders! You can also give it a try and see if it works for you too :)

Best of luck :)

- gastly

---

### Post by caljohnsmith on 2008-09-27
If you want a little help with testdisk, then boot your Ubuntu Live CD, enable all your repositories in System > Prefs > Software Sources, install and run testdisk:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Please post the output of that screen. Then do "proceed", Y/N depending on if you have any Vista partitions, hit enter, and select "search!" so it does a deeper search, which could take a while. Post the output of that screen too.

And lastly, please post the results of both the following:
```
sudo fdisk -l
sudo fdisk -lu

```
I know they are similar, but it will save me from having to do any math in converting between cylinders and sectors when checking your partition structure. :)

---

