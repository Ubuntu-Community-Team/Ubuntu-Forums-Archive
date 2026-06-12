---
title: "[SOLVED] how do i format a usb external hdd so i can save data to it???"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by stinger30au on 2008-06-29
i have installed qtparted from the repos. and started it from shell via

sudo qtparted

i have deleted the parttion that was there, ntfs. and told it to create new one and format it and commit changes.

now it tells me either i dont have enough permssions to mount it or i dont have enough permissions to create a directory on it let alone copy any data to it.

qtparted says it is partition 

/dev/sdd1

and set up a ext3.


what i have not done to allow me to use it????
im sure it will be something simple.

Thanks

---

### Post by sisco311 on 2008-06-29
By default a new partition is owned by root.
To change the owner of the partition open a terminal and type:
```
sudo chown -R *username:username* */media/my-disk*
```
assuming that *username* is your user name and */media/my-disk* is the mount point of the partition.

---

### Post by stinger30au on 2008-06-29
thanks for the tip.


i tired it and it says now when i try and access it via nautilus  "can not mount volume.your not privileged to mount the volume 'external' 


i wanted to name the hdd "external' as it is my external drive just to make my life easier.

---

### Post by lukjad on 2008-06-29
> **stinger30au said:**
> thanks for the tip.


i tired it and it says now when i try and access it via nautilus  "can not mount volume.your not privileged to mount the volume 'external' 


i wanted to name the hdd "external' as it is my external drive just to make my life easier.

To get access to something privileged go to a command prompt and type:
```
gksudo nautilus
```
This will give you a Graphical SuperUser powers (O.o). Then drill your way to the external hard drive, right click on it and select preferences. Make yourself owner and able to modify anything. Then close the Preference box and right click it again, this time selecting rename. 

That should just about do it.

Hope this helped.

---

### Post by stinger30au on 2008-06-29
> **lukjad007 said:**
> To get access to something privileged go to a command prompt and type:
```
gksudo nautilus
```This will give you a Graphical SuperUser powers (O.o). Then drill your way to the external hard drive, right click on it and select preferences. Make yourself owner and able to modify anything. Then close the Preference box and right click it again, this time selecting rename. 

That should just about do it.

Hope this helped.

ok, i tried this an now it says  "invalid mount option when trying to mount"

i started up qtparted via

sudo qtparted 

and tried again

even tried 

gksudo qtparted 

and deleted the partition and reinstalled and formatted partition and tried again.
no go.

got to be something real simple  i bet that im not doing.

any other ideas???

---

### Post by stinger30au on 2008-06-29
ok, found it.

did some googling and some reading.

i installed 

gparted

its a gnome partition manager
do this by applications -> add remove -> search on gparted and install. only about 400k so a few seconds

fireup terminal and type in
sudo gparted


in the upper right hand corner scroll down to your drive you want to format and mount.

then right click on it an unmount it if it not already done.

*CAREFUL WE ARE ABOUT TO DELETE EVERYTHING ON THIS DRIVE DO NOT GO ANY FURTHER IF THIS IS NOT WHAT YO WANT TO DO*

right click on it and click on 

format to -ext3

click the green apply button up top screen

then right lcick and itsays 

mount on

and next to it will be a drive letter, click that.

now exit and you can see the drive in nautilus and use it!!!!


YEE-HAW!!!

---

### Post by stinger30au on 2008-06-29
oops... bit to hasty on marking solved i was....

i can use this drive but only if i do a 

gksudo nautilus

i cant change the drive permissions...

help... any ideas

*sigh*

so close... so close

---

### Post by stinger30au on 2008-06-29
ok, now i have got it working....

i gave up on etx 3... something i was doing wrong.

so i reformatted and partitioned it as fat 32

set the permissions and off it goes.

log off and log on and still working....

just to power down pc and test agian, but looks good so far

---

### Post by stinger30au on 2008-06-29
*sigh*

power down and start up and gone again...


man... this is so frustrating

---

### Post by timcredible on 2008-06-29
don't use fat32 if you want file permissions, because fat32 doesn't have any.  so, if you want file permissions, go back to gparted, and run it from the menu this time System->Administration->Partition Editor, and try to make it ext3.  no reason it shouldn't work.  and just a little info on sudo, it's for command line stuff, gksu is for gui stuff.

---

### Post by stinger30au on 2008-06-29
> **timcredible said:**
> don't use fat32 if you want file permissions, because fat32 doesn't have any.  so, if you want file permissions, go back to gparted, and run it from the menu this time System->Administration->Partition Editor, and try to make it ext3.  no reason it shouldn't work.  and just a little info on sudo, it's for command line stuff, gksu is for gui stuff.


i dont want any file permissions.... i just want it to be blank, that i can plug in and back up some data to it every now and then and thats it.

if i can then plug it in to a xp box and copy the data to it , then even better.

thanks for the tip about sudo and gksu

---

### Post by stinger30au on 2008-06-29
got it working.... it even auto mounts on statup as well

did this

gksudo gedit /etc/fstab


you should see somewhere a line similar to this

/dev/hdd1                                  /media/hdd1    vfat  defaults                     0  0 

you need to delete everything after vfat, so delete the word "defaults" and the two number zero as well.

after the vfat word, add this

rw,user,umask=000 0 0

save the file and exit and restart pc.
all going to plan, you should now have read/write access to all data

just change the /dev/hdd1 to what ever your drive is


IT WORKS!!!

FINALLY!!!!


HOO-RAY!!

---

### Post by lukjad on 2008-06-30
Congrats!

---

### Post by stinger30au on 2008-07-01
> **lukjad007 said:**
> Congrats!

no worries.
the secret to my success was to format the hdd as fat32.
i dont care bout security on my backup, a backup is a backup and if i need to retrieve data in a hurry i dont want permissions.

if you could not tell, i was so thrilled when i got it working.

much googling and "tinkering"

persistence wins

---

