---
title: "What Ubuntu version supports AMD HD 5450?"
date: 2017-03-20
forum: New to Ubuntu
---

### Post by kiicki on 2017-03-20
I have been using the open source driver but it's really not performing that well. I have tried Ubuntu 14.05 and even though I can see the "fglrx" I keep getting errors and in terminal it says it's not enabled. I guess this has something to do with the kernel?

I'm really new to Linux and want to make "fglrx" work. Is it still possible?

---

### Post by QIII on 2017-03-20
For about one more month, 12.04 will work.  14.04 will work.  The point releases .1, .2, .3 and .4 are no longer supported.  .5 uses an HWE that fglrx does not support.  fglrx is completely gone from 16.04 forward.  In short, that GPU is currently supported only by the open source Radeon driver.

---

### Post by mörgæs on 2017-03-21
This is essentially the same thread as [https://ubuntuforums.org/showthread.php?t=2355915](https://ubuntuforums.org/showthread.php?t=2355915) , isn't it?

---

### Post by mastablasta on 2017-03-21
it is, so perhaps essentially same answer (maybe someone finds it by title):

So this is option one - 17.04 (beta). 17.04 will be released end of April. it will have latest kernel which means latest drivers. 

 option 2 - 14.04 - but you need to install the 14.04.0 or 14.04.1 version. 14.04.2 up to 14.04.5 have kernel and xserver that won't allow you to install the AMD close soruce drivers. 14.04 is supported until 2019 and the AMD drivers should work just fine on it. downgrading just the kernel won't do it. i have a HD 6xxx series chip with similar issue, though it works fine on 14.04 with AMD drivers. these first 14.04 version will also keep kernel on same version addign security patches only.
 you will find older versions here: [http://old-releases.ubuntu.com/releases/14.04.0/](http://old-releases.ubuntu.com/releases/14.04.0/)

 option 3 - 16.04 - then use a PPA to upgrade the drivers to latest version. i believe oibaf's PPA is the popular one: [https://launchpad.net/~oibaf/+archiv...aphics-drivers]("https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers")

---

