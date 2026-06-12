---
title: "Help with Installing Ubuntu 11.04"
date: 2011-09-25
forum: New to Ubuntu
---

### Post by 12gToby on 2011-09-25
Hi there
 
I'm trying to install Ubuntu 11.04 on an old Dell Inspiron 2500. I am installing from a CD having downloaded from the Ubuntu website. It installs fine but then requires a restart at the end of the installation process. It never restarts successfully. If I switch it off then back on again it comes up with a menu of four options (Run Ubuntu, Run in Recovery Mode and two Memory Test options). If I select Run Ubuntu or the Recovery Mode Option nothing happens.
 
Has anyone got any ideas about how I could fix this problem. Any help would be very much appreciated. (Looks really good on the sample version running from disk)

---

### Post by Chiel92 on 2011-09-25
> **12gToby said:**
> If I switch it off then back on again it comes up with a menu of four options (Run Ubuntu, Run in Recovery Mode and two Memory Test options). If I select Run Ubuntu or the Recovery Mode Option nothing happens.


What exactly does the menu look like, and what exactly happens when you select 'Run ubuntu'?

---

### Post by coffeecat on 2011-09-25
Two potential problems I can envisage, and I'm surprised you managed to finish an installation.

According to a google search, your machine came with 64MB of RAM upgradeable to 512MB. 512 is (just) enough for it to run Ubuntu. Less than 512 it will stagger or not run at all with less than 256. How much RAM do you have? Also, the same source says you have Intel 815EM integrated graphics. Getting that ancient video chipset working in 11.04 will be a challenge at best. Sorry.

Which brings us to how you got it installed in the first place. Did you use the live desktop DD or the alternate CD ISO?

---

### Post by kens60 on 2011-09-25
I had the same problem with my DELL 3000  2005 and was talked into going for 10.04.3 and it seems to be working ok. Think are computers are to old and 11.04 is for more modern computers, too strong for our old model;s... un-install the 11.04 and install 10.04 then do not upgrade.

---

### Post by elysianfields44 on 2011-09-25
Ubuntu 10.04 requires a minimum of **256 MB** of memory: 

[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#System_Requirements](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#System_Requirements)

Whereas 11.04 requires a minimum of **384 MB**:

[https://wiki.ubuntu.com/NattyNarwhal/ReleaseNotes#System_Requirements](https://wiki.ubuntu.com/NattyNarwhal/ReleaseNotes#System_Requirements)

So indeed you might be better off with 10.04.

---

### Post by kens60 on 2011-09-25
My sons 2500 had 2-256 in 2 of the 4 slots the 2500 has. I have a 3000 and it had 2-512 in the 2 slots the 3000 has. I exchanged my 2 - 512 for 2 - 1024 and put my 2-512 into the extra slots in his 2500 giving him 1536 and I have 2048, both work great now....

So if he has 4 slots he can add lot of memory and it is pretty cheap now.

---

### Post by Captain Smiley Pants on 2011-09-25
If it need be you can always try [Xubuntu](http://www.xubuntu.org/) and use the [Alternate Installation Method](https://help.ubuntu.com/community/Installation#Alternate_Installation).

---

### Post by 12gToby on 2011-09-26
Thanks for so many replies.
 
I used the live desktop CD. 
 
The demonstration runs very well so the graphics card looks up to the job. I have upgraded to 1Mb RAM and the speed's ok. The Hard disk has 40 Gb capacity.
 
One odd thing is that when I do the install I have to select F6 / apic=off otherwise it won't go any further.
 
Following the installation and reboot I see the GNU GRUB version 199~rcl-13ubuntu3 menu with the run ubuntu options inviting me to use the up/down arrows to navigate through the options and also use 'e' and 'c' to edit commands or get a command prompt. 
 
I select 'Ubuntu, with Linux 2.6.38.8-generic' and nothing happens.
 
Once again, any help would be greatly appreciated

---

