---
title: "Ubuntu won't indentify I/O and etc...."
date: 2008-07-10
forum: New to Ubuntu
---

### Post by CERNYSMRT on 2008-07-10
I am new to the linux world and have heard all the great stuff..
so .. Why not try it? 

Got Ubuntu today and am trying to install it on my:

XFX 750a SLI, AMD64 fx-62, 4gb dual ch. ram, 8800gts oc
with xp and a blank partition for ubuntu

I have downloaded the Right Ubuntu file and have burn the ISO correctly. Here's my problem: Go to install via bootable cd/.. 
the first gui screen comes up with the install and etc..
click on install and it craps.. so i go back and delete the "quiet splash --" text from the cmd line. reboot and got a little farther.. 
I never got to the GUI screen with time, date, region, etc... it was only in the "dos" mode shooting cmds across the screen until it stopped and displayed that it:

"failed to identify (I/O error, err_mask=0x4)" and 
failed to recovery some devices 

 does this mean it doesn't like my hardware, compatibility issue, etc??? 

I hate to say it but this has been a bigger pain in the a$$ than windows. At least windows loads right....

---

### Post by tech9 on 2008-07-10
> **CERNYSMRT said:**
> I am new to the linux world and have heard all the great stuff..
so .. Why not try it? 

Got Ubuntu today and am trying to install it on my:

XFX 750a SLI, AMD64 fx-62, 4gb dual ch. ram, 8800gts oc
with xp and a blank partition for ubuntu

I have downloaded the Right Ubuntu file and have burn the ISO correctly. Here's my problem: Go to install via bootable cd/.. 
the first gui screen comes up with the install and etc..
click on install and it craps.. so i go back and delete the "quiet splash --" text from the cmd line. reboot and got a little farther.. 
I never got to the GUI screen with time, date, region, etc... it was only in the "dos" mode shooting cmds across the screen until it stopped and displayed that it:

"failed to identify (I/O error, err_mask=0x4)" and 
failed to recovery some devices 

 does this mean it doesn't like my hardware, compatibility issue, etc??? 

I hate to say it but this has been a bigger pain in the a$$ than windows. At least windows loads right....

could be a bad disk... what kind of media did you burn the ISO to?

---

### Post by avtolle on 2008-07-10
Do you recall which device? BTW, do you have SATA drives, by any chance? Anyway, look at [https://help.ubuntu.com/community/BootOptions#When%20installing]("https://help.ubuntu.com/community/BootOptions#When%20installing") for some thoughts on boot options.

EDIT: Scroll down the page if Ubuntu has been installed, BTW.

---

### Post by CERNYSMRT on 2008-07-10
> **avtolle said:**
> Do you recall which device? BTW, do you have SATA drives, by any chance? Anyway, look at [https://help.ubuntu.com/community/BootOptions#When%20installing]("https://help.ubuntu.com/community/BootOptions#When%20installing") for some thoughts on boot options.

EDIT: Scroll down the page if Ubuntu has been installed, BTW.

hey thanks guys.. will review this info...

forgot to tell you that i have 2 sata drives....

---

### Post by CERNYSMRT on 2008-07-10
ok.. after some quick googling... it seems to be a SATA issue... 
and with that.. there is an update for the linux kernel that has fixed previous instances on other linux platforms..

but how do i update, if any, a bootable cd?

---

### Post by CERNYSMRT on 2008-07-10
OK, been about 4 hours now of searching online of why this "great system" won't boot....](*,) all my settings in my bios are right.. and it's up to date... 

there seems to be a sata/ahci issue within the linux kernel 

getting really disinterested now.. and sorry to say, but xp is more appealling now... 

I guess they picked the right name for it.. cause like the host of the name.. this os doesn't want to work either... :-D

---

### Post by nowshining on 2008-07-10
hmmm, have u tried other distros?

---

### Post by CERNYSMRT on 2008-07-10
> **nowshining said:**
> hmmm, have u tried other distros?

and what might that be??? sorry for the stupid question but i am new to linux terminology...

---

### Post by munkyboy on 2008-07-10
try Kubuntu I use 2 sata drives and no problem

[http://kubuntu.org/getkubuntu](http://kubuntu.org/getkubuntu)

---

### Post by CERNYSMRT on 2008-07-10
forget ubuntu... gonna try kubuntu:(

---

