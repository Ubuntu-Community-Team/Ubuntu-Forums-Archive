---
title: "unable to kill dpkg"
date: 2013-05-11
forum: New to Ubuntu
---

### Post by koolninad on 2013-05-11
Hello,

I am using very old compaq presario v3000 laptop and i recently installed Lubuntu because its light. Installation was successful but i noticed that my WiFi isnt working so i googled and found that I am using bcm43 wifi and tried to install its driver but unfortunatly its not getting installed it gets stucked to connecting to [www.lwfinger.com]("http://www.lwfinger.com") i used ps ax | grep dpkg command to see the task and then kill it using sudo kill but whenever i restart my laptop i have to follow same process again and again. when i am installing new software they are not properly installed because it again start connecting to [www.lwfinger.com]("http://www.lwfinger.com"), recently i tried installing bind9 and configure the same for experimental purpose but configuration was not successful and when i tried to remove bind9 it was not completely removed and now I am getting error 2 program are not properly installed or removed. now because of this i am not able to install new software nor able to update the system, and dpkg gets locked and its says that use sudo dpkg --configure -a command and when i hit this command it again gets stucked into [www.lwfinger.com]("http://www.lwfinger.com") connecting m fade up :( :( :(  please help I tried searching a lot but with no gain
even i tried installing broadcom driver offline but some or the other way its not working.


Thanks in advance. Need help:(:(:(:(

---

### Post by Archit88 on 2013-05-11
Hey ,

try to run ```
fsck
``` if reports no errors and it is still can not run dpkg, 
```
sudo mount / -o remount,rw
```

For broad-com get Ubuntu 12.04 cd and install ```
bcmwl-kernel-source_5.100.82.112+bdcom-0ubuntu3_amd64.deb 
``` you can find this package under
```
pool/restricted/b/bcmwl/bcmwl-kernel-source_5.100.82.112+bdcom-0ubuntu3_amd64.deb 
```

---

### Post by koolninad on 2013-05-11
I got the following output when i tried running command fsck

ninad@ninad-Presario-V3000-RZ896PA-ACJ:~$ sudo fsck
[sudo] password for ninad: 
fsck from util-linux 2.20.1
e2fsck 1.42.5 (29-Jul-2012)
/dev/sda1 is mounted.
e2fsck: Cannot continue, aborting.

---

### Post by koolninad on 2013-05-11
And one more thing.... my laptop does not have CD Rom.. i have installed Lubuntu using usb stick.. so can i use the same to install those driver?

---

### Post by Archit88 on 2013-05-12
Yes you can install all you need is older version of [COLOR=#000000][FONT=Ubuntu Mono]bcmwl-kernel-source 

try to run this command 
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]sudo mount / -o remount,rw[/FONT][/COLOR]

---

