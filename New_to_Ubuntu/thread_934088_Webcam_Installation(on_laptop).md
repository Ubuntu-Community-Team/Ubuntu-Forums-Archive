---
title: "Webcam Installation(on laptop)"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by avjois89 on 2008-09-30
Can someone please help me install my toshiba sattelite L310 model. I dont kno where to get the drivers or whatever it is that u need to do. They put up some support on their website but it doesnt seem to work. 

                                            Grateful if anyone does reply :D

---

### Post by NESFreak on 2008-09-30
have you tried to make it work without installing drivers? Try installing and running cheese (a small application to make snapshots) Since i don't know what device you are using, could you please post the output of the command ```
lsusb
```

cheers, nesfreak

---

### Post by avjois89 on 2008-10-05
> **NESFreak said:**
> have you tried to make it work without installing drivers? Try installing and running cheese (a small application to make snapshots) Since i don't know what device you are using, could you please post the output of the command ```
lsusb
```

cheers, nesfreak

I did as you said the output of the code was this



Bus 006 Device 001: ID 0000:0000  
Bus 007 Device 001: ID 0000:0000  
Bus 005 Device 003: ID 08ff:1600 AuthenTec, Inc. 
Bus 005 Device 002: ID 15d9:0a37  
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 04f3:0103 Elan Microelectronics Corp. 
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 004: ID 04f2:b070 Chicony Electronics Co., Ltd 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000 

I have a toshiba sattelite L310 series...if that helps....

---

### Post by NESFreak on 2008-10-11
sorry for the late reply. here is a thread that might interest you
[https://answers.launchpad.net/ubuntu/+question/17099](https://answers.launchpad.net/ubuntu/+question/17099)

cheers
---edit---
btw this driver should be included in the .27 kernel release. which was released 2 days ago. It should be in backports any time.

---

### Post by avjois89 on 2008-10-19
Well..thanks a lot...the thread says it all...and really sorry for the super late reply...didnt have a connection to tell u the truth...

---

### Post by purefan on 2008-11-16
So it worked for you? Im trying to get my webcam work on my toshiba L300D too but this is a "production" laptop so cant really afford to mess up...

Thanks for the contributions!!

EDIT:
I went ahead and tried the instructions on [this link]("https://answers.launchpad.net/ubuntu/+question/17099") and came up with an error that says:
> 
scripts/Makefile.build:46: *** CFLAGS was changed in "/usr/src/modules/gspca/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.

So read in internet and:
```
sudo gedit Makefile
```
and changed all the CFLAGS to EXTRA_CFLAGS
then tried again the sudo make and it got a little further this time but still having problems:
> 
purefan@laptop-ub-64:/usr/src/modules/gspca$ sudo make
make -C /lib/modules/`uname -r`/build SUBDIRS=/usr/src/modules/gspca CC=cc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /usr/src/modules/gspca/gspca_core.o
/usr/src/modules/gspca/gspca_core.c:2567: error: unknown field ‘hardware’ specified in initializer
/usr/src/modules/gspca/gspca_core.c: In function ‘cd_to_spca50x’:
/usr/src/modules/gspca/gspca_core.c:2616: warning: initialization from incompatible pointer type
/usr/src/modules/gspca/gspca_core.c: In function ‘spca50x_create_sysfs’:
/usr/src/modules/gspca/gspca_core.c:2655: warning: passing argument 2 of ‘video_device_create_file’ from incompatible pointer type
/usr/src/modules/gspca/gspca_core.c:2657: warning: passing argument 2 of ‘video_device_create_file’ from incompatible pointer type
/usr/src/modules/gspca/gspca_core.c:2659: warning: passing argument 2 of ‘video_device_create_file’ from incompatible pointer type
/usr/src/modules/gspca/gspca_core.c:2665: warning: passing argument 2 of ‘video_device_remove_file’ from incompatible pointer type
/usr/src/modules/gspca/gspca_core.c:2667: warning: passing argument 2 of ‘video_device_remove_file’ from incompatible pointer type
/usr/src/modules/gspca/gspca_core.c:2669: warning: passing argument 2 of ‘video_device_remove_file’ from incompatible pointer type
make[2]: *** [/usr/src/modules/gspca/gspca_core.o] Error 1
make[1]: *** [_module_/usr/src/modules/gspca] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [default] Error 2
purefan@laptop-ub-64:/usr/src/modules/gspca$ 


But to be honest this is already over my head now and dont know how to take it from here... any help please?

---

