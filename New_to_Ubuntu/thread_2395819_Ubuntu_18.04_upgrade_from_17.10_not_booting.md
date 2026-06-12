---
title: "Ubuntu 18.04 upgrade from 17.10 not booting"
date: 2018-07-07
forum: New to Ubuntu
---

### Post by evergreengardenservices on 2018-07-07
Hi Friends ,

A new user of Ubuntu after being introduced by a friend, I am not technical person. Just know how to use a computer.
After update from Software Updater prompt, post install , the system hangs at the 4th dot.
After some searching , was able to login using recovery mode.
Upon which , it prompted to send a error report, which has been  done.
Hope the issue is resolved soon , so that I can rectify this using Software Updater, until then I am thinking of using the system in recovery mode.
If it needs to be physically rectified please let me know.

Thanks

---

### Post by evergreengardenservices on 2018-07-07
please find the system details attached[IMG]https://photos.app.goo.gl/J1vvCeqDMaRoZTyb9 [/IMG] below [IMG]https://photos.app.goo.gl/zGKLtUaycYt3Ndo58 [/IMG]

---

### Post by evergreengardenservices on 2018-07-07
[https://photos.app.goo.gl/J1vvCeqDMaRoZTyb9](https://photos.app.goo.gl/J1vvCeqDMaRoZTyb9)  


[https://photos.app.goo.gl/rM4GeZHg5ZWZZ5U6A](https://photos.app.goo.gl/rM4GeZHg5ZWZZ5U6A)

---

### Post by Autodave on 2018-07-07
Is there any reason why you cannot do a clean install of Ubuntu? Can you back up your needed files to an external source and then re-install Ubuntu?

I rarely have any luck with upgrading. I prefer to clean install the current long term service (LTS) release and use that until the next LTS comes out (every 2 years).  You could even skip one LTS release since the LTSs are maintained for 5 years. Right now, i have machines running 14.04, 16.04, and 18.04. The 14.04 machine will be updated to 18.04 soon, but the 16.04 machines will run with that for at least 2 more years.

---

### Post by Impavidus on 2018-07-07
I've never had anything but luck when doing release upgrades, but I agree that fixing a broken upgrade is hard. A fresh install is usually easier.

When you boot using recovery mode, then proceed to the normal graphical login, the difference with the normal booting process is that you end up using the open source drivers. So this suggests there's a problem with your drivers. Have a look at the additional drivers-tool. Maybe there's something useful in there. I've no experience there, I've never used anything but open source drivers.

---

### Post by evergreengardenservices on 2018-07-08
Hi Friends,

Thanks for the support , i have not installed additional drivers apart from the one that came with the installation.

If it needs,  will do fresh installation.

[https://photos.app.goo.gl/yeyvHPuBsV1SQboo8](https://photos.app.goo.gl/yeyvHPuBsV1SQboo8) 

[https://photos.app.goo.gl/Erv9KL6pwhrfA81Q7](https://photos.app.goo.gl/Erv9KL6pwhrfA81Q7)

[https://photos.app.goo.gl/F1gNc9WWsTT9d4CN7](https://photos.app.goo.gl/F1gNc9WWsTT9d4CN7)

---

### Post by mIk3_08 on 2018-07-08
This maybe a lot of work but it might be good to solve your system problem. (Do a reformat since this is the easiet way and install 16.04 LTS ) Then if you like to do a disk upgrade then upgrade from 16.04 to 17 up to the latest with is 18.04 LTS (Long Term Support) where we do have the support. I think using a brand new SSD is best. Because I encounter a lot of problem using my old hdd like fsck and etc. to recover the installation. I'm also new to Open Source but now I don't encounter any problem of my machine right now, so far so good. Using my new ssd. Thanks to the Ubuntu. Its a Big and a lot of help to me.

---

### Post by wildmanne39 on 2018-07-08
> **mike082112 said:**
> This maybe a lot of work but it might be good to solve your system problem. (Do a reformat since this is the easiet way and install 16.04 LTS ) Then if you like to do a disk upgrade then upgrade from 16.04 to 17 up to the latest with is 18.04 LTS (Long Term Support) where we do have the support. I think using a brand new SSD is best. Because I encounter a lot of problem using my old hdd like fsck and etc. to recover the installation. I'm also new to Open Source but now I don't encounter any problem of my machine right now, so far so good. Using my new ssd. Thanks to the Ubuntu. Its a Big and a lot of help to me.
This is an unnecessary  method to get 18.04, if the OP is going to do a reformat and clean install then it would be best to just install 18.04 and not mess with installing 16.04 then upgrading to 17.10 to 18.04, I have had success doing upgrades but I have also had failures and I always do a clean install these days.

Also since 16.04 is an LTS version and so is 18.04 he can upgrade from 16.04 to 18.04 without installing 17.10 which reaches EOL in a few days and will not be up-gradable soon there after.

Edit: It is late here but after further thought the OP can not upgrade from 16.04 to 17.10 to 18.04 because he would have to upgrade from 16.04 to 17.04 before he can upgrade to 17.10 and 17.04 has reached EOL already and it is not possible to upgrade to it now.

---

### Post by mIk3_08 on 2018-07-08
> **wildmanne39 said:**
> This is an unnecessary  method to get 18.04, if the OP is going to do a reformat and clean install then it would be best to just install 18.04 and not mess with installing 16.04 then upgrading to 17.10 to 18.04, I have had success doing upgrades but I have also had failures and I always do a clean install these days.

Also since 16.04 is an LTS version and so is 18.04 he can upgrade from 16.04 to 18.04 without installing 17.10 which reaches EOL in a few days and will not be up-gradable soon there after.


Thanks wildmanne39 for the good advice. 
And so, if you are planning to buy a new ssd be sure to match with your hardware specification. Be sure that it is compatible with your hardware. specially the speed.

---

