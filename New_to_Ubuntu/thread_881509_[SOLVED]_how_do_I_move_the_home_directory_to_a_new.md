---
title: "[SOLVED] how do I move the /home directory to a new partition?"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by tgyorgyi on 2008-08-06
I'd like to move my /home directory to an empty partition.
I have created a new partition for that with Gparted, but would like to know if and how can I move the /home directory to this new partition so that the system would still know where to look for it... I'm quite sure that a simple copy-paste would not do...

---

### Post by Megatog615 on 2008-08-06
[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

An article from way back in 2006.

---

### Post by kpkeerthi on 2008-08-06
A good one... 
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by c2olen on 2008-08-06
Nope, copy and paste won't do it.
There are actually two steps to be taken.

You need to move or copy your data to the new partition, and you need to have the new partition mounted during boot.

I prefer doing this in single user mode or from a live-CD session.. This way you can make sure no files are in use or modified after copy, which could be one you'd need or want to have. But this is not really necessary if you don't care about some session specific save files.

Moving or copying the data;
Make a temporary mountpoint for your new partition.
Then copy (not move, in case something goes wrong, you can start over) the old home to the new home.
```

#sudo mkdir /mnt/newhome
#sudo mount /dev/<your_new_partition> /mnt/newhome
#sudo cp -prxv /home /mnt/newhome

```See the [cp man pages]("http://unixhelp.ed.ac.uk/CGI/man-cgi?cp") for more info on the switches. These switches mean : preserver attributes, recurse into subdirectories, do not leave this filesystem and be verbose.

If you prefer using DD, you could read this [archived thread]("http://ubuntuforums.org/archive/index.php/t-435585.html").

Having the new partition mounted during boot is easy. Just update your /etc/fstab file and make the /home mountpoint refer to the new partition. This is now probably something like /dev/sda2 (just a guess). If your new partition would be /dev/sda5, you would need to change sda2 to sda5 obviously.

After a reboot, your new /home will be mounted, and the old /home will be a partition (but still holding your data). U can use Gparted to give it a new destination.

---

