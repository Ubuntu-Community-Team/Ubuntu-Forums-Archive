---
title: "permanently change location of /home/&lt;username&gt;/Music"
date: 2013-12-09
forum: New to Ubuntu
---

### Post by neil-phillips5 on 2013-12-09
Hi, I cannot find the solution to my problem despite spending a couple of hours googling.

What I want to do;
Change the location of /home/<username>/Music to somewhere else, ie a different hard drive than the one being used for / and the other os mount points.

what I DO NOT want to do;
relocate my entire /home

My progress
/etc/fstab
# store on 1TB drive
UUID=ac3435fb-f1b3-4d5a-8380-9edc9823caa3 /media/Storage ext4 defaults,user 0 3

manually
sudo mount --bind /media/Storage/Music/ ~/Music/

more info,
I am using an SSD for my mint 16 os. rather than fill that up with stuff I want to use a partition i have set aside on another hdd.
I have tried having a google, and thought pysdm would be my salvation, but that has been removed.
disks does not allow what i am trying to do either.

/media/Storage has folders named Music, Pictures, Videos etc so they are ready to be mounted

i believe i cannot edit /etc/fstab to do what i want as it does not understand who the user is due to it being run before a login [so to speak]

yes i can just paste in the manual line into program startup, but as you can guess i don't want to stop with just relocating my Music folder.

one solution may be to run a script for the user once the user has logged in, but i have never scripted in linux so i don't know;
what to put into the script or where to put the script to get it to run.

i have tried ubuntu tweaks and whilst it did work during one of my tests, it forgot the settings when i rebooted.
similarly .config/user-dirs.dirs did not stick after reboot

hope i posted this request for help in the right place.

---

### Post by Bucky Ball on 2013-12-09
Welcome. Move the folder to a new partition (or location), once you know it has copied correctly delete the /Music folder in /home/user/Music, create a symlink at /home/user/ that links to the copied folder:

```
sudo ln -s /home/user/Music /path/to/copied/music
```

This will create a symbolic link called /Music in /home/user to the copied folder, wherever you have put it. I use this method with ALL directories in my /home directory. I have three installs and this way all of them access the same directories, /Music, /Video, /Documents, etc. ;)

PS: Not sure you need the 'sudo' at the beginning of that command.

---

### Post by neil-phillips5 on 2013-12-10
Cheers that seems to have done the trick.

---

### Post by Bucky Ball on 2013-12-10
Great. If so, please mark thread as solved by following the info in my signature. Cheers. ;)

---

