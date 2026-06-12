---
title: "Sound stopped working today, shutdown also not working"
date: 2012-08-12
forum: New to Ubuntu
---

### Post by Webgazer on 2012-08-12
I'm a Ubuntu newbie and I'm having problems with my machine.

The main problem is that no sound plays. It was not working a while ago as I described here:

[http://ubuntuforums.org/showthread.php?t=2032980](http://ubuntuforums.org/showthread.php?t=2032980)

And it started working on its own last week, until today when upon reboot, it didn't work. It could be due to a software update.

When the computer boots up, there is sound at the BIOS screen, so I know the hardware works. It's only when Ubuntu starts up when there is no sound.

When the sound problem first emerged, I turned off the computer (actually I couldn't shut it down, and had to manually power it off, but I'll get to that later), and restarted it, and while it was booting up, a quick message appeared stating:

"HDA-Intel Codecs not found!"

I did some research and found this:

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/719437](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/719437)

and following the instructions given and added the line:

options snd-hda-intel probe_mask=0x101

to the /etc/modprobe.d/alsa-base.conf file.

I turned off the computer, and restarted, and this time I got

"HDA-Intel no codecs initialized"

As per the instructions in the page linked, I edited the line I had added to 

options snd-hda-intel probe_mask=0x102

I turned off, turned back on, and this time no message about the HDA-Intel codec appeared.

The sound though still doesn't work. Also, youtube videos are suddenly running at 2 or 3 times the normal speed.

The other problem that has emerged today is that I can't shutdown the computer. Neither clicking the shutdown button in the GUI, nor using the "sudo shutdown -h now" command works.

When I click shutdown by clicking the top right and selecting the option with my mouse, it simply logs me out. 

When I use the command in terminal, it logs out, goes to a purple screen, has a message about Apache2, and hangs there, and I have to manually power it off.

I have two websites installed on my machine with a custom setup so I can't simply reinstall Ubuntu and need the problem with my audio (and hopefully shutdown) identified and fixed without wiping/altering any thing else on my computer.

---

### Post by jroa on 2012-08-12
For the sound problem, can you boot the live disk and see if the sound works?  If so, the least painful method might be to just do a fresh install after you back up your important stuff.

As for the shutdown problem, I had something similar happen to me: after an update, I think.  Anyway, when I clicked on shutdown or reboot, it would just log me out.  Next kernal update, the problem went away.  Go figure.  The way I got around it was to use the terminal to either shutdown or reboot.  I know it is not a fix, but it will do what you need it to.

To shutdown
```
sudo shutdown -h now
```

To reboot
```
sudo reboot
```

---

### Post by Webgazer on 2012-08-12
> **jroa said:**
> For the sound problem, can you boot the live disk and see if the sound works?  If so, the least painful method might be to just do a fresh install after you back up your important stuff.


I don't have a live disk available, so I'll buy a USB or recordable disc, create a bootable stick/disc, then do that.

> As for the shutdown problem, I had something similar happen to me: after an update, I think.  Anyway, when I clicked on shutdown or reboot, it would just log me out.  Next kernal update, the problem went away.  Go figure.  The way I got around it was to use the terminal to either shutdown or reboot.  I know it is not a fix, but it will do what you need it to.

To shutdown
```
sudo shutdown -h now
```

To reboot
```
sudo reboot
```

That doesn't work unfortunately:

Neither clicking the shutdown button in the GUI, nor using the "sudo shutdown -h now" command works.

When I click shutdown by clicking the top right and selecting the option with my mouse, it simply logs me out. 

When I use the command in terminal, it logs out, goes to a purple screen, has a message about Apache2, and hangs there, and I have to manually power it off.

---

### Post by mastablasta on 2012-08-13
whoa so many different issues in one thread. it would be better to separate them.
 
 
for sound fix it back to the way it was then reboot and run
 
sudo alsa reload -c 
 
see if that brings the sound back. i was htinking that maybe my motherboard has same issue. it probably wants to output the sound to hdmi instead of speakers... hmm.
 
for youtube i don't know what is going on but maybe you accidentally clicked a you tube setting that changed the speed?!
 
for shut down - it would be best to give the exact output of the error here. you can also try googling it. 
 
it seems something is wrong with apache. you could try purging reisntalling only apache server.
 
backing up website is easy. just backup the www folder. if you have mysql on it you can backup the database using phpmyadmin.

---

### Post by Shadius on 2012-08-13
I don't know if
```
sudo alsa reload -c
```
is the same as 
```
sudo alsa force-reload
```
but I've used the *sudo alsa force-reload* command before to bring my sound back when it wasn't working. Might worth a try if it's not the same as the previously suggested command.

---

