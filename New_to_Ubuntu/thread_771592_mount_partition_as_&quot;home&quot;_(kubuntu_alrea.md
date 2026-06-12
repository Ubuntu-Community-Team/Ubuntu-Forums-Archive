---
title: "mount partition as &quot;/home&quot; (kubuntu already installed)"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by TMcKSmith on 2008-04-27
I just installed Hardy Heron, and forgot to configure the previous /home partition I had when I installed.  Kubuntu created a new '/home' directory for me but I want to use my partition.  It's listed under 'media' now and when I go into the mount properties and try to change the mountpoint from /media to /home (and check off 'mount automatically') it gives me this error:

"Mountpoint has to be below /media"

How can I do this?  Thanks for the responses in advance...

---

### Post by gug@fnal.gov on 2008-04-27
Hi,
   I am no expert, but I suspect that the system may not like changing mount points when those are currently mounted. I would approach this as follows:
cd /etc
sudo cp fstab fstab.save
sudo umount /media
sudo umount /home   # probably won't work but I would try anyway
sudo vi fstab # edit to change /home to /media and vice versa
sudo mount -a
sudo /sbin/shutdown -r now # reboot


Of couse an expert might say I am crazy, so you might want to wait for a second opinion. I have administered RedHat Linux machines before, and while I have renamed mounts before I have never done /home.

---

### Post by Paqman on 2008-04-27
[Psychocats knows all](http://www.psychocats.net/ubuntu/separatehome) ;)

---

