---
title: "Can no longer boot into ubuntu"
date: 2015-08-05
forum: New to Ubuntu
---

### Post by newbie13 on 2015-08-05
4-5 days ago I formatted my HP Pavilion g6 2301ax laptop to upgrade to windows 10. After upgrading and installing ubuntu again I was able to boot into ubuntu without any problem just one time out of hundreds of time.

Before formatting laptop, I have installed ubuntu for minimum 10 times (on the same laptop for various reasons) so I know there is nothing wrong that I did while installing it.
The problem seems to be with 'default' boot manager that HP laptops come with (photo attached).

The procedure I used to follow to boot into ubuntu before this was to hit F9 at start up, select ubuntu (not Ubuntu), which opened grub and select ubuntu again which used to boot ubuntu without any problem.
Now after reinstalling ubuntu, there is no 'ubuntu' option in boot manager. There's only 'Ubuntu' option, which boots Windows 10 if secure boot is enabled. If it is turned off  then 'Ubuntu' option takes me to grub. From here if I select ubuntu, screen turns off, so I have to add 'radeon.modeset=0' to start ubuntu. But soon the laptop reaches temperature of 90 degree celcius, as gpu is off, and shuts down.
Same with legacy mode on.

[to sum up,
1. legacy mode off, secure boot on - no way to load grub. Anything that I select from boot manager boots windows 10
2. legacy mode off, secure boot off - need to add radeon.modeset=0. Otherwise, have no option but to stare at black screen (or sometimes turned off screen)
3. legacy mode on, secure boot option disabled - same as 2nd case
]

I have tried installing ubuntu 3-4 times but it doesn't add that 'ubuntu' (not 'Ubuntu') option in boot manager. Earlier, it used add both the options on a new installation.

The only time when ubuntu was booted without any problem was when I used EasyBCD on windows and ran boot repair option. It added that 'ubuntu' option in the boot manager. But now its gone again. I am left with Ubuntu again. There is nothing that I did between appearance and disappearance of ubuntu. When that 'ubuntu' option was available, I selected it so it took me to grub then again I selected ubuntu and it booted up just like the good old days. After using it and updating everything using 'apt-get update and upgrade' I shut it down. Then just 2 hours ago I started my laptop again and that 'ubuntu' option is gone. 
EasyBCD is doing nothing and I couldn't find any way to change entries in that default boot manager of HP.

Please suggest something.

---

### Post by cressrt2 on 2015-08-05
I had problems with a new HP machine last year, I used this link to help [http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html), that someone here suggested, the part you may need to try is the Boot Repair at step 7.
Hope this helps

---

### Post by newbie13 on 2015-08-06
It's showing this error when I try to install boot repair 'E: Unable to locate package boot-repair'. I am on 14.04 and I read that boot repair is not available for it. So I am downloading it from website but it's 600mb file so it's gonna take some time.

In the mean time, can someone suggest a way to add entries to that boot manager I have attached the photo of?? HP forums are as good as dead. And there is nothing on google about that boot manager either.

---

### Post by newbie13 on 2015-08-08
Boot repair disc did the job.
Thanks for suggesting it.

I had actually read the same article before but I thought it removes that boot manager and displays grub instead. I didn't want that so I hadn't given much attention to it.
It has successfully restored 'ubuntu' option in boot manager, no more or no less than what I wanted.

Thanks

---

