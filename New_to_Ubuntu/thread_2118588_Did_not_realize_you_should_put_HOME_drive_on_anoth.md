---
title: "Did not realize you should put HOME drive on another partition"
date: 2013-02-21
forum: New to Ubuntu
---

### Post by kittkatt on 2013-02-21
Hello.

I installed ubuntu 12.04 and accidentally placed my HOME directory on my SSD by default.  This means that I only have 4GB of free space.  I was wondering if there is a way to fix this without having to reinstall Ubuntu.  I would like to have my home drive on a HDD with room.  I am willing to set up a new account, anything really with less hassle than wiping the partition and reinstalling the OS from scratch.  

Thank you for your help

---

### Post by JiuJitsu500 on 2013-02-21
Well, not too hard I guess.

Boot into a live environment first (so as to reduced room for error) and COPY, not move, the /home folder to the other hdd.

Then, you can either do this from live, but I'd prefer doing it from your install (get out of live). Get to your fstab by however you like ("sudo gedit /etc/fstab" will work from your install, or "gksu nautilus" and navigate through GUI from live environment).

Add the line:

UUID=XXXXXXXXXXXXXXXXXXX /home ext4 defaults 0 2

Note:

 the x's obviously need to be replaced by the UUID of the terget hdd. Find this by running "sudo blkid" and that should give the UUID of all your drives.

the "ext4" needs to be whatever type of fs you formatted the drive with - ubuntu works best on ext4 I think and it's usually a default anyway, so the line is probably safe as is.

Also, if you DO screw up and it won't boot, you COPIED the /home, so if you can't boot or anything goes wrong, get to that fstab again by whatever means and delete that line. If all goes well, you can remove the /home folder on the SSD saving you tons of room. Make sure everything goes right though, and you should be okay.

Alternately as well, you CAN replace the UUID with /dev/sda or whatever the /home is on, but because ubuntu does sometimes change what goes where (usually not a problem at all), it can be a MAJOR issue. Using the UUID is a MUCH safer option.

---

### Post by oldos2er on 2013-02-21
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

[http://www.howtogeek.com/116742/how-to-create-a-separate-home-partition-after-installing-ubuntu/](http://www.howtogeek.com/116742/how-to-create-a-separate-home-partition-after-installing-ubuntu/)

---

