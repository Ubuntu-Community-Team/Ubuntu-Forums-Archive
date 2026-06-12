---
title: "Need Help, problems :("
date: 2012-01-22
forum: New to Ubuntu
---

### Post by mattmers on 2012-01-22
I have a couple problems:
1. My graphics card is not working right. I tryed installing the ati drivers but it would not download them. so i tryed finding another way to do it and i lost the Drivers area, I use to be able to search Drivers in the dash home and find it but now it does not show up, its not even in system settings anymore. 

2. skype does not even open when clicked. had to download from skype website because when I tryed installing from ubuntu software center it would say "package dependencies can not be resolved." 

please help, new to ubuntu. I like it but I have problems

thanks in advance

---

### Post by mastablasta on 2012-01-22
> **mattmers said:**
> I have a couple problems:
1. My graphics card is not working right. I tryed installing the ati drivers but it would not download them. so i tryed finding another way to do it and i lost the Drivers area, I use to be able to search Drivers in the dash home and find it but now it does not show up, its not even in system settings anymore. 


what graphics card do you have? if you have trouble downloading them, you should change the sources mirror server.
> 
2. skype does not even open when clicked. had to download from skype website because when I tryed installing from ubuntu software center it would say "package dependencies can not be resolved." 
then use the one from Skype site.

you can open terminal and type in skype then you will see what kind of errors it gives. you can copy and post the errors here.

---

### Post by mattmers on 2012-01-22
My computer has a ATI® Mobility Radeon™ HD 4250
My computer: [http://us.toshiba.com/computers/laptops/satellite/L640/L645D-S4030/](http://us.toshiba.com/computers/laptops/satellite/L640/L645D-S4030/)

So what should I install?

skype: error while loading shared libraries: libQtDBus.so.4: cannot open shared object file: No such file or directory

---

### Post by MG&amp;TL on 2012-01-22
I imagine you can fix the skype error by opening a terminal and typing:

```
sudo apt-get install libqt4-dbus
```

Although it really should have been installed when you installed skype.

---

### Post by Gone fishing on 2012-01-22
With the drivers you have tried the addition drivers utility?

If not start there, it will install all that is needed

---

### Post by mattmers on 2012-01-22
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libqt4-dbus is already the newest version.
libqt4-dbus set to manually installed.
The following packages were automatically installed and are no longer required:
  libsdl-ttf2.0-0 libatk1.0-0:i386 libstdc++6:i386 libxfixes3:i386
  libxcomposite1:i386 liblcms1:i386 libidn11:i386 libnss3:i386 libwrap0:i386
  libsamplerate0:i386 stellarium-data ssh-import-id libqt4-test:i386
  libsdl-mixer1.2 libxxf86vm1:i386 libgl1-mesa-dri:i386 libgl1-mesa-glx:i386
  libjack-jackd2-0:i386 java-common libnspr4-0d:i386 libgnutls26:i386
  libglapi-mesa:i386 libtasn1-3:i386 hedgewars-data libexpat1:i386
  libdatrie1:i386 libavahi-common-data:i386 libjson0:i386 libsdl-image1.2
  libxcb1:i386 libxau6:i386 libpixman-1-0:i386 libgdbm3:i386 libqtcore4:i386
  libxinerama1:i386 libmikmod2 libice6:i386 libspeexdsp1:i386 libxdmcp6:i386
  libgcrypt11:i386 libthai0:i386 libkeyutils1:i386 libqt4-sql:i386
  libasound2:i386 libflac8:i386 libxrender1:i386 libnspr4:i386
  libvorbisenc2:i386 libqt4-xml:i386 libasyncns0:i386 libxss1:i386
  libtiff4:i386 libsdl-net1.2 libjpeg62:i386 libavahi-client3:i386
  libx11-6:i386 libsasl2-2:i386 libsm6:i386 libxdamage1:i386
  libxcb-render0:i386 librtmp0:i386 libxi6:i386 libvorbis0a:i386
  libaudio2:i386 libxcursor1:i386 libxcb-shm0:i386 libxt6:i386 libxext6:i386
  libsasl2-modules:i386 libavahi-common3:i386 libxrandr2:i386 libnss3-1d:i386
  libsndfile1:i386 libsqlite3-0:i386 libmng1:i386 libllvm2.9:i386
  libgpg-error0:i386 libogg0:i386 libsmpeg0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


Nothing

---

### Post by muteXe on 2012-01-22
so now what happens if you type 'skype' at the command line?

---

### Post by mattmers on 2012-01-22
Forget all that, now it "fail to load session "ubuntu"" when I try to login, and the same if I try guest session. So I think I may switch to Mint os or pinguy. What do you think? If I do, how do I install them over ubuntu. I have windows on my computer and partitioned some for ubuntu.

---

