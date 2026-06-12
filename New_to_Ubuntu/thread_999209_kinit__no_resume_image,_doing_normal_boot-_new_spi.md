---
title: "kinit:  no resume image, doing normal boot- new spin on it"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by medievalman86 on 2008-12-01
first of all, Ive searched these forums, read and applied what i thought i could. So i dont believe im needlessly reposting something.

my computer specs
Specs for my computer are as follows:

1) XFX PVT96GYDF4 GeForce 9600 GT 512MB 256-bit GDDR3 
2) MSI K9N2 SLI Platinum AM2+/AM2 NVIDIA nForce 750a SLI AMD Motherboard
3) AMD Athlon 64 X2 5000+ Brisbane 2.6GHz Socket AM2 65W Dual-Core Black Edition Processor Model ADO5000DSWOF
4 )Patriot Extreme Performance 2GB (2 x 1GB) 240-Pin DDR2 SDRAM DDR2 800 (PC2 6400) Dual Channel Kit Desktop Memory Model PDC22G6400LLK
---- leading up to problem:
this is a single boot computer. Downloaded Ubuntu 8.10, burned it to cd, installed it. It started on first boot fine. I updated it with every update it said was available. I then enabled the recommeded hardware driver for my video card. and restarted. during reboot, goes to the screen with the bar, then comes up with the whole 
```

usplash:setting 1152x864 failed
usplash:using 1024x768
Kinit: no resume image, doing normal boot.

Ubuntu is free ware, no warranty, etc. etc. for ubuntu info, go to www._______.com

Login:
password:
 name@name~desktop:


```

--------->what ive tried thus far.
1) if i remove video card and  use integrated graphics- it works meaning normal gui login screen etc.
2) ive booted linux in recovery mode, checked the dpkgs, files, etc.. everything i can do in the recovery mode, ive done- it all checks out.
3) ive done the memtest86. this too checks out.
4) regardless of wether or not i type in my login/pass it stays at that screen... (waited 15 min both times)
5) default runlevel is 2.
6) no partitions.

so, any thoughts?

---

### Post by medievalman86 on 2008-12-01
ps. one more thing ive tried is ```
startx
```

the results of doing so are:

```
primary device is not pcI
(EE) no devices connected

Fatal server error
no screens found

giving up
xinit: connection refused errno 111
xinit: no such process server error
```

---

### Post by medievalman86 on 2008-12-01
the xserver repair in recovery mode does nothing either.

---

### Post by medievalman86 on 2008-12-01
im out of ideas from other posts, so any ideas? :confused:

---

### Post by medievalman86 on 2008-12-01
I now did a complete reinstall.

still no luck though.

---

### Post by medievalman86 on 2008-12-02
bump

---

### Post by medievalman86 on 2008-12-02
ive tried killing GDM and downloading/installing that way- to no availk.

---

### Post by medievalman86 on 2008-12-02
should I - move this to a differnt forum like under hardware or  something??? am i missing something?

or should i try a older version of ubuntu?

---

### Post by dlcCol on 2008-12-12
> **medievalman86 said:**
> first of all, Ive searched these forums, read and applied what i thought i could. So i dont believe im needlessly reposting something.

my computer specs
Specs for my computer are as follows:

1) XFX PVT96GYDF4 GeForce 9600 GT 512MB 256-bit GDDR3 
2) MSI K9N2 SLI Platinum AM2+/AM2 NVIDIA nForce 750a SLI AMD Motherboard
3) AMD Athlon 64 X2 5000+ Brisbane 2.6GHz Socket AM2 65W Dual-Core Black Edition Processor Model ADO5000DSWOF
4 )Patriot Extreme Performance 2GB (2 x 1GB) 240-Pin DDR2 SDRAM DDR2 800 (PC2 6400) Dual Channel Kit Desktop Memory Model PDC22G6400LLK
---- leading up to problem:
this is a single boot computer. Downloaded Ubuntu 8.10, burned it to cd, installed it. It started on first boot fine. I updated it with every update it said was available. I then enabled the recommeded hardware driver for my video card. and restarted. during reboot, goes to the screen with the bar, then comes up with the whole 
```

usplash:setting 1152x864 failed
usplash:using 1024x768
Kinit: no resume image, doing normal boot.

Ubuntu is free ware, no warranty, etc. etc. for ubuntu info, go to www._______.com

Login:
password:
 name@name~desktop:


```

--------->what ive tried thus far.
1) if i remove video card and  use integrated graphics- it works meaning normal gui login screen etc.
2) ive booted linux in recovery mode, checked the dpkgs, files, etc.. everything i can do in the recovery mode, ive done- it all checks out.
3) ive done the memtest86. this too checks out.
4) regardless of wether or not i type in my login/pass it stays at that screen... (waited 15 min both times)
5) default runlevel is 2.
6) no partitions.

so, any thoughts?

--  I had the same problem. And I resolved as follows:
1. Check that you have access to the network for example:

```
[INDENT]ifconfig-a [/INDENT]
```
Then something like:  inet address: 192.168.1.1 you have.

2) Now like a root user, reinstall the GNOME desktop
```
[INDENT]apt-get install gnome[/INDENT]
```

3)```
[INDENT]Reboot[/INDENT]

```
It worked !!
Goog Luck

---

### Post by Deadmode on 2009-03-01
I remember I had to do this exact thing about 8 months ago with another ubuntu client I have.  Luckily that machine was hooked up to the internet via ethernet.  This one is all the way upstairs using wireless.  And of course the machine is HEAVY.  Anyone got any recommendations for me to connect to wireless to get the ubuntu desktop back up without hauling this thing down 3 stories?

---

### Post by Yashiro on 2009-03-01
To the OP. Start again but update/enable everything EXCEPT the video driver.
Once that's all done you should consider making a backup image.

Then do some reading up on issues with using nvidia drivers.

---

### Post by Deadmode on 2009-03-01
Ahhh! Nvidia drivers...blah.  I see I activated some nvidia drivers and now ubuntu desktop has died lol. 8800gt's came back to kick me in the butt.  Thanks I'll give it a try.

---

### Post by gonkyouka on 2009-04-10
> **dlcCol said:**
> --  I had the same problem. And I resolved as follows:
1. Check that you have access to the network for example:

```
[INDENT]ifconfig-a [/INDENT]
```
Then something like:  inet address: 192.168.1.1 you have.

2) Now like a root user, reinstall the GNOME desktop
```
[INDENT]apt-get install gnome[/INDENT]
```

3)```
[INDENT]Reboot[/INDENT]

```
It worked !!
Goog Luck


i did what you said but it says:
inet addr: 127.0.0.1

and because of that i cant install gnome. im connected to a router. i only activated the nvidia driver i think its 180.. i used 177 before but it says theres a new driver... so i activated it and when i reboot thats what happened. im a complete noob in ubuntu..

what should i do?

thanks!

---

