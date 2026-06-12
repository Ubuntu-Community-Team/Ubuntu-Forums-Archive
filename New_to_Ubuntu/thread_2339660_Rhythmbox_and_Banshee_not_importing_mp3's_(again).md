---
title: "Rhythmbox and Banshee not importing mp3's (again)"
date: 2016-10-11
forum: New to Ubuntu
---

### Post by kaleidopunk on 2016-10-11
Hi, I've done lots of looking around because many people seem to have the same problem, but can't find a solution!

Neither Rhythmbox or Banshee will import my mp3 files. I'm getting rather vexed. 
I just reinstalled Ubuntu 16. 04 LTS 32-bit after never ending error fixing... It hadn't installed properly the first time around ( i think ). 

Please bear with me I'm new to linux and struggling a bit!

Any good fixes for this? Tried to change preferred format to mp3 in Preferences, but it failed to find relevant plugins.

Please halp

---

### Post by #&amp;thj^% on 2016-10-11
Hi kaleidopunk...what dose this report from the terminal
```
apt-cache policy gstreamer1.0-plugins-ugly
```
If nothing appears as installed then install with 
```
sudo apt-get install gstreamer1.0-plugins-ugly
```

---

### Post by kaleidopunk on 2016-10-11
Thanks for your reply! It says it's already installed. After running the install command

Reading package lists... Done
Building dependency tree       
Reading state information... Done
gstreamer1.0-plugins-ugly is already the newest version (1.8.2-1ubuntu0.1).
gstreamer1.0-plugins-ugly set to manually installed.
0 to upgrade, 0 to newly install, 0 to remove and 192 not to upgrade.

---

### Post by #&amp;thj^% on 2016-10-11
Well that should have been enough...So when you say it or they are not importing files...Are these files on your harddrive or from an Mp3 player device of some sort.
IE: External Device.

---

### Post by ajgreeny on 2016-10-11
And if it is from an external device is that device mounted all the time?
You may need to edit /etc/fstab to mount the disk/device at boot if this turns out to be the reason for the problem.

---

### Post by Geoffrey_Arndt on 2016-10-13
Or just use the "Disks" program . . a gui program installed by default in Ubuntu.   It will allow for automount at login and update the fstab file also.

---

### Post by Geoffrey_Arndt on 2016-10-14
Have you done the standard post-install tweaks to get the codecs/plugins?   Perhaps you're not yet aware of those so, . . . . take a close look at this link and see if you've installed.   See item #4 especially as regards to "Install Ubuntu Restricted Extras" . . . . 

[http://www.omgubuntu.co.uk/2016/04/10-things-to-do-after-installing-ubuntu-16-04-lts](http://www.omgubuntu.co.uk/2016/04/10-things-to-do-after-installing-ubuntu-16-04-lts)

Let us know how it goes so others don't go down this same rabbit hole.

---

