---
title: "no sound.."
date: 2008-11-05
forum: New to Ubuntu
---

### Post by mike22 on 2008-11-05
I'm getting no sound after recently installing intrepid ibex. I had sound yesterday after I updated, but today I have no sound. When I reboot it takes longer than usual. Any help? thanks.

---

### Post by cmittle on 2008-11-05
I've had intermittent sound issues on my laptop.  If the sounds is not working all I have to do is open a terminal and type alsamixer.  This will bring up a volume control that should be fairly intuitive.  Pressing left and right go across, and up and down to make sure that the volume is at least into the green section.  Also if you see that something like CD or Line doesn't have a bar but a little box with MM in it, press the m button on your keyboard and turn the volume up.  For some reason alsamixer doesn't keep all of the settings exactly the same sometimes when it starts..at least not for me.

In order for someone to help you with your boot problems you'll want to "sudo apt-get install bootchart".  This program creates a picture everytime you start your computer of how long it took to boot and what process took the longest etc...  You will be able to find this picture (similar to [this]("http://i16.photobucket.com/albums/b6/promiscuousman/hardy-20081102-6.png")) in /var/log/bootchart/yyyymmdd.png Post this picture here and someone can probably help with that.

---

### Post by mike22 on 2008-11-05
I have the volume in alsamixer to 100, and still no audio. I will post a picture of the boot processes next time I reboot. 
Thanks.

Btw I hear static noises from the built in speakers when I play a youtube video.

---

### Post by mike22 on 2008-11-06
bump.

---

