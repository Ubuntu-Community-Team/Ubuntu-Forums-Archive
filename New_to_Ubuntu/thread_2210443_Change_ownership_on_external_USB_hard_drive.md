---
title: "Change ownership on external USB hard drive"
date: 2014-03-09
forum: New to Ubuntu
---

### Post by frankentower on 2014-03-09
The chown command with username:username allows my external USB drive to appear and I am then able to run my back ups from my home folder to my external drive. However when I  restart I have to do the same thing again after turning off my USB drive and restarting my computer the next day, it shows up not at all only /root shows up under media.
 
Is there any way for me to make a setting somewhere to give it permanent permissions  so that every time I start up my computer and turn on my external USB hard drive it will be recognized by lucky back( with sudo privileges) up to  run the back up I have set up? 

I have my USB drive in an enclosure that I just safely unmount it from the computer then  hit an off switch on the back of the enclosure and it shuts down the external drive.

It would be great if Ii could have a permanent solution set  up so I can just turn it on , back  up and turn it off..

Can I do this?

Thanks for any help!

---

### Post by oldos2er on 2014-03-10
Post moved to its own thread.

---

### Post by frankentower on 2014-03-11
For those wondering who may not have had the answer, I  figured out what the problem was. I  changed the chmod after a re install of my OS on the separate SSD drive, so only the first time I tried to access the USB drive did I have to  change the chmod to username:username subsequent reboots were fine and I was able to access the USB drive just by flipping the switch on it and spinning up the device. I just finished a back up now and can confirm it does work on subsequent reboots. perhaps the first reboot it didn't take or upon making a new set of instructions in the "Lucky backup ( superuser)" app may have caused it not see the drive on first try, dunno but its working now...

In case a beginner (me included) may  have had the same problem  I didn't want to confuse them  further and in case an  experienced Linux user could not figure out why the chmod command didn't work on my setup this problem is solved, I'm going to try to mark it solved on top, if this forum allows that type thing.

Thanks to the Moderator for posting this in the correct thread.

---

