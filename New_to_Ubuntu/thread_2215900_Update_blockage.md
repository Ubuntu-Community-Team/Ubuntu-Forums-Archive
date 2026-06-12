---
title: "Update blockage"
date: 2014-04-09
forum: New to Ubuntu
---

### Post by flyfishingphil on 2014-04-09
Just installed Ubuntu 12.04LTS in a desktop that is an older Dell Precision T5400 and was trying to set up everything. Just went in to check on updates and received this:

flyfishingphil@ffpDell:~$ sudo apt-get install -f
[sudo] password for flyfishingphil: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to 

I do have an external hard drive attached as drive E. So do I need to remove that, restart, and try and do the update again or is there something else I need to do. (Understand I am trying to update the Flash Drive so I can watch videos on a 2nd screen and it all started with trying to get it so I could watch videos at Amazon or Netflix.)

Please take the time to start at ground zero. I understand doing an entry in erminal but that's about as far as it goes so the steps need to be listed.

Thanks for any assist.

ffp

EDIT: Went back into the update window and it suggested a partial. Ran that and it checked again and showed no further updates available so I would guess it corrected the problem. Now for where all of this started:

If I go into Amazon, and try to watch a video this shows up on the screen:

An error occurred and your player could not be updated.This is likely because your Flash Player or Browser needs to be updated.This update is required to play back this video.

There is no solution offered. Suggestions on this?

Thanks again, ffp

---

### Post by lisati on 2014-04-09
The reference to "E:" ha no direct connection to disk drive labels; it is simply short for "Error." As is the case with other Linux distros, Ubuntu generally uses a different way to specify disk drives.

Messages like **E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)** commonly occur when there is already something running that could potentially update the software you have installed on your system.

Did you have something like Software Centre or Synaptic running when you tried updating? (By "synaptic" I'm referring to a program to update software, not a laptop's touchpad.)

---

### Post by 23dornot23d on 2014-04-09
> 
An error occurred and your player could not be updated.This is likely  because your Flash Player or Browser needs to be updated.This update is  required to play back this video.

There is no solution offered. Suggestions on this?


You need to update flashplugin-installer


**sudo apt-get install  flashplugin-installer**

---

### Post by flyfishingphil on 2014-04-09
lisati, I don't think so but after several days of working on getting things working again I'm a little rummy. I'll try the sudo 23dornot23d listed and see if that takes care of it.

23dornot23d, Just to make sure went to the software center and it shows the flash pluin installer as installed. Next thought?

---

