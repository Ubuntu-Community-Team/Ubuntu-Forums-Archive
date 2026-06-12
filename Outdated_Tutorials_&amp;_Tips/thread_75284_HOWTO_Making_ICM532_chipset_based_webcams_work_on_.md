---
title: "HOWTO: Making ICM532 chipset based webcams work on breezy"
date: 2005-10-13
forum: Outdated Tutorials &amp; Tips
---

### Post by arnieboy on 2005-10-13
Some of you probably might have noticed ICM532 chipset based webcams freezing on breezy (for a comprehensive list refer to: [http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html) ) when u turn on gnomemeeting or camorama. Herez the fix for that:
**FOLLOW ALL THE STEPS! DONT TAKE SHORTCUTS OR MAKE MODIFICATIONS IF YOU DON'T KNOW WHAT YOU ARE DOING**
You need to do the following step by step 

**FOR DAPPER and EDGY**
If you are on Dapper or Edgy do the following instead of the above:
```
sudo apt-get install linux-headers-`uname -r` linux-restricted-modules-`uname -r` build-essential
wget http://mxhaard.free.fr/spca50x/Download/spca5xx-20060501.tar.gz
tar xvfz spca5xx-20060501.tar.gz
cd spca5xx-20060501
make
sudo modprobe -r spca5xx
sudo rm -rf /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx*
sudo make install
sudo modprobe spca5xx
```

**FOR BREEZY**
```
sudo apt-get install linux-headers-`uname -r` linux-restricted-modules-`uname -r` build-essential gcc-3.4
wget http://mxhaard.free.fr/spca50x/Download/spca5xx-20060501.tar.gz
tar xvfz spca5xx-20060501.tar.gz
cd spca5xx-20060501
sudo make CC=gcc-3.4
sudo modprobe -r spca5xx
sudo rm -rf /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx*
sudo make install
sudo modprobe spca5xx
```
Now you should be all set to use ur ICM532 chipset based webcam.

---

### Post by steil on 2005-10-13
Nice How-To. Good Work arnieboy!

---

### Post by arnieboy on 2005-10-13
thanks :)

---

### Post by steil on 2005-10-13
-

---

### Post by arnieboy on 2005-10-13
--------

---

### Post by Koba on 2005-10-13
ummm, i did EXACTLY what you said, every last letter, no errors at all, it was perfect, but gnome meeting freezes when i click "test" for my Creative Live! and yes Creative Live! is supported on spca5xx. any other programs i could use to test out my webcam? i can't get camorama going, i need to d/l more dependancies... maybe amsn...

---

### Post by arnieboy on 2005-10-13
[QUOTE=Koba]ummm, i did EXACTLY what you said, every last letter, no errors at all, it was perfect, but gnome meeting freezes when i click "test" for my Creative Live! and yes Creative Live! is supported on spca5xx. any other programs i could use to test out my webcam? i can't get camorama going, i need to d/l more dependancies... maybe amsn...[/QUOTE]
is it just gnomemeeting which is freezing or the whole system? there is a command line app called gqcam
```
sudo apt-get install gqcam
```

---

### Post by pitigrilli on 2005-10-15
Thank you very much for your advice. The pc-ocular (USB SPCA5XX camera found. SONIX sn9c102 Hv7131R) for my microscope works now perfectly!

Take this leg of a fly as present.
[IMG]http://www.bempf.de/images/Webcam-1129414280.png[/IMG]

---

### Post by arnieboy on 2005-10-15
[QUOTE=pitigrilli]Thank you very much for your advice. The pc-ocular (USB SPCA5XX camera found. SONIX sn9c102 Hv7131R) for my microscope works now perfectly!

Take this leg of a fly as present.
[IMG]http://www.bempf.de/images/Webcam-1129414280.png[/IMG][/QUOTE]
flies like these keep me going.. is that kid on choloroform or did u kill it?

---

### Post by tseliot on 2005-10-19
Arnav, you're GREAT. It worked like a charm.
Thanks

---

### Post by EnglishRob on 2005-11-04
You're a star!

I've been trying to get my two webcam's working on Linux for ages.  Both my cameras (Viewquest M318B and Chicony Twinklecam DC-2110) work now.  Must admit, the brightness is a little high on the Viewquest camera but I can live with that for now.

Rob

---

### Post by snigri on 2005-11-07
Thank you very much Arnieboy!!!!

My PC-CAM-300 (Creative) is working very well on Gnomemeeting and Mercury.

Your instructions worrked perfectly.

snigri:D

---

### Post by 4plus2 on 2005-11-18
Nice instructions, got no errorrs and it worked for me too! Thanks. 
I have the USB Z-Star VIMICRO ZC0301P webcam.

Just one question though. Is 20050906 the latest version or will this date need to be changed as time goes on?

---

### Post by arnieboy on 2005-11-18
[QUOTE=4plus2]Nice instructions, got no errorrs and it worked for me too! Thanks. 
I have the USB Z-Star VIMICRO ZC0301P webcam.

Just one question though. Is 20050906 the latest version or will this date need to be changed as time goes on?[/QUOTE]
1) u generally wudnt need a later version if it already works for u cuz most future versions work on including chipsets thats dont work
2) if u are still interested in updates herez where to look:
[http://mxhaard.free.fr/spca50x/Download/](http://mxhaard.free.fr/spca50x/Download/)

---

### Post by yhotg on 2005-11-22
hi arnieboy
i followed your instructions long ago and was working without any kind of problem...
that's it, until today that i thought - folly me :mad: - "the cam's resolution is not good, maybe i'll update the driver..."

so, i tried and now don't have cam. :( 

error message:

root@shlita:/home/yhotg/paquetes/webcam/spca5xx-20051105# sudo modprobe spca5xx
FATAL: Error inserting spca5xx (/lib/modules/2.6.12-9-386/kernel/drivers/usb/media/spca5xx.ko): Invalid module format

then i tried to re install the first one following all and every step of your howto again, but still same error, well almost :
root@shlita:/home/yhotg/paquetes/webcam/spca5xx-20050906# sudo modprobe spca5xx
FATAL: Error inserting spca5xx (/lib/modules/2.6.12-9-386/kernel/drivers/usb/media/spca5xx.ko): Invalid module format

Helppppp pls. uff

i already miss my cam, oh precious cam my preeecioussss

:p 
thanks

update after 3 hours 

well, i had a fortuitous accident with the electricity and after rebooting I tried again the step by step howto and it did work again. amazing.
i don't know what was exactly the problem before, but i have my precious cam back.
so ...

---

### Post by waffen on 2005-11-22
Hello,

I have the same problem with a Genius VideoCAM Messenger and I try this instruction:

[QUOTE=arnieboy]Some of you probably might have noticed ICM532 chipset based webcams freezing on breezy (for a comprehensive list refer to: [http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html) ) when u turn on gnomemeeting or camorama. Herez the fix for that:
**FOLLOW ALL THE STEPS! DONT TAKE SHORTCUTS IF U DONT KNOW WHAT U ARE DOING**
U need to do the following first of all:
```
sudo apt-get install linux-headers-`uname -r` linux-restricted-modules-`uname -r` build-essential gcc-3.4
```
now do the following:
```
sudo passwd root
```
and set the root password if u already dont have one
now do the following
```
su
CC=gcc-3.4
export CC
exit
CC=gcc-3.4
export CC
wget http://mxhaard.free.fr/spca50x/Download/spca5xx-20050906.tar.gz
tar xvfz spca5xx-20050906.tar.gz
cd spca5xx-20050906
make
sudo modprobe -r spca5xx
```

And not found....

Above not make because I dont receipt any error message:
Never mind if the last command above throws up an error.
```
sudo rm -rf /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx*
sudo make install
sudo modprobe spca5xx
```
Now u should be all set to use ur ICM532 chipset based webcam.[/QUOTE]

I found this page: [http://genius-europe.com/service/faq/tuxcam.htm](http://genius-europe.com/service/faq/tuxcam.htm)

but I dont know how install thats drivers :( 

Any idea???

Thanks!!

---

### Post by arnieboy on 2005-11-22
I am not sure what problem u are facing because u havent mentioned that. Have u tried following the instructions step by step? The link that u sent didnt make any sense apart from giving the list of genius webcams.

---

### Post by waffen on 2005-11-22
Hello Arnieboy!!

:-) my problem is in Gnomemeeting, I open a new thread for this: [http://www.ubuntuforums.org/showthread.php?t=93855](http://www.ubuntuforums.org/showthread.php?t=93855) 

if you want read the details....please!

I make step by step your how to, the only lines then I not execute:

sudo rm -rf /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx*
sudo make install
sudo modprobe spca5xx

because I dont receipt any error message...or I translate into spanish bad your sentence??: 
"Never mind if the last command above throws up an error."

Thanks!!

[QUOTE=arnieboy]I am not sure what problem u are facing because u havent mentioned that. Have u tried following the instructions step by step? The link that u sent didnt make any sense apart from giving the list of genius webcams.[/QUOTE]

---

### Post by arnieboy on 2005-11-22
[QUOTE=waffen]Hello Arnieboy!!

:-) my problem is in Gnomemeeting, I open a new thread for this: [http://www.ubuntuforums.org/showthread.php?t=93855](http://www.ubuntuforums.org/showthread.php?t=93855) 

if you want read the details....please!

I make step by step your how to, the only lines then I not execute:

sudo rm -rf /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx*
sudo make install
sudo modprobe spca5xx

because I dont receipt any error message...or I translate into spanish bad your sentence??: 
"Never mind if the last command above throws up an error."

Thanks!![/QUOTE]
lol.. this is a perfect case of "lost in translation"... 
The following line [HTML]
Never mind if the last command above throws up an error.[/HTML]
does NOT mean that you have to stop after that. it means, CARRY ON!
anyway, redo all the steps. but before that make sure u have deleted the spca5xx-20050906 directory from your home folder.

---

### Post by waffen on 2005-11-22
Jajajaja!! ok....

but now I receipt this error:

mario@laptop:~/spca5xx-20050906$ make
   Building SPCA5XX driver for 2.5/2.6 kernel.
   Remember: you must have read/write access to your kernel source tree.
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/mario/spca5xx-20050906 CC=gcc-3.4 modules
make: *** /lib/modules/2.6.12-9-386/build: No existe el fichero o el directorio.  Alto.
make: *** [default] Error 2

Im newbie in Linux and I apreciate your help...this error I dont remenber the appears the last time I execute....


[QUOTE=arnieboy]lol.. this is a perfect case of "lost in translation"... 
The following line [HTML]
Never mind if the last command above throws up an error.[/HTML]
does NOT mean that you have to stop after that. it means, CARRY ON!
anyway, redo all the steps. but before that make sure u have deleted the spca5xx-20050906 directory from your home folder.[/QUOTE]

---

### Post by waffen on 2005-11-22
Sorry!! the translate of error mesage is:

make: *** /lib/modules/2.6.12-9-386/build:Not found the file or dir.
Stop.

mario@laptop:~/spca5xx-20050906$ make
   Building SPCA5XX driver for 2.5/2.6 kernel.
   Remember: you must have read/write access to your kernel source tree.
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/mario/spca5xx-20050906 CC=gcc-3.4 modules
make: *** /lib/modules/2.6.12-9-386/build: No existe el fichero o el directorio.  Alto.
make: *** [default] Error 2

---

### Post by arnieboy on 2005-11-22
[QUOTE=waffen]Sorry!! the translate of error mesage is:

make: *** /lib/modules/2.6.12-9-386/build:Not found the file or dir.
Stop.

mario@laptop:~/spca5xx-20050906$ make
   Building SPCA5XX driver for 2.5/2.6 kernel.
   Remember: you must have read/write access to your kernel source tree.
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/mario/spca5xx-20050906 CC=gcc-3.4 modules
make: *** /lib/modules/2.6.12-9-386/build: No existe el fichero o el directorio.  Alto.
make: *** [default] Error 2[/QUOTE]
did u delete the spca5xx-20050906 directory and **REDO** all the steps?

---

### Post by waffen on 2005-11-22
Yes!! attach a copy of my console:

mario@laptop:~$ sudo apt-get install linux-headers-`uname -r` linux-restricted-modules-`uname -r` build-essential gcc-3.4
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias... Hecho
linux-headers-2.6.12-9-386 ya está en su versión más reciente.
linux-restricted-modules-2.6.12-9-386 ya está en su versión más reciente.
build-essential ya está en su versión más reciente.
gcc-3.4 ya está en su versión más reciente.
0 actualizados, 0 se instalarán, 0 para eliminar y 0 no actualizados.
mario@laptop:~$ clear

mario@laptop:~$ sudo passwd root
Enter new UNIX password:
Retype new UNIX password:
passwd: password updated successfully
mario@laptop:~$ su
Password:
root@laptop:/home/mario# CC=gcc-3.4
root@laptop:/home/mario# export CC
root@laptop:/home/mario# exit
exit
mario@laptop:~$ CC=gcc-3.4
mario@laptop:~$ export CC
mario@laptop:~$ wget [http://mxhaard.free.fr/spca50x/Download/spca5xx-20050906.tar.gz](http://mxhaard.free.fr/spca50x/Download/spca5xx-20050906.tar.gz)
--23:00:23--  [http://mxhaard.free.fr/spca50x/Download/spca5xx-20050906.tar.gz](http://mxhaard.free.fr/spca50x/Download/spca5xx-20050906.tar.gz)
           => `spca5xx-20050906.tar.gz'
Resolviendo mxhaard.free.fr... 212.27.63.116
Connecting to mxhaard.free.fr|212.27.63.116|:80... conectado.
Petición HTTP enviada, esperando respuesta... 200 OK
Longitud: 179,010 (175K) [application/x-gzip]

100%[====================================>] 179,010       42.94K/s    ETA 00:00

23:00:28 (40.39 KB/s) - `spca5xx-20050906.tar.gz' saved [179010/179010]

mario@laptop:~$ tar xvfz spca5xx-20050906.tar.gz
spca5xx-20050906/
spca5xx-20050906/Makefile
spca5xx-20050906/RGB-YUV%2fmodule-setting
spca5xx-20050906/README
spca5xx-20050906/drivers/
spca5xx-20050906/drivers/usb/
spca5xx-20050906/drivers/usb/spcai2c_init.h
spca5xx-20050906/drivers/usb/spcagamma.h
spca5xx-20050906/drivers/usb/cx11646.h
spca5xx-20050906/drivers/usb/sn9cxxx.h
spca5xx-20050906/drivers/usb/cxlib.h
spca5xx-20050906/drivers/usb/zc3xx.h
spca5xx-20050906/drivers/usb/cs2102.h
spca5xx-20050906/drivers/usb/jpeg_qtables.h
spca5xx-20050906/drivers/usb/pas106b.h
spca5xx-20050906/drivers/usb/spca504_init.h
spca5xx-20050906/drivers/usb/spca506.h
spca5xx-20050906/drivers/usb/spca533.h
spca5xx-20050906/drivers/usb/spca536.h
spca5xx-20050906/drivers/usb/spca561.h
spca5xx-20050906/drivers/usb/mr97311.h
spca5xx-20050906/drivers/usb/sonix.h
spca5xx-20050906/drivers/usb/spca5xx.c
spca5xx-20050906/drivers/usb/spca5xx.h
spca5xx-20050906/drivers/usb/spcausb.h
spca5xx-20050906/drivers/usb/icm105a.h
spca5xx-20050906/drivers/usb/hv7131b.h
spca5xx-20050906/drivers/usb/hv7131c.h
spca5xx-20050906/drivers/usb/spca501_init.h
spca5xx-20050906/drivers/usb/pb0330.h
spca5xx-20050906/drivers/usb/et61xx51.h
spca5xx-20050906/drivers/usb/jpeg_header.h
spca5xx-20050906/drivers/usb/spca508_init.h
spca5xx-20050906/drivers/usb/spcaCompat.h
spca5xx-20050906/drivers/usb/dummy_cam.h
spca5xx-20050906/drivers/usb/spcadecoder.c
spca5xx-20050906/drivers/usb/spcadecoder.h
spca5xx-20050906/drivers/usb/tas5130c.h
spca5xx-20050906/drivers/usb/hdcs2020.h
spca5xx-20050906/drivers/usb/spca505_init.h
spca5xx-20050906/drivers/usb/spca500_init.h
spca5xx-20050906/drivers/usb/tv8532.h
spca5xx-20050906/CHANGELOG
spca5xx-20050906/README-TV8532
spca5xx-20050906/INSTALL
spca5xx-20050906/cutlog.py
mario@laptop:~$ cd spca5xx-20050906
mario@laptop:~/spca5xx-20050906$ make
   Building SPCA5XX driver for 2.5/2.6 kernel.
   Remember: you must have read/write access to your kernel source tree.
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/mario/spca5xx-20050906 CC=gcc-3.4 modules
make: *** /lib/modules/2.6.12-9-386/build: No existe el fichero o el directorio.  Alto.
make: *** [default] Error 2


[QUOTE=arnieboy]did u delete the spca5xx-20050906 directory and **REDO** all the steps?[/QUOTE]

---

### Post by arnieboy on 2005-11-22
> **waffen]Yes!! attach a copy of my console:

mario@laptop:~$ sudo apt-get install linux-headers-`uname -r` linux-restricted-modules-`uname -r` build-essential gcc-3.4
Leyendo lista de paquetes... Hecho
Creando &#225 said:**
> http://mxhaard.free.fr/spca50x/Download/spca5xx-20050906.tar.gz[/url]
--23:00:23--  [http://mxhaard.free.fr/spca50x/Download/spca5xx-20050906.tar.gz](http://mxhaard.free.fr/spca50x/Download/spca5xx-20050906.tar.gz)
           => `spca5xx-20050906.tar.gz'
Resolviendo mxhaard.free.fr... 212.27.63.116
Connecting to mxhaard.free.fr|212.27.63.116|:80... conectado.
Petici&#243;n HTTP enviada, esperando respuesta... 200 OK
Longitud: 179,010 (175K) [application/x-gzip]

100%[====================================>] 179,010       42.94K/s    ETA 00:00

23:00:28 (40.39 KB/s) - `spca5xx-20050906.tar.gz' saved [179010/179010]

mario@laptop:~$ tar xvfz spca5xx-20050906.tar.gz
spca5xx-20050906/
spca5xx-20050906/Makefile
spca5xx-20050906/RGB-YUV%2fmodule-setting
spca5xx-20050906/README
spca5xx-20050906/drivers/
spca5xx-20050906/drivers/usb/
spca5xx-20050906/drivers/usb/spcai2c_init.h
spca5xx-20050906/drivers/usb/spcagamma.h
spca5xx-20050906/drivers/usb/cx11646.h
spca5xx-20050906/drivers/usb/sn9cxxx.h
spca5xx-20050906/drivers/usb/cxlib.h
spca5xx-20050906/drivers/usb/zc3xx.h
spca5xx-20050906/drivers/usb/cs2102.h
spca5xx-20050906/drivers/usb/jpeg_qtables.h
spca5xx-20050906/drivers/usb/pas106b.h
spca5xx-20050906/drivers/usb/spca504_init.h
spca5xx-20050906/drivers/usb/spca506.h
spca5xx-20050906/drivers/usb/spca533.h
spca5xx-20050906/drivers/usb/spca536.h
spca5xx-20050906/drivers/usb/spca561.h
spca5xx-20050906/drivers/usb/mr97311.h
spca5xx-20050906/drivers/usb/sonix.h
spca5xx-20050906/drivers/usb/spca5xx.c
spca5xx-20050906/drivers/usb/spca5xx.h
spca5xx-20050906/drivers/usb/spcausb.h
spca5xx-20050906/drivers/usb/icm105a.h
spca5xx-20050906/drivers/usb/hv7131b.h
spca5xx-20050906/drivers/usb/hv7131c.h
spca5xx-20050906/drivers/usb/spca501_init.h
spca5xx-20050906/drivers/usb/pb0330.h
spca5xx-20050906/drivers/usb/et61xx51.h
spca5xx-20050906/drivers/usb/jpeg_header.h
spca5xx-20050906/drivers/usb/spca508_init.h
spca5xx-20050906/drivers/usb/spcaCompat.h
spca5xx-20050906/drivers/usb/dummy_cam.h
spca5xx-20050906/drivers/usb/spcadecoder.c
spca5xx-20050906/drivers/usb/spcadecoder.h
spca5xx-20050906/drivers/usb/tas5130c.h
spca5xx-20050906/drivers/usb/hdcs2020.h
spca5xx-20050906/drivers/usb/spca505_init.h
spca5xx-20050906/drivers/usb/spca500_init.h
spca5xx-20050906/drivers/usb/tv8532.h
spca5xx-20050906/CHANGELOG
spca5xx-20050906/README-TV8532
spca5xx-20050906/INSTALL
spca5xx-20050906/cutlog.py
mario@laptop:~$ cd spca5xx-20050906
mario@laptop:~/spca5xx-20050906$ make
   Building SPCA5XX driver for 2.5/2.6 kernel.
   Remember: you must have read/write access to your kernel source tree.
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/mario/spca5xx-20050906 CC=gcc-3.4 modules
make: *** /lib/modules/2.6.12-9-386/build: No existe el fichero o el directorio.  Alto.
make: *** [default] Error 2
try the following:
```
make clean
make
```
and then carry on with the rest of the steps
also let me know if u find any errors

---

### Post by waffen on 2005-11-24
Hi,
yersterday my entire system crash!! I dont know why?... right now I'm reinstalling the Breezy (I couldn't fix the xserver)...and try install de camera :-) 

Thanks!

---

### Post by waffen on 2005-11-24
PERFECT!!!!

Thanks Arnieboy for your support!!! the camera works perfect in gnomemeeting...

but.... in camorama I receipt this error:

"Could not connect to video device (/dev/video0/). Please check connection."

any idea? :D

---

### Post by arnieboy on 2005-11-24
[QUOTE=waffen]PERFECT!!!!

Thanks Arnieboy for your support!!! the camera works perfect in gnomemeeting...

but.... in camorama I receipt this error:

"Could not connect to video device (/dev/video0/). Please check connection."

any idea? :D[/QUOTE]
please paste the results of the following command in terminal:
```
ls /dev/video*
```

---

### Post by waffen on 2005-11-24
Hi,

teh reply is: File not found...

[QUOTE=arnieboy]please paste the results of the following command in terminal:
```
ls /dev/video*
```[/QUOTE]

---

### Post by arnieboy on 2005-11-24
[QUOTE=waffen]Hi,

teh reply is: File not found...[/QUOTE]
alright herez what u need to do.. u need to find out which device file is being used by gnomemeeting and link the same file to /dev/video0. so u have to figure which file it is. if the file is /dev/xyz (lets say) then u wud have to do the following:
```
sudo ln -s /dev/xyz /dev/video0
```
and camorama will work.
hope this helps.

---

### Post by `GooZ´ on 2005-11-26
Well THIS is an idea for putting in automatix! :-)

---

### Post by derrick1985 on 2005-11-30
Hey

I followed the directions and I can't get my SPC102 based chipset (microdia, made by logitech electronics (not THE LOGITECH) to work. Gnome meeting doesn't detect it in v4l or v4l2.

any ideas? the USB microphone part of the webcam works, just not the cam.

Thanks.

---

### Post by Cuppa-Chino on 2005-12-01
this might be a bit of ridiculous newbie question, but I will shoot anyway:

there a deb-packages at [http://mxhaard.free.fr/]("http://mxhaard.free.fr/") which steps can I avoid?

---

### Post by arnieboy on 2005-12-01
[QUOTE=Cuppa-Chino]this might be a bit of ridiculous newbie question, but I will shoot anyway:

there a deb-packages at [http://mxhaard.free.fr/]("http://mxhaard.free.fr/") which steps can I avoid?[/QUOTE]
dont avoid anything. take that or leave it.
and dont use the deb

---

### Post by imranj on 2005-12-02
Hello, i am planning to install Ubuntu (Aka Kubuntu:),:KS 

Ok, checking this thread out, i wanted to know how can u know what chipset is my web cam running on, say Creative PC-Cam 550.

And did any one else , was able to make it work with any of the available applications of Linux?

Thanks, please help me make my Ubuntu installation successful.:smile:

---

### Post by jerryluis on 2005-12-02
Excuse me but how did you solve the installation process of spca5xx?

you untar and unzip OK!
after that step by step what did you do?
I try 
make
but I receive your error. PLease inform me because the same problem I have with ubuntu 5.10 and with suse 10:confused:

---

### Post by Cuppa-Chino on 2005-12-03
Hi arnieboy et al, 
followed the instructions exactly and webcam works okay. Now I cannot my wireless card to connect to my router anymore (had to write this from a Windo$ boot :( ) . I was using ndiswrapper and wpa_supplicant and had no problems before.

Could this have to do with the **gcc**-change required for the webcam? 

[QUOTE=arnieboy]
```
sudo passwd root
```
and set the root password if u already dont have one
now do the following
```
su
CC=gcc-3.4
export CC
exit
CC=gcc-3.4
export CC
wget http://mxhaard.free.fr/spca50x/Download/spca5xx-20050906.tar.gz
tar xvfz spca5xx-20050906.tar.gz
cd spca5xx-20050906
make
sudo modprobe -r spca5xx
```
[/QUOTE]

How can I change it back? Just as the above but with **CC=gcc-4**?? And will the cam still work than?

Thanks for you help ...

---

### Post by arnieboy on 2005-12-03
[QUOTE=Cuppa-Chino]Hi arnieboy et al, 
followed the instructions exactly and webcam works okay. Now I cannot my wireless card to connect to my router anymore (had to write this from a Windo$ boot :( ) . I was using ndiswrapper and wpa_supplicant and had no problems before.

Could this have to do with the **gcc**-change required for the webcam? 



How can I change it back? Just as the above but with **CC=gcc-4**?? And will the cam still work than?

Thanks for you help ...[/QUOTE]
installing ur webcam modules has nothing to with ndiswrapper. by exporting gcc to version 3.4, u merely make modules compile with version 3.4 of gcc in that session. when u log off and get back to gnome, gcc 4.0 will again become the default. something like ndiswrapper which already has been compiled prior to your compiling the webcam modules will not get affected even if u set gcc to 3.4 for one session because ndiswrapper does not get compiled every time its run. its just a binary which has nothing to do with gcc once its set up. u need to look around and find out why ndiswrapper is not working. it has nothing to do with following this howto.

---

### Post by Cuppa-Chino on 2005-12-03
okay thanks arnie - just learned something :) - will see if I can repair the system ...

---

### Post by pipepool on 2005-12-04
Hello, it would be useful know if i can use this HOWTO in hoary. Well, really, i have used it, but when i do "sudo modprob spca5xxx" the output is:
 
"FATAL: Error inserting spca5xx (/lib/modules/2.6.10-6-386/kernel/drivers/usb/media/spca5xx.ko): Invalid module format

I think that i have followed step to step the Howto, i think. If i want to repeat it, i have to do anything before? Well, thx for all

---

### Post by arnieboy on 2005-12-04
[QUOTE=pipepool]Hello, it would be useful know if i can use this HOWTO in hoary. Well, really, i have used it, but when i do "sudo modprob spca5xxx" the output is:
 
"FATAL: Error inserting spca5xx (/lib/modules/2.6.10-6-386/kernel/drivers/usb/media/spca5xx.ko): Invalid module format

I think that i have followed step to step the Howto, i think. If i want to repeat it, i have to do anything before? Well, thx for all[/QUOTE]
this howto was **not** written for hoary, hence u shd not have followed it. anyway this is how to do it for **hoary** (i am not sure it will work but u can give it a try)
assuming u have the headers installed and the gzipped file downloaded, do the following:
```
cd spca5xx-20050906
make clean
make
sudo modprobe -r spca5xx
sudo rm -rf /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx*
sudo make install
sudo modprobe spca5xx
```

if u get any errors at any of the above steps paste it here.

---

### Post by pipepool on 2005-12-04
Thnx, thnx and more thnx :D  :D  :D  :D It worked correctly

---

### Post by arnieboy on 2005-12-04
[QUOTE=pipepool]Thnx, thnx and more thnx :D  :D  :D  :D It worked correctly[/QUOTE]
nice :)

---

### Post by Cybercool on 2005-12-06
I justed installed the webcam on my laptop.
And it works.

But now i want to install it on my system and when i want to do v4l-conf i get the next error:
keizers@pcivo:~/spca5xx-20050906$ v4l-conf
v4l-conf: using X11 display :0.0
WARNING: Your X-Server has no DGA support.
mode: 1280x1024, depth=24, bpp=32, bpl=5120, base=unknown
can't open /dev/video0: No space left on device
keizers@pcivo:~/spca5xx-20050906$


What to do?

---

### Post by jerryluis on 2005-12-08
[QUOTE=arnieboy]
U need to do the following first of all:
```
sudo apt-get install linux-headers-`uname -r` linux-restricted-modules-`uname -r` build-essential gcc-3.4
```
[/QUOTE]

Sorry but it doesn't work for me, when I run it I receive an errore message, like that files don't exist..
```

Reading package lists ...Done
Building dependency tree... Done
E:Couldn't find package linux-headers-uname -r
```
Do you know how can I solve?

---

### Post by arnieboy on 2005-12-08
u are not copying and pasting the command. u left out the quotation marks and tried to manually type it, thats why it didnt work. `uname -r` is an argument here, not a switch.
**Please copy and paste the commands**

---

### Post by jerryluis on 2005-12-08
[QUOTE=arnieboy]u are not copying and pasting the command. u left out the quotation marks and tried to manually type it, thats why it didnt work. `uname -r` is an argument here, not a switch.
**Please copy and paste the commands**[/QUOTE]

You're right, infact now my webcam work properly with camorama. you're my hero.
By the way I don't understand what keys I should type, because on my keyboard there is only " ' " and you use one different.
thank you

:p

---

### Post by arnieboy on 2005-12-08
[QUOTE=jerryluis]You're right, infact now my webcam work properly with camorama. you're my hero.
By the way I don't understand what keys I should type, because on my keyboard there is only " ' " and you use one different.
thank you

:p[/QUOTE]
use the key just left of the 1/! key on the top row.

---

### Post by Cybercool on 2005-12-08
Does anybody has an answer on my problem already?

---

### Post by arnieboy on 2005-12-08
[QUOTE=Cybercool]Does anybody has an answer on my problem already?[/QUOTE]
why are u trying to use v4l-conf? have u tried using camorama or gnomemeeting?

---

### Post by Cybercool on 2005-12-09
[QUOTE=arnieboy]why are u trying to use v4l-conf? have u tried using camorama or gnomemeeting?[/QUOTE]


gnomemeeting says, no devices found!!

---

### Post by arnieboy on 2005-12-10
[QUOTE=Cybercool]gnomemeeting says, no devices found!![/QUOTE]
did u follow this howto step by step?

---

### Post by dresnu on 2005-12-10
i followed everything step by step, no errors, but my camera doesn't work :-(. Neither in camorama nor in kopete. Camorama says it can't connect to the device, and in kopete there is no device that i can select. ls /dev/video* returns "/dev/video0". thx

---

### Post by arnieboy on 2005-12-10
[QUOTE=dresnu]i followed everything step by step, no errors, but my camera doesn't work :-(. Neither in camorama nor in kopete. Camorama says it can't connect to the device, and in kopete there is no device that i can select. ls /dev/video* returns "/dev/video0". thx[/QUOTE]
whats the make of ur webcam?

---

### Post by derrick1985 on 2005-12-10
[QUOTE=dresnu]i followed everything step by step, no errors, but my camera doesn't work :-(. Neither in camorama nor in kopete. Camorama says it can't connect to the device, and in kopete there is no device that i can select. ls /dev/video* returns "/dev/video0". thx[/QUOTE]

Yeah, that's the same problem i'm having.

Mine (in XP) is detected as SN9C103, Driver provider sonix

---

### Post by arnieboy on 2005-12-10
alright  plz make sure your webcam is listed on the following page before u try this howto:
[http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html) 
if its not, this howto wont work.

---

### Post by dresnu on 2005-12-11
ok, my fault :D... I had read that the quickcam was supported but I then realised that I have a different product ID than the one listed :(. Sorry. (It's very annoying to have the simpliest webcam in the world but not being able to use it...)

---

### Post by Cybercool on 2005-12-11
[QUOTE=arnieboy]alright  plz make sure your webcam is listed on the following page before u try this howto:
[http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html) 
if its not, this howto wont work.[/QUOTE]


I followed the howto step by step, and the webcam also works on my laptop ubuntu.
So why not my normal desktop.

Greetingz,
Ivo

---

### Post by arnieboy on 2005-12-11
[QUOTE=Cybercool]I followed the howto step by step, and the webcam also works on my laptop ubuntu.
So why not my normal desktop.

Greetingz,
Ivo[/QUOTE]
alright try this (ALL) from terminal:
```
sudo apt-get install gqcam
sudo ln -s /dev/video0 /dev/video
gqcam
```
if the cam runs fine, u are all set. If it doesnt please list the errors here.

---

### Post by Cybercool on 2005-12-11
[QUOTE=arnieboy]alright try this (ALL) from terminal:
```
sudo apt-get install gqcam
sudo ln -s /dev/video0 /dev/video
gqcam
```
if the cam runs fine, u are all set. If it doesnt please list the errors here.[/QUOTE]

OK i did what you asked for:
keizers@pcivo:~$ sudo ln -s /dev/video0 /dev/video
keizers@pcivo:~$ gqcam

But i get the next error when i start op gqcam: :( :( 
/dev/video: No space left on device

So, it doesn't work!

---

### Post by Chris Tucker on 2005-12-12
about the wifi stop'd working post, if your on a laptop like mine, you needed to change some kernel things for your ACPI to work... and that change also needed to be made for wifi to work in my case, try redoing any changes you made to make your wifi work in the first place.

i'll be trying this with my spca5 compatible camera when i get home today... 

Anyone know any linux msn messenger clients that support voice/vid? i have a lot of family members that use MSN messenger on windows and have webcams.. with the holiday season coming up, i'll need to be able to chat with them.

---

### Post by Cybercool on 2005-12-12
[QUOTE=Chris Tucker]about the wifi stop'd working post, if your on a laptop like mine, you needed to change some kernel things for your ACPI to work... and that change also needed to be made for wifi to work in my case, try redoing any changes you made to make your wifi work in the first place.

i'll be trying this with my spca5 compatible camera when i get home today... 

Anyone know any linux msn messenger clients that support voice/vid? i have a lot of family members that use MSN messenger on windows and have webcams.. with the holiday season coming up, i'll need to be able to chat with them.[/QUOTE]


Mercury supports almost everything MSN 7.0 does!! :D

---

### Post by Chris Tucker on 2005-12-12
thanks, i'll try mercury...

few notes.. well, heres a suprise: MY CAMERA IS WORKING! YEEHAW! thanks thanks and yet more thanks! this was a major reason i dualbooted..
(types around cat that is trying to use the trackpad on this notebook)

ok, question though, is there a way to change the capture image size? i know in windows it can capture small images or big ones (resolution speaking) i know the framrate jumps down to 15fps or less with the max res on this camera but for internet conversation, thats quite above adiquite for a camera i got for free with my notebook.. and ideas?

also, gqcam gives me some control over brightness, but in all my apps my picture is signifigantly darker than in any vid view app in windows, any ways to enhance it? (may autmatically be better when i fix my picture capture size and stuff.)
EDIT: OH YEA, forgot to mention, make it easier for anyone else with this webcam to find a howto, its a Nextech webcam...

---

### Post by arnieboy on 2005-12-12
[QUOTE=Chris Tucker]thanks, i'll try mercury...

few notes.. well, heres a suprise: MY CAMERA IS WORKING! YEEHAW! thanks thanks and yet more thanks! this was a major reason i dualbooted..
(types around cat that is trying to use the trackpad on this notebook)

ok, question though, is there a way to change the capture image size? i know in windows it can capture small images or big ones (resolution speaking) i know the framrate jumps down to 15fps or less with the max res on this camera but for internet conversation, thats quite above adiquite for a camera i got for free with my notebook.. and ideas?

also, gqcam gives me some control over brightness, but in all my apps my picture is signifigantly darker than in any vid view app in windows, any ways to enhance it? (may autmatically be better when i fix my picture capture size and stuff.)
EDIT: OH YEA, forgot to mention, make it easier for anyone else with this webcam to find a howto, its a Nextech webcam...[/QUOTE]
tried camorama? not sure but it might help u control the picture capture size.
```
sudo apt-get install camorama
```

---

### Post by Chris Tucker on 2005-12-12
when i try to change the size of the image in camorama it crashes and dumps this several times: (camorama:13235): Gtk-CRITICAL **: gtk_entry_set_text: assertion `text != NULL' failed
camorama is an awesome little app though, but looks like i need a more direct way to adjust the camera.. err.. directly.. lol

thanks for the great help! keep it up!

---

### Post by arnieboy on 2005-12-12
alright try this.. change the desktop theme to the default "human" theme and try running camorama again.

---

### Post by Chris Tucker on 2005-12-12
erm.. playing with camorama i fuged it up :S where would i find the camorama config file? i was playing with auto capture and it froze, now it freezes on start :S i cant get back to the menu to turn it off that way.
once i do that i'll try the theme thing....

---

### Post by arnieboy on 2005-12-12
[QUOTE=Chris Tucker]erm.. playing with camorama i fuged it up :S where would i find the camorama config file? i was playing with auto capture and it froze, now it freezes on start :S i cant get back to the menu to turn it off that way.
once i do that i'll try the theme thing....[/QUOTE]
try doing
```
rm -rf ~/.camorama
```
from terminal and then start camorama again

---

### Post by Chris Tucker on 2005-12-12
config fixed, theme changed, x server restarted to completely apply theme. no GTK warnings now when i try to change the size in camorama, but it just errors "unable to capture image" and exits. is there a more direct way to change how images are gotten from the camera?

---

### Post by arnieboy on 2005-12-12
[QUOTE=Chris Tucker]config fixed, theme changed, x server restarted to completely apply theme. no GTK warnings now when i try to change the size in camorama, but it just errors "unable to capture image" and exits. is there a more direct way to change how images are gotten from the camera?[/QUOTE]
yes, changing the theme fixed the GTK warnings.. the reason why i asked u to do that was to get a cleaner camorama error output from terminal (by running camorama from terminal)
I have tried the following progs which use my webcam on linux:
> gnomemeeting
camorama
gqcam
spcagui (made by the same guy who wrote the spca5xx drivers.. its a little rough around the edges but u might wanna give it a try)
amsn
u can try these or others to get what u want.
I have never tried video still capturing on linux and therez certainly no way I can do it at work (right now) but I maybe able to give u some feedback when I get back home later tonight.

---

### Post by Cybercool on 2005-12-12
[QUOTE=Cybercool]OK i did what you asked for:
keizers@pcivo:~$ sudo ln -s /dev/video0 /dev/video
keizers@pcivo:~$ gqcam

But i get the next error when i start op gqcam: :( :( 
/dev/video: No space left on device

So, it doesn't work![/QUOTE]

Do you have an answer for this?? arnieboy??

---

### Post by arnieboy on 2005-12-12
[QUOTE=Cybercool]Do you have an answer for this?? arnieboy??[/QUOTE]
ok try this..
unplug all usb devices from your desktop, and plug in the webcam first and try and see if ur webcam works this time (with camorama or gqcam). if it does, plug in the rest of the usb devices.
if this procedure does not work, unplug all the USB devices again and redo the steps in the first post with one change. before doing "**make**", do a "**make clean**". finish all the steps and now plug in your cam and see if it works or not.

---

### Post by Chris Tucker on 2005-12-12
[QUOTE=Cybercool]Do you have an answer for this?? arnieboy??[/QUOTE]
when i did the ln -s line it worked fine for me .. my camera also showed up as /dev/video0 , try gqcam -v /dev/video0  <-- specifying the device

---

### Post by Cybercool on 2005-12-13
OK i got it working.
But sometimes my hotplug runs stuck.
Or i can't get an image of the cam because resource is busy.
And when i want to rmmod spca5xx (of course) it busy.
Howto get this write when this happends?

---

### Post by pinballkid on 2005-12-14
I have a Genius VideoCAM GE111. I've tried following the instructions in this howto and everything went smoothly, except that GnomeMeeeting doesn't detect my webcam. I also cant find a /dev/video0 or /dev/video file or anything else that might indicate that my system has loaded a new usb device.

lsusb comes up with this:
Bus 002 Device 005: ID 093a:2471 Pixart Imaging, Inc.
which does seem to be supported on [this page]("http://mxhaard.free.fr/spca5xx.html")

lsmod | grep spca5xx give me this:
spca5xx               640432  0
videodev                9344  1 spca5xx
usbcore               104316  6 spca5xx,usb_storage,usbhid,ehci_hcd,ohci_hcd

Does anyone have any idea how to get ubuntu to create the /dev/video or /dev/video0 file when I plug in my webcam?

Thanks

---

### Post by jmn2k1 on 2005-12-15
[QUOTE=pinballkid]I have a Genius VideoCAM GE111. I've tried following the instructions in this howto and everything went smoothly, except that GnomeMeeeting doesn't detect my webcam. I also cant find a /dev/video0 or /dev/video file or anything else that might indicate that my system has loaded a new usb device.[/QUOTE]
I have the same webcam, and is running ok.... follow _all_ the steps in the how-to.

Anyone knows how to tweak the brightness in gnomemeeting?? (or somewhere else... but to using it with gnomemeeting...)

---

### Post by pinballkid on 2005-12-19
[QUOTE=jmn2k1]I have the same webcam, and is running ok.... follow _all_ the steps in the how-to.[/QUOTE]

Glad to hear it works! I've followed all the steps again very carefully and still no luck. What version kernel are you running on? Gnomemeeting still wont detect a device on my machine (ubuntu breezy kernel 2.6.12-10-386)

---

### Post by arnieboy on 2005-12-19
[QUOTE=pinballkid]Glad to hear it works! I've followed all the steps again very carefully and still no luck. What version kernel are you running on? Gnomemeeting still wont detect a device on my machine (ubuntu breezy kernel 2.6.12-10-386)[/QUOTE]
redo the instructions again with one difference:
do a ```
make clean
``` before doing ```
make
```

---

### Post by mjshepherd on 2005-12-19
I followed your instructions to the letter to try to install this driver for my digital camera, but when i get to the "make" command, i get the error message
bash: make: command not found

I tried to ignore this, and went on to "make install", and received the same sort of error message.

what can I do?

Thanks, Matthew

---

### Post by arnieboy on 2005-12-19
[QUOTE=mjshepherd]I followed your instructions to the letter to try to install this driver for my digital camera, but when i get to the "make" command, i get the error message
bash: make: command not found

I tried to ignore this, and went on to "make install", and received the same sort of error message.

what can I do?

Thanks, Matthew[/QUOTE]
do the following and try again
```
sudo apt-get install make
```

---

### Post by mjshepherd on 2005-12-19
Thanks - now "make" is working but there are other problems.  This is what happened the last time i tried to install this driver (from the make command)

matthew@ubuntu:~/spca5xx-20050906$ make
   Building SPCA5XX driver for 2.5/2.6 kernel.
   Remember: you must have read/write access to your kernel source tree.
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/matthew/spca5xx-20050906 CC=gcc-3.4 modules
make: *** /lib/modules/2.6.12-9-386/build: No such file or directory.  Stop.
make: *** [default] Error 2
matthew@ubuntu:~/spca5xx-20050906$ sudo modprobe -r spca5xx
matthew@ubuntu:~/spca5xx-20050906$ sudo rm -rf /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx*
matthew@ubuntu:~/spca5xx-20050906$ sudo make install
mkdir -p /lib/modules/`uname -r`/kernel/drivers/usb/media/
rm -f /lib/modules/`uname -r`/kernel/drivers/usb/media/spca50x.ko
rm -f /lib/modules/`uname -r`/kernel/drivers/usb/media/et61x.ko
install -c -m 0644 spca5xx.ko /lib/modules/`uname -r`/kernel/drivers/usb/media/
install: cannot stat `spca5xx.ko': No such file or directory
make: *** [install] Error 1
matthew@ubuntu:~/spca5xx-20050906$ sudo modprobe spca5xx
FATAL: Could not open '/lib/modules/2.6.12-9-386/kernel/drivers/usb/media/spca5xx/spca5xx.ko': No such file or directory
matthew@ubuntu:~/spca5xx-20050906$

I'm getting very tired now.  Do i have to go through the entire process every time, or can i cut in at a later stage (eg. do i have to download the driver package every time?)

---

### Post by arnieboy on 2005-12-19
do the following step-by-step after opening up terminal
```
su
CC=gcc-3.4
export CC
exit
CC=gcc-3.4
export CC
cd spca5xx-20050906
make clean
make
sudo modprobe -r spca5xx
sudo rm -rf /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx*
sudo make install
sudo modprobe spca5xx
```

---

### Post by mjshepherd on 2005-12-19
thanks for the revised instructions! this time i got as far as "make install" before things went wrong! here's what happened:

matthew@ubuntu:~/spca5xx-20050906$ sudo make install
mkdir -p /lib/modules/`uname -r`/kernel/drivers/usb/media/
rm -f /lib/modules/`uname -r`/kernel/drivers/usb/media/spca50x.ko
rm -f /lib/modules/`uname -r`/kernel/drivers/usb/media/et61x.ko
install -c -m 0644 spca5xx.ko /lib/modules/`uname -r`/kernel/drivers/usb/media/
install: cannot stat `spca5xx.ko': No such file or directory
make: *** [install] Error 1
matthew@ubuntu:~/spca5xx-20050906$ sudo modprobe spca5xx
FATAL: Could not open '/lib/modules/2.6.12-9-386/kernel/drivers/usb/media/spca5xx/spca5xx.ko': No such file or directory

---

### Post by arnieboy on 2005-12-19
are u sure u did this?
```
sudo apt-get install linux-headers-`uname -r` linux-restricted-modules-`uname -r` build-essential gcc-3.4
```
if not, then redo the above and then the following:

```

su
CC=gcc-3.4
export CC
exit
CC=gcc-3.4
export CC
cd spca5xx-20050906
make clean
make
sudo make install
sudo modprobe spca5xx
```

---

### Post by mjshepherd on 2005-12-19
i did, but look what happened - there's another error, right at the beginning of the process!

Reading package lists... Done
Building dependency tree... Done
linux-restricted-modules-2.6.12-9-386 is already the newest version.
E: Couldn't find package gcc-3.4

Sorry!

---

### Post by arnieboy on 2005-12-19
[QUOTE=mjshepherd]i did, but look what happened - there's another error, right at the beginning of the process!

Reading package lists... Done
Building dependency tree... Done
linux-restricted-modules-2.6.12-9-386 is already the newest version.
E: Couldn't find package gcc-3.4

Sorry![/QUOTE]
that explains it.. why it wasnt getting compiled..
well paste the contents of 
```
sudo cat /etc/apt/sources.list 
```

---

### Post by mjshepherd on 2005-12-19
do you mean type this into terminal, and paste what comes out?  Ok... but there's a lot of it!

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
# deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy main restricted
# deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-updates main restricted
# deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy universe
# deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

---

### Post by arnieboy on 2005-12-19
ok do the following:
```
sudo gedit /etc/apt/sources.list
```
and make the contents of file look exactly like the following:
> ## deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

save and exit and then do the following:
```
sudo apt-get update
sudo apt-get install linux-headers-`uname -r` linux-restricted-modules-`uname -r` build-essential gcc-3.4
su
CC=gcc-3.4
export CC
exit
CC=gcc-3.4
export CC
cd spca5xx-20050906
make clean
make
sudo modprobe -r spca5xx
sudo rm -rf /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx*
sudo make install
sudo modprobe spca5xx
```

---

### Post by arnieboy on 2005-12-19
i made a small correction in  the above..
added "make clean" before "make"

---

### Post by mjshepherd on 2005-12-20
Well, I'm increasingly convinced that this will actually work.  I installed the updates as you suggested.  However, i'm on dial-up access, and this took about an hour.  I then tried:

sudo apt-get install linux-headers-`uname -r` linux-restricted-modules-`uname -r` build-essential gcc-3.4

and it started to download following my acceptance of the unpacked disk usage.  However, i could see that this next download would take another hour and a half at least.

By then it was nearly 3 in the morning, and I was knackered (I still am) so I went to bed.

Is there any way i can download this installation on my broadband connection at work (windows system) and install it from a CD when i get home?  I've found a HOW TO at

[http://ubuntuforums.org/archive/index.php/t-79896.html](http://ubuntuforums.org/archive/index.php/t-79896.html)

should i follow the advice here?

I am beginning to wonder how much i need to use this camera...

---

### Post by mjshepherd on 2005-12-20
Rats.

I'm not sure i've even managed to update yet.  I think i may be in download hell!

if you do apt-get update does this actually download and install updates, or does it just work out which updates are available for download?  I ask this because after typing sudo apt-get update, and downloading stuff for ages, i got a message in the top right of the screen saying that new updates were available.  When i later clicked on this I got to the update manager, and, now offline, clicking on "install"  meant that i got repeated error messages saying that the server wasn't available!  I now appear to have lost the information on which updates are available (update manager now tells me that I am up to date - which I don't believe).

Is it possible to download only those updates that I need, so that i can install gcc-3.4 (now downloaded as per the HOW TO above), so that i can install spca5xx, so that i can use my camera?

Or should i just give up?

---

### Post by pinballkid on 2005-12-23
I've finally managed to get my Genius ViewCAM working with this driver :smile: ! The howto worked in every way, except that I needed to download the latest version of spca5xx from the website (instead of using spca5xx-20050906).

Thanks to everyone for all the help!

---

### Post by Al_maverick on 2005-12-25
I followed this how-to and got my cam working. But then I enabled the noapic and no_timer_check kernel boot option. (it was to correct with the clock going too fast on amd64)
Now the pc freezes whenever I try to use the cam. For example, in the configuration panel of kopete.
Did anyone have the same problem?

---

### Post by albacker on 2005-12-26
dont have an icm532 web cam... i have a quickcam messenger.
eni@madgeek:~$ lsusb | grep Logitech
Bus 002 Device 003: ID 046d:08f0 Logitech, Inc.
if i see its ID i get its a quickcam messenger.. 
i have camorama camstream and some other cam-utils installed..
i installed qc-usb-source and tried to compile it, but i got some errors..
some friend told me i had to re-compile my kernel.
can someone help me ? it would be nice a step-by-step tutorial or something like it.

---

### Post by viscount on 2005-12-26
Worked very well for me, gnomemeeting, camorama, and even gqcam once
video was linked to video0.

thanks for this.. now if only we could get a good msn/yahoo video msg
client that would support cameras I wouldnt feel quite so isolated
from friends and family overseas.

Thanks!

---

### Post by albacker on 2005-12-26
i would really appreciate to know what did you do, for making the qcam work ?
Step by step please..
Did you compile anything ? 
Did you recompile kerenel ?
Did you link any other device to video0 

thanks

---

### Post by albacker on 2005-12-26
i tried following th step-by-step tuto and i couldnt make it work, 
beucase i cant find the right linux-headers; here it is :
[email]root@madgeek:/dev/.stat[/email]ic/dev # uname -r
2.6.12-8-386
[email]root@madgeek:/dev/.stat[/email]ic/dev # apt-cache search linux | grep header | grep 2.6.12[COLOR="Red"]-8[/COLOR]
[email]root@madgeek:/dev/.stat[/email]ic/dev # apt-cache search linux | grep header | grep 2.6.12
linux-headers-2.6.12-9 - Header files related to Linux kernel version 2.6.12
linux-headers-2.6.12-9-386 - Linux kernel headers 2.6.12 on 386
linux-headers-2.6.12-9-686 - Linux kernel headers 2.6.12 on PPro/Celeron/PII/PIII/PIV
linux-headers-2.6.12-9-686-smp - Linux kernel headers 2.6.12 on PPro/Celeron/PII/PIII/PIV SMP
linux-headers-2.6.12-9-k7 - Linux kernel headers 2.6.12 on AMD K7
linux-headers-2.6.12-9-k7-smp - Linux kernel headers 2.6.12 on AMD K7 SMP
linux-headers-2.6.12-10 - Header files related to Linux kernel version 2.6.12
linux-headers-2.6.12-10-386 - Linux kernel headers 2.6.12 on 386
linux-headers-2.6.12-10-686 - Linux kernel headers 2.6.12 on PPro/Celeron/PII/PIII/PIV
linux-headers-2.6.12-10-686-smp - Linux kernel headers 2.6.12 on PPro/Celeron/PII/PIII/PIV SMP
linux-headers-2.6.12-10-k7 - Linux kernel headers 2.6.12 on AMD K7
linux-headers-2.6.12-10-k7-smp - Linux kernel headers 2.6.12 on AMD K7 SMP

---

### Post by viscount on 2005-12-26
[QUOTE=albacker]i would really appreciate to know what did you do, for making the qcam work ?
Step by step please..
Did you compile anything ? 
Did you recompile kerenel ?
Did you link any other device to video0 
[/QUOTE]

I followed the instructions step by step from the original post.
Then you must `ln -s /dev/video0 /dev/video`

and it worked, that simple

---

### Post by albacker on 2005-12-27
theres also the problem that i dont see my video or video0 in /dev
so if i do ls 
# ls /dev/  | grep video
i get nothing :S
..
any idea ? what about the linux-headers that i cant find any same as my kernel ?

---

### Post by pinballkid on 2005-12-27
I got this problem when I was using the wrong version of spca5xx. Perhaps downloading the newest version from their website will do the trick?

---

### Post by Stonekeeper on 2006-01-03
Downloading the latest version certainly helped me. However, I'm getting capture at way less than .5 fps. My camera is a Orite My-Cam but is being detected as an LG LIC-200. Does anyone else have this issue with being really slow?

---

### Post by arnieboy on 2006-01-03
howto updated with link to latest driver pack.

---

### Post by GQed76 on 2006-01-04
```
install linux-headers-`uname -r` linux-restricted-modules-`uname 
```

This tends to break my kernel since I have installed the nvidia drivers on my own.  Is this step necessary

---

### Post by arnieboy on 2006-01-04
[QUOTE=GQed76]```
install linux-headers-`uname -r` linux-restricted-modules-`uname 
```

This tends to break my kernel since I have installed the nvidia drivers on my own.  Is this step necessary[/QUOTE]
this step ensures that u have the kernel headers corresponding to your kernel version installed. if u can do it manually, nothing wrong with it.

---

### Post by imranj on 2006-01-05
Bus 002 Device 002: ID 041e:400f Creative Technology, Ltd


This is reported by my lsusb command of my webcam PC-550.
So do you know , which chipset it uses? or any other details
or project working to enable this cam to work?

Help.

---

### Post by encompass on 2006-01-05
I get the following error....> root@lappy:/home/jason/Work_Programs/New_Work/spca5xx-20060101# modprobe spca5xxFATAL: Error inserting spca5xx (/lib/modules/2.6.12-10-686/kernel/drivers/usb/media/spca5xx.ko): Invalid module format
root@lappy:/home/jason/Work_Programs/New_Work/spca5xx-20060101#


any ideas?  I have the Quickcam Express Messenger
oh yes and lsusb
jason@lappy:~$ lsusb
Bus 001 Device 003: ID 046d:08f6 Logitech, Inc.
Bus 001 Device 002: ID 1267:0210 Logic3 / SpectraVideo plc
Bus 001 Device 001: ID 0000:0000
jason@lappy:~$

---

### Post by mike.beta on 2006-01-05
Works like a charm for my creative nx pro! Wiii!

Thx a lot! :)

---

### Post by arnieboy on 2006-01-05
[QUOTE=encompass]I get the following error....

any ideas?  I have the Quickcam Express Messenger
oh yes and lsusb
jason@lappy:~$ lsusb
Bus 001 Device 003: ID 046d:08f6 Logitech, Inc.
Bus 001 Device 002: ID 1267:0210 Logic3 / SpectraVideo plc
Bus 001 Device 001: ID 0000:0000
jason@lappy:~$[/QUOTE]
the error probably occurs because u have not compiled it with gcc 3.4. did u follow the instructions line by line? read them again and u will know what u missed.
when u redo the stuff, do a  
```
make clean
``` in the source folder before u try recompiling.

---

### Post by kevingc on 2006-01-07
I followed the instructions (totally copy and paste), but running gqcam returns "/dev/video: No such file or directory"

Running camstream or xawtv freezes the computer.

I have an Ezonics EZ USB CAM III (Model No. EZ-306).

BTW, the install procedure throws no errors.

---

### Post by louis_nichols on 2006-01-08
WORKED LIKE A CHARM!! :smile: 

so the whole problem was compiling spca5xx with gcc 3.4 instead of 4.0. I seem to remember though that once I compiled it under Fedora Core 4 with gcc 4.0 and it worked.... maybe I'm wong. Anyway... 2 newbie questions, if anyone can help:

1. running modprobe means that the module will be loaded on startup in the future? If not, how can I do that?

2 the command CC=gcc-3.4 doesn't have a permanent effect, right? after a reboot, it will go back to 4.0?

---

### Post by arnieboy on 2006-01-08
[QUOTE=louis_nichols]WORKED LIKE A CHARM!! :smile: 

so the whole problem was compiling spca5xx with gcc 3.4 instead of 4.0. I seem to remember though that once I compiled it under Fedora Core 4 with gcc 4.0 and it worked.... maybe I'm wong. Anyway... 2 newbie questions, if anyone can help:

1. running modprobe means that the module will be loaded on startup in the future? If not, how can I do that?

2 the command CC=gcc-3.4 doesn't have a permanent effect, right? after a reboot, it will go back to 4.0?[/QUOTE]
correct guesses on both questions.

---

### Post by fp-www.tonepad.com on 2006-01-09
Worked for me.

Thanks!

Fp

---

### Post by gslater on 2006-01-09
Sweet....I am now up and running on the webcam.

Gnome meeting is ok....but does anyone know when Skype will be updating the linux version to have video calling....or do they leave it up to the open source community to do that?

---

### Post by louis_nichols on 2006-01-10
the thing with setting the CC environment variable, isn't it the same as just using

sudo make CC=gcc-3.4

?

---

### Post by arnieboy on 2006-01-10
[QUOTE=louis_nichols]the thing with setting the CC environment variable, isn't it the same as just using

sudo make CC=gcc-3.4

?[/QUOTE]
if this actually works, its a great find and I will update my howto. The last time I tried to export CC with sudo (and that was many months back when I wrote this howto), it didnt work.

---

### Post by arnieboy on 2006-01-10
[QUOTE=gslater]Sweet....I am now up and running on the webcam.

Gnome meeting is ok....but does anyone know when Skype will be updating the linux version to have video calling....or do they leave it up to the open source community to do that?[/QUOTE]
skype is closed source. we've got to wait...

---

### Post by louis_nichols on 2006-01-10
well... I'm a newb and I haven't seen it work this way, but I seeem to remember seing that somewhere. I don't know if it depends on the way makefile is configured or is a universal option for make. (I'm not sure of the syntax, either)

---

### Post by arnieboy on 2006-01-10
[QUOTE=louis_nichols]well... I'm a newb and I haven't seen it work this way, but I seeem to remember seing that somewhere. I don't know if it depends on the way makefile is configured or is a universal option for make. (I'm not sure of the syntax, either)[/QUOTE]
yes I came back home and checked! It actually does work when a valid makefile is present. I will now re-write this howto! thanks a lot for the input!!
this makes the howto a lot shorter and removes the use of root :)

---

### Post by francpalm on 2006-01-13
Hi all, I'm a newb in this forum and in ubuntu.
I'd follow the guide for this module but I've this result:

after the make command:
make: *** [default] Segmentation fault

someone can help me?
Many thanks.

---

### Post by jamesshuang on 2006-01-13
I recently purchased a Logitech Quickcam Chat, USB ID 0x046d:0x092c, stated as supported on the spca5xx page. The cam does in fact work, but with three problems - resolution is much lower than advertised (advertised 640x480, only actually goes up to 320x240), the colors are very very bad (oversaturated, overcontrast), and frame rate is abysmal (advertised 30 fps, getting around 5).

Does anyone happen to know why this is happening? I can live with the colors, but the resolution and frame rate are killing me.

---

### Post by chele on 2006-01-14
EasyCam [https://wiki.ubuntu.com/Webcam]("https://wiki.ubuntu.com/Webcam") did the trick for me. It automatically downloads and builds the drivers for many webcams.

---

### Post by peter.faller on 2006-01-14
By following the excellent instructions on page 1 of this thread, I have a Genius GE111 webcam up and running on Breezy. However, there are a few problems: in camorama or camstream, the colours and brightness are poor, and while the contrast and brightness controls work, the colour, hue and white balance don't. Trying to use streamer for video capture gives a very dark picture. Are there some other controls or settings that I can use to adjust the image? (I get a good picture with good colour balance on Windows). Thanks!

---

### Post by arnieboy on 2006-01-18
[QUOTE=peter.faller]By following the excellent instructions on page 1 of this thread, I have a Genius GE111 webcam up and running on Breezy. However, there are a few problems: in camorama or camstream, the colours and brightness are poor, and while the contrast and brightness controls work, the colour, hue and white balance don't. Trying to use streamer for video capture gives a very dark picture. Are there some other controls or settings that I can use to adjust the image? (I get a good picture with good colour balance on Windows). Thanks![/QUOTE]
u cant get the windows picture quality simply because windows uses the real proprietary drivers which genius provides. The linux drivers are mostly reverse-engineering attempts and the results quite expectedly cannot be perfect. All these hardware manufacturers simply need to release their specs and drivers to us.. or else the results will be hard to change.

---

### Post by imranj on 2006-01-19
As told before, i am saying it once more, i have Creative Web Cam 550 and i also have being able to find out the chipset its using the Image sensor, thanks to one dude at creative.

Their have being few users who have told about their similar cams but they also had no luck in getting the cam to work.

So can any one pls advise with this information that i have posted below of where i can get a working driver for linux please.

**[CENTER]Macronix MX88L60 + Hynix HV7131E (sensor)[/CENTER]**

So please advise............

---

### Post by nighttime on 2006-01-19
Man, you are so cool, thank you SO much.

---

### Post by mattjackets on 2006-01-26
help please...

cam: logitech quickcam for notebooks.  ID 046d:08ae
kernel:  2.6.12-10-k7

the stock kernel driver works as well as the 20060101 spca source....which is not very well.  /dev/video1 is created, and demsg looks all well & good, but camorama and gnomemeeting hang when trying to access the cam.  xawtv shows nothing.

here's the output from dmesg with the 20060101 driver:
```
[4296462.793000] /home/matt/spca5xx-20060101/drivers/usb/spca5xx.c: USB SPCA5XX camera found. Logitech QC for Notebooks
[4296462.793000] /home/matt/spca5xx-20060101/drivers/usb/spca5xx.c: [spca5xx_probe:8435] Camera type JPEG
[4296462.848000] /home/matt/spca5xx-20060101/drivers/usb/zc3xx.h: [zcxx_probeSensor:193] sensor 3w Vga ??? 0x0000
[4296462.851000] /home/matt/spca5xx-20060101/drivers/usb/zc3xx.h: [zc3xx_config:367] Find Sensor UNKNOW_0 force Tas5130
[4296462.852000] /home/matt/spca5xx-20060101/drivers/usb/spca5xx.c: [spca5xx_getcapability:2217] maxw 640 maxh 480 minw 176 minh 144
[4296496.384000] /home/matt/spca5xx-20060101/drivers/usb/zc3xx.h: [zcxx_probeSensor:193] sensor 3w Vga ??? 0x0000
[4296519.740000] /home/matt/spca5xx-20060101/drivers/usb/zc3xx.h: [zcxx_probeSensor:193] sensor 3w Vga ??? 0x0000
[4296520.016000] /home/matt/spca5xx-20060101/drivers/usb/zc3xx.h: [zcxx_probeSensor:193] sensor 3w Vga ??? 0x0000
```

lines such as:
```
[4295076.758000] /home/matt/spca5xx-20060101/drivers/usb/spca5xx.c: VIDIOCMCAPTURE: invalid format (7)
```
and
```
[4295076.864000] /home/matt/spca5xx-20060101/drivers/usb/zc3xx.h: [zcxx_probeSensor:193] sensor 3w Vga ??? 0x0000
```
occur when trying to use any program to capture video.  the readme file in the 20060101 release indicates that my device id is supported.

ideas?  please help.

EDIT:
after looking over the info at [http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html) it would seem that the problem may be that the sensor can't be detected and is being forced to Tas5130 when according to the web it's a PAS202 sensor.  can anyone confirm/deny that using the srong sensor info will cause a hang?

EDIT2:
forced the probesensor function to return the code for the PAS202 sensor, and it didn't work.  i'm out of ideas again...

---

### Post by Huub on 2006-01-29
Alright, I've followed the instructions and it worked. For 2 images that is :neutral: (and I didn't change any settings between the working and failing of the webcam). After that I tried fixing it by compiling the latest driver and the 20050906 one, but I keep on getting the following error from 'webcam': "can't get rgb24 data". (since I don't run X on the PC I can only use command line programs). And if it helps anybody understand my problem, another program (camE) gives me the following error: "/dev/video0: no v4l device".

Any chance somebody knows whats going wrong (or what I'm doing wrong)? The webcam still works fine on my Windows PC (and as said, worked well for 2 images on the Linux PC).

---

### Post by simosx on 2006-01-29
Worked like a charm!

Thanks!

---

### Post by louis_nichols on 2006-01-30
Does anyody know how I can adjust image properties? Brightness, contrast and stuff? Possibly while using the webcam in, say kopete... thx

By the way! It works grrreat in kopete. Webcamming cross-platform :D .

---

### Post by Chris Tucker on 2006-02-01
well my webcam in linux plain sucks.. it worked with the spca5xx driver for a really short while.. now for some reason refuses to do that.. "connection error" yet /dev/video0 only exists when the camera is plugged in.
i found out from gnomemeeting that its only working now with an sn9c10x driver. gnomemeeting works fine with this but quality sucks.

im going to be selling a lot of my stuff i dont need on eBay over hte next little while.. i think that camera is going. it will if i can find some nice cheap webcams that have more than a 3fps/ 120x240 capability under linux >.< .. yea thats about all this ones giving me.. im gonna look for some that actually give results of 15fps+ @ 640x480.

---

### Post by chiefofthejojos on 2006-02-03
arnieboy, first of all thank you so much for the huge amount of support you've put into this issue.  You rock!
For me, it fails to compile:
```
brad@a6ubuntu:~/Projects/spca5xx-20060202$ sudo make CC=gcc-3.4
   Building SPCA5XX driver for 2.5/2.6 kernel.
   Remember: you must have read/write access to your kernel source tree.
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/brad/Projects/spca5xx-20060202 CC=gcc-3.4 modules
make[1]: Entering directory `/lib/modules/2.6.12-10-386/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.12-10-386/build'
make: *** [default] Error 2

```

any ideas?

---

### Post by arnieboy on 2006-02-03
[QUOTE=chiefofthejojos]arnieboy, first of all thank you so much for the huge amount of support you've put into this issue.  You rock!
For me, it fails to compile:
```
brad@a6ubuntu:~/Projects/spca5xx-20060202$ sudo make CC=gcc-3.4
   Building SPCA5XX driver for 2.5/2.6 kernel.
   Remember: you must have read/write access to your kernel source tree.
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/brad/Projects/spca5xx-20060202 CC=gcc-3.4 modules
make[1]: Entering directory `/lib/modules/2.6.12-10-386/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.12-10-386/build'
make: *** [default] Error 2

```

any ideas?[/QUOTE]

did u do this step?
```
sudo apt-get install linux-headers-`uname -r` linux-restricted-modules-`uname -r` build-essential gcc-3.4
```

u need to have the headers and restricted modules installed before u attempt compiling the spca modules.

---

### Post by chiefofthejojos on 2006-02-03
[quote=arnieboy]did u do this step?
```
sudo apt-get install linux-headers-`uname -r` linux-restricted-modules-`uname -r` build-essential gcc-3.4
``` 
u need to have the headers and restricted modules installed before u attempt compiling the spca modules.[/quote] 
Yes I did and it looks like I got everything:
```
sudo apt-get install linux-headers-`uname -r` linux-restricted-modules-`uname -r` build-essential gcc-3.4
Reading package lists... Done
Building dependency tree... Done
linux-headers-2.6.12-10-386 is already the newest version.
linux-restricted-modules-2.6.12-10-386 is already the newest version.
build-essential is already the newest version.
gcc-3.4 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
brad@a6ubuntu:~/Projects/spca5xx-20060202$ sudo make clean
rm -r -f drivers/usb/*.o drivers/usb/.spcadecoder.o.cmd \
drivers/usb/.spca5xx.o.cmd  *.o *.ko *.mod.* .[a-z]* core *.i
brad@a6ubuntu:~/Projects/spca5xx-20060202$ sudo make CC=gcc-3.4    Building SPCA5XX driver for 2.5/2.6 kernel.
   Remember: you must have read/write access to your kernel source tree.
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/brad/Projects/spca5xx-20060202 CC=gcc-3.4 modules
make[1]: Entering directory `/lib/modules/2.6.12-10-386/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.12-10-386/build'
make: *** [default] Error 2
``` 
I also tried with the 20060101 version and I had the same problem.

---

### Post by arnieboy on 2006-02-03
well I would suggest u keep trying with older versions.. till one eventually works.. I dont see any other reason why it shouldn't.

---

### Post by robinl on 2006-02-04
I followed your instruction exactly (except replaced it with the 20060202 package as the 20060101 one doesn't work (not found)) and I can see that it uses spca5xx as the driver in Device Manager but neither GnomeMeeting nor Kopete nor Camorama regonise it. GnomeMeeting say no webcam found, Kopete just display a blue screen and Camorama say "Could not connect to Video Device (/dev/video/0). Please check connnection". Am I doing something wrong? Please help. Thanks.

---

### Post by gertdesmet on 2006-02-04
Hi,

I have followed the instructions to install my Logitech Quickcam Chat but everytime i try to start it, it freezes my computer and i have to manually restart it.

Here is the vendor id of the cam : Bus 001 Device 003: ID 046d:092c Logitech, Inc.

Edit: I recompiled the driver with the correct GCC version and now it works perfectly :)

---

### Post by kubuntu2k6 on 2006-02-05
thank you!

this guide rox :)

---

### Post by joppe on 2006-02-10
Thanks. Guides like this roxxors!
Finally the webcam works, for some reason not as many fps as it had on windows, but good enough for msn!

---

### Post by ragjaws on 2006-02-11
Hello I am trying this solution to install my Logitech webcam after entering the second command....
 wget [http://mxhaard.free.fr/spca50x/Download/spca5xx-20060101.tar.gz](http://mxhaard.free.fr/spca50x/Download/spca5xx-20060101.tar.gz)

I am getting the following error, can someone help please...a real newbie here.

-15:21:58--  [http://mxhaard.free.fr/spca50x/Download/spca5xx-20060101.tar.gz](http://mxhaard.free.fr/spca50x/Download/spca5xx-20060101.tar.gz)
           => `spca5xx-20060101.tar.gz'
Resolving mxhaard.free.fr... 212.27.63.122
Connecting to mxhaard.free.fr|212.27.63.122|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
15:21:59 ERROR 404: Not Found.

---

### Post by chiefofthejojos on 2006-02-11
[quote=ragjaws]Hello I am trying this solution to install my Logitech webcam after entering the second command....
 wget [http://mxhaard.free.fr/spca50x/Download/spca5xx-20060101.tar.gz]("http://mxhaard.free.fr/spca50x/Download/spca5xx-20060101.tar.gz")
[/quote] 
try this instead:
```
wget http://mxhaard.free.fr/spca50x/Download/spca5xx-20060202.tar.gz
```

---

### Post by ragjaws on 2006-02-11
[QUOTE=chiefofthejojos]try this instead:
```
wget http://mxhaard.free.fr/spca50x/Download/spca5xx-20060202.tar.gz
```[/QUOTE]
Thanks....here is a copy of my 'Terminal' window should it look like this

[B] angus@ubuntuangus:~$ wget [http://mxhaard.free.fr/spca50x/Download/spca5xx-20060202.tar.gz](http://mxhaard.free.fr/spca50x/Download/spca5xx-20060202.tar.gz)
--15:55:23--  [http://mxhaard.free.fr/spca50x/Download/spca5xx-20060202.tar.gz](http://mxhaard.free.fr/spca50x/Download/spca5xx-20060202.tar.gz)
           => `spca5xx-20060202.tar.gz'
Resolving mxhaard.free.fr... 212.27.63.122
Connecting to mxhaard.free.fr|212.27.63.122|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 193,391 (189K) [application/x-gzip]
instead:
100%[====================================>] 193,391       55.60K/s    ETA 00:00

15:55:27 (55.49 KB/s) - `spca5xx-20060202.tar.gz' saved [193391/193391]

angus@ubuntuangus:~$ wget [http://mxhaard.free.fr/spca50xinstead:/Download/spca5xx-20060202.tar.gz](http://mxhaard.free.fr/spca50xinstead:/Download/spca5xx-20060202.tar.gz)
--15:55:57--  [http://mxhaard.free.fr/spca50x/Download/spca5xx-20060202.tar.gz](http://mxhaard.free.fr/spca50x/Download/spca5xx-20060202.tar.gz)
           => `spca5xx-20060202.tar.gz.1'
Resolving mxhaard.free.fr... 212.27.63.122
Connecting to mxhaard.free.fr|212.27.63.122|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 193,391 (189K) [application/x-gzip]

100%[====================================>] 193,391       60.12K/s    ETA 00:00

15:56:01 (59.99 KB/s) - `spca5xx-20060202.tar.gz.1' saved [193391/193391]

angus@ubuntuangus:~$ tar xvfz spca5xx-20060101.tar.gz
tar: spca5xx-20060101.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverinstead:able: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
angus@ubuntuangus:~$ tar xvfz spca5xx-20060102.tar.gz
tar: spca5xx-20060102.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
angus@ubuntuangus:~$ tar xvfz `spca5xx-20060202.tar.gz.1
> cd spca5xx-20060202
> sudo make CC=gcc-3-4
> sudo modprobe -r spcs5xx
> sudo rm -rf /lib/modules/"uname -r"/kernel/drivers/usb/media/spca5xx*
> sudo make install
> sudo modprobe spca5xx
>

[/B]

---

### Post by chiefofthejojos on 2006-02-12
first of all, it looks like you did several steps twice.  I'm not sure why your doing that.  Also, after the wget step you will need to adjust the file name accordingly, like so:
```
wget http://mxhaard.free.fr/spca50x/Download/spca5xx-20060202.tar.gz
tar xvfz spca5xx-20060202.tar.gz
cd spca5xx-20060202
```
and then continue as before

---

### Post by gmalac on 2006-02-13
error

---

### Post by caish5 on 2006-02-14
Well I got the crashing to stop. But really the picture now is to dark to be usefull. I have a noname brand nightvision camera but even with lots of light it is very dark.
Anyone have any ideas.
Thanks for the guide it was very helpfull.....but not quite!!!:p

---

### Post by arnieboy on 2006-02-14
the driver used for all these ICM532 cams is a reverse-engineered hack and can never equal the quality of native windows drivers which are released by the manufacturers. It is important that all of you send emails to your cam manufacturers requesting them to release drivers for linux. Joint petitions are even better.

A website on the lines of [www.linuxprinting.org](www.linuxprinting.org) can also be started .. It can be called [www.linuxwebcams.org](www.linuxwebcams.org) for example.

---

### Post by JNik on 2006-02-19
I get this error when I try to apt-get:
```
Couldn't find package linux-headers-2.6.12-10-386
```

And I guess that causes the make command not to work:
```
giannis@JohnLap:~/Desktop/spca5xx-20060202$ make
   Building SPCA5XX driver for 2.5/2.6 kernel.
   Remember: you must have read/write access to your kernel source tree.
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/giannis/Desktop/spca5xx-20060202 CC=cc modules
make[1]: Entering directory `/lib/modules/2.6.12-10-386/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.12-10-386/build'
make: *** [default] Error 2
```

---

### Post by Zangdar on 2006-02-19
Hello,

I followed your howto and it works well,
but the day after when I tried :

zangdar@zangdar:~$ sudo modprobe spca5xx
FATAL: Error inserting spca5xx (/lib/modules/2.6.12-10-386/kernel/drivers/usb/media/spca5xx.ko): Unknown symbol in module, or unknown parameter (see dmesg)

I don't understand because before rebooting it worked well...

Thanks for your help !

Zangdar

---

### Post by ragjaws on 2006-02-19
I am also getting this message. I tried both Terminal and root with the same message...
> root@ubuntuangus:/home/angus# cd spca5xx-20060202
root@ubuntuangus:/home/angus/spca5xx-20060202# sudo make CC=gcc-3.4
   Building SPCA5XX driver for 2.5/2.6 kernel.
   Remember: you must have read/write access to your kernel source tree.
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/angus/spca5xx-20060202 CC=gcc-3.4 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-386'
  Building modules, stage 2.
  MODPOST
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-386'
root@ubuntuangus:/home/angus/spca5xx-20060202# sudo modprobe -r spca5xx
FATAL: Module spca5xx not found.
root@ubuntuangus:/home/angus/spca5xx-20060202#


---

### Post by yaye on 2006-02-21
[QUOTE=ragjaws]root@ubuntuangus:/home/angus/spca5xx-20060202#** sudo modprobe -r spca5xx**
FATAL: Module spca5xx not found. ..........[/QUOTE]

The command:

sudo modprobe -r spca5xx

removes the module from memory.  If the module isn't there, you should get this message.  Try continuing with the next step.

Ian

---

### Post by mikelygee on 2006-02-22
Following the advice elsewhere on this thread, I've installe the spca5xx drivers, and my Ezonics II camera is now working...nearly.  Everything is upside down! 

Any advice would be appreciated.

--Mike

---

### Post by Zangdar on 2006-02-25
Help please !!

> 
Hello,

I followed your howto and it works well,
but the day after when I tried :

zangdar@zangdar:~$ sudo modprobe spca5xx
FATAL: Error inserting spca5xx (/lib/modules/2.6.12-10-386/kernel/drivers/usb/media/spca5xx.ko): Unknown symbol in module, or unknown parameter (see dmesg)

I don't understand because before rebooting it worked well...

Thanks for your help !

Zangdar


Even if I make a "make clean" before make...

Thanks.

---

### Post by yaye on 2006-02-25
Thanks again arnieboy.  I used the commands with a Labtec Webcam Pro and it worked perfectly.

Ian

---

### Post by Olisoft on 2006-02-26
Hi

Thank you for your "tutorial", my 'Intel Easy Cam' is now working well using the simple command given at the begining of the thread.

_But I have two small problems : _

-Red-Green-Blue color of image from the webcam is inverted : I see Blue-Green-Red image !

-I have +- 3 images/sec, is it normal ? I get better fps in Ms Windows XP.

Does someone has a solution to one of these problems ?

---

### Post by patrick295767 on 2006-02-27
Thank you arnie !!

Your script worked for me !!
  

====
(after so much posts, and trying ... a single well written script did it !)
 
(Btw, camorama gaves results
(gqcam not really ))

---

### Post by patrick295767 on 2006-02-27
Picture worked too !

---

### Post by patrick295767 on 2006-02-27
Another problem now... 'cos trying now on  my tower PC ...

I have an ATI all in wonder Tuner Tv video card ...
(not yet installed)

I plugged the usb webcam ... runned ur script
and try camorama and it says no device ...

i can post my dmesg :
```
294671.940000]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:pio, hdd:DMA
[4294671.940000] Probing IDE interface ide0...
[4294672.324000] hda: SAMSUNG SP1604N, ATA DISK drive
[4294672.579000] hdb: MAXTOR 4K080H4, ATA DISK drive
[4294672.630000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294672.630000] Probing IDE interface ide1...
[4294673.677000] hdd: LITE-ON DVDRW SHW-1635S, ATAPI CD/DVD-ROM drive
[4294673.728000] ide1 at 0x170-0x177,0x376 on irq 15
[4294673.728000] Probing IDE interface ide2...
[4294674.241000] Probing IDE interface ide3...
[4294674.753000] Probing IDE interface ide4...
[4294675.265000] Probing IDE interface ide5...
[4294675.782000] hda: max request size: 1024KiB
[4294675.787000] hda: 312581808 sectors (160041 MB) w/2048KiB Cache, CHS=19457/255/63, UDMA(33)
[4294675.787000] hda: cache flushes supported
[4294675.787000]  /dev/ide/host0/bus0/target0/lun0: p1 < p5 p6 > p2
[4294675.802000] hdb: max request size: 128KiB
[4294675.803000] hdb: 156301488 sectors (80026 MB) w/2000KiB Cache, CHS=65535/16/63, UDMA(33)
[4294675.803000] hdb: cache flushes supported
[4294675.803000]  /dev/ide/host0/bus0/target1/lun0: p1 p2 < p5 p6 p7 p8 p9 p10 p11 p12 p13 p14 p15 >
[4294675.954000] hdd: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache
[4294675.954000] Uniform CD-ROM driver Revision: 3.20
[4294676.357000] Attempting manual resume
[4294676.357000] swsusp: Suspend partition has wrong signature?
[4294676.393000] ne2k-pci.c:v1.03 9/22/2003 D. Becker/P. Gortmaker
[4294676.393000]   http://www.scyld.com/network/ne2k-pci.html
[4294676.393000] ACPI: PCI Interrupt 0000:00:05.0[A] -> GSI 16 (level, low) -> IRQ 16
[4294676.394000] eth0: RealTek RTL-8029 found at 0xe800, IRQ 16, 00:00:B4:98:CE:F7.
[4294676.429000] usbcore: registered new driver usbfs
[4294676.429000] usbcore: registered new driver hub
[4294676.431000] USB Universal Host Controller Interface driver v2.2
[4294676.431000] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 21
[4294676.431000] PCI: Via IRQ fixup for 0000:00:10.0, from 11 to 5
[4294676.431000] uhci_hcd 0000:00:10.0: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
[4294676.493000] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[4294676.493000] uhci_hcd 0000:00:10.0: irq 21, io base 0x0000d800
[4294676.493000] hub 1-0:1.0: USB hub found
[4294676.493000] hub 1-0:1.0: 2 ports detected
[4294676.496000] ACPI: PCI Interrupt 0000:00:10.1[b] -> GSI 21 (level, low) -> IRQ 21
[4294676.496000] PCI: Via IRQ fixup for 0000:00:10.1, from 10 to 5
[4294676.496000] uhci_hcd 0000:00:10.1: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#2)
[4294676.558000] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[4294676.558000] uhci_hcd 0000:00:10.1: irq 21, io base 0x0000dc00
[4294676.558000] hub 2-0:1.0: USB hub found
[4294676.558000] hub 2-0:1.0: 2 ports detected
[4294676.561000] ACPI: PCI Interrupt 0000:00:10.2[C] -> GSI 21 (level, low) -> IRQ 21
[4294676.561000] PCI: Via IRQ fixup for 0000:00:10.2, from 10 to 5
[4294676.561000] uhci_hcd 0000:00:10.2: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#3)
[4294676.623000] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[4294676.623000] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000e000
[4294676.623000] hub 3-0:1.0: USB hub found
[4294676.623000] hub 3-0:1.0: 2 ports detected
[4294676.660000] ACPI: PCI Interrupt 0000:00:10.3[D] -> GSI 21 (level, low) -> IRQ 21
[4294676.660000] ehci_hcd 0000:00:10.3: VIA Technologies, Inc. USB 2.0
[4294676.660000] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[4294676.660000] ehci_hcd 0000:00:10.3: irq 21, io mem 0xdfffff00
[4294676.660000] ehci_hcd 0000:00:10.3: USB 2.0 initialized, EHCI 1.00, driver 10 Dec 2004
[4294676.661000] hub 4-0:1.0: USB hub found
[4294676.661000] hub 4-0:1.0: 6 ports detected
[4294676.671000] usb 1-1: new full speed USB device using uhci_hcd and address 2
[4294677.419000] usb 4-1: new high speed USB device using ehci_hcd and address 2
[4294677.493000] hub 4-1:1.0: USB hub found
[4294677.493000] hub 4-1:1.0: 4 ports detected
[4294677.876000] usb 4-1.2: new low speed USB device using ehci_hcd and address 4
[4294678.045000] usb 4-1.4: new low speed USB device using ehci_hcd and address 5
[4294678.265000] usb 1-2: new full speed USB device using uhci_hcd and address 3
[4294678.785000] usbcore: registered new driver hiddev
[4294678.789000] input: USB HID v1.10 Mouse [Acrox USB & PS/2 Mouse] on usb-0000:00:10.3-1.2
[4294678.797000] input: USB HID v1.10 Joystick [Logitech Logitech Dual Action] on usb-0000:00:10.3-1.4
[4294678.797000] usbcore: registered new driver usbhid
[4294678.797000] drivers/usb/input/hid-core.c: v2.01:USB HID core driver
[4294679.253000] ACPI: CPU0 (power states: C1[C1])
[4294679.253000] ACPI: Processor [CPU1] (supports 16 throttling states)
[4294679.586000] Attempting manual resume
[4294679.587000] swsusp: Suspend partition has wrong signature?
[4294679.605000] kjournald starting.  Commit interval 5 seconds
[4294679.605000] EXT3-fs: mounted filesystem with ordered data mode.
[4295431.297000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4295435.681000] Adding 746948k swap on /dev/hda6.  Priority:-1 extents:1
[4295435.785000] EXT3 FS on hda2, internal journal
[4295441.924000] parport: PnPBIOS parport detected.
[4295441.924000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[4295442.016000] lp0: using parport0 (interrupt-driven).
[4295442.072000] mice: PS/2 mouse device common for all mice
[4295445.879000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[4295446.844000] cdrom: open failed.
[4295525.285000] Linux agpgart interface v0.101 (c) Dave Jones
[4295525.330000] agpgart: Detected VIA KT266/KY266x/KT333 chipset
[4295525.348000] agpgart: AGP aperture is 128M @ 0xe0000000
[4295525.551000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4295525.575000] shpchp: shpc_init : shpc_cap_offset == 0
[4295525.575000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4295526.013000] ACPI: PCI Interrupt 0000:00:06.0[A] -> GSI 17 (level, low) -> IRQ 17
[4295527.104000] gameport: EMU10K1 is pci0000:00:06.1/gameport0, io 0xec00, speed 1169kHz
[4295527.610000] irda_init()
[4295527.610000] NET: Registered protocol family 23
[4295529.551000] Linux video capture interface: v1.00
[4295529.588000] /root/spca5xx-20060202/drivers/usb/spca5xx.c: USB SPCA5XX camera found.Logitech QuickCam Express II(SPCA561A)
[4295529.588000] /root/spca5xx-20060202/drivers/usb/spca5xx.c: [spca5xx_probe:8188] Camera type S561
[4295529.593000] /root/spca5xx-20060202/drivers/usb/spca5xx.c: [spca5xx_getcapability:2176] maxw 352 maxh 288 minw 160 minh 120
[4295529.620000] usbcore: registered new driver spca5xx
[4295529.620000] /root/spca5xx-20060202/drivers/usb/spca5xx.c: spca5xx driver 00.57.09 registered
[4295530.043000] Floppy drive(s): fd0 is 1.44M
[4295530.058000] FDC 0 is a post-1991 82077
[4295530.489000] Real Time Clock Driver v1.12
[4295530.596000] input: PC Speaker
[4295531.067000] ts: Compaq touchscreen protocol output
[4295533.040000] NET: Registered protocol family 17
[4295542.126000] NET: Registered protocol family 10
[4295542.126000] Disabled Privacy Extensions on device c02eb280(lo)
[4295542.126000] IPv6 over IPv4 tunneling driver
[4295543.363000] ACPI: Power Button (FF) [PWRF]
[4295543.363000] ACPI: Power Button (CM) [PWRB]
[4295543.363000] ACPI: Sleep Button (CM) [SLPB]
[4295543.531000] ibm_acpi: ec object not found
[4295549.728000] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[4295553.082000] eth0: no IPv6 routers present
[4295554.689000] kjournald starting.  Commit interval 5 seconds
[4295554.690000] EXT3-fs warning: mounting unchecked fs, running e2fsck is recommended
[4295554.691000] EXT3 FS on hda5, internal journal
[4295554.691000] EXT3-fs: mounted filesystem with ordered data mode.
[4295567.271000] nfs warning: mount version older than kernel
[4295567.330000] nfs warning: mount version older than kernel
[4295567.378000] nfs warning: mount version older than kernel
[4295753.708000] usbcore: deregistering driver spca5xx
[4295753.743000] /root/spca5xx-20060202/drivers/usb/spca5xx.c: driver spca5xx deregistered
[4295760.585000] Linux video capture interface: v1.00
[4295760.609000] /root/spca5xx-20060202/drivers/usb/spca5xx.c: USB SPCA5XX camera found.Logitech QuickCam Express II(SPCA561A)
[4295760.609000] /root/spca5xx-20060202/drivers/usb/spca5xx.c: [spca5xx_probe:8188] Camera type S561
[4295760.619000] /root/spca5xx-20060202/drivers/usb/spca5xx.c: [spca5xx_getcapability:2176] maxw 352 maxh 288 minw 160 minh 120
[4295760.622000] usbcore: registered new driver spca5xx
[4295760.622000] /root/spca5xx-20060202/drivers/usb/spca5xx.c: spca5xx driver 00.57.09 registered
[4295825.246000] usb 1-2: USB disconnect, address 3
[4295831.912000] usb 1-2: new full speed USB device using uhci_hcd and address 4
[4295832.007000] /root/spca5xx-20060202/drivers/usb/spca5xx.c: USB SPCA5XX camera found.Logitech QuickCam Express II(SPCA561A)
[4295832.007000] /root/spca5xx-20060202/drivers/usb/spca5xx.c: [spca5xx_probe:8188] Camera type S561
[4295832.013000] /root/spca5xx-20060202/drivers/usb/spca5xx.c: [spca5xx_getcapability:2176] maxw 352 maxh 288 minw 160 minh 120
root@tower05:/# ls /dev/video*
/dev/video0
root@tower05:/#       
```


Thank you very much of you precious help,

Sincerely & greetings, 

Patrick

---

### Post by Olisoft on 2006-02-28
Trying to solve my FPS problem of my webcam with the driver given in this thread, I have programmed a small program in C++ that show if VIDEO4LINUX and the CAMERA is well working on Ubuntu :

   -test the camera and V4L initialisation
   -if test are OK, it shows the camera image at the highest possible resolution and speed.

It's a 4.6 Mo compiled program (because need several libraries such as LTI-LIB, which are +- hard to install and compile).

If it interests someone ... I don't know if the compiled file will work standalone on another PC ?!?

> -Camera opened : OK
-Camera V4L detected : OK
 Capabilities of camera : height = 288 , width = 352
-Video overlay obtained : OK
-Max resolution of camera obtained : OK
-Image properties found : OK
 Image properties are : width = 352 , height = 288 , bytes/pixel = 3
-Memory for image storage : OK
-Image 0 readed in 826431 microsec
 Conversion to LTI-Image : 627 microsec
-Image 1 readed in 622086 microsec
 Conversion to LTI-Image : 650 microsec
-Image 2 readed in 670294 microsec
 Conversion to LTI-Image : 661 microsec
...


---

### Post by Cuppa-Chino on 2006-03-03
Hi

yes works like a charm, maybe I am thick (probably the case ;) ), thought I would try and use spcagui to configure the cam 

cannot seem to compile it - always get (same error some other person posted but I cannot find a fix)
```
make
cc -DUSE_SDL -O2 -DLINUX -I/usr/include/SDL -D_REENTRANT -DHAVE_LIBJPEG=1   -c -o spcagui.o spcagui.c
In file included from spcagui.c:23:
gui.h:12:23: error: SDL_image.h: No such file or directory
make: *** [spcagui.o] Error 1

```

*any other clever way to configure* - have figured it out with camorama - would still like to know how to install spcagui just to learn

---

### Post by wawa on 2006-03-03
Thanks arnieboy, works like a charm. 

PS. You may wana update 
```
wget http://mxhaard.free.fr/spca50x/Download/spca5xx-20060301.tar.gz 
```

Cheers

---

### Post by Al_maverick on 2006-03-03
Hi,
this method works for me. Sometimes I have to restart a couple of times, but it works.
The problem is, that after a couple of weeks or months, it depends, I have to run everything to reinstall the webcam.
Any idea what might be the problem. I didnt install anything weird, only the regular upgrades through apt (not the last kernel update)

Anyway, if anyone has an idea where I can start looking, I would really appreciate it.

Tnx!

- Al

---

### Post by arnieboy on 2006-03-05
[QUOTE=Al_maverick]Hi,
this method works for me. Sometimes I have to restart a couple of times, but it works.
The problem is, that after a couple of weeks or months, it depends, I have to run everything to reinstall the webcam.
Any idea what might be the problem. I didnt install anything weird, only the regular upgrades through apt (not the last kernel update)

Anyway, if anyone has an idea where I can start looking, I would really appreciate it.

Tnx!

- Al[/QUOTE]
everytime the kernel headers get updated, u need to redo this howto. the good news is that this bug has been fixed in dapper which is just a month away from final release.

---

### Post by Al_maverick on 2006-03-06
[QUOTE=arnieboy]everytime the kernel headers get updated, u need to redo this howto. the good news is that this bug has been fixed in dapper which is just a month away from final release.[/QUOTE]

Ok. I'll just keep doing it :D 

By the way, I've noticed you updated the procedure and it is much faster now. 
Webcam working again in 5min, including download. Tnx a lot! :)

---

### Post by WanStiller on 2006-03-08
This worked great for me. Thanks!

However, the package has changed again from 20060202 to 20060301. Probably it's best to update the original steps with the comment that you need to verify the current package version or something like that :D

---

### Post by arnieboy on 2006-03-08
first post updated. thanks.

---

### Post by sandyeggoboy on 2006-03-09
I have a Veo Advanced Connect, and i downloaded drivers from [http://www.veo.com/Advanced_Connect/drivers.asp](http://www.veo.com/Advanced_Connect/drivers.asp)

can i use these drivers somehow?

---

### Post by ramirez on 2006-03-15
Thank you so much. I just wanted to play around with ekiga and found this old Logitech ClickSmart, plugged it in and was quite surprised when I saw it was recognized correctly in dmesg. The freezing computer after xawtv -scan brought me down, and your help brought me up again... :D

---

### Post by irober02 on 2006-03-19
Worked a charm first time on two separate ubbuntu BB workstations using a Logitech QuickCam IM. Thanks ArnieBoy. Now I can watch the plants grow in my front garden while I'm at work -How did I get along without that ability! ;-)

---

### Post by SlugO on 2006-03-20
I've been getting my Logitech QuickCam Messenger Plus to work with EasyCam 1.35 but I've had to run it again every time I've rebooted my computer. I thought that this tutorial might give me a bit more permanent results and it did, to a certain extent.

Now gqcam recognizes my webcam (after sudo ln -s /dev/video0 /dev/video) but Ekiga complains that it can't open the camera.

So could you please tell me how to undo the changes shown in this topic?
Ekiga is a lot more useful application than gqcam :)

[EDIT]
Or maybe I should just be asking advice on how to get Ekiga to work with the camera.
Cos the webcam seems to work fine now since even camorama can use it.
Ekiga just complains:> Error while opening video device Logitech QuickCam USB

Blah blah...

Opening the selected channel failed.
(A translation from Finnish btw)

I tried all the 10 channels with Ekiga but nothing... :confused:
Any ideas?

---

### Post by SlugO on 2006-03-20
LOL :D

Nevermind, it's always the one you least expect or don't notice to try.
In this case channel 0 :)

Now it's working fine, just too bad that Ekiga crops a piece of the video
image so that my head seems to fill the whole screen.

---

### Post by xbill on 2006-03-20
Your HOWTO just work.

Thanx for your work.

Useless post but keep it on!

---

### Post by isaric on 2006-03-21
I'm French :-k 
Extract of [Driver pour Webcam Philips SPC 200NC/]("http://forum.ubuntu-fr.org/viewtopic.php?id=23086&p=3")

Before that good. Since  the update of the kernel, more means of making go the webcam.  
One follows this howto that walks once and then in aMSN -- >V4L:  Philips SPS200NC --  >zc301-2 that blocks the computer completely !

Perhaps do you have an idea?

---

### Post by ddumanis on 2006-04-02
Now gnome-meeting works like a charm, but AMSN and Mercury still don't see my webcam. (Although before, running webcam in either one would freeze the system.)

Any thoughts on getting AMSN and Mercury running with my Labtec relic?

---

### Post by isaric on 2006-04-03
Even problem under Dapper

I install it and that goes once on aMSN.
```

sudo apt-get install linux-headers-`uname -r` linux-restricted-modules-`uname -r` build-essential gcc-4.0
wget http://mxhaard.free.fr/spca50x/Download/spca5xx-20060402.tar.gz
tar xvfz spca5xx-20060402.tar.gz
cd spca5xx-20060402
sudo make CC=gcc-4.0

sudo modprobe -r spca5xx
sudo rm -rf /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx*
sudo make install
sudo modprobe spca5xx
```

With the restarting of the computer and then while launching the webcam on aMSN that blocks the computer.

extract of : [Webcam Philips SPC 200NC/"]http://forum.ubuntu-fr.org/viewtopic.php?pid=250600#p250600]("[Marche plus)

---

### Post by SamTheShaman on 2006-04-05
[QUOTE=arnieboy]Some of you probably might have noticed ICM532 chipset based webcams freezing on breezy (for a comprehensive list refer to: [http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html) ) when u turn on gnomemeeting or camorama. Herez the fix for that:
**FOLLOW ALL THE STEPS! DONT TAKE SHORTCUTS OR MAKE MODIFICATIONS IF YOU DON'T KNOW WHAT YOU ARE DOING**
You need to do the following step by step 
```
sudo apt-get install linux-headers-`uname -r` linux-restricted-modules-`uname -r` build-essential gcc-3.4
wget http://mxhaard.free.fr/spca50x/Download/spca5xx-20060301.tar.gz
tar xvfz spca5xx-20060301.tar.gz
cd spca5xx-20060301
sudo make CC=gcc-3.4
sudo modprobe -r spca5xx
sudo rm -rf /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx*
sudo make install
sudo modprobe spca5xx
```
Now you should be all set to use ur ICM532 chipset based webcam.[/QUOTE]


Is there anywhere else i can get this?
[http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html) gives me a 404 not found.


I found the link changed to [http://mxhaard.free.fr/spca50x/Download/spca5xx-20060402.tar.gz](http://mxhaard.free.fr/spca50x/Download/spca5xx-20060402.tar.gz)

I tried all the commands seem to work I had to changespca5xx-20060301 for  spca5xx-20060402

The last command doesn't work.
I get
ubuntu@ubuntu:~/spca5xx-20060402$ sudo modprobe spca5xx
FATAL: Error inserting spca5xx (/lib/modules/2.6.15-19-386/kernel/drivers/usb/media/spca5xx.ko): Invalid module format

Any ideas?

---

### Post by isaric on 2006-04-05
I'm french but you look for this ?
[http://mxhaard.free.fr/spca50x/Download/]("http://mxhaard.free.fr/spca50x/Download/")

To make function my webcam (chust to try !), I use 
[spcaview]("http://isaric.cof.free.fr/spcaview.xhtml")

because aMSN, camorama and Ekiga do not go. :(

---

### Post by pataphysician on 2006-04-06
this howto workd for me previously, but on a new breezy install, the cameras fail. testing in vlc i get: "v4l demuxer error: chroma selection failed." i've noticed there seems to be a new version of the spca5xx drivers. spca5xx-20060402.tar.gz is the latest at time of posting, whereas the walkthru references spca5xx-20060301.tar.gz. using the 20060301 version instead of the latest worked for me. at the time of posting you can find the functioning drivers here:

[http://mxhaard.free.fr/spca50x/Download/oldrelease/spca5xx-20060301.tar.gz](http://mxhaard.free.fr/spca50x/Download/oldrelease/spca5xx-20060301.tar.gz)

---

### Post by pataphysician on 2006-04-06
[QUOTE=SamTheShaman]The last command doesn't work.
I get
ubuntu@ubuntu:~/spca5xx-20060402$ sudo modprobe spca5xx
FATAL: Error inserting spca5xx (/lib/modules/2.6.15-19-386/kernel/drivers/usb/media/spca5xx.ko): Invalid module format

Any ideas?[/QUOTE]

i got that error when i tried to install under hoary. you need to follow the OP's directions for hoary, instead. pretty much the same thing, except you toss a "make clean" in there somewhere. it's mentioned in this thread somewhere...

---

### Post by SamTheShaman on 2006-04-07
[QUOTE=arnieboy]this howto was **not** written for hoary, hence u shd not have followed it. anyway this is how to do it for **hoary** (i am not sure it will work but u can give it a try)
assuming u have the headers installed and the gzipped file downloaded, do the following:
```
cd spca5xx-20050906
make clean
make
sudo modprobe -r spca5xx
sudo rm -rf /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx*
sudo make install
sudo modprobe spca5xx
```

if u get any errors at any of the above steps paste it here.[/QUOTE]
Been trying and trying still no work.
Gone over this thread 3 times did 3 or 4 installs Breezy, Hoary you name it. She don't work.
I am using Dapper.
with canorama I get could not connect to video device(/dev/video0) Please check connection.
The web cam light flashes on my ezonics ezcamIII

---

### Post by SamTheShaman on 2006-04-07
[QUOTE=arnieboy]alright try this (ALL) from terminal:
```
sudo apt-get install gqcam
sudo ln -s /dev/video0 /dev/video
gqcam
```
if the cam runs fine, u are all set. If it doesnt please list the errors here.[/QUOTE]

Tried that one too.

ubuntu@ubuntu:~$ ls video
ls: video: No such file or directory
ubuntu@ubuntu:~$ ls /dev/video*
/dev/video  /dev/video0
ubuntu@ubuntu:~$ sudo apt-get install gqcam
Password:
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed
  gqcam
0 upgraded, 1 newly installed, 0 to remove and 101 not upgraded.
Need to get 37.9kB of archives.
After unpacking 160kB of additional disk space will be used.
Get: 1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe gqcam 0.9.1-3 [37.9kB]
Fetched 37.9kB in 1s (37.2kB/s)
Selecting previously deselected package gqcam.
(Reading database ... 90679 files and directories currently installed.)
Unpacking gqcam (from .../gqcam_0.9.1-3_i386.deb) ...
Setting up gqcam (0.9.1-3) ...

ubuntu@ubuntu:~$ sudo ln -s /dev/video0 /dev/video
ln: creating symbolic link `/dev/video' to `/dev/video0': File exists
ubuntu@ubuntu:~$ gqcam
ioctl (VIDIOCSPICT): Invalid argument
ioctl (VIDIOCSWIN): Invalid argument


Program starts up with a black screen

---

### Post by Doc on 2006-04-08
Works great, thanks!!!

---

### Post by RapidFirePT on 2006-04-11
Thanks, Arnad! My Creative WebCam NX Pro is working fine. 
We 've installed the latest driver from [http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html) , the spca5xx-20060402.tar.gz.
Here's the hardware specs:

root@dc:/home/dc# lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 041e:401e Creative Technology, Ltd WebCam NX Pro
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 045e:007d Microsoft Corp. Notebook Optical Mouse
Bus 001 Device 001: ID 0000:0000 

dmesg output:
[4296352.036000] Linux video capture interface: v1.00
[4296352.059000] /home/dc/spca5xx-20060402/drivers/usb/spca5xx.c: USB SPCA5XX ca mera found. Type Creative NX Pro Zc301+hv7131b
[4296352.059000] /home/dc/spca5xx-20060402/drivers/usb/spca5xx.c: [spca5xx_probe :8301] Camera type JPEG
[4296352.253000] /home/dc/spca5xx-20060402/drivers/usb/zc3xx.h: [zc3xx_config:46 4] Find Sensor HV7131B
[4296352.256000] /home/dc/spca5xx-20060402/drivers/usb/spca5xx.c: [spca5xx_getca pability:2198] maxw 640 maxh 480 minw 176 minh 144
[4296352.259000] usbcore: registered new driver spca5xx
[4296352.259000] /home/dc/spca5xx-20060402/drivers/usb/spca5xx.c: spca5xx driver  00.57.11 registered

We tested with the application GnomeMeeting  (Preferences > Video > PluginVideo V4L) . Snapshot attached (me and my colleague from Germany, on Erasmus in Instituto Superior Técnico-Portugal)...:D

---

### Post by Basheer on 2006-04-14
can someone please tell me where I am going wrong?

basheer@Qaaderiyah:~$ lsusb
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 004: ID 046d:08a6 Logitech, Inc.
Bus 001 Device 003: ID 04e8:326c Samsung Electronics Co., Ltd
Bus 001 Device 002: ID 046d:c506 Logitech, Inc. MX-700 Cordless Mouse Receiver
Bus 001 Device 001: ID 0000:0000
basheer@Qaaderiyah:~$ sudo apt-get install linux-headers-`uname -r` linux-restricted-modules-`uname -r` build-essential gcc-3.4
Reading package lists... Done
Building dependency tree... Done
linux-headers-2.6.12-10-686 is already the newest version.
linux-restricted-modules-2.6.12-10-686 is already the newest version.
build-essential is already the newest version.
gcc-3.4 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
basheer@Qaaderiyah:~$ wget [http://mxhaard.free.fr/spca50x/Download/oldrelease/spca5xx-20050906.tar.gz](http://mxhaard.free.fr/spca50x/Download/oldrelease/spca5xx-20050906.tar.gz)
--16:19:21--  [http://mxhaard.free.fr/spca50x/Download/oldrelease/spca5xx-20050906.tar.gz](http://mxhaard.free.fr/spca50x/Download/oldrelease/spca5xx-20050906.tar.gz)
           => `spca5xx-20050906.tar.gz'
Resolving mxhaard.free.fr... 212.27.63.122
Connecting to mxhaard.free.fr|212.27.63.122|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 179,010 (175K) [application/x-gzip]

100%[====================================>] 179,010      172.57K/s

16:19:23 (172.01 KB/s) - `spca5xx-20050906.tar.gz' saved [179010/179010]

basheer@Qaaderiyah:~$ tar xvfz spca5xx-20050906.tar.gz
spca5xx-20050906/
spca5xx-20050906/Makefile
spca5xx-20050906/RGB-YUV%2fmodule-setting
spca5xx-20050906/README
spca5xx-20050906/drivers/
spca5xx-20050906/drivers/usb/
spca5xx-20050906/drivers/usb/spcai2c_init.h
spca5xx-20050906/drivers/usb/spcagamma.h
spca5xx-20050906/drivers/usb/cx11646.h
spca5xx-20050906/drivers/usb/sn9cxxx.h
spca5xx-20050906/drivers/usb/cxlib.h
spca5xx-20050906/drivers/usb/zc3xx.h
spca5xx-20050906/drivers/usb/cs2102.h
spca5xx-20050906/drivers/usb/jpeg_qtables.h
spca5xx-20050906/drivers/usb/pas106b.h
spca5xx-20050906/drivers/usb/spca504_init.h
spca5xx-20050906/drivers/usb/spca506.h
spca5xx-20050906/drivers/usb/spca533.h
spca5xx-20050906/drivers/usb/spca536.h
spca5xx-20050906/drivers/usb/spca561.h
spca5xx-20050906/drivers/usb/mr97311.h
spca5xx-20050906/drivers/usb/sonix.h
spca5xx-20050906/drivers/usb/spca5xx.c
spca5xx-20050906/drivers/usb/spca5xx.h
spca5xx-20050906/drivers/usb/spcausb.h
spca5xx-20050906/drivers/usb/icm105a.h
spca5xx-20050906/drivers/usb/hv7131b.h
spca5xx-20050906/drivers/usb/hv7131c.h
spca5xx-20050906/drivers/usb/spca501_init.h
spca5xx-20050906/drivers/usb/pb0330.h
spca5xx-20050906/drivers/usb/et61xx51.h
spca5xx-20050906/drivers/usb/jpeg_header.h
spca5xx-20050906/drivers/usb/spca508_init.h
spca5xx-20050906/drivers/usb/spcaCompat.h
spca5xx-20050906/drivers/usb/dummy_cam.h
spca5xx-20050906/drivers/usb/spcadecoder.c
spca5xx-20050906/drivers/usb/spcadecoder.h
spca5xx-20050906/drivers/usb/tas5130c.h
spca5xx-20050906/drivers/usb/hdcs2020.h
spca5xx-20050906/drivers/usb/spca505_init.h
spca5xx-20050906/drivers/usb/spca500_init.h
spca5xx-20050906/drivers/usb/tv8532.h
spca5xx-20050906/CHANGELOG
spca5xx-20050906/README-TV8532
spca5xx-20050906/INSTALL
spca5xx-20050906/cutlog.py
basheer@Qaaderiyah:~$ cd spca5xx-20050906
basheer@Qaaderiyah:~/spca5xx-20050906$ sudo make CC=gcc-3.4
   Building SPCA5XX driver for 2.5/2.6 kernel.
   Remember: you must have read/write access to your kernel source tree.
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/basheer/spca5xx-20050906 CC=gcc-3.4 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-686'
  CC [M]  /home/basheer/spca5xx-20050906/drivers/usb/spca5xx.o
  CC [M]  /home/basheer/spca5xx-20050906/drivers/usb/spcadecoder.o
  LD [M]  /home/basheer/spca5xx-20050906/spca5xx.o
  Building modules, stage 2.
  MODPOST
  CC      /home/basheer/spca5xx-20050906/spca5xx.mod.o
  LD [M]  /home/basheer/spca5xx-20050906/spca5xx.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-686'
basheer@Qaaderiyah:~/spca5xx-20050906$ sudo modprobe -r spca5xx
basheer@Qaaderiyah:~/spca5xx-20050906$ sudo rm -rf /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx*
basheer@Qaaderiyah:~/spca5xx-20050906$ sudo make install
mkdir -p /lib/modules/`uname -r`/kernel/drivers/usb/media/
rm -f /lib/modules/`uname -r`/kernel/drivers/usb/media/spca50x.ko
rm -f /lib/modules/`uname -r`/kernel/drivers/usb/media/et61x.ko
install -c -m 0644 spca5xx.ko /lib/modules/`uname -r`/kernel/drivers/usb/media/
/sbin/depmod -ae
basheer@Qaaderiyah:~/spca5xx-20050906$ sudo modprobe spca5xx

---

### Post by arnieboy on 2006-04-14
do the modprobe again. everything has gone right. if ur webcam still doesnt work, its not supported by this driver.

---

### Post by Basheer on 2006-04-14
it doesnt make sense

it is on that support page

---

### Post by arnieboy on 2006-04-14
ok now I see what went wrong. u are using an archaic version of the driver. check the first post for an updated version.

---

### Post by polo_step on 2006-04-16
wget [http://mxhaard.free.fr/spca50x/Download/spca5xx-20060301.tar.gz](http://mxhaard.free.fr/spca50x/Download/spca5xx-20060301.tar.gz)

[FONT="Courier New"]Dang.  This gets a 404 error. 

Man, I'm having fun with dead links tonight, huh? 

](*,) 

Be cool if I got this "Gamestar" webcam up, though.  It does the usual thing of crashing GnomeMeeting.

Fry's had them this weekend for free after rebate so I bagged one.  Picture quality in XP is excellent.[/FONT]

---

### Post by polo_step on 2006-04-16
[FONT="Courier New"]Well, it's probably a good thing that the link was bad; I think Creative may use a different chip in this little camera.

[I'll try to use very Googleable phraseology here, so someone else's searching isn't as futile as mine was...]

What chip does the Creative Game Star webcam have?:

OK, I couldn't find anything on the Creative website or on Google, so I busted open my brand new webcam and looked.  Here's what it says on the main chip:

ZC0301 Plus
Vmc-48L-LF
TS0010A2790304

Anyone happen to know what this is?  I'm assuming it's not the ICM532. :rolleyes: 

[Later:] According to the page at: --

[http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html) 

-- this is a Z-Star device supported by the spca5xx/LE driver set.

[/FONT]

---

### Post by SVwanders on 2006-04-17
>Well, it's probably a good thing that the link was bad; I think Creative may use >a different chip in this little camera.

Add oldrelease/ . . . after download and you can get that file.

---

### Post by SVwanders on 2006-04-17
>What chip does the Creative Game Star webcam have?:

I have a Creative NX and once I installed as instructed but adding the different directory it works well. Hope you get yours working.

Tim

---

### Post by modemsutra on 2006-04-19
I installed the spca5xx latest driver but the quality of the image is poor as you can see in my profile pic I'm wondering if someone has a workaround for this or this is the most I can get from this web cam?:roll: 

Remember if you compile this driver you have to use the same version of GCC as your kernel otherwise it could not work properly=D>

---

### Post by erbedo on 2006-04-21
Hi all, and thank you arnieboy for your great work.

I have both an ibook G3 and a 32-bit PC, both with breezy. I've also a Logitech quickcam express that is fully supported with the spca5xx driver. So i've followed your howto on the ibook and it worked great! But on the 32-bit, doing all the same instructions, still don't work. It gives me, when i try to start for example gqcam:
bedo@harry:~$ gqcam -v /dev/video0
/dev/video0: No space left on device
bedo@harry:~$

and when i try to start camorama it gives me an error (in GUI) telling me to check /dev/video0.

Any ideas?

---

### Post by woland on 2006-04-25
I'm using Dapper and Chinese Z-star no-name P.O.S webcam. 
Used this guide with gcc-3.4 but ```
sudo modprobe spca5xx
``` returns error. With gcc-4.0 everything went without errors. In both cases /dev/video is not installed.
Any ideas what to? :-k

---

### Post by sreyan on 2006-04-25
The spca5xx-main.c file includes quite a few dirty references. I understand programmers freedoms (i'm not sure this should be patched except for ubuntu specifically and even then only if parents wanted it for their children) but perhaps this is "too human" for ubuntu.

The portion in question begins on line 1356

Although the code in question would be quite amusing on a t-shirt print.

---

### Post by chuko on 2006-04-28
First thing to say:

[http://mxhaard.free.fr/spca50x/Download/spca5xx-20060301.tar.gz](http://mxhaard.free.fr/spca50x/Download/spca5xx-20060301.tar.gz)

is broken, but you can try

[http://gd.tuwien.ac.at/opsys/linux/gentoo/distfiles/spca5xx-20060301.tar.gz](http://gd.tuwien.ac.at/opsys/linux/gentoo/distfiles/spca5xx-20060301.tar.gz)

instead.

Now, i've successfully managed to follow all the steps in this HOWTO but still my camera doesn't work, I've tried mercury, camorama, gqcam and gnomemeeting with no success.

Here is some info of what is happening to me:

stefan@pcchuko:/dev$ lsusb
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 06a5:d800 Divio Chicony TwinkleCam
Bus 001 Device 001: ID 0000:0000

stefan@pcchuko:/dev$ ls -l /dev/video*
lrwxrwxrwx  1 root root      11 2006-04-28 19:37 /dev/video -> /dev/video0
crw-rw-rw-  1 root video 81,  0 2006-04-28 19:27 /dev/video0
crw-rw----  1 root video 81,  1 2006-04-28 19:27 /dev/video1
crw-rw----  1 root video 81, 10 2006-04-28 19:27 /dev/video10
crw-rw----  1 root video 81, 11 2006-04-28 19:27 /dev/video11
crw-rw----  1 root video 81, 12 2006-04-28 19:27 /dev/video12
crw-rw----  1 root video 81, 13 2006-04-28 19:27 /dev/video13
crw-rw----  1 root video 81, 14 2006-04-28 19:27 /dev/video14
crw-rw----  1 root video 81, 15 2006-04-28 19:27 /dev/video15
crw-rw----  1 root video 81, 16 2006-04-28 19:27 /dev/video16
crw-rw----  1 root video 81, 17 2006-04-28 19:27 /dev/video17
crw-rw----  1 root video 81, 18 2006-04-28 19:27 /dev/video18
crw-rw----  1 root video 81, 19 2006-04-28 19:27 /dev/video19
crw-rw----  1 root video 81,  2 2006-04-28 19:27 /dev/video2
crw-rw----  1 root video 81, 20 2006-04-28 19:27 /dev/video20
crw-rw----  1 root video 81, 21 2006-04-28 19:27 /dev/video21
crw-rw----  1 root video 81, 22 2006-04-28 19:27 /dev/video22
crw-rw----  1 root video 81, 23 2006-04-28 19:27 /dev/video23
crw-rw----  1 root video 81, 24 2006-04-28 19:27 /dev/video24
crw-rw----  1 root video 81, 25 2006-04-28 19:27 /dev/video25
crw-rw----  1 root video 81, 26 2006-04-28 19:27 /dev/video26
crw-rw----  1 root video 81, 27 2006-04-28 19:27 /dev/video27
crw-rw----  1 root video 81, 28 2006-04-28 19:27 /dev/video28
crw-rw----  1 root video 81, 29 2006-04-28 19:27 /dev/video29
crw-rw----  1 root video 81,  3 2006-04-28 19:27 /dev/video3
crw-rw----  1 root video 81, 30 2006-04-28 19:27 /dev/video30
crw-rw----  1 root video 81, 31 2006-04-28 19:27 /dev/video31
crw-rw----  1 root video 81, 32 2006-04-28 19:27 /dev/video32
crw-rw----  1 root video 81, 33 2006-04-28 19:27 /dev/video33
crw-rw----  1 root video 81, 34 2006-04-28 19:27 /dev/video34
crw-rw----  1 root video 81, 35 2006-04-28 19:27 /dev/video35
crw-rw----  1 root video 81, 36 2006-04-28 19:27 /dev/video36
crw-rw----  1 root video 81, 37 2006-04-28 19:27 /dev/video37
crw-rw----  1 root video 81, 38 2006-04-28 19:27 /dev/video38
crw-rw----  1 root video 81, 39 2006-04-28 19:27 /dev/video39
crw-rw----  1 root video 81,  4 2006-04-28 19:27 /dev/video4
crw-rw----  1 root video 81, 40 2006-04-28 19:27 /dev/video40
crw-rw----  1 root video 81, 41 2006-04-28 19:27 /dev/video41
crw-rw----  1 root video 81, 42 2006-04-28 19:27 /dev/video42
crw-rw----  1 root video 81, 43 2006-04-28 19:27 /dev/video43
crw-rw----  1 root video 81, 44 2006-04-28 19:27 /dev/video44
crw-rw----  1 root video 81, 45 2006-04-28 19:27 /dev/video45
crw-rw----  1 root video 81, 46 2006-04-28 19:27 /dev/video46
crw-rw----  1 root video 81, 47 2006-04-28 19:27 /dev/video47
crw-rw----  1 root video 81, 48 2006-04-28 19:27 /dev/video48
crw-rw----  1 root video 81, 49 2006-04-28 19:27 /dev/video49
crw-rw----  1 root video 81,  5 2006-04-28 19:27 /dev/video5
crw-rw----  1 root video 81, 50 2006-04-28 19:27 /dev/video50
crw-rw----  1 root video 81, 51 2006-04-28 19:27 /dev/video51
crw-rw----  1 root video 81, 52 2006-04-28 19:27 /dev/video52
crw-rw----  1 root video 81, 53 2006-04-28 19:27 /dev/video53
crw-rw----  1 root video 81, 54 2006-04-28 19:27 /dev/video54
crw-rw----  1 root video 81, 55 2006-04-28 19:27 /dev/video55
crw-rw----  1 root video 81, 56 2006-04-28 19:27 /dev/video56
crw-rw----  1 root video 81, 57 2006-04-28 19:27 /dev/video57
crw-rw----  1 root video 81, 58 2006-04-28 19:27 /dev/video58
crw-rw----  1 root video 81, 59 2006-04-28 19:27 /dev/video59
crw-rw----  1 root video 81,  6 2006-04-28 19:27 /dev/video6
crw-rw----  1 root video 81, 60 2006-04-28 19:27 /dev/video60
crw-rw----  1 root video 81, 61 2006-04-28 19:27 /dev/video61
crw-rw----  1 root video 81, 62 2006-04-28 19:27 /dev/video62
crw-rw----  1 root video 81, 63 2006-04-28 19:27 /dev/video63
crw-rw----  1 root video 81,  7 2006-04-28 19:27 /dev/video7
crw-rw----  1 root video 81,  8 2006-04-28 19:27 /dev/video8
crw-rw----  1 root video 81,  9 2006-04-28 19:27 /dev/video9

stefan@pcchuko:/dev$ gqcam
/dev/video: No such device


Thanks for your help


EDIT: No idea why, but now when I type ls /dev/video* it says that such file doesn't exist (nodes are not created)

---

### Post by erbedo on 2006-05-01
Hi, tried another time on a fresh breezy_i386 install and still same problem. Follewd all the steps on Post #21, no errors given but when i launch camorama, gqcam or everithing else i got:
camorama: Could not connect to video device /dev/video0. Please check connection.
gqcam:
  bedo@harry:~$ gqcam -v /dev/video0
  /dev/video0: No space left on device
  bedo@harry:~$

No ideas what's wrong. Please help me :)

---

### Post by new2linux9 on 2006-05-05
This is the new location:

[http://mxhaard.free.fr/spca50x/Download/spca5xx-20060501.tar.gz]("http://mxhaard.free.fr/spca50x/Download/spca5xx-20060501.tar.gz")

Just change the line in red to:

wget [http://mxhaard.free.fr/spca50x/Download/spca5xx-20060501.tar.gz](http://mxhaard.free.fr/spca50x/Download/spca5xx-20060501.tar.gz)

and keep everything else exactly the same for it to work.

> sudo apt-get install linux-headers-`uname -r` linux-restricted-modules-`uname -r` build-essential gcc-3.4
[COLOR="Red"]wget [http://mxhaard.free.fr/spca50x/Download/spca5xx-20060301.tar.gz](http://mxhaard.free.fr/spca50x/Download/spca5xx-20060301.tar.gz)[/COLOR]
tar xvfz spca5xx-20060301.tar.gz
cd spca5xx-20060301
sudo make CC=gcc-3.4
sudo modprobe -r spca5xx
sudo rm -rf /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx*
sudo make install
sudo modprobe spca5xx

Well, it worked for me.

---

### Post by arnieboy on 2006-05-05
First post updated. thanks.

---

### Post by Robert A. Matthews on 2006-05-05
The fix sounds great - will it be incorporated into Dapper, so
it all "just works" ?

Robert

---

### Post by arnieboy on 2006-05-05
[QUOTE=Robert A. Matthews]The fix sounds great - will it be incorporated into Dapper, so
it all "just works" ?

Robert[/QUOTE]
yes ICM532 webcams already work by default on dapper.

---

### Post by new2linux9 on 2006-05-05
[QUOTE=arnieboy]First post updated. thanks.[/QUOTE]

You're more than welcome.  Thanks for "automatix", and your "How to's".  I'm an ex windows user who still doesn't have a clue about Linux.  Anything to make life easier.

---

### Post by erbedo on 2006-05-05
Still not working. Updated spca5xx driver, but acmorama and gqcam always give me an error such:
bedo@harry:/usr/src/spca5xx-20060501$ gqcam -v /dev/video0
/dev/video0: No space left on device
bedo@harry:/usr/src/spca5xx-20060501$

Any ideas? Could it be something strange in the BIOS?

---

### Post by dhruv_1884 on 2006-05-05
Arnie boy u r the best

regards
-
dc

---

### Post by Sponge34 on 2006-05-05
Hi,
just installed the latest kernel updates and recompiled the ICM drivers having downloaded the new versions (no errors at all and the cam worked ok with the old drivers and kernel) - now the cam only refreshes the top half of the picture, after the first frame.
weirdness indeed.
I haven't yet rebooted, but that is a windoze reflex.
Any ideas?
*edit: well the reboot made it worse until I unplugged the cam and re connected it, but it is still very flakey*
TIA
S.

---

### Post by mozzi on 2006-05-07
Thanx this worked :-D

---

### Post by DooDle on 2006-05-07
It works for me too!!!
You made me save a lot of time!!!
Thanks a lot. :D

---

### Post by GQed76 on 2006-05-07
FATAL: Error inserting spca5xx (/lib/modules/2.6.16-ck3/kernel/drivers/usb/media/spca5xx.ko): Invalid module format


:(

---

### Post by arnieboy on 2006-05-07
[QUOTE=GQed76]FATAL: Error inserting spca5xx (/lib/modules/2.6.16-ck3/kernel/drivers/usb/media/spca5xx.ko): Invalid module format


:([/QUOTE]
u are using a custom made kernel (possibly compiled with gcc 4.0)
you should not compile the spca5xx modules with gcc-3.4
thats why its throwing up the error.

---

### Post by GQed76 on 2006-05-07
DUUUH

thanks :)

---

### Post by Smittey on 2006-05-08
I get kind of the same error: FATAL: Error inserting spca5xx (/lib/modules/2.6.15-22-386/kernel/drivers/usb/media/spca5xx.ko): Invalid module format

What should I do? Compile with 4.0?

---

### Post by arnieboy on 2006-05-08
[QUOTE=Smittey]I get kind of the same error: FATAL: Error inserting spca5xx (/lib/modules/2.6.15-22-386/kernel/drivers/usb/media/spca5xx.ko): Invalid module format

What should I do? Compile with 4.0?[/QUOTE]
yes

---

### Post by Smittey on 2006-05-09
I did, it gave no error but the camera (a Intel CS120) is still not reckognized :( In fact, the Logitech Sphere that I also have and which worked in Camarera (but no other application) now isn't reckognized by Camarera either (dev/video0 is now not accessible) How do I get the thing uninstalled? :$

---

### Post by gabbar_singh on 2006-05-11
hey!!!
I did exactly what the code said. No error what so ever throughtout the process. But no device found in gnome-meeting or camorama or gqcam.. 
error is:
"/dev/video: No such file or directory"
there is no /dev/video or /dev/video0
I also tried installing the older versions.. still doesnt work.. 
webcam make is Chicony Twinklecam DC-2110... while going through this thread.. i saw people being also to install it successfully.. 
I am on amd64-generic platform.. is it supported???
Any inputs.. 
-gabbar
EDIT: when I do "lsmod" I see spca5xxx module loaded but not used by any...... there was another module "videodev" which was used by "spca5xxx".. if this helps

---

### Post by EdThaSlayer on 2006-05-13
Thanks for the information. Now i can use my webcam to chat with people!
ur a...webcam saver!(now its actually worth something)

---

### Post by SmokinJuan on 2006-05-13
arnieboy, your patience is commendable and your instructions worked wonders on my system.  gqcam and canorama no longer hang the system, but the video is black.  If I turn the brightness up the video is maroon.  No errors are reported.  The lense cap is off.  /dev/video0 exists.  My cam is in the list of supported.
lsusb provides:

smokinjuan@compaq:~$ lsusb
Bus 001 Device 002: ID 0733:0401 ViewQuest Technologies, Inc. CS330 WebCam
Bus 001 Device 001: ID 0000:0000

I'm too close to give up now!

---

### Post by arnieboy on 2006-05-13
[QUOTE=SmokinJuan]arnieboy, your patience is commendable and your instructions worked wonders on my system.  gqcam and canorama no longer hang the system, but the video is black.  If I turn the brightness up the video is maroon.  No errors are reported.  The lense cap is off.  /dev/video0 exists.  My cam is in the list of supported.
lsusb provides:

smokinjuan@compaq:~$ lsusb
Bus 001 Device 002: ID 0733:0401 ViewQuest Technologies, Inc. CS330 WebCam
Bus 001 Device 001: ID 0000:0000

I'm too close to give up now![/QUOTE]
whatever picture quality you are getting is the best possible right now with the spca5xx drivers.. what you must understand is that these drivers are based on a lot of reverse-engineered stuff.. webcam manufacturers will not release their hardware specs to us and hence driver writers have to keep "guessing" and reverse engineering these drivers.
For the time being, some webcams (read some models of logitech) are better supported than others.. we have to live with that till something better happens.

---

### Post by AlvaroBF on 2006-05-14
I can't get my Creative Webcam NX Pro working, I'm Using Dapper AMD64

alvaro@ubuntu:~$ uname -r
2.6.15-22-amd64-k8

  alvaro@ubuntu:~$ lsusb
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 007: ID 041e:401e Creative Technology, Ltd WebCam NX 

alvaro@ubuntu:~$ lsmod
Module                  Size  Used by
spca5xx               666236  0
videodev               13056  1 spca5xx

alvaro@ubuntu:~$ gqcam
/dev/video: No space left on device

alvaro@ubuntu:~$ webcam
reading config file: /home/alvaro/.webcamrc
v4l2: open /dev/video0: No space left on device
v4l2: open /dev/video0: No space left on device
v4l: open /dev/video0: No space left on device
no grabber device available




Anyone knows the reason?

---

### Post by dolny on 2006-05-14
delete this post.

---

### Post by chuko on 2006-05-14
[QUOTE=gabbar_singh]hey!!!
I did exactly what the code said. No error what so ever throughtout the process. But no device found in gnome-meeting or camorama or gqcam.. 
error is:
"/dev/video: No such file or directory"
there is no /dev/video or /dev/video0
I also tried installing the older versions.. still doesnt work.. 
webcam make is Chicony Twinklecam DC-2110... while going through this thread.. i saw people being also to install it successfully.. 
I am on amd64-generic platform.. is it supported???
Any inputs.. 
-gabbar
EDIT: when I do "lsmod" I see spca5xxx module loaded but not used by any...... there was another module "videodev" which was used by "spca5xxx".. if this helps[/QUOTE]


Same camera and problem here!!!! (in an i386)
I've already posted before, but no reply ](*,)

---

### Post by arnieboy on 2006-05-15
gabbar_singh and chuko:
Chicony Twinklecam is not supported by the spca5xx driver (It's based on the sonix chipset) . You need a different driver for that called "sn9c102"
for v4l2, check the following site out:
[http://www.linux-projects.org/modules/mydownloads/viewcat.php?cid=2](http://www.linux-projects.org/modules/mydownloads/viewcat.php?cid=2)
for v4l1 check out the following:
[http://sonix.sourceforge.net/](http://sonix.sourceforge.net/)
Hope this helps.

---

### Post by medication on 2006-05-15
Thanks!  This 'HowTo' worked great for me. Just for anyone else using the same or similar setup here's my information: 
AMD64 3200+
Breezy 64
Logitech QuickCam Communicate STX

Thanks again, this was completely painless...

---

### Post by Geoneil on 2006-05-15
Cheers Arnie - that even sorted out the "invalid module" error from the [other](http://ubuntuforums.org/showpost.php?p=383244&postcount=21)thread. Now just some cam-specific problems to sort...

---

### Post by berserker on 2006-05-15
This may help out some people who receive errors when trying to access their webcams:

1.  Mine didn't work while plugged into the USB port of my Dell monitor.  I had to plug it directly into my USB card.

2.  Video in Gnomemeeting wouldn't work under V4L2.  I had to select V4L.

3.  Video in Gnomemeeting wouldn't work under Channel 1.  I had to select Channel 0.

Hope this helps out some who struggled (like I did) to enable a webcam in Ubuntu.

---

### Post by erbedo on 2006-05-16
Any ideas for my problem?

bedo@harry:~/universita/programmazione$ gqcam -v /dev/video0
/dev/video0: No space left on device
bedo@harry:~/universita/programmazione$

And problems also with camorama and xawtv...

---

### Post by arnieboy on 2006-05-16
[QUOTE=erbedo]Any ideas for my problem?

bedo@harry:~/universita/programmazione$ gqcam -v /dev/video0
/dev/video0: No space left on device
bedo@harry:~/universita/programmazione$

And problems also with camorama and xawtv...[/QUOTE]
whats the make and model of your webcam?

---

### Post by jackb on 2006-05-17
hello. I have logitech communicate STX and I have the same problem. when I gave:

[jacek@pldmachine~]$ sudo gqcam --video /dev/video0 
/dev/video: No space left on device

BTW I'm from poland and I have PLD-linux (pld-linux.org), with 2.6.14.7-4 kernel

apologize for my english

---

### Post by AlvaroBF on 2006-05-20
Same problem here with a Webcam NX PRO ( Creative )

---

### Post by jackb on 2006-05-20
I have solved problem with my webcam. I must directly connect my webcam  for my PC. but I have my pc behind wall. On saparate room,  so I can't  connect my webcam for my PC,  when I connect webcam to usb hub with keyboard and mouse  it's don't work, but when i connect webcam to usb hub and keybord and mouse for other usb hub,  everything it works ,  but usb hub for webcam must have extra power supply.

apologize for my engish

---

### Post by dolny on 2006-05-27
Thanks for this howto.

---

### Post by erbedo on 2006-05-28
[QUOTE=arnieboy]whats the make and model of your webcam?[/QUOTE]

I've a logitech quickcam express. It works fine on another i386 machine with same step followed for compiling the driver. It's directly connected to the PC, no hub beetween..
Bye

---

### Post by bennett on 2006-05-28
I have been trying to get my Logitech Quickcam for Notebooks Deluxe (which I *believe* uses the ICM532 chipset but it seems hard to know for sure) working with Breezy, on a Dell Inspiron 1300. I have tried a number of approaches & drivers etc. with no luck <frustrated sigh>. 

I followed the directions above but when I try to make CC=gcc-3.4, I am told in no uncertain terms:
make: *** No targets specified and no makefile found.  Stop.

Can anyone out there tell me: NOW WHAT???!!!

---

### Post by Yoric on 2006-06-09
My problem is slightly different from what's described at the beginning of this thread.

My configuration:
[LIST]
[*] Dapper Drake
[*] QuickCam Messenger, with usb_device.product_id 2288 (0x8f0)
[*] Kernel 2.6.15-23-686 #1 SMP PREEMPT
[*] Module quickcam, installed by easycam2.
[/LIST]

The webcam works fine with camorama. However, a single press on its button causes an immediate kernel panic, even from the console and without launching camorama. 

I'd like to avoid patching my kernel modules with the wrong fix for my problem. Would your howto help ?

---

### Post by Yoric on 2006-06-09
[QUOTE=bennett]I followed the directions above but when I try to make CC=gcc-3.4, I am told in no uncertain terms:
make: *** No targets specified and no makefile found.  Stop.

Can anyone out there tell me: NOW WHAT???!!![/QUOTE]

Best guess: are you in the correct directory when you launch compilation ?

---

### Post by arnieboy on 2006-06-09
[QUOTE=Yoric]My problem is slightly different from what's described at the beginning of this thread.

My configuration:
[LIST]
[*] Dapper Drake
[*] QuickCam Messenger, with usb_device.product_id 2288 (0x8f0)
[*] Kernel 2.6.15-23-686 #1 SMP PREEMPT
[*] Module quickcam, installed by easycam2.
[/LIST]

The webcam works fine with camorama. However, a single press on its button causes an immediate kernel panic, even from the console and without launching camorama. 

I'd like to avoid patching my kernel modules with the wrong fix for my problem. Would your howto help ?[/QUOTE]
yes.

---

### Post by dave.goodfellow on 2006-06-11
I'd appreciate your help please Arnieboy.
I get an error on the last terminal command you give.
Here's a paste of my terminal
dave@dave-ubuntu:~/Desktop/spca5xx-20060501$ sudo apt-get install linux-headers- `uname -r` linux-restricted-modules-`uname -r` build-essential gcc-3.4
Reading package lists... Done
Building dependency tree... Done
linux-restricted-modules-2.6.15-23-686 is already the newest version.
build-essential is already the newest version.
The following extra packages will be installed:
  cpp-3.4 gcc-3.4-base linux-headers-2.6.15-23
Suggested packages:
  gcc-3.4-doc libc6-dev-amd64 lib64gcc1
The following NEW packages will be installed
  cpp-3.4 gcc-3.4 gcc-3.4-base linux-headers-2.6.15-23
  linux-headers-2.6.15-23-686
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 10.1MB of archives.
After unpacking 88.2MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main gcc-3.4-base 3.4.6-1ubuntu2 [164kB]
Get: 2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main cpp-3.4 3.4.6-1ubuntu2 [1687kB]
Get: 3 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main gcc-3.4 3.4.6-1ubuntu2 [494kB]
Get: 4 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main linux-headers-2.6.15-23 2.6.15-23.3 9 [6895kB]
Get: 5 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main linux-headers-2.6.15-23-686 2.6.15- 23.39 [852kB]
Fetched 10.1MB in 43s (231kB/s)
Selecting previously deselected package gcc-3.4-base.
(Reading database ... 93158 files and directories currently installed.)
Unpacking gcc-3.4-base (from .../gcc-3.4-base_3.4.6-1ubuntu2_i386.deb) ...
Selecting previously deselected package cpp-3.4.
Unpacking cpp-3.4 (from .../cpp-3.4_3.4.6-1ubuntu2_i386.deb) ...
Selecting previously deselected package gcc-3.4.
Unpacking gcc-3.4 (from .../gcc-3.4_3.4.6-1ubuntu2_i386.deb) ...
Selecting previously deselected package linux-headers-2.6.15-23.
Unpacking linux-headers-2.6.15-23 (from .../linux-headers-2.6.15-23_2.6.15-23.39 _i386.deb) ...
Selecting previously deselected package linux-headers-2.6.15-23-686.
Unpacking linux-headers-2.6.15-23-686 (from .../linux-headers-2.6.15-23-686_2.6. 15-23.39_i386.deb) ...
Setting up gcc-3.4-base (3.4.6-1ubuntu2) ...
Setting up cpp-3.4 (3.4.6-1ubuntu2) ...
Setting up gcc-3.4 (3.4.6-1ubuntu2) ...
Setting up linux-headers-2.6.15-23 (2.6.15-23.39) ...

Setting up linux-headers-2.6.15-23-686 (2.6.15-23.39) ...
dave@dave-ubuntu:~/Desktop/spca5xx-20060501$ wget [http://mxhaard.free.fr/spca50x](http://mxhaard.free.fr/spca50x) /Download/spca5xx-20060501.tar.gz
--18:24:09--  [http://mxhaard.free.fr/spca50x/Download/spca5xx-20060501.tar.gz](http://mxhaard.free.fr/spca50x/Download/spca5xx-20060501.tar.gz)
           => `spca5xx-20060501.tar.gz'
Resolving mxhaard.free.fr... 212.27.63.122
Connecting to mxhaard.free.fr|212.27.63.122|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 192,817 (188K) [application/x-gzip]

100%[====================================>] 192,817      208.20K/s

18:24:10 (207.88 KB/s) - `spca5xx-20060501.tar.gz' saved [192817/192817]

dave@dave-ubuntu:~/Desktop/spca5xx-20060501$ tar xvfz spca5xx-20060501.tar.gz
spca5xx-20060501/
spca5xx-20060501/README-KERNEL-UPTO-2.6.16
spca5xx-20060501/Makefile
spca5xx-20060501/LICENSE
spca5xx-20060501/RGB-YUV%2fmodule-setting
spca5xx-20060501/README
spca5xx-20060501/drivers/
spca5xx-20060501/drivers/usb/
spca5xx-20060501/drivers/usb/spca500.dat
spca5xx-20060501/drivers/usb/spca501.dat
spca5xx-20060501/drivers/usb/spca505.dat
spca5xx-20060501/drivers/usb/spca508.dat
spca5xx-20060501/drivers/usb/spcagamma.h
spca5xx-20060501/drivers/usb/cx11646.h
spca5xx-20060501/drivers/usb/sn9cxxx.h
spca5xx-20060501/drivers/usb/pac207.h
spca5xx-20060501/drivers/usb/cxlib.h
spca5xx-20060501/drivers/usb/zc3xx.h
spca5xx-20060501/drivers/usb/cs2102.h
spca5xx-20060501/drivers/usb/jpeg_qtables.h
spca5xx-20060501/drivers/usb/pas106b.h
spca5xx-20060501/drivers/usb/spca506.h
spca5xx-20060501/drivers/usb/spca561.h
spca5xx-20060501/drivers/usb/mr97311.h
spca5xx-20060501/drivers/usb/sonix.h
spca5xx-20060501/drivers/usb/spca5xx.c
spca5xx-20060501/drivers/usb/spca5xx.h
spca5xx-20060501/drivers/usb/spcausb.h
spca5xx-20060501/drivers/usb/icm105a.h
spca5xx-20060501/drivers/usb/hv7131b.h
spca5xx-20060501/drivers/usb/hv7131c.h
spca5xx-20060501/drivers/usb/spca501_init.h
spca5xx-20060501/drivers/usb/pb0330.h
spca5xx-20060501/drivers/usb/ov7630c.h
spca5xx-20060501/drivers/usb/et61xx51.h
spca5xx-20060501/drivers/usb/sp5xxfw2.h
spca5xx-20060501/drivers/usb/jpeg_header.h
spca5xx-20060501/drivers/usb/spca508_init.h
spca5xx-20060501/drivers/usb/spcaCompat.h
spca5xx-20060501/drivers/usb/dummy_cam.h
spca5xx-20060501/drivers/usb/spcadecoder.c
spca5xx-20060501/drivers/usb/spcadecoder.h
spca5xx-20060501/drivers/usb/tas5130c.h
spca5xx-20060501/drivers/usb/sp5xxfw2.dat
spca5xx-20060501/drivers/usb/hdcs2020.h
spca5xx-20060501/drivers/usb/spca505_init.h
spca5xx-20060501/drivers/usb/spca500_init.h
spca5xx-20060501/drivers/usb/tv8532.h
spca5xx-20060501/CHANGELOG
tar: spca5xx-20060501/drivers: implausibly old time stamp 1970-01-01 01:00:00
spca5xx-20060501/README-SONIX
spca5xx-20060501/README-TV8532
spca5xx-20060501/INSTALL
spca5xx-20060501/cutlog.py
dave@dave-ubuntu:~/Desktop/spca5xx-20060501$ cd spca5xx-20060501
dave@dave-ubuntu:~/Desktop/spca5xx-20060501/spca5xx-20060501$ sudo make CC=gcc-3 .4
   Building SPCA5XX driver for 2.5/2.6 kernel.
   Remember: you must have read/write access to your kernel source tree.
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/dave/Desktop/spca5xx-2006050 1/spca5xx-20060501 CC=gcc-3.4 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-23-686'
  CC [M]  /home/dave/Desktop/spca5xx-20060501/spca5xx-20060501/drivers/usb/spca5 xx.o
  CC [M]  /home/dave/Desktop/spca5xx-20060501/spca5xx-20060501/drivers/usb/spcad ecoder.o
  LD [M]  /home/dave/Desktop/spca5xx-20060501/spca5xx-20060501/spca5xx.o
  Building modules, stage 2.
  MODPOST
  CC      /home/dave/Desktop/spca5xx-20060501/spca5xx-20060501/spca5xx.mod.o
  LD [M]  /home/dave/Desktop/spca5xx-20060501/spca5xx-20060501/spca5xx.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-23-686'
dave@dave-ubuntu:~/Desktop/spca5xx-20060501/spca5xx-20060501$ sudo modprobe -r s pca5xx
dave@dave-ubuntu:~/Desktop/spca5xx-20060501/spca5xx-20060501$ sudo rm -rf /lib/m odules/`uname -r`/kernel/drivers/usb/media/spca5xx*
dave@dave-ubuntu:~/Desktop/spca5xx-20060501/spca5xx-20060501$ sudo make install
mkdir -p /lib/modules/`uname -r`/kernel/drivers/usb/media/
rm -f /lib/modules/`uname -r`/kernel/drivers/usb/media/spca50x.ko
rm -f /lib/modules/`uname -r`/kernel/drivers/usb/media/et61x.ko
install -c -m 0644 spca5xx.ko /lib/modules/`uname -r`/kernel/drivers/usb/media/
/sbin/depmod -ae
dave@dave-ubuntu:~/Desktop/spca5xx-20060501/spca5xx-20060501$ sudo modprobe spca 5xx
FATAL: Error inserting spca5xx (/lib/modules/2.6.15-23-686/kernel/drivers/usb/me dia/spca5xx.ko): Invalid module format
dave@dave-ubuntu:~/Desktop/spca5xx-20060501/spca5xx-20060501$ sudo modprobe spca 5xx
FATAL: Error inserting spca5xx (/lib/modules/2.6.15-23-686/kernel/drivers/usb/me dia/spca5xx.ko): Invalid module format
dave@dave-ubuntu:~/Desktop/spca5xx-20060501/spca5xx-20060501$

My webcam is creative live and I'm running dapper drake.
Any help appreciated
Cheers Dave.

---

### Post by arnieboy on 2006-06-11
[QUOTE=dave.goodfellow]I'd appreciate your help please Arnieboy.
I get an error on the last terminal command you give.
Here's a paste of my terminal
dave@dave-ubuntu:~/Desktop/spca5xx-20060501$ sudo apt-get install linux-headers- `uname -r` linux-restricted-modules-`uname -r` build-essential gcc-3.4
Reading package lists... Done
Building dependency tree... Done
linux-restricted-modules-2.6.15-23-686 is already the newest version.
build-essential is already the newest version.
The following extra packages will be installed:
  cpp-3.4 gcc-3.4-base linux-headers-2.6.15-23
Suggested packages:
  gcc-3.4-doc libc6-dev-amd64 lib64gcc1
The following NEW packages will be installed
  cpp-3.4 gcc-3.4 gcc-3.4-base linux-headers-2.6.15-23
  linux-headers-2.6.15-23-686
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 10.1MB of archives.
After unpacking 88.2MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main gcc-3.4-base 3.4.6-1ubuntu2 [164kB]
Get: 2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main cpp-3.4 3.4.6-1ubuntu2 [1687kB]
Get: 3 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main gcc-3.4 3.4.6-1ubuntu2 [494kB]
Get: 4 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main linux-headers-2.6.15-23 2.6.15-23.3 9 [6895kB]
Get: 5 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main linux-headers-2.6.15-23-686 2.6.15- 23.39 [852kB]
Fetched 10.1MB in 43s (231kB/s)
Selecting previously deselected package gcc-3.4-base.
(Reading database ... 93158 files and directories currently installed.)
Unpacking gcc-3.4-base (from .../gcc-3.4-base_3.4.6-1ubuntu2_i386.deb) ...
Selecting previously deselected package cpp-3.4.
Unpacking cpp-3.4 (from .../cpp-3.4_3.4.6-1ubuntu2_i386.deb) ...
Selecting previously deselected package gcc-3.4.
Unpacking gcc-3.4 (from .../gcc-3.4_3.4.6-1ubuntu2_i386.deb) ...
Selecting previously deselected package linux-headers-2.6.15-23.
Unpacking linux-headers-2.6.15-23 (from .../linux-headers-2.6.15-23_2.6.15-23.39 _i386.deb) ...
Selecting previously deselected package linux-headers-2.6.15-23-686.
Unpacking linux-headers-2.6.15-23-686 (from .../linux-headers-2.6.15-23-686_2.6. 15-23.39_i386.deb) ...
Setting up gcc-3.4-base (3.4.6-1ubuntu2) ...
Setting up cpp-3.4 (3.4.6-1ubuntu2) ...
Setting up gcc-3.4 (3.4.6-1ubuntu2) ...
Setting up linux-headers-2.6.15-23 (2.6.15-23.39) ...

Setting up linux-headers-2.6.15-23-686 (2.6.15-23.39) ...
dave@dave-ubuntu:~/Desktop/spca5xx-20060501$ wget [http://mxhaard.free.fr/spca50x](http://mxhaard.free.fr/spca50x) /Download/spca5xx-20060501.tar.gz
--18:24:09--  [http://mxhaard.free.fr/spca50x/Download/spca5xx-20060501.tar.gz](http://mxhaard.free.fr/spca50x/Download/spca5xx-20060501.tar.gz)
           => `spca5xx-20060501.tar.gz'
Resolving mxhaard.free.fr... 212.27.63.122
Connecting to mxhaard.free.fr|212.27.63.122|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 192,817 (188K) [application/x-gzip]

100%[====================================>] 192,817      208.20K/s

18:24:10 (207.88 KB/s) - `spca5xx-20060501.tar.gz' saved [192817/192817]

dave@dave-ubuntu:~/Desktop/spca5xx-20060501$ tar xvfz spca5xx-20060501.tar.gz
spca5xx-20060501/
spca5xx-20060501/README-KERNEL-UPTO-2.6.16
spca5xx-20060501/Makefile
spca5xx-20060501/LICENSE
spca5xx-20060501/RGB-YUV%2fmodule-setting
spca5xx-20060501/README
spca5xx-20060501/drivers/
spca5xx-20060501/drivers/usb/
spca5xx-20060501/drivers/usb/spca500.dat
spca5xx-20060501/drivers/usb/spca501.dat
spca5xx-20060501/drivers/usb/spca505.dat
spca5xx-20060501/drivers/usb/spca508.dat
spca5xx-20060501/drivers/usb/spcagamma.h
spca5xx-20060501/drivers/usb/cx11646.h
spca5xx-20060501/drivers/usb/sn9cxxx.h
spca5xx-20060501/drivers/usb/pac207.h
spca5xx-20060501/drivers/usb/cxlib.h
spca5xx-20060501/drivers/usb/zc3xx.h
spca5xx-20060501/drivers/usb/cs2102.h
spca5xx-20060501/drivers/usb/jpeg_qtables.h
spca5xx-20060501/drivers/usb/pas106b.h
spca5xx-20060501/drivers/usb/spca506.h
spca5xx-20060501/drivers/usb/spca561.h
spca5xx-20060501/drivers/usb/mr97311.h
spca5xx-20060501/drivers/usb/sonix.h
spca5xx-20060501/drivers/usb/spca5xx.c
spca5xx-20060501/drivers/usb/spca5xx.h
spca5xx-20060501/drivers/usb/spcausb.h
spca5xx-20060501/drivers/usb/icm105a.h
spca5xx-20060501/drivers/usb/hv7131b.h
spca5xx-20060501/drivers/usb/hv7131c.h
spca5xx-20060501/drivers/usb/spca501_init.h
spca5xx-20060501/drivers/usb/pb0330.h
spca5xx-20060501/drivers/usb/ov7630c.h
spca5xx-20060501/drivers/usb/et61xx51.h
spca5xx-20060501/drivers/usb/sp5xxfw2.h
spca5xx-20060501/drivers/usb/jpeg_header.h
spca5xx-20060501/drivers/usb/spca508_init.h
spca5xx-20060501/drivers/usb/spcaCompat.h
spca5xx-20060501/drivers/usb/dummy_cam.h
spca5xx-20060501/drivers/usb/spcadecoder.c
spca5xx-20060501/drivers/usb/spcadecoder.h
spca5xx-20060501/drivers/usb/tas5130c.h
spca5xx-20060501/drivers/usb/sp5xxfw2.dat
spca5xx-20060501/drivers/usb/hdcs2020.h
spca5xx-20060501/drivers/usb/spca505_init.h
spca5xx-20060501/drivers/usb/spca500_init.h
spca5xx-20060501/drivers/usb/tv8532.h
spca5xx-20060501/CHANGELOG
tar: spca5xx-20060501/drivers: implausibly old time stamp 1970-01-01 01:00:00
spca5xx-20060501/README-SONIX
spca5xx-20060501/README-TV8532
spca5xx-20060501/INSTALL
spca5xx-20060501/cutlog.py
dave@dave-ubuntu:~/Desktop/spca5xx-20060501$ cd spca5xx-20060501
dave@dave-ubuntu:~/Desktop/spca5xx-20060501/spca5xx-20060501$ sudo make CC=gcc-3 .4
   Building SPCA5XX driver for 2.5/2.6 kernel.
   Remember: you must have read/write access to your kernel source tree.
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/dave/Desktop/spca5xx-2006050 1/spca5xx-20060501 CC=gcc-3.4 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-23-686'
  CC [M]  /home/dave/Desktop/spca5xx-20060501/spca5xx-20060501/drivers/usb/spca5 xx.o
  CC [M]  /home/dave/Desktop/spca5xx-20060501/spca5xx-20060501/drivers/usb/spcad ecoder.o
  LD [M]  /home/dave/Desktop/spca5xx-20060501/spca5xx-20060501/spca5xx.o
  Building modules, stage 2.
  MODPOST
  CC      /home/dave/Desktop/spca5xx-20060501/spca5xx-20060501/spca5xx.mod.o
  LD [M]  /home/dave/Desktop/spca5xx-20060501/spca5xx-20060501/spca5xx.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-23-686'
dave@dave-ubuntu:~/Desktop/spca5xx-20060501/spca5xx-20060501$ sudo modprobe -r s pca5xx
dave@dave-ubuntu:~/Desktop/spca5xx-20060501/spca5xx-20060501$ sudo rm -rf /lib/m odules/`uname -r`/kernel/drivers/usb/media/spca5xx*
dave@dave-ubuntu:~/Desktop/spca5xx-20060501/spca5xx-20060501$ sudo make install
mkdir -p /lib/modules/`uname -r`/kernel/drivers/usb/media/
rm -f /lib/modules/`uname -r`/kernel/drivers/usb/media/spca50x.ko
rm -f /lib/modules/`uname -r`/kernel/drivers/usb/media/et61x.ko
install -c -m 0644 spca5xx.ko /lib/modules/`uname -r`/kernel/drivers/usb/media/
/sbin/depmod -ae
dave@dave-ubuntu:~/Desktop/spca5xx-20060501/spca5xx-20060501$ sudo modprobe spca 5xx
FATAL: Error inserting spca5xx (/lib/modules/2.6.15-23-686/kernel/drivers/usb/me dia/spca5xx.ko): Invalid module format
dave@dave-ubuntu:~/Desktop/spca5xx-20060501/spca5xx-20060501$ sudo modprobe spca 5xx
FATAL: Error inserting spca5xx (/lib/modules/2.6.15-23-686/kernel/drivers/usb/me dia/spca5xx.ko): Invalid module format
dave@dave-ubuntu:~/Desktop/spca5xx-20060501/spca5xx-20060501$

My webcam is creative live and I'm running dapper drake.
Any help appreciated
Cheers Dave.[/QUOTE]
The howto is for Breezy (not Dapper). The spca5xx modules work fine on Dapper by default.
However, if you still want to compile the modules try the following from the directory in which the make file exists:
```
sudo make clean
sudo make
sudo modprobe -r spca5xx
sudo rm -rf /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx*
sudo make install
sudo modprobe spca5xx
```

and let me know how it goes.

---

### Post by dave.goodfellow on 2006-06-11
Thanks for getting back, that was really quick.
Here's my terminal:
dave@dave-ubuntu:~$ wget [http://mxhaard.free.fr/spca50x/Download/spca5xx-20060501.tar.gz](http://mxhaard.free.fr/spca50x/Download/spca5xx-20060501.tar.gz)
--19:00:35--  [http://mxhaard.free.fr/spca50x/Download/spca5xx-20060501.tar.gz](http://mxhaard.free.fr/spca50x/Download/spca5xx-20060501.tar.gz)
           => `spca5xx-20060501.tar.gz'
Resolving mxhaard.free.fr... 212.27.63.122
Connecting to mxhaard.free.fr|212.27.63.122|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 192,817 (188K) [application/x-gzip]

100%[====================================>] 192,817      188.95K/s

19:00:36 (188.39 KB/s) - `spca5xx-20060501.tar.gz' saved [192817/192817]

dave@dave-ubuntu:~$ tar xvfz spca5xx-20060501.tar.gz
spca5xx-20060501/
spca5xx-20060501/README-KERNEL-UPTO-2.6.16
spca5xx-20060501/Makefile
spca5xx-20060501/LICENSE
spca5xx-20060501/RGB-YUV%2fmodule-setting
spca5xx-20060501/README
spca5xx-20060501/drivers/
spca5xx-20060501/drivers/usb/
spca5xx-20060501/drivers/usb/spca500.dat
spca5xx-20060501/drivers/usb/spca501.dat
spca5xx-20060501/drivers/usb/spca505.dat
spca5xx-20060501/drivers/usb/spca508.dat
spca5xx-20060501/drivers/usb/spcagamma.h
spca5xx-20060501/drivers/usb/cx11646.h
spca5xx-20060501/drivers/usb/sn9cxxx.h
spca5xx-20060501/drivers/usb/pac207.h
spca5xx-20060501/drivers/usb/cxlib.h
spca5xx-20060501/drivers/usb/zc3xx.h
spca5xx-20060501/drivers/usb/cs2102.h
spca5xx-20060501/drivers/usb/jpeg_qtables.h
spca5xx-20060501/drivers/usb/pas106b.h
spca5xx-20060501/drivers/usb/spca506.h
spca5xx-20060501/drivers/usb/spca561.h
spca5xx-20060501/drivers/usb/mr97311.h
spca5xx-20060501/drivers/usb/sonix.h
spca5xx-20060501/drivers/usb/spca5xx.c
spca5xx-20060501/drivers/usb/spca5xx.h
spca5xx-20060501/drivers/usb/spcausb.h
spca5xx-20060501/drivers/usb/icm105a.h
spca5xx-20060501/drivers/usb/hv7131b.h
spca5xx-20060501/drivers/usb/hv7131c.h
spca5xx-20060501/drivers/usb/spca501_init.h
spca5xx-20060501/drivers/usb/pb0330.h
spca5xx-20060501/drivers/usb/ov7630c.h
spca5xx-20060501/drivers/usb/et61xx51.h
spca5xx-20060501/drivers/usb/sp5xxfw2.h
spca5xx-20060501/drivers/usb/jpeg_header.h
spca5xx-20060501/drivers/usb/spca508_init.h
spca5xx-20060501/drivers/usb/spcaCompat.h
spca5xx-20060501/drivers/usb/dummy_cam.h
spca5xx-20060501/drivers/usb/spcadecoder.c
spca5xx-20060501/drivers/usb/spcadecoder.h
spca5xx-20060501/drivers/usb/tas5130c.h
spca5xx-20060501/drivers/usb/sp5xxfw2.dat
spca5xx-20060501/drivers/usb/hdcs2020.h
spca5xx-20060501/drivers/usb/spca505_init.h
spca5xx-20060501/drivers/usb/spca500_init.h
spca5xx-20060501/drivers/usb/tv8532.h
spca5xx-20060501/CHANGELOG
tar: spca5xx-20060501/drivers: implausibly old time stamp 1970-01-01 01:00:00
spca5xx-20060501/README-SONIX
spca5xx-20060501/README-TV8532
spca5xx-20060501/INSTALL
spca5xx-20060501/cutlog.py
dave@dave-ubuntu:~$ cd spca5xx-20060501
dave@dave-ubuntu:~/spca5xx-20060501$ sudo make clean
Password:
rm -r -f drivers/usb/*.o drivers/usb/.spcadecoder.o.cmd \
        drivers/usb/.spca5xx.o.cmd  *.o *.ko *.mod.* .[a-z]* core *.i
dave@dave-ubuntu:~/spca5xx-20060501$ sudo make
   Building SPCA5XX driver for 2.5/2.6 kernel.
   Remember: you must have read/write access to your kernel source tree.
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/dave/spca5xx-20060501 CC=cc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-23-686'
  CC [M]  /home/dave/spca5xx-20060501/drivers/usb/spca5xx.o
  CC [M]  /home/dave/spca5xx-20060501/drivers/usb/spcadecoder.o
  LD [M]  /home/dave/spca5xx-20060501/spca5xx.o
  Building modules, stage 2.
  MODPOST
  CC      /home/dave/spca5xx-20060501/spca5xx.mod.o
  LD [M]  /home/dave/spca5xx-20060501/spca5xx.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-23-686'
dave@dave-ubuntu:~/spca5xx-20060501$ sudo modprobe -r spca5xx
dave@dave-ubuntu:~/spca5xx-20060501$ sudo rm -rf /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx*
dave@dave-ubuntu:~/spca5xx-20060501$ sudo make install
mkdir -p /lib/modules/`uname -r`/kernel/drivers/usb/media/
rm -f /lib/modules/`uname -r`/kernel/drivers/usb/media/spca50x.ko
rm -f /lib/modules/`uname -r`/kernel/drivers/usb/media/et61x.ko
install -c -m 0644 spca5xx.ko /lib/modules/`uname -r`/kernel/drivers/usb/media/
/sbin/depmod -ae
dave@dave-ubuntu:~/spca5xx-20060501$ sudo modprobe spca5xx
dave@dave-ubuntu:~/spca5xx-20060501$

What next? Do I need to reboot?

Dave

---

### Post by arnieboy on 2006-06-11
no you dont need to reboot. The module was successfully inserted. now just plug in your webcam and if it is supported, you will see it working if you turn on camorama or anything similar.

---

### Post by dave.goodfellow on 2006-06-11
[QUOTE=arnieboy]no you dont need to reboot. The module was successfully inserted. now just plug in your webcam and if it is supported, you will see it working if you turn on camorama or anything similar.[/QUOTE]

dave@dave-ubuntu:~/spca5xx-20060501$ **lsusb**
Bus 005 Device 005: ID 041e:403c Creative Technology, Ltd WebCam Live! Ultra
Bus 005 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 002: ID 045e:006a Microsoft Corp.
Bus 002 Device 001: ID 0000:0000

Error (camorama)
Could not conect to video device (/dev/video0).
Please check connection.

It's obviously plugged in looking at lsusb
but
dave@dave-ubuntu:/dev$ cd /dev/video0
bash: cd: /dev/video0: No such file or directory

Any ideas?
Dave

---

### Post by arnieboy on 2006-06-11
[QUOTE=dave.goodfellow]dave@dave-ubuntu:~/spca5xx-20060501$ **lsusb**
Bus 005 Device 005: ID 041e:403c Creative Technology, Ltd WebCam Live! Ultra
Bus 005 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 002: ID 045e:006a Microsoft Corp.
Bus 002 Device 001: ID 0000:0000

Error (camorama)
Could not conect to video device (/dev/video0).
Please check connection.

It's obviously plugged in looking at lsusb
but
dave@dave-ubuntu:/dev$ cd /dev/video0
bash: cd: /dev/video0: No such file or directory

Any ideas?
Dave[/QUOTE]
go to the /dev directory and get a list of files starting with "video"
if you find a file like /dev/video
do the following:
```
sudo ln -s /dev/video /dev/video0
```
now run camorama again

---

### Post by dave.goodfellow on 2006-06-11
dave@dave-ubuntu:~$ cd /dev
dave@dave-ubuntu:/dev$ ls
acpi       ptyaa  ptype  ptyv2  ram14       tty60  ttyed   ttyS35  ttyw5
admmidi    ptyab  ptypf  ptyv3  ram15       tty61  ttyee   ttyS36  ttyw6
adsp       ptyac  ptyq0  ptyv4  ram2        tty62  ttyef   ttyS37  ttyw7
agpgart    ptyad  ptyq1  ptyv5  ram3        tty63  ttyp0   ttyS38  ttyw8
amidi      ptyae  ptyq2  ptyv6  ram4        tty7   ttyp1   ttyS39  ttyw9
audio      ptyaf  ptyq3  ptyv7  ram5        tty8   ttyp2   ttys4   ttywa
bus        ptyb0  ptyq4  ptyv8  ram6        tty9   ttyp3   ttyS4   ttywb
cdrom      ptyb1  ptyq5  ptyv9  ram7        ttya0  ttyp4   ttyS40  ttywc
cdrw       ptyb2  ptyq6  ptyva  ram8        ttya1  ttyp5   ttyS41  ttywd
console    ptyb3  ptyq7  ptyvb  ram9        ttya2  ttyp6   ttyS42  ttywe
core       ptyb4  ptyq8  ptyvc  random      ttya3  ttyp7   ttyS43  ttywf
disk       ptyb5  ptyq9  ptyvd  rtc         ttya4  ttyp8   ttyS44  ttyx0
dmmidi     ptyb6  ptyqa  ptyve  sda         ttya5  ttyp9   ttyS45  ttyx1
dri        ptyb7  ptyqb  ptyvf  sda1        ttya6  ttypa   ttyS46  ttyx2
dsp        ptyb8  ptyqc  ptyw0  sda2        ttya7  ttypb   ttyS47  ttyx3
dvd        ptyb9  ptyqd  ptyw1  sda3        ttya8  ttypc   ttys5   ttyx4
dvdrw      ptyba  ptyqe  ptyw2  sda5        ttya9  ttypd   ttyS5   ttyx5
evms       ptybb  ptyqf  ptyw3  sequencer   ttyaa  ttype   ttys6   ttyx6
fb0        ptybc  ptyr0  ptyw4  sequencer2  ttyab  ttypf   ttyS6   ttyx7
fd         ptybd  ptyr1  ptyw5  sg0         ttyac  ttyq0   ttys7   ttyx8
fd0        ptybe  ptyr2  ptyw6  shm         ttyad  ttyq1   ttyS7   ttyx9
full       ptybf  ptyr3  ptyw7  snd         ttyae  ttyq2   ttys8   ttyxa
hda        ptyc0  ptyr4  ptyw8  sndstat     ttyaf  ttyq3   ttyS8   ttyxb
hdb        ptyc1  ptyr5  ptyw9  stderr      ttyb0  ttyq4   ttys9   ttyxc
hpet       ptyc2  ptyr6  ptywa  stdin       ttyb1  ttyq5   ttyS9   ttyxd
hwrng      ptyc3  ptyr7  ptywb  stdout      ttyb2  ttyq6   ttysa   ttyxe
initctl    ptyc4  ptyr8  ptywc  tty         ttyb3  ttyq7   ttysb   ttyxf
input      ptyc5  ptyr9  ptywd  tty0        ttyb4  ttyq8   ttysc   ttyy0
kmem       ptyc6  ptyra  ptywe  tty1        ttyb5  ttyq9   ttysd   ttyy1
kmsg       ptyc7  ptyrb  ptywf  tty10       ttyb6  ttyqa   ttyse   ttyy2
log        ptyc8  ptyrc  ptyx0  tty11       ttyb7  ttyqb   ttysf   ttyy3
loop       ptyc9  ptyrd  ptyx1  tty12       ttyb8  ttyqc   ttyt0   ttyy4
lp0        ptyca  ptyre  ptyx2  tty13       ttyb9  ttyqd   ttyt1   ttyy5
lvm        ptycb  ptyrf  ptyx3  tty14       ttyba  ttyqe   ttyt2   ttyy6
MAKEDEV    ptycc  ptys0  ptyx4  tty15       ttybb  ttyqf   ttyt3   ttyy7
mapper     ptycd  ptys1  ptyx5  tty16       ttybc  ttyr0   ttyt4   ttyy8
md0        ptyce  ptys2  ptyx6  tty17       ttybd  ttyr1   ttyt5   ttyy9
md1        ptycf  ptys3  ptyx7  tty18       ttybe  ttyr2   ttyt6   ttyya
md10       ptyd0  ptys4  ptyx8  tty19       ttybf  ttyr3   ttyt7   ttyyb
md11       ptyd1  ptys5  ptyx9  tty2        ttyc0  ttyr4   ttyt8   ttyyc
md12       ptyd2  ptys6  ptyxa  tty20       ttyc1  ttyr5   ttyt9   ttyyd
md13       ptyd3  ptys7  ptyxb  tty21       ttyc2  ttyr6   ttyta   ttyye
md14       ptyd4  ptys8  ptyxc  tty22       ttyc3  ttyr7   ttytb   ttyyf
md15       ptyd5  ptys9  ptyxd  tty23       ttyc4  ttyr8   ttytc   ttyz0
md16       ptyd6  ptysa  ptyxe  tty24       ttyc5  ttyr9   ttytd   ttyz1
md17       ptyd7  ptysb  ptyxf  tty25       ttyc6  ttyra   ttyte   ttyz2
md18       ptyd8  ptysc  ptyy0  tty26       ttyc7  ttyrb   ttytf   ttyz3
md19       ptyd9  ptysd  ptyy1  tty27       ttyc8  ttyrc   ttyu0   ttyz4
md2        ptyda  ptyse  ptyy2  tty28       ttyc9  ttyrd   ttyu1   ttyz5
md20       ptydb  ptysf  ptyy3  tty29       ttyca  ttyre   ttyu2   ttyz6
md21       ptydc  ptyt0  ptyy4  tty3        ttycb  ttyrf   ttyu3   ttyz7
md22       ptydd  ptyt1  ptyy5  tty30       ttycc  ttys0   ttyu4   ttyz8
md23       ptyde  ptyt2  ptyy6  tty31       ttycd  ttyS0   ttyu5   ttyz9
md24       ptydf  ptyt3  ptyy7  tty32       ttyce  ttys1   ttyu6   ttyza
md3        ptye0  ptyt4  ptyy8  tty33       ttycf  ttyS1   ttyu7   ttyzb
md4        ptye1  ptyt5  ptyy9  tty34       ttyd0  ttyS10  ttyu8   ttyzc
md5        ptye2  ptyt6  ptyya  tty35       ttyd1  ttyS11  ttyu9   ttyzd
md6        ptye3  ptyt7  ptyyb  tty36       ttyd2  ttyS12  ttyua   ttyze
md7        ptye4  ptyt8  ptyyc  tty37       ttyd3  ttyS13  ttyub   ttyzf
md8        ptye5  ptyt9  ptyyd  tty38       ttyd4  ttyS14  ttyuc   urandom
md9        ptye6  ptyta  ptyye  tty39       ttyd5  ttyS15  ttyud   vcs
mem        ptye7  ptytb  ptyyf  tty4        ttyd6  ttyS16  ttyue   vcs1
midi       ptye8  ptytc  ptyz0  tty40       ttyd7  ttyS17  ttyuf   vcs2
mixer      ptye9  ptytd  ptyz1  tty41       ttyd8  ttyS18  ttyv0   vcs3
net        ptyea  ptyte  ptyz2  tty42       ttyd9  ttyS19  ttyv1   vcs4
null       ptyeb  ptytf  ptyz3  tty43       ttyda  ttys2   ttyv2   vcs5
nvidia0    ptyec  ptyu0  ptyz4  tty44       ttydb  ttyS2   ttyv3   vcs6
nvidiactl  ptyed  ptyu1  ptyz5  tty45       ttydc  ttyS20  ttyv4   vcs7
parport0   ptyee  ptyu2  ptyz6  tty46       ttydd  ttyS21  ttyv5   vcsa
port       ptyef  ptyu3  ptyz7  tty47       ttyde  ttyS22  ttyv6   vcsa1
ppp        ptyp0  ptyu4  ptyz8  tty48       ttydf  ttyS23  ttyv7   vcsa2
psaux      ptyp1  ptyu5  ptyz9  tty49       ttye0  ttyS24  ttyv8   vcsa3
ptmx       ptyp2  ptyu6  ptyza  tty5        ttye1  ttyS25  ttyv9   vcsa4
pts        ptyp3  ptyu7  ptyzb  tty50       ttye2  ttyS26  ttyva   vcsa5
ptya0      ptyp4  ptyu8  ptyzc  tty51       ttye3  ttyS27  ttyvb   vcsa6
ptya1      ptyp5  ptyu9  ptyzd  tty52       ttye4  ttyS28  ttyvc   vcsa7
ptya2      ptyp6  ptyua  ptyze  tty53       ttye5  ttyS29  ttyvd   xconsole
ptya3      ptyp7  ptyub  ptyzf  tty54       ttye6  ttys3   ttyve   zero
ptya4      ptyp8  ptyuc  ram0   tty55       ttye7  ttyS3   ttyvf
ptya5      ptyp9  ptyud  ram1   tty56       ttye8  ttyS30  ttyw0
ptya6      ptypa  ptyue  ram10  tty57       ttye9  ttyS31  ttyw1
ptya7      ptypb  ptyuf  ram11  tty58       ttyea  ttyS32  ttyw2
ptya8      ptypc  ptyv0  ram12  tty59       ttyeb  ttyS33  ttyw3
ptya9      ptypd  ptyv1  ram13  tty6        ttyec  ttyS34  ttyw4
dave@dave-ubuntu:/dev$

video doesn't seem to be there???

---

### Post by arnieboy on 2006-06-11
That means the spcs5xx driver and other webcam drivers which come standard with Dapper do not support your webcam. For a complete list of spca5xx supported webcams look here:
[http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)
You should look around with your webcam model on google with "ubuntu or linux driver" in the end to see if there are other drivers out there which support your cam.

The fact that your webcam is being listed in the list of USB devices does not mean that its driver is installed.

---

### Post by dave.goodfellow on 2006-06-11
Thanks for trying
I'll give google a go and report back if I have any joy.
Otherwise it's off to the shops.
Can you recommend a good linux webcam?
Cheers
Dave

---

### Post by arnieboy on 2006-06-11
try to go for one which has 5 stars and has a "yes" on the link that I gave.

For example: labtec webcam pro.

---

### Post by samotano on 2006-06-12
I have a logitech quickcam fusion.  Fairly new to ubuntu/linux.  I can't get my webcam to work (the mic part works in gnomemeeting).  I followed arnieboy instructions throughout this forum, but the camera does not show up as a device (gnomemeeting).  I checked the website referred and my webcam is listed as supported by the drivers.  HELP!!!!
thx.
S

---

### Post by athan on 2006-06-14
Hi,
I have the same camera working in dapper. Unfortunately the quickcam & spca5xx drivers won't work for the quickcam fusion. You'll have to use uvcvideo which can be downloaded here: [http://svn.berlios.de/svnroot/repos/linux-uvc/linux-uvc/trunk/](http://svn.berlios.de/svnroot/repos/linux-uvc/linux-uvc/trunk/)

If you have the installed the kernel-headers & build essential package a simple 'make' & 'make install' should do the work. You can load the module with 'modprobe uvcvideo' and check 'tail -f /var/log/messages'. The module should load with no errors.

For Ekiga: Press Settings -> Video Devices -> Search Devices. The cam should be found automatically.

Hope this helps!

---

### Post by gymsmoke on 2006-06-17
Arnie~
First, Thank you !!! I had almost everything figured out, except that part about the version of the compilation.  Undoing all my mess and just following the commands you outlined were perfect!

Second, you must have the patience of a croc watching a titmouse waiting for his lunch... 25 pages of thread (and counting).  I commend you for your tenacity in answering all of these.

Lastly, I installed a Logitech quickcam pro 3000 on my desktop.  Video worked first time out.  However, the audio borks.   I've been trying this using gnomemeeting (since it's really the only app I know of that will test both audio and video).  It recognizes the cam just fine, image sizing is no problem, all video functions work as expected. On the audio device panel ALSA/quicknet show as the plugin , output device shows as Intel 82801DB-ICH4 / default.  Input device shows as USB Device 0x64d:0x8b0 (selected) / default / Intel 82801DB-ICH4

lsusb shows this:
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 006: ID 046d:08b0 Logitech, Inc. Quickcam 3000 Pro [pwc]
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 003: ID 043d:0072 Lexmark International, Inc. X6170 Printer
Bus 002 Device 002: ID 046d:c404 Logitech, Inc. TrackMan Wheel
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

(In case anyone asks - NO  the lexmark doesn't work.  I've since disconnected it and quit trying to get anything lexmark to talk to Linux).

uname -r  = 2.6.12.10-386
Ubuntu 5.10 

Any thoughts on why the video, but no audio?

Thanks.

Jon

---

### Post by JoeG on 2006-06-17
I'm running Dapper (kubuntu) here and the cam (Ezonics EZ-305) worked out of the box.  Just one problem:  the image is inverted ... as in flipped upside-down.  Is there a fix for this, or am I just gonna have to mount it upside-down to get the image right?

---

### Post by gymsmoke on 2006-06-18
Joe~
Depending on the app, there is a control that inverts the image.  So far, I've only just got my webcam working (video only, no sound), so I haven't experimented too far with this.  If I get the audio portion working, I have a few apps that I'm waiting to try out...

---

### Post by JoeG on 2006-06-19
[QUOTE=gymsmoke]Joe~
Depending on the app, there is a control that inverts the image.  So far, I've only just got my webcam working (video only, no sound), so I haven't experimented too far with this.  If I get the audio portion working, I have a few apps that I'm waiting to try out...[/QUOTE]
Hmm.  I've tried gqcam and camstream to no avail.  The cam works, I just can't find a control that fixes the inverted image.  Any ideas, folks?  ](*,)

---

### Post by Sakhaara on 2006-06-24
sakhaara@Nosferatu:~/spca5xx-20060501$ sudo make CC=gcc-3.4
   Building SPCA5XX driver for 2.5/2.6 kernel.
   Remember: you must have read/write access to your kernel source tree.
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/sakhaara/spca5xx-20060501 CC=gcc-3.4 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-23-386'
  CC [M]  /home/sakhaara/spca5xx-20060501/drivers/usb/spca5xx.o
  CC [M]  /home/sakhaara/spca5xx-20060501/drivers/usb/spcadecoder.o
  LD [M]  /home/sakhaara/spca5xx-20060501/spca5xx.o
  Building modules, stage 2.
  MODPOST
  CC      /home/sakhaara/spca5xx-20060501/spca5xx.mod.o
  LD [M]  /home/sakhaara/spca5xx-20060501/spca5xx.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-23-386'
sakhaara@Nosferatu:~/spca5xx-20060501$ sudo modprobe -r spca5xx
sakhaara@Nosferatu:~/spca5xx-20060501$ sudo rm -rf /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx*
sakhaara@Nosferatu:~/spca5xx-20060501$ sudo make install
mkdir -p /lib/modules/`uname -r`/kernel/drivers/usb/media/
rm -f /lib/modules/`uname -r`/kernel/drivers/usb/media/spca50x.ko
rm -f /lib/modules/`uname -r`/kernel/drivers/usb/media/et61x.ko
install -c -m 0644 spca5xx.ko /lib/modules/`uname -r`/kernel/drivers/usb/media/
/sbin/depmod -ae
sakhaara@Nosferatu:~/spca5xx-20060501$ sudo modprobe spca5xx
FATAL: Error inserting spca5xx (/lib/modules/2.6.15-23-386/kernel/drivers/usb/media/spca5xx.ko): Invalid module format


I have an error..and i tryed the "make clean" command too..and it doesn't work

---

### Post by Sakhaara on 2006-06-24
i've fixed the problem. i just exchanged the gcc

sudo make CC=gcc-4.0

to this.

---

### Post by JoeG on 2006-06-24
well, barring getting the inverted images fixed, are there any cams that work correctly out of the box with a reasonably high quality?

---

### Post by ilferrons on 2006-06-24
Hi all
I have a Philips SPC200NC. I've read that my webcam is fully supported by the latest spca5xx driver. 
I've been downloaded the driver, I've been compiled it and installed as specified in many posts but it can work. 
I can load driver without errors but when I try to use my webcam with gqcam or camorama, my system (ubuntu dapper) freeze and I have to reset. 
AMSN recognize webcam and sets channel correctly but when I try to use it, system freezes. 
I've compiled the driver with gcc-4.0.3, that is the same version of the kernel (2.6.15-25-386, that is the last ubuntu kernel I've downloaded).
I've followed all instructions I've found in ubuntu forums but problem is not solved for me.
Can anyone help me???

---

### Post by cesera on 2006-07-11
> **arnieboy said:**
> The howto is for Breezy (not Dapper). The spca5xx modules work fine on Dapper by default.

 
I am running Dapper-Kubuntu-AMD64. When I plug my webcam in, the spca5xxmodule gets loaded successfully according to the logs. However when I try to access it my system still freezes.
 
 
 
 
> **arnieboy said:**
> For a complete list of spca5xx supported webcams look here:
[http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)
 
My webcam is  bought in China, make: Hayden, but according to KInfoCenter&#65306; Manufacturer: Vimicro Corp.
 
lsusb says:
Bus 001 Device 005: ID 0ac8:303b Z-Star Microelectronics Corp. ZC0303 WebCam
 
According to the link above that is fully supported, but it still freeze the system.
 
 
 
Any help would be greatly appreciated.

---

### Post by Postino on 2006-07-11
Hello arnieboy
not sure if you still read this thread...

here is my problem:
i have a logitech quickcam IM.
it does get recognized and, in fact, at boot up, the green light comes on the camera, which indicates that it is in use.

when i check, i have two entries: /dev/video and /dev/video0

when i try to view my webcam, it tells me that it is already in use, which is probably right since it comes on during hardware detection.

do you have any idea how i can fix it or point me in the right direction? i'm using kernel 2.6.15 686

thanks in advance.

---

### Post by Paulo Wageck on 2006-07-19
i used gcc 4-0 on dapper and it worked....

using 3-4 was giving me an error message...

~/spca5xx-20060501$ sudo modprobe spca5xx
FATAL: Error inserting spca5xx (/lib/modules/2.6.15-26-k7/kernel/drivers/usb/media/spca5xx.ko): Invalid module format

---

### Post by arnieboy on 2006-07-19
first post updated to include instructions for dapper.

---

### Post by fakie_flip on 2006-08-07
I have tried everything I know to get my webcam working in Ubuntu. My webcam must be impossible in Linux, but I don't give up trying. I followed the directions from here and the community wiki page on Webcams to try to get it working. I do not know my webcam's model #. I bought it about 4 years ago, so I am unable to go to the store and see what model I purchased or look on the box it came in. Any suggestions to get this thing working or know whether it can work in Ubuntu? Camarok and gqview do not display when I try to run them from terminal.

I do have the output of "hwinfo --usb --camera" about my webcam (it is a lot of output, so use control f in firefox to search for cam):

[http://pastebin.com/764612](http://pastebin.com/764612)

and lsusb:

```
ubuntu@ubuntu:~$ sudo lsusb -v

Bus 005 Device 001: ID 0000:0000
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         1 Single TT
  bMaxPacketSize0        64
  idVendor           0x0000
  idProduct          0x0000
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.15-23-386 ehci_hcd
  iProduct                2 EHCI Host Controller
  iSerial                 1 0000:00:13.2
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0xc0
      Self Powered
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval              12
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             4
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
    TT think time 8 FS bits
  bPwrOn2PwrGood       10 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x48
  PortPwrCtrlMask    0xc0
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0100 power
   Port 4: 0000.0100 power
Device Status:     0x0001
  Self Powered

Bus 003 Device 001: ID 0000:0000
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0
  bMaxPacketSize0        64
  idVendor           0x0000
  idProduct          0x0000
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.15-23-386 uhci_hcd
  iProduct                2 UHCI Host Controller
  iSerial                 1 0000:00:13.0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             2
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood        1 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0xc0
  PortPwrCtrlMask    0xc0
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 004 Device 001: ID 0000:0000
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0
  bMaxPacketSize0        64
  idVendor           0x0000
  idProduct          0x0000
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.15-23-386 uhci_hcd
  iProduct                2 UHCI Host Controller
  iSerial                 1 0000:00:13.1
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             2
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood        1 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x38
  PortPwrCtrlMask    0xc1
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 002 Device 001: ID 0000:0000
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0
  bMaxPacketSize0        64
  idVendor           0x0000
  idProduct          0x0000
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.15-23-386 ohci_hcd
  iProduct                2 OHCI Host Controller
  iSerial                 1 0000:00:02.3
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0xc0
      Self Powered
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             3
  wHubCharacteristic 0x0002
    No power switching (usb 1.0)
    Ganged overcurrent protection
  bPwrOn2PwrGood        1 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0xf0
  PortPwrCtrlMask    0x00
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0100 power
Device Status:     0x0001
  Self Powered

Bus 001 Device 003: ID 046d:c501 Logitech, Inc. Cordless Mouse Receiver
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0         8
  idVendor           0x046d Logitech, Inc.
  idProduct          0xc501 Cordless Mouse Receiver
  bcdDevice            9.10
  iManufacturer           1 Logitech
  iProduct                2 USB Receiver
  iSerial                 0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower               50mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Devices
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              0
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.10
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      82
         Report Descriptors:
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
Device Status:     0x0000
  (Bus Powered)

Bus 001 Device 002: ID 046d:0840 Logitech, Inc. QuickCam Express
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.00
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass       255 Vendor Specific Subclass
  bDeviceProtocol       255 Vendor Specific Protocol
  bMaxPacketSize0         8
  idVendor           0x046d Logitech, Inc.
  idProduct          0x0840 QuickCam Express
  bcdDevice            1.00
  iManufacturer           0
  iProduct                1 Camera
  iSerial                 0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           55
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval              16
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       1
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x03ff  1x 1023 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval              16
Device Status:     0x0001
  Self Powered

Bus 001 Device 001: ID 0000:0000
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0
  bMaxPacketSize0        64
  idVendor           0x0000
  idProduct          0x0000
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.15-23-386 ohci_hcd
  iProduct                2 OHCI Host Controller
  iSerial                 1 0000:00:02.2
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0xc0
      Self Powered
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             3
  wHubCharacteristic 0x0002
    No power switching (usb 1.0)
    Ganged overcurrent protection
  bPwrOn2PwrGood        1 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0xe8
  PortPwrCtrlMask    0x01
 Hub Port Status:
   Port 1: 0000.0103 power enable connect
   Port 2: 0000.0303 lowspeed power enable connect
   Port 3: 0000.0100 power
Device Status:     0x0001
  Self Powered
ubuntu@ubuntu:~$

```

---

### Post by carney1979 on 2006-08-07
Arnieboy,

First, a bit of history.

I have a Logitech QuickCam IM (usb webcam). I was running Fedora Core 5 and the spca5xx module worked perfectly with this webcam. The only program I had problems with was Camorama which wouldn't open, probably due to a permissions problem with /dev/video or /dev/video0. 

Now to the present:

I followed your instructions for Dapper on my fresh Dapper install. In fact, I cut and pasted one line at a time into a terminal. The module compiled perfectly, no errors noted.

HAL (I assume) finds the webcam at boot time and automagically inserts the module. The little green LED on the camera comes on.

Here's a quick output of lsmod:

```
david@n1zhe:~$ lsmod | grep spca5xx
spca5xx               664720  0
videodev                9856  2 spca5xx,quickcam
usbcore               130692  12 spca5xx,quickcam,snd_usb_audio,snd_usb_lib,usblp,usb_storage,usbhid,ehci_hcd,ohci_hcd
``` 

And here's lsusb:

```
david@n1zhe:~$ lsusb
Bus 003 Device 006: ID 046d:08d9 Logitech, Inc.
Bus 003 Device 002: ID 0409:013c NEC Corp.
Bus 003 Device 007: ID 051d:0002 American Power Conversion Back-UPS Pro 500/1000/1500
Bus 003 Device 001: ID 0000:0000
Bus 001 Device 003: ID 045e:003c Microsoft Corp. SideWinder Joystick
Bus 001 Device 004: ID 058f:9360 Alcor Micro Corp.
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 002: ID 03f0:0604 Hewlett-Packard DeskJet 840c
Bus 002 Device 001: ID 0000:0000

``` 
ls -la /dev/video* returns:

```
david@n1zhe:~$ ls -la /dev/video*
lrwxrwxrwx 1 root root      6 2006-08-07 03:16 /dev/video -> video0
crw-rw---- 1 root video 81, 0 2006-08-07 03:16 /dev/video0
``` 
caminfo returns:

```
david@n1zhe:~$ caminfo
Detected 1 Video4Linux devices.
Device node      : /dev/video0
Name of device   : "Logitech QuickCam IM/Connect "
Minimum size     : 176x144
Current size     : 0x0
Maximum size     : 640x480
Video inputs     : 1
 Input 0
  Name             : "ZC301-2"
  Type             : Camera
  Audio            : no
  Tuners           : 0
Audio inputs     : 0
``` 
My problem is whenever I start Camerama, Camstream or Ekiga, when these apps try to access the camera the green LED comes on and then the program locks up. I get no picture, usually just a black screen in the window where the camera's output should be.

Any suggestions? IS spca5xx the right module?

David

P.S. automatix DOES rock! Thanks!

---

### Post by patrick295767 on 2006-08-07
> **carney1979 said:**
> Arnieboy,

First, a bit of history.

I have a Logitech QuickCam IM (usb webcam). I was running Fedora Core 5 and the spca5xx module worked perfectly with this webcam. The only program I had problems with was Camorama which wouldn't open, probably due to a permissions problem with /dev/video or /dev/video0. 

Now to the present:

I followed your instructions for Dapper on my fresh Dapper install. In fact, I cut and pasted one line at a time into a terminal. The module compiled perfectly, no errors noted.

HAL (I assume) finds the webcam at boot time and automagically inserts the module. The little green LED on the camera comes on.

Here's a quick output of lsmod:

```
david@n1zhe:~$ lsmod | grep spca5xx
spca5xx               664720  0
videodev                9856  2 spca5xx,quickcam
usbcore               130692  12 spca5xx,quickcam,snd_usb_audio,snd_usb_lib,usblp,usb_storage,usbhid,ehci_hcd,ohci_hcd
``` 

And here's lsusb:

```
david@n1zhe:~$ lsusb
Bus 003 Device 006: ID 046d:08d9 Logitech, Inc.
Bus 003 Device 002: ID 0409:013c NEC Corp.
Bus 003 Device 007: ID 051d:0002 American Power Conversion Back-UPS Pro 500/1000/1500
Bus 003 Device 001: ID 0000:0000
Bus 001 Device 003: ID 045e:003c Microsoft Corp. SideWinder Joystick
Bus 001 Device 004: ID 058f:9360 Alcor Micro Corp.
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 002: ID 03f0:0604 Hewlett-Packard DeskJet 840c
Bus 002 Device 001: ID 0000:0000

``` 
ls -la /dev/video* returns:

```
david@n1zhe:~$ ls -la /dev/video*
lrwxrwxrwx 1 root root      6 2006-08-07 03:16 /dev/video -> video0
crw-rw---- 1 root video 81, 0 2006-08-07 03:16 /dev/video0
``` 
caminfo returns:

```
david@n1zhe:~$ caminfo
Detected 1 Video4Linux devices.
Device node      : /dev/video0
Name of device   : "Logitech QuickCam IM/Connect "
Minimum size     : 176x144
Current size     : 0x0
Maximum size     : 640x480
Video inputs     : 1
 Input 0
  Name             : "ZC301-2"
  Type             : Camera
  Audio            : no
  Tuners           : 0
Audio inputs     : 0
``` 
My problem is whenever I start Camerama, Camstream or Ekiga, when these apps try to access the camera the green LED comes on and then the program locks up. I get no picture, usually just a black screen in the window where the camera's output should be.

Any suggestions? IS spca5xx the right module?

David

P.S. automatix DOES rock! Thanks!

  
If this is due to permissions problems, I also had similar problem. I am running on the Linux machine a script at the startup that detects the newly plugs USB (looks the name via lsusb). If it's the webcam I have, it gives the necessary permissions to the folder where are the webcam /proc ... 
The functionality is Watch (script)
[http://linux.about.com/library/cmd/blcmdl1_watch.htm](http://linux.about.com/library/cmd/blcmdl1_watch.htm)
 
There is certainly other & better way, but it's fully workign
 
You could make somethg similar.

---

### Post by carney1979 on 2006-08-07
> If this is due to permissions problems, I also had similar problem. I am running on the Linux machine a script at the startup that detects the newly plugs USB (looks the name via lsusb). If it's the webcam I have, it gives the necessary permissions to the folder where are the webcam /proc ... 
The functionality is Watch (script)
[http://linux.about.com/library/cmd/blcmdl1_watch.htm](http://linux.about.com/library/cmd/blcmdl1_watch.htm)
 
There is certainly other & better way, but it's fully workign
 
You could make somethg similar. 
Would you please be a bit more specific? Perhaps an example?

Thanks!

David

---

### Post by patrick295767 on 2006-08-07
> **carney1979 said:**
> Would you please be a bit more specific? Perhaps an example?

Thanks!

David
 
As soon as I am in front of my linux box, I'll post my script.
  But I d rather be helped by someone who knows how to make it work with the hotplugs in the /etc...
That's the very best !(better than watch)

Cheers

---

### Post by patrick295767 on 2006-08-07
Hi Arnie, 
  
Firstly, thank you for this thread which is helping lot of persons. 
  
I have been using your script to install my logitech quickcam quick messenger on my computers. This works perfectly. 
  
But... 
On one computer, I have already a /dev/video0. That's an ATI rage 64MB card All In Wonder. 
When I 
1/ install the script & 
2/ plug the Webcam, 
3/ starts any program for seeing the video, 
4/ then the PC freezes totally. I have then to do Cold Reboot.
  
Woould you know what to do? I tried once to play with the ln -s /dev/video ... 
But couldnt make it , or I didnt do what I had to... 
  
I am stucked. ](*,) ](*,) Would you have any ideas how to make the webcam working on such hardware (aleady having an /dev/video0)
  
--
Concenring the video card I have, I am using now XFREE instead of XORG because XORG is not capable to have Glx accerelation with it. 
The tuner tv, I still didnt do it yet with gatos ... 
It should be possible, I am sure. 
--
  
Thank you very much for your experience & advices !!!

Patrick

---

### Post by jvpgomes on 2006-08-13
I did everything exactly as it is explain, and I still can't use the camera.

If I try to use gqcam I have the message:
/dev/video: No such file or directory


:(

---

### Post by patrick295767 on 2006-08-14
that's the script for the rights:
```
#!/bin/bash

if [ "$(cat /root/lsusbresult.log)" != "$(lsusb)"  ] ; then
	echo " $(date) : changes" >> "/root/lsusb_changes.log"
	echo "$(lsusb)" >> "/root/lsusb_changes.log"
	echo " tutu !" | festival --tts
	chmod -R $$$$$$ /proc/bus/usb

	if [ "$(lsusb | grep Canon)" != "" ] ; then
		echo " "
		lsusb
		echo " Canon detected " | festival --tts
	fi


	if [ "$(lsusb | grep Epson)" != "" ] ; then
		echo " "
		echo " Epson detected " | festival --tts
	fi

fi
```

replace $$$$$ by what you need

---

### Post by Fe01 on 2006-08-30
Greetings everybody :) my first post 

Thanks for helping poeople Arnieboy and others!

Can you advise me plz:

-installation went fine

-lsmod:
spca5xx               664592  0
videodev                9856  1 spca5xx
usbcore               130692  9 spca5xx,usb_storage,usbhid,snd_usb_audio,snd_usb_lib,hci_usb,ehci_hcd,uhci_hcd

-lsusb
Bus 004 Device 007: ID 046d:08c3 Logitech, Inc.
Bus 004 Device 004: ID 041e:3020 Creative Technology, Ltd SoundBlaster Audigy 2 NX
Bus 004 Device 006: ID 0ea0:2118 Ours Technology, Inc.
Bus 004 Device 005: ID 046d:c01d Logitech, Inc.
Bus 004 Device 002: ID 050d:0237 Belkin Components
Bus 004 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 003 Device 002: ID 049f:0086 Compaq Computer Corp.
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000

-/dev/ appeared after connection
audio2
dsp2
mixer2
no video

-dmesg
[17179720.416000] Linux video capture interface: v1.00
[17179720.548000] usbcore: registered new driver spca5xx
[17179720.548000] /drivers/usb/spca5xx.c: spca5xx driver 00.60.00 registered
[17179743.700000] usb 4-2: new high speed USB device using ehci_hcd and address 7
[17179745.008000] 7:3:1: cannot set freq 0 to ep 0x86
[17179746.008000] 7:3:2: cannot set freq 0 to ep 0x86
[17179746.976000] 7:3:3: cannot set freq 16000 to ep 0x86

I'm running Kubuntu Dapper 2.6.15-26-386.
Webcam is 046d:08c3 Logitech QuickCam for Notebooks Pro.

Acoording to [http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html) support is written "TEST" and the driver Linux-UVC:
Logitech	2	0x046d	0x08c3	QC pro for Notebooks	Sunplus	spca525a	 	Test	mjpeg	linux-UVC	********

Does that just mean that I have to install in addition this BerliOS driver?

Has anyone done it before here?

Thanks a lot in advance!


**FOR DAPPER**
If you are on Dapper do the following instead of the above:
```
sudo apt-get install linux-headers-`uname -r` linux-restricted-modules-`uname -r` build-essential
wget http://mxhaard.free.fr/spca50x/Download/spca5xx-20060501.tar.gz
tar xvfz spca5xx-20060501.tar.gz
cd spca5xx-20060501
make
sudo modprobe -r spca5xx
sudo rm -rf /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx*
sudo make install
sudo modprobe spca5xx
```[/QUOTE]

---

### Post by tenchi39 on 2006-09-03
Hi!

Dear Arnieboy...

I just bough (what a mistake...) a König USB Webcam CMP-WEBCAM21. lsusb gives the following:

Bus 002 Device 002: ID 0ac8:303b Z-Star Microelectronics Corp. ZC0303 WebCam

It seems to need the spca5xx driver which upon trying the camera, instantly locks up the computer. I followed your instructions for dapper drake (I have kubuntu 6.06.1 LTS), but still it locks up...

Any ideas?

---

### Post by Pilsner on 2006-09-03
> sudo apt-get install linux-headers-`uname -r` linux-restricted-modules-`uname -r` build-essential
wget [http://mxhaard.free.fr/spca50x/Download/spca5xx-20060501.tar.gz](http://mxhaard.free.fr/spca50x/Download/spca5xx-20060501.tar.gz)
tar xvfz spca5xx-20060501.tar.gz
cd spca5xx-20060501
make
sudo modprobe -r spca5xx
sudo rm -rf /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx*
sudo make install
sudo modprobe spca5xx

Its for dapper.


When i ran the first command > sudo apt-get install linux-headers-`uname -r` linux-restricted-modules-`uname -r` build-essential

I got error message "couldnt find linux-headers-2.6.17.7"

I have compiled the kernel into 2.6.17.7

Any idea?

---

### Post by rami on 2006-09-07
I have two webcams one logitech quickcam traveller and a labtec, never was able to get the logitech cam to work, and the labtec cam, whenever I access its channel whether from camorama, amsn, or gqcam, my system totally freezes and nothing becomes responsive. Only pressing the on/off button is the solution.

Whats wrong??

---

### Post by amac777 on 2006-09-15
Hi! I had a problem following this HOWTO and I have figured out why so just wanted to post my experience in the hopes it will help someone.

The Problem:

I have already followed this HOWTO once for Dapper and it worked perfectly the first time. I am now re-installing my webcam drivers after upgrading my kernel (the webcame stopped working after I upgraded my kernel) and am following the HOWTO steps exactly, but the problem is that I got the following error message when I typed the "make" step:

```
nigol@nigol-desktop:~/linux stuff/spca5xx-20060501$ make
   Building SPCA5XX driver for 2.5/2.6 kernel.
   Remember: you must have read/write access to your kernel source tree.
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/nigol/linux stuff/spca5xx-20060501 CC=cc modulesmake[1]: Entering directory `/usr/src/linux-headers-2.6.15-26-386'
make[1]: *** No rule to make target `stuff/spca5xx-20060501'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-26-386'
make: *** [default] Error 2
```

On hindsight I suppose the problem is obvious, but it took me many hours reading and searching this thread, googling, trying to figure out if it was because I just upgraded my kernel, and general smashing my head against the wall since I'm totally new to linux. 

The solution:

Don't have any directories with a space (" ") somewhere in their names when you download and un-tar the spca5xx-20060501.tar.gz file!

Specifically, I had stored the spca5xx-20060501.tar.gz file in a sub-directory called 'Linux stuff' and that space between the word Linux and the word stuff in the directory name was my problem. As simple as that. Once I got rid of it (i.e., renamed the directory to a single word with no space), everything worked fine and the webcam is fully operational now. I'm very happy! Thanks for the great HOWTO!

---

### Post by Postino on 2006-09-18
Hello,
I had posted earlier, and was having problems with my webcam, Logitech QuickCam IM not working.
I solved the problem, and this might help someone else too, so here it is. I actually found the solution in another thread, so credit is due to the following post:
[http://www.ubuntuforums.org/showpost.php?p=1431577&postcount=10](http://www.ubuntuforums.org/showpost.php?p=1431577&postcount=10)

I had my webcam connected to a USB hub. In the above post, the poster was using a hub too, but decided to connect it directly to the computer, which is what I did and now, it is working flawlessly!

Just a FYI.

---

### Post by berserker on 2006-09-20
Things seemed to have changed when compiling under kernel 2.6.18:

```
   Building SPCA5XX driver for 2.5/2.6 kernel.
   Remember: you must have read/write access to your kernel source tree.
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/erich/applications/programs/spca5xx-20060501 CC=cc modules
make[1]: Entering directory `/usr/src/linux-2.6.18'
  CC [M]  /home/erich/applications/programs/spca5xx-20060501/drivers/usb/spca5xx.o
/home/erich/applications/programs/spca5xx-20060501/drivers/usb/spca5xx.c: In function ‘spca5xx_open’:
/home/erich/applications/programs/spca5xx-20060501/drivers/usb/spca5xx.c:2392: warning: implicit declaration of function ‘video_devdata’
/home/erich/applications/programs/spca5xx-20060501/drivers/usb/spca5xx.c:2392: warning: initialization makes pointer from integer without a cast
/home/erich/applications/programs/spca5xx-20060501/drivers/usb/spca5xx.c:2397: warning: implicit declaration of function ‘video_get_drvdata’
/home/erich/applications/programs/spca5xx-20060501/drivers/usb/spca5xx.c:2397: warning: initialization makes pointer from integer without a cast
/home/erich/applications/programs/spca5xx-20060501/drivers/usb/spca5xx.c: In function ‘spca5xx_close’:
/home/erich/applications/programs/spca5xx-20060501/drivers/usb/spca5xx.c:2487: warning: initialization makes pointer from integer without a cast
/home/erich/applications/programs/spca5xx-20060501/drivers/usb/spca5xx.c: In function ‘spca5xx_do_ioctl’:
/home/erich/applications/programs/spca5xx-20060501/drivers/usb/spca5xx.c:2547: warning: initialization makes pointer from integer without a cast
/home/erich/applications/programs/spca5xx-20060501/drivers/usb/spca5xx.c: In function ‘spca5xx_ioctl’:
/home/erich/applications/programs/spca5xx-20060501/drivers/usb/spca5xx.c:3091: warning: implicit declaration of function ‘video_usercopy’
/home/erich/applications/programs/spca5xx-20060501/drivers/usb/spca5xx.c: In function ‘spca5xx_read’:
/home/erich/applications/programs/spca5xx-20060501/drivers/usb/spca5xx.c:3110: warning: initialization makes pointer from integer without a cast
/home/erich/applications/programs/spca5xx-20060501/drivers/usb/spca5xx.c: In function ‘spca5xx_mmap’:
/home/erich/applications/programs/spca5xx-20060501/drivers/usb/spca5xx.c:3209: warning: initialization makes pointer from integer without a cast
/home/erich/applications/programs/spca5xx-20060501/drivers/usb/spca5xx.c: At top level:
/home/erich/applications/programs/spca5xx-20060501/drivers/usb/spca5xx.c:3261: error: variable ‘spca50x_template’ has initializer but incomplete type
/home/erich/applications/programs/spca5xx-20060501/drivers/usb/spca5xx.c:3262: error: unknown field ‘owner’ specified in initializer
/home/erich/applications/programs/spca5xx-20060501/drivers/usb/spca5xx.c:3262: warning: excess elements in struct initializer
/home/erich/applications/programs/spca5xx-20060501/drivers/usb/spca5xx.c:3262: warning: (near initialization for ‘spca50x_template’)
/home/erich/applications/programs/spca5xx-20060501/drivers/usb/spca5xx.c:3263: error: unknown field ‘name’ specified in initializer
/home/erich/applications/programs/spca5xx-20060501/drivers/usb/spca5xx.c:3263: warning: excess elements in struct initializer
/home/erich/applications/programs/spca5xx-20060501/drivers/usb/spca5xx.c:3263: warning: (near initialization for ‘spca50x_template’)
/home/erich/applications/programs/spca5xx-20060501/drivers/usb/spca5xx.c:3264: error: unknown field ‘type’ specified in initializer
/home/erich/applications/programs/spca5xx-20060501/drivers/usb/spca5xx.c:3264: warning: excess elements in struct initializer
/home/erich/applications/programs/spca5xx-20060501/drivers/usb/spca5xx.c:3264: warning: (near initialization for ‘spca50x_template’)
/home/erich/applications/programs/spca5xx-20060501/drivers/usb/spca5xx.c:3265: error: unknown field ‘hardware’ specified in initializer
/home/erich/applications/programs/spca5xx-20060501/drivers/usb/spca5xx.c:3265: warning: excess elements in struct initializer
/home/erich/applications/programs/spca5xx-20060501/drivers/usb/spca5xx.c:3265: warning: (near initialization for ‘spca50x_template’)
/home/erich/applications/programs/spca5xx-20060501/drivers/usb/spca5xx.c:3266: error: unknown field ‘fops’ specified in initializer
/home/erich/applications/programs/spca5xx-20060501/drivers/usb/spca5xx.c:3266: warning: excess elements in struct initializer
/home/erich/applications/programs/spca5xx-20060501/drivers/usb/spca5xx.c:3266: warning: (near initialization for ‘spca50x_template’)
/home/erich/applications/programs/spca5xx-20060501/drivers/usb/spca5xx.c:3268: error: unknown field ‘release’ specified in initializer
/home/erich/applications/programs/spca5xx-20060501/drivers/usb/spca5xx.c:3268: error: ‘video_device_release’ undeclared here (not in a function)
/home/erich/applications/programs/spca5xx-20060501/drivers/usb/spca5xx.c:3268: warning: excess elements in struct initializer
/home/erich/applications/programs/spca5xx-20060501/drivers/usb/spca5xx.c:3268: warning: (near initialization for ‘spca50x_template’)
/home/erich/applications/programs/spca5xx-20060501/drivers/usb/spca5xx.c:3270: error: unknown field ‘minor’ specified in initializer
/home/erich/applications/programs/spca5xx-20060501/drivers/usb/spca5xx.c:3270: warning: excess elements in struct initializer
/home/erich/applications/programs/spca5xx-20060501/drivers/usb/spca5xx.c:3270: warning: (near initialization for ‘spca50x_template’)
/home/erich/applications/programs/spca5xx-20060501/drivers/usb/spca5xx.c: In function ‘cd_to_spca50x’:
/home/erich/applications/programs/spca5xx-20060501/drivers/usb/spca5xx.c:3338: warning: implicit declaration of function ‘to_video_device’
/home/erich/applications/programs/spca5xx-20060501/drivers/usb/spca5xx.c:3338: warning: initialization makes pointer from integer without a cast
/home/erich/applications/programs/spca5xx-20060501/drivers/usb/spca5xx.c:3339: warning: return makes pointer from integer without a cast
/home/erich/applications/programs/spca5xx-20060501/drivers/usb/spca5xx.c: In function ‘spca50x_create_sysfs’:
/home/erich/applications/programs/spca5xx-20060501/drivers/usb/spca5xx.c:3448: warning: implicit declaration of function ‘video_device_create_file’
/home/erich/applications/programs/spca5xx-20060501/drivers/usb/spca5xx.c: In function ‘spca5xx_probe’:
/home/erich/applications/programs/spca5xx-20060501/drivers/usb/spca5xx.c:5504: warning: implicit declaration of function ‘video_device_alloc’
/home/erich/applications/programs/spca5xx-20060501/drivers/usb/spca5xx.c:5504: warning: assignment makes pointer from integer without a cast
/home/erich/applications/programs/spca5xx-20060501/drivers/usb/spca5xx.c:5507: error: invalid application of ‘sizeof’ to incomplete type ‘struct video_device’
/home/erich/applications/programs/spca5xx-20060501/drivers/usb/spca5xx.c:5507: error: invalid application of ‘sizeof’ to incomplete type ‘struct video_device’
/home/erich/applications/programs/spca5xx-20060501/drivers/usb/spca5xx.c:5507: error: invalid application of ‘sizeof’ to incomplete type ‘struct video_device’
/home/erich/applications/programs/spca5xx-20060501/drivers/usb/spca5xx.c:5509: error: dereferencing pointer to incomplete type
/home/erich/applications/programs/spca5xx-20060501/drivers/usb/spca5xx.c:5511: warning: implicit declaration of function ‘video_set_drvdata’
/home/erich/applications/programs/spca5xx-20060501/drivers/usb/spca5xx.c:5516: warning: implicit declaration of function ‘video_register_device’
/home/erich/applications/programs/spca5xx-20060501/drivers/usb/spca5xx.c:5516: error: ‘VFL_TYPE_GRABBER’ undeclared (first use in this function)
/home/erich/applications/programs/spca5xx-20060501/drivers/usb/spca5xx.c:5516: error: (Each undeclared identifier is reported only once
/home/erich/applications/programs/spca5xx-20060501/drivers/usb/spca5xx.c:5516: error: for each function it appears in.)
/home/erich/applications/programs/spca5xx-20060501/drivers/usb/spca5xx.c:5545: error: dereferencing pointer to incomplete type
/home/erich/applications/programs/spca5xx-20060501/drivers/usb/spca5xx.c:5546: warning: implicit declaration of function ‘video_device_release’
/home/erich/applications/programs/spca5xx-20060501/drivers/usb/spca5xx.c:5548: warning: implicit declaration of function ‘video_unregister_device’
make[2]: *** [/home/erich/applications/programs/spca5xx-20060501/drivers/usb/spca5xx.o] Error 1
make[1]: *** [_module_/home/erich/applications/programs/spca5xx-20060501] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.18'
make: *** [default] Error 2
```

---

### Post by berserker on 2006-09-22
The source code needs to be patched in order for the spca5xx module to work with kernel 2.6.18.  Download the attached file into your spca5xx-20060501 directory and then do:

```
patch -p1 < spca5xx_2.6.18.bin.txt
make
sudo make install
sudo modprobe spca5xx
```

---

### Post by easyease on 2006-09-24
Thanks Arnie! your a star, this is a very  very useful howto. :)

---

### Post by apoth on 2006-10-03
I can't get my webcam working... 0c45:60c0 Microdia

I get this output in dmesg:
```
[17179591.664000] /home/rich/spca5xx-20060501/drivers/usb/spca5xx.c: USB SPCA5XX camera found. SONIX sn9c105 + MI0360 
[17179591.664000] /home/rich/spca5xx-20060501/drivers/usb/spca5xx.c: [spca5xx_probe:5480] Camera type JPEG 
[17179591.668000] /home/rich/spca5xx-20060501/drivers/usb/spca5xx.c: [spca5xx_getcapability:1765] maxw 640 maxh 480 minw 176 minh 144
[17179591.676000] usbcore: registered new driver spca5xx
[17179591.676000] /home/rich/spca5xx-20060501/drivers/usb/spca5xx.c: spca5xx driver 00.60.00 registered
```

The actual output in camerama, gqcam, ekiga, etc... is a screen which, by moving the webcam to face the monitor or covering it with my hand I can see minor colour changes - it's mostly white but there are flashes of blue or yellow and it's not really usable. No errors but the display's not usable.

---

### Post by apoth on 2006-10-03
Oh and after a while it crashes the whole machine.

---

### Post by sk1nnycowboy on 2006-10-21
Got mine working with Arnieboy's howto. Good stuff. Had tried Yoriko's howto, but that didnt work for me. Also tried installing Easycam and Easycam2, also no luck. My unit is a quickcam messenger:
Bus 002 Device 003: ID 046d:08da Logitech, Inc.

---

### Post by AdonisV on 2006-10-25
I have 2 webcams, an A4tech-837 and an Intell PC Cam. I wonder if these will work coz none of them is in the SPCA5xx list.. :( I hope they give support for these as well. 

Go Linux!:KS

---

### Post by yaye on 2006-10-25
> **AdonisV said:**
> I have 2 webcams, an A4tech-837 and an **Intell PC Cam**. I wonder if these will work coz none of them is in the SPCA5xx list.. :( I hope they give support for these as well. 

Go Linux!:KS

I know someone who has an Intel USB webcam and it works on Dapper with no driver configuration needed.  He said he just plugged it in and started Gnomemeeting (Ekiga).  I don't know if Intel makes different versions of their webcam.

---

### Post by fakie_flip on 2006-10-25
I've tried for hours more than once to get my webcam to work in Ubuntu. All I can find out about the make and model is that it is a Logitech Quickcam Express. I bought it about 5 years ago. I have used lspci and hwinfo. What can I do? Do the numbers, colons and characters next to it in lspci mean anything useful? I'm asking because someone told me they could help. I must have compiled the wrong driver from source code because it did not work. What else can I do?

---

### Post by Maragato on 2006-10-27
I got a GeniusVideoCam Look, I know the last kernel from edgy was released like yesterday thou I wonder if someone already managed it I'm using kernel 2.6.17-10-386. Can I do like was suggested for the firsts 2.6.xx where I could patch the module and compile it?

---

### Post by amac777 on 2006-11-04
Does anyone know how to install these spca drivers for Edgy? 

I tried following the instructions for dapper and it *almost* worked. The only thing wrong is the colors are messed up. Red objects show up as blue objects etc. But the picture is clear.

---

### Post by ToneDispenser on 2006-11-16
Hi everyone,

thanks to this thread I managed to get my Sunplus Flexcam 100 working in Dapper!

Unfortunately it wasn't as easy as I hoped, but that's due to my cusom kernel.

Problems I had to deal with:
1. You need a patch for kernel v2.6.18
[http://ubuntuforums.org/showpost.php?p=1531572&postcount=272]("http://ubuntuforums.org/showpost.php?p=1531572&postcount=272")

2. Use the same gcc version you compiled your kernel with

3. Compiled driver doesn't seem to work when the webcam is attached to a usb hub.
I have a USB 2.0 Hub and the webcam shows up when I use type 'lsusb'. But all the programs complain that they can't connect to the cam when it's attached to the hub. It works without a hitch when I connect it to the PC directly.

Is there any way to fix this? Do I have to tell the driver that the WebCam is attached to a hub?


Thanks for any hints/tips/suggestions/ideas/whatever :)

---

### Post by ampop on 2006-11-28
Any idea where I find the driver for ACER Aspire 5601 OrbiCam?

---

### Post by Nim on 2007-01-17
When I type in 

"wget http://mxhaard.free.fr/spca50x/Download/spca5xx-20060501.tar.gz"

from arnieboys original step by step guide, I get this message:

"Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name."

any ideas??

---

### Post by ampop on 2007-01-17
> **Nim said:**
> When I type in 

"wget http://mxhaard.free.fr/spca50x/Download/spca5xx-20060501.tar.gz"

from arnieboys original step by step guide, I get this message:

"Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name."

any ideas??

There is new drivers:
for kernel up from 2.6.11 : [gspcav1-20070110.tar.gz]("http://mxhaard.free.fr/spca50x/Download/gspcav1-20070110.tar.gz")
for kernel below 2.6.11: [spca5xx-20060501.tar.gz]("http://mxhaard.free.fr/spca50x/Download/spca5xx-20060501.tar.gz")

---

### Post by Nim on 2007-01-17
Ok i clicked on the links and downloaded, but I still get the same message when I type that command into terminal - do I need to type something different?

---

### Post by ampop on 2007-01-17
> **Nim said:**
> Ok i clicked on the links and downloaded, but I still get the same message when I type that command into terminal - do I need to type something different?

What command did you typed?

---

### Post by Nim on 2007-01-17
"wget http://mxhaard.free.fr/spca50x/Download/spca5xx-20060501.tar.gz"

---

### Post by ampop on 2007-01-17
> **Nim said:**
> "wget http://mxhaard.free.fr/spca50x/Download/spca5xx-20060501.tar.gz"

wget it's a command to download files. If you already have the file, you don't need to do wget.
Type:
```
wget --help
```
for more information.

About the webcam driver, do:
```
sudo apt-get install linux-headers-`uname -r` linux-restricted-modules-`uname -r` build-essential gcc-3.4
tar xvfz spca5xx-20060501.tar.gz
cd spca5xx-20060501
sudo make CC=gcc-3.4
sudo modprobe -r spca5xx
sudo rm -rf /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx*
sudo make install
sudo modprobe spca5xx
```

With my webcam, the 2 driver's didn't worked. May be you have better luck.

---

### Post by Nim on 2007-01-18
I followed your instructions and this is what it says:

naomi@ubuntu:~$ sudo apt-get install linux-headers-`uname -r` linux-restricted-modules-`uname -r` build-essential gcc-3
Password:
Reading package lists... Done
Building dependency tree... Done
linux-headers-2.6.15-27-386 is already the newest version.
linux-restricted-modules-2.6.15-27-386 is already the newest version.
build-essential is already the newest version.
E: Couldn't find package gcc-3
naomi@ubuntu:~$ tar xvfz spca5xx-20060501.tar.gz
tar: spca5xx-20060501.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
naomi@ubuntu:~$

is this because the drivers don't work or because I've done something wrong?

---

### Post by ampop on 2007-01-18
> **Nim said:**
> I followed your instructions and this is what it says:

naomi@ubuntu:~$ sudo apt-get install linux-headers-`uname -r` linux-restricted-modules-`uname -r` build-essential gcc-3
Password:
Reading package lists... Done
Building dependency tree... Done
linux-headers-2.6.15-27-386 is already the newest version.
linux-restricted-modules-2.6.15-27-386 is already the newest version.
build-essential is already the newest version.
E: Couldn't find package gcc-3
naomi@ubuntu:~$ tar xvfz spca5xx-20060501.tar.gz
tar: spca5xx-20060501.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
naomi@ubuntu:~$

is this because the drivers don't work or because I've done something wrong?

About error:
```
E: Couldn't find package gcc-3
```
You must type:
```
sudo apt-get install gcc-3.4
```
Not:
```
sudo apt-get install gcc-3
```

About **tar** error, you must: or go to the path where the file is (cd ...) or:
```
tar xvfz /path-to-file/file.tar.gz
```

If you have more problems with this issue, ask again.

---

### Post by wavesound on 2007-01-20
Hi 
Anyone know how to get The creative Live cam to work on 6.6lt.
I downloaded the spacavxxx file but don't get a make file.
When I sudo Makefile or ./Makefile I get errors:

************

-desktop:/tmp/gspcav1-20070110$ sudo ./Makefile
./Makefile: line 1: VERSION: command not found
./Makefile: line 3: DEFINES: command not found
./Makefile: line 11: DEFINES: command not found
./Makefile: line 21: DEFINES: command not found
./Makefile: line 27: DEFINES: command not found
./Makefile: line 28: VERSION: command not found
./Makefile: line 28: DEFINES: command not found
./Makefile: line 30: syntax error near unexpected token `$(KERNELRELEASE),'
./Makefile: line 30: `ifneq ($(KERNELRELEASE),)   # We were called by kbuild'
***************************

I'm not a programer so am now stuck.
I was aware that this cam is supported under Linux.

Hope you can help.

Cheers
Bob

---

### Post by wavesound on 2007-01-23
Hi
Thanks for this post.
I have the webcam Live cam and have followed these instuctions.
Here is what I get:

******************************************************

studio@studio-desktop:~/downloads/gspcav1-20070110$ sudo rm -rf /lib/modules/`uname -r`/kernel/drivers/usb/media/gspcav1-20070110
studio@studio-desktop:~/downloads/gspcav1-20070110$ sudo make install
mkdir -p /lib/modules/`uname -r`/kernel/drivers/usb/media/
rm -f /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx.ko
rm -f /lib/modules/`uname -r`/kernel/drivers/media/video/gspca.ko
install -c -m 0644 gspca.ko /lib/modules/`uname -r`/kernel/drivers/usb/media/
/sbin/depmod -ae
studio@studio-desktop:~/downloads/gspcav1-20070110$ sudo modprobe gspcav1-20070110
FATAL: Module gspcav1_20070110 not found.

*********************************************************

What am I doing wrong here?
I'm on a new edgy install on this machine.  ;) 


Cheers
Bob

---

### Post by markfoged on 2007-02-20
This made my Logitech Quickcam Messenger work like a charm!

Thanks a lot!

~Kim

---

### Post by SBFC on 2007-03-01
So if you use gspcav1-20070110.tar.gz instead of spca5xx-20060501.tar.gz do the instructions still apply? Do you still insert the spca5xx module or is a different one created with the contents of the gspcv1 tarball?

I used the gspcav1 tarball and followed the instructions and camorama complains that it can't connect to /dev/video0.

---

### Post by berserker on 2007-03-01
> **SBFC said:**
> So if you use gspcav1-20070110.tar.gz instead of spca5xx-20060501.tar.gz do the instructions still apply? Do you still insert the spca5xx module or is a different one created with the contents of the gspcv1 tarball?

I used the gspcav1 tarball and followed the instructions and camorama complains that it can't connect to /dev/video0.

Did you try

```
sudo modprobe gspca
```

Also add gspca to your /etc/modules file.

---

### Post by SBFC on 2007-03-01
Thank you very much. I had to restart as well, but all is working now.

---

### Post by uylenspiegel on 2007-03-08
Nice post however ... I'm stuck at the end : 
```
 sudo modprobe spca5xx
FATAL: Error inserting spca5xx (/lib/modules/2.6.15-26-386/kernel/drivers/usb/media-back/spca5xx.ko): Invalid module format

```
I'm using 
```

Linux version 2.6.15-26-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006

```
Thanks for your help... I'm clueless. :confused: 

Uylenspiegel

---

### Post by fbm on 2007-03-10
Hello to all,

I would just like to verify the previous post about plugging the webcam directly to the USB port at the back of the PC. I had an edimax USB 2.0 hub and connected it initially to it and didn't work. Read the previous post and tried it on  and my webcam now works. It's an A4Tech pk-5 cam. Hope this information is useful to others.

---

### Post by diskotek on 2007-03-14
the instructions on first post worked great with my creative vista plus webcam; (i'm on xubuntu 6.10). i worked it out with ekiga. thank you so much!

but the picture is not so good q&#305;ality, and there is a delay on visiual. this is normal?

---

### Post by fakie_flip on 2007-03-14
I have two webcams. Are either of these ICM532 chipset based webcams?

```
chris@ubuntu:~$ lsusb 
[COLOR="Blue"]Bus 002 Device 007: ID 046d:0840 Logitech, Inc. QuickCam Express
Bus 002 Device 006: ID 046d:0870 Logitech, Inc. QuickCam Express[/COLOR]
Bus 002 Device 005: ID 03f0:0601 Hewlett-Packard ScanJet 6300c
Bus 002 Device 003: ID 046e:5250 Behavior Tech. Computer Corp. 
Bus 002 Device 002: ID 046d:c501 Logitech, Inc. Cordless Mouse Receiver
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
chris@ubuntu:~$ 
```

---

### Post by Ench on 2007-04-05
I have an USB hub, and the camera was connected there and it didn't work, I changed it to another USB port directly to the computer and it works...

The picture is too dark and all... any ideas how to make it better? I've read most of this thread and didn't notice anything about the brightness of the picture.

I have Genius Videocam NB :)

---

### Post by n1nj4Lo on 2007-08-14
I have a Ezonics EzCam III a.k.a. iCatch (VI) PC Camera and a USB2.0 PC Camera (SN9C201) [6 LED Light Night Vision Webcam]

Would either of these work with this code also do I jus open a console and paste the code in there, Or......? Sorry yes I'm a newby to Linux, Thanks in advance...

---

### Post by vivalant on 2007-08-29
There's a single binary-only driver for all the SN9C101, 102, 103, 105, 110, 120, 201, 202 webcams. It supports any V4L1+V4L2 applications and replaces the GSPCA driver (regarding the part of the sn9c1xx controllers). The main difference between the SN9C1XX (in the kernel by default) and the generic SN9CXXX driver (living outside the kernel) is that the latter has more features and supports more hardware.other than applications.
 
The author's homepage is [http://www.linux-projects.org](http://www.linux-projects.org)

---

### Post by peregrine on 2007-11-08
I keep getting this driver when i type make.

```
ason@Lappy:~/Desktop/spca5xx-v4l1goodbye$ make
   Building SPCA5XX driver for 2.5/2.6 kernel.
   Remember: you must have read/write access to your kernel source tree.
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/jason/Desktop/spca5xx-v4l1goodbye CC=cc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/jason/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.o
/home/jason/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:39:26: error: linux/config.h: No such file or directory
/home/jason/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c: In function &#8216;spca50x_init_isoc&#8217;:
/home/jason/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:1623: warning: assignment from incompatible pointer type
/home/jason/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c: In function &#8216;spca5xx_open&#8217;:
/home/jason/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:2394: warning: implicit declaration of function &#8216;video_devdata&#8217;
/home/jason/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:2394: warning: initialization makes pointer from integer without a cast
/home/jason/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:2399: warning: implicit declaration of function &#8216;video_get_drvdata&#8217;
/home/jason/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:2399: warning: initialization makes pointer from integer without a cast
/home/jason/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c: In function &#8216;spca5xx_close&#8217;:
/home/jason/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:2489: warning: initialization makes pointer from integer without a cast
/home/jason/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c: In function &#8216;spca5xx_do_ioctl&#8217;:
/home/jason/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:2549: warning: initialization makes pointer from integer without a cast
/home/jason/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c: In function &#8216;spca5xx_ioctl&#8217;:
/home/jason/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3093: warning: implicit declaration of function &#8216;video_usercopy&#8217;
/home/jason/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c: In function &#8216;spca5xx_read&#8217;:
/home/jason/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3112: warning: initialization makes pointer from integer without a cast
/home/jason/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c: In function &#8216;spca5xx_mmap&#8217;:
/home/jason/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3211: warning: initialization makes pointer from integer without a cast
/home/jason/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c: At top level:
/home/jason/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3263: error: variable &#8216;spca50x_template&#8217; has initializer but incomplete type
/home/jason/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3264: error: unknown field &#8216;owner&#8217; specified in initializer
/home/jason/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3264: warning: excess elements in struct initializer
/home/jason/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3264: warning: (near initialization for &#8216;spca50x_template&#8217;)
/home/jason/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3265: error: unknown field &#8216;name&#8217; specified in initializer
/home/jason/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3265: warning: excess elements in struct initializer
/home/jason/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3265: warning: (near initialization for &#8216;spca50x_template&#8217;)
/home/jason/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3266: error: unknown field &#8216;type&#8217; specified in initializer
/home/jason/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3266: warning: excess elements in struct initializer
/home/jason/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3266: warning: (near initialization for &#8216;spca50x_template&#8217;)
/home/jason/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3267: error: unknown field &#8216;hardware&#8217; specified in initializer
/home/jason/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3267: warning: excess elements in struct initializer
/home/jason/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3267: warning: (near initialization for &#8216;spca50x_template&#8217;)
/home/jason/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3268: error: unknown field &#8216;fops&#8217; specified in initializer
/home/jason/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3268: warning: excess elements in struct initializer
/home/jason/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3268: warning: (near initialization for &#8216;spca50x_template&#8217;)
/home/jason/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3270: error: unknown field &#8216;release&#8217; specified in initializer
/home/jason/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3270: error: &#8216;video_device_release&#8217; undeclared here (not in a function)
/home/jason/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3270: warning: excess elements in struct initializer
/home/jason/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3270: warning: (near initialization for &#8216;spca50x_template&#8217;)
/home/jason/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3272: error: unknown field &#8216;minor&#8217; specified in initializer
/home/jason/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3272: warning: excess elements in struct initializer
/home/jason/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3272: warning: (near initialization for &#8216;spca50x_template&#8217;)
/home/jason/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c: In function &#8216;cd_to_spca50x&#8217;:
/home/jason/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3340: warning: implicit declaration of function &#8216;to_video_device&#8217;
/home/jason/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3340: warning: initialization makes pointer from integer without a cast
/home/jason/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3341: warning: return makes pointer from integer without a cast
/home/jason/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c: In function &#8216;spca50x_create_sysfs&#8217;:
/home/jason/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3450: warning: implicit declaration of function &#8216;video_device_create_file&#8217;
/home/jason/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c: In function &#8216;spca5xx_probe&#8217;:
/home/jason/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5509: warning: implicit declaration of function &#8216;video_device_alloc&#8217;
/home/jason/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5509: warning: assignment makes pointer from integer without a cast
/home/jason/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5512: error: invalid application of &#8216;sizeof&#8217; to incomplete type &#8216;struct video_device&#8217; 
/home/jason/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5512: error: invalid application of &#8216;sizeof&#8217; to incomplete type &#8216;struct video_device&#8217; 
/home/jason/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5512: error: invalid application of &#8216;sizeof&#8217; to incomplete type &#8216;struct video_device&#8217; 
/home/jason/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5514: error: dereferencing pointer to incomplete type
/home/jason/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5516: warning: implicit declaration of function &#8216;video_set_drvdata&#8217;
/home/jason/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5521: warning: implicit declaration of function &#8216;video_register_device&#8217;
/home/jason/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5521: error: &#8216;VFL_TYPE_GRABBER&#8217; undeclared (first use in this function)
/home/jason/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5521: error: (Each undeclared identifier is reported only once
/home/jason/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5521: error: for each function it appears in.)
/home/jason/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5550: error: dereferencing pointer to incomplete type
/home/jason/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5551: warning: implicit declaration of function &#8216;video_device_release&#8217;
/home/jason/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5553: warning: implicit declaration of function &#8216;video_unregister_device&#8217;
make[2]: *** [/home/jason/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.o] Error 1
make[1]: *** [_module_/home/jason/Desktop/spca5xx-v4l1goodbye] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [default] Error 2

```

Can anyone help me please I have a logitech QuickCam for Notebooks.

---

### Post by berserker on 2007-11-08
> **peregrine said:**
> I keep getting this driver when i type make.

```
ason@Lappy:~/Desktop/spca5xx-v4l1goodbye$ make
   Building SPCA5XX driver for 2.5/2.6 kernel.
   Remember: you must have read/write access to your kernel source tree.
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/jason/Desktop/spca5xx-v4l1goodbye CC=cc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/jason/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.o
/home/jason/Desktop/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:39:26: error: linux/config.h: No such file or directory
```

Can anyone help me please I have a logitech QuickCam for Notebooks.

The error is in this line:

```
error: linux/config.h: No such file or directory
```

The makefile is looking for /usr/src/linux-headers-2.6.22-14-generic/include/linux/config.h which you obviously don't have.  I noticed that config.h is missing from some recent kernel sources.  Trying downloading another kernel from kernel.org, untar it and copy the config.h over to the appropriate directory.

HTH

---

### Post by peregrine on 2007-11-09
I searched in 2 different kernals 2.6.22.5 and 2.6.23.1 and ive got no config.h...?

So what should I do Ive got the only version of the kerna I can get from apt-get.

---

### Post by cchevy on 2007-11-17
there are so many pages here...can somebody tell me how to install my intel cs330 webcam on gutsy?

i found spca packages - gspca and spca5xx on synaptic, and the first one has instructions

what do i install on 7.10 and how do i continue? (the first file requires my ubuntu install cd, which i dont have now:(

---

### Post by minospl on 2007-11-18
How install the newest driver GSPCA at Ubuntu 7.10?

---

### Post by newOldUser on 2007-11-18
Take a look at this thread: [http://ubuntuforums.org/showthread.php?t=303330&highlight=gspcav1&page=2](http://ubuntuforums.org/showthread.php?t=303330&highlight=gspcav1&page=2)

at the bottom of the page is a September 11th, 2007 post from binselam. Those instructions should work just fine.  

Before you do them make sure you have downloaded the linux-headers. Use the Synaptic Package Manager on your system to find them and download them.

Also when you are entering the commands be careful.  The Tilde (`) character looks a lot like the apostrophe (') but they are very different in how they operate in the terminal. Most of the commands contain tilde characters.

It would be nice if someone would host a site for this compiled driver.

---

### Post by cchevy on 2007-11-19
Compile it and I'll host it !

Just send me the link on pvt.

---

### Post by shields on 2007-11-19
There needs to be a new thread started with the title: 
*"How to make webcams work on Gutsy."*

---

### Post by newOldUser on 2007-11-22
I have compiled the driver and cchevy has posted it at: [http://365.com.mk/video/andrej/gspca.ko](http://365.com.mk/video/andrej/gspca.ko)

On my Xubuntu 7.10 system the driver is placed in the following directory:
/lib/modules/2.6.22-14-generic/kernel/drivers/usb/media/

If you don't have this directory then my guess is you have a different kernal version then me and the driver may not work for you. In a terminal do the command:
uname -r
or
uname -a
If you have 2.6.22 then there's a good  chance it may work.  Creating the driver wasn't hard if you follow the directions noted in my previous post.

The driver name is gspca.ko

File information:
ls -l gspca*
-rw-r--r-- 1 root root 960780 2007-11-15 18:13 gspca.ko

system information:
uname -a
Linux uServer 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007
i686 GNU/Linux

After installing the driver and attaching your camera enter this in a terminal

dmesg

       you should see some message about a usb device being added (that's your camera)

sudo modprobe gspca

       this will try to associate the driver with the camera

dmesg

       with any luck you'll see some lines at the bottom about the driver initiating.


       If you didn't receive any errors then the driver may be working.

       Enter the command

 tail  /var/log/messages

       this will show you the last 20 or 30 system messages.  Sometimes the gspca driver starts spitting out error messages. You can issue this command as many times as you like and there may be new messages to help you understand why the driver is or is not working.

Good luck

---

### Post by diablo75 on 2008-03-05
I need some help please.  I have Ubuntu Gutsy, and the guide (at least the first of 33 pages of posts) don't include Gutsy.  I'm assuming the install is similar or the same, but I just want to be sure so I don't screw anything up.

I have a  (0733:0401) ViewQuest Technologies, Inc. CS330 WebCam.

What's the best way to get this thing running?

---

### Post by HepBak on 2009-03-19
> **arnieboy said:**
> Some of you probably might have noticed ICM532 chipset based webcams freezing on breezy (for a comprehensive list refer to: [http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html) ) when u turn on gnomemeeting or camorama. Herez the fix for that:
**FOLLOW ALL THE STEPS! DONT TAKE SHORTCUTS OR MAKE MODIFICATIONS IF YOU DON'T KNOW WHAT YOU ARE DOING**
You need to do the following step by step 

**FOR DAPPER and EDGY**
If you are on Dapper or Edgy do the following instead of the above:
```
sudo apt-get install linux-headers-`uname -r` linux-restricted-modules-`uname -r` build-essential
wget http://mxhaard.free.fr/spca50x/Download/spca5xx-20060501.tar.gz
tar xvfz spca5xx-20060501.tar.gz
cd spca5xx-20060501
make
sudo modprobe -r spca5xx
sudo rm -rf /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx*
sudo make install
sudo modprobe spca5xx
```

**FOR BREEZY**
```
sudo apt-get install linux-headers-`uname -r` linux-restricted-modules-`uname -r` build-essential gcc-3.4
wget http://mxhaard.free.fr/spca50x/Download/spca5xx-20060501.tar.gz
tar xvfz spca5xx-20060501.tar.gz
cd spca5xx-20060501
sudo make CC=gcc-3.4
sudo modprobe -r spca5xx
sudo rm -rf /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx*
sudo make install
sudo modprobe spca5xx
```
Now you should be all set to use ur ICM532 chipset based webcam.


 i try to set ICM532 but... 

root@HEPBAK:/home/koko/spca5xx-20060501# sudo make CC=gcc-3.4
   Building SPCA5XX driver for 2.5/2.6 kernel.
   Remember: you must have read/write access to your kernel source tree.
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/koko/spca5xx-20060501 CC=gcc-3.4 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-12-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/koko/spca5xx-20060501/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[1]: *** [_module_/home/koko/spca5xx-20060501] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-12-generic'
make: *** [default] Error 2
 
give me some help please

---

### Post by szirakitamas on 2009-04-09
Hi!
Instead of this: [http://mxhaard.free.fr/spca50x/Download/spca5xx-20060501.tar.gz](http://mxhaard.free.fr/spca50x/Download/spca5xx-20060501.tar.gz) use this:
[http://mxhaard.free.fr/spca50x/Download/gspcav1-20071224.tar.gz](http://mxhaard.free.fr/spca50x/Download/gspcav1-20071224.tar.gz)
maybe! :)
and of course instead of all spca5xx-20060501 use gspcav1-20071224

---

### Post by elcisitiak on 2009-06-01
Okay, I know this is an old topic but how can I make this all work on Jaunty? I get error messages:

```
rel@Set:~$ wget http://mxhaard.free.fr/spca50x/Download/gspcav1-20071224.tar.gz
--2009-05-31 23:22:07--  http://mxhaard.free.fr/spca50x/Download/gspcav1-20071224.tar.gz
Resolving mxhaard.free.fr... 212.27.63.150
Connecting to mxhaard.free.fr|212.27.63.150|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 214717 (210K) [application/x-gzip]
Saving to: `gspcav1-20071224.tar.gz'

100%[======================================>] 214,717     44.8K/s   in 5.3s    

2009-05-31 23:22:13 (39.8 KB/s) - `gspcav1-20071224.tar.gz' saved [214717/214717]

rel@Set:~$ tar xvfz gspcav1-20071224.tar.gz
gspcav1-20071224/
gspcav1-20071224/decoder/
gspcav1-20071224/decoder/gspcadecoder.c
gspcav1-20071224/decoder/gspcadecoder.h
gspcav1-20071224/decoder/gspcadecoder-OSX.c
gspcav1-20071224/decoder/gspcadecoder-OSX.h
gspcav1-20071224/Makefile
gspcav1-20071224/Vimicro/
gspcav1-20071224/Vimicro/vc032x_sensor.h
gspcav1-20071224/Vimicro/zc3xx.h
gspcav1-20071224/Vimicro/cs2102.h
gspcav1-20071224/Vimicro/vc032x.h
gspcav1-20071224/Vimicro/pas106b.h
gspcav1-20071224/Vimicro/icm105a.h
gspcav1-20071224/Vimicro/hv7131b.h
gspcav1-20071224/Vimicro/hv7131c.h
gspcav1-20071224/Vimicro/pb0330.h
gspcav1-20071224/Vimicro/ov7630c.h
gspcav1-20071224/Vimicro/mc501cb.h
gspcav1-20071224/Vimicro/tas5130c_vf0250.h
gspcav1-20071224/Vimicro/ov7620.h
gspcav1-20071224/Vimicro/tas5130c.h
gspcav1-20071224/Vimicro/hdcs2020.h
gspcav1-20071224/Etoms/
gspcav1-20071224/Etoms/et61xx51.h
gspcav1-20071224/Sonix/
gspcav1-20071224/Sonix/sn9cxxx.h
gspcav1-20071224/Sonix/sonix.h
gspcav1-20071224/utils/
gspcav1-20071224/utils/spcagamma.h
gspcav1-20071224/utils/spcausb.h
gspcav1-20071224/utils/spcaCompat.h
gspcav1-20071224/Conexant/
gspcav1-20071224/Conexant/cx11646.h
gspcav1-20071224/Conexant/cxlib.h
gspcav1-20071224/Pixart/
gspcav1-20071224/Pixart/pac207-OSX.h
gspcav1-20071224/Pixart/pac7311.h
gspcav1-20071224/Pixart/pac207.h
gspcav1-20071224/changelog
gspcav1-20071224/license
gspcav1-20071224/gspca_core.c
gspcav1-20071224/Transvision/
gspcav1-20071224/Transvision/tv8532.h
gspcav1-20071224/Makefile.kld
gspcav1-20071224/gspca.h
gspcav1-20071224/Sunplus/
gspcav1-20071224/Sunplus/spca501.dat
gspcav1-20071224/Sunplus/spca505.dat
gspcav1-20071224/Sunplus/spca508.dat
gspcav1-20071224/Sunplus/spca561-OSX.h
gspcav1-20071224/Sunplus/spca506.h
gspcav1-20071224/Sunplus/spca561.h
gspcav1-20071224/Sunplus/spca501_init.h
gspcav1-20071224/Sunplus/spca508_init-OSX.h
gspcav1-20071224/Sunplus/spca508_init.h
gspcav1-20071224/Sunplus/spca501_init-OSX.h
gspcav1-20071224/Sunplus/spca505_init.h
gspcav1-20071224/Sunplus-jpeg/
gspcav1-20071224/Sunplus-jpeg/spca500.dat
gspcav1-20071224/Sunplus-jpeg/jpeg_qtables.h
gspcav1-20071224/Sunplus-jpeg/sp5xxfw2.h
gspcav1-20071224/Sunplus-jpeg/sp5xxfw2.dat
gspcav1-20071224/Sunplus-jpeg/spca500_init.h
gspcav1-20071224/gspca_build
gspcav1-20071224/READ_AND_INSTALL
gspcav1-20071224/Mars-Semi/
gspcav1-20071224/Mars-Semi/mr97311.h
gspcav1-20071224/cutlog.py
rel@Set:~$ cd gspcav1-20071224
rel@Set:~/gspcav1-20071224$ make
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/rel/gspcav1-20071224 CC=cc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
  CC [M]  /home/rel/gspcav1-20071224/gspca_core.o
/home/rel/gspcav1-20071224/gspca_core.c:54:27: error: asm/semaphore.h: No such file or directory
/home/rel/gspcav1-20071224/gspca_core.c: In function ‘spca5xx_ioctl’:
/home/rel/gspcav1-20071224/gspca_core.c:2463: error: implicit declaration of function ‘video_usercopy’
/home/rel/gspcav1-20071224/gspca_core.c: At top level:
/home/rel/gspcav1-20071224/gspca_core.c:2609: error: unknown field ‘owner’ specified in initializer
/home/rel/gspcav1-20071224/gspca_core.c:2609: warning: initialization from incompatible pointer type
/home/rel/gspcav1-20071224/gspca_core.c:2611: error: unknown field ‘type’ specified in initializer
/home/rel/gspcav1-20071224/gspca_core.c: In function ‘spca50x_create_sysfs’:
/home/rel/gspcav1-20071224/gspca_core.c:2769: error: implicit declaration of function ‘video_device_create_file’
/home/rel/gspcav1-20071224/gspca_core.c:2780: error: implicit declaration of function ‘video_device_remove_file’
/home/rel/gspcav1-20071224/gspca_core.c: In function ‘spca5xx_probe’:
/home/rel/gspcav1-20071224/gspca_core.c:4301: error: incompatible types in assignment
make[2]: *** [/home/rel/gspcav1-20071224/gspca_core.o] Error 1
make[1]: *** [_module_/home/rel/gspcav1-20071224] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make: *** [default] Error 2
rel@Set:~/gspcav1-20071224$ sudo modprobe -r spca5xx
FATAL: Module spca5xx not found.
rel@Set:~/gspcav1-20071224$ sudo rm -rf /lib/modules/`uname -r`/kernel/drivers/usb/media/gspcav1*
rel@Set:~/gspcav1-20071224$ sudo make install
mkdir -p /lib/modules/`uname -r`/kernel/drivers/usb/media/
rm -f /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx.ko
rm -f /lib/modules/`uname -r`/kernel/drivers/media/video/gspca.ko
install -c -m 0644 gspca.ko /lib/modules/`uname -r`/kernel/drivers/usb/media/
install: cannot stat `gspca.ko': No such file or directory
make: *** [install] Error 1
rel@Set:~/gspcav1-20071224$ sudo modprobe spca5xx
rel@Set:~/gspcav1-20071224$ rel@Set:~$ tar xvfz spca5xx-20060501.tar.gz
No such file or directory
/home/rel/gsbash: rel@Set:~$: command not found
rel@Set:~/gspcav1-20071224$ tar: spca5xx-20060501.tar.gz: Cannot open: No such file or directory
pcav1-20071224/gspca_core.c: In function ‘spca5xx_ioctl’:
/home/rbash: tar:: command not found
rel@Set:~/gspcav1-20071224$ tar: Error is not recoverable: exiting now
el/gspcav1-20071224/gspca_core.c:2463: erro
bash: tar:: command not found
rel@Set:~/gspcav1-20071224$ tar: Child returned status 2
/home/rel/gspcav1-20071224/g
bash: tar:: command not found
rel@Set:~/gspcav1-20071224$ tar: Error exit delayed from previous errors
/home/rel/gspcav1-20071224/gspca_core.c:2609
bash: tar:: command not found
rel@Set:~/gspcav1-20071224$ rel@Set:~$ cd spca5xx-20060501
/home/rel/gspcav1-20071224/gsp
bash: rel@Set:~$: command not found
rel@Set:~/gspcav1-20071224$ bash: cd: spca5xx-20060501: No such file or directory
/home/rel/gspcav1-20071224/gspca_core.c:2611: error: 
bash: bash:: command not found
rel@Set:~/gspcav1-20071224$ rel@Set:~$ make
/home/rel/gspca
bash: rel@Set:~$: command not found
rel@Set:~/gspcav1-20071224$ make: *** No targets specified and no makefile found.  Stop.
/home/rel/gspcav1-20071224/gspca_core.c:2769: error: implici
bash: make:: command not found
rel@Set:~/gspcav1-20071224$ rel@Set:~$ sudo modprobe -r spca5xx
/home/rel/gspcav1-20071224/gspca_co
bash: rel@Set:~$: command not found
rel@Set:~/gspcav1-20071224$ FATAL: Module spca5xx not found.
/home/rel/gspcav1-20071224/gspca
bash: FATAL:: command not found
rel@Set:~/gspcav1-20071224$ rel@Set:~$ sudo rm -rf /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx*rel@Set:~$ sudo make install
/home/rel/gspcav1-20071224/gspca_core.c:4301: error: incompatible types in assignment
make[2]: *** [/home/rebash: rel@Set:~$: command not found
rel@Set:~/gspcav1-20071224$ make: *** No rule to make target `install'.  Stop.
l/gspcav1-20071224/gspca_core.o] Error 1
make[1]: *> rel@Set:~$ sudo modprobe spca5xxsudo apt-get install linux-headers-`linux-restricted-modules-`uname -r` build-essential
> FATAL: Module spca5xxsudo not found.
> rel@Set:~$ wget http://mxhaard.free.fr/spca50x/Download/gspcav1-20071224.tar.gz
> --2009-05-31 23:22:07--  http://mxhaard.free.fr/spca50x/Download/gspcav1-20071224.tar.gz
> Resolving mxhaard.free.fr... 212.27.63.150
> Connecting to mxhaard.free.fr|212.27.63.150|:80... connected.
> HTTP request sent, awaiting response... 200 OK
> Length: 214717 (210K) [application/x-gzip]
> Saving to: `gspcav1-20071224.tar.gz'
> 
> 100%[======================================>] 214,717     44.8K/s   in 5.3s    
> 
> 2009-05-31 23:22:13 (39.8 KB/s) - `gspcav1-20071224.tar.gz' saved [214717/214717]
bash: command substitution: line 1: unexpected EOF while looking for matching `''
** [_module_/home/rel/gspcav1-20071224] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make: *** [default] Error 2
rel@Set:~/gspcav1-20071224$ sudo modprobe -r spca5xx
FATAL: Module spca5xx not found.
rel@Set:~/gspcav1-20071224$ sudo rm -rf /lib/modules/`uname -r`/kernel/drivers/usb/media/gspcav1*
rel@Set:~/gspcav1-20071224$ sudo make install
mkdir -p /lib/modules/`uname -r`/kernel/drivers/usb/media/
rm -f /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx.ko
rm -f /lib/modules/`uname -r`/kernel/drivers/media/video/gspca.ko
install -c -m 0644 gspca.ko /lib/modules/`uname -r`/kernel/drivers/usb/media/
install: cannot stat `gspca.ko': No such file or directory
make: *** [install] Error 1
bash: command substitution: line 3: syntax error: unexpected end of file
bash: linux-restricted-modules-: command not found
bash: build-essential: command not found
bash: FATAL:: command not found
bash: rel@Set:~$: command not found
bash: --2009-05-31: command not found
bash: Resolving: command not found
bash: :80...: command not found
bash: 212.27.63.150: command not found
bash: Connecting: command not found
bash: HTTP: command not found
bash: command substitution: line 8: syntax error near unexpected token `('
bash: command substitution: line 8: `Length: 214717 (210K) [application/x-gzip]'
bash: make:: command not found
rel@Set:~/gspcav1-20071224$ 
rel@Set:~/gspcav1-20071224$ rel@Set:~$ tar xvfz gspcav1-20071224.tar.gz
bash: rel@Set:~$: command not found
rel@Set:~/gspcav1-20071224$ gspcav1-20071224/
bash: gspcav1-20071224/: No such file or directory
rel@Set:~/gspcav1-20071224$ gspcav1-20071224/decoder/
bash: gspcav1-20071224/decoder/: No such file or directory
rel@Set:~/gspcav1-20071224$ gspcav1-20071224/decoder/gspcadecoder.c
bash: gspcav1-20071224/decoder/gspcadecoder.c: No such file or directory
rel@Set:~/gspcav1-20071224$ gspcav1-20071224/decoder/gspcadecoder.h
bash: gspcav1-20071224/decoder/gspcadecoder.h: No such file or directory
rel@Set:~/gspcav1-20071224$ gspcav1-20071224/decoder/gspcadecoder-OSX.c
bash: gspcav1-20071224/decoder/gspcadecoder-OSX.c: No such file or directory
rel@Set:~/gspcav1-20071224$ gspcav1-20071224/decoder/gspcadecoder-OSX.h
bash: gspcav1-20071224/decoder/gspcadecoder-OSX.h: No such file or directory
rel@Set:~/gspcav1-20071224$ gspcav1-20071224/Makefile
bash: gspcav1-20071224/Makefile: No such file or directory
rel@Set:~/gspcav1-20071224$ gspcav1-20071224/Vimicro/
bash: gspcav1-20071224/Vimicro/: No such file or directory
rel@Set:~/gspcav1-20071224$ gspcav1-20071224/Vimicro/vc032x_sensor.h
bash: gspcav1-20071224/Vimicro/vc032x_sensor.h: No such file or directory
rel@Set:~/gspcav1-20071224$ gspcav1-20071224/Vimicro/zc3xx.h
bash: gspcav1-20071224/Vimicro/zc3xx.h: No such file or directory
rel@Set:~/gspcav1-20071224$ gspcav1-20071224/Vimicro/cs2102.h
bash: gspcav1-20071224/Vimicro/cs2102.h: No such file or directory
rel@Set:~/gspcav1-20071224$ gspcav1-20071224/Vimicro/vc032x.h
bash: gspcav1-20071224/Vimicro/vc032x.h: No such file or directory
rel@Set:~/gspcav1-20071224$ gspcav1-20071224/Vimicro/pas106b.h
bash: gspcav1-20071224/Vimicro/pas106b.h: No such file or directory
rel@Set:~/gspcav1-20071224$ gspcav1-20071224/Vimicro/icm105a.h
bash: gspcav1-20071224/Vimicro/icm105a.h: No such file or directory
rel@Set:~/gspcav1-20071224$ gspcav1-20071224/Vimicro/hv7131b.h
bash: gspcav1-20071224/Vimicro/hv7131b.h: No such file or directory
rel@Set:~/gspcav1-20071224$ gspcav1-20071224/Vimicro/hv7131c.h
bash: gspcav1-20071224/Vimicro/hv7131c.h: No such file or directory
rel@Set:~/gspcav1-20071224$ gspcav1-20071224/Vimicro/pb0330.h
bash: gspcav1-20071224/Vimicro/pb0330.h: No such file or directory
rel@Set:~/gspcav1-20071224$ gspcav1-20071224/Vimicro/ov7630c.h
bash: gspcav1-20071224/Vimicro/ov7630c.h: No such file or directory
rel@Set:~/gspcav1-20071224$ gspcav1-20071224/Vimicro/mc501cb.h
bash: gspcav1-20071224/Vimicro/mc501cb.h: No such file or directory
rel@Set:~/gspcav1-20071224$ gspcav1-20071224/Vimicro/tas5130c_vf0250.h
bash: gspcav1-20071224/Vimicro/tas5130c_vf0250.h: No such file or directory
rel@Set:~/gspcav1-20071224$ gspcav1-20071224/Vimicro/ov7620.h
bash: gspcav1-20071224/Vimicro/ov7620.h: No such file or directory
rel@Set:~/gspcav1-20071224$ gspcav1-20071224/Vimicro/tas5130c.h
bash: gspcav1-20071224/Vimicro/tas5130c.h: No such file or directory
rel@Set:~/gspcav1-20071224$ gspcav1-20071224/Vimicro/hdcs2020.h
bash: gspcav1-20071224/Vimicro/hdcs2020.h: No such file or directory
rel@Set:~/gspcav1-20071224$ gspcav1-20071224/Etoms/
bash: gspcav1-20071224/Etoms/: No such file or directory
rel@Set:~/gspcav1-20071224$ gspcav1-20071224/Etoms/et61xx51.h
bash: gspcav1-20071224/Etoms/et61xx51.h: No such file or directory
rel@Set:~/gspcav1-20071224$ gspcav1-20071224/Sonix/
bash: gspcav1-20071224/Sonix/: No such file or directory
rel@Set:~/gspcav1-20071224$ gspcav1-20071224/Sonix/sn9cxxx.h
bash: gspcav1-20071224/Sonix/sn9cxxx.h: No such file or directory
rel@Set:~/gspcav1-20071224$ gspcav1-20071224/Sonix/sonix.h
bash: gspcav1-20071224/Sonix/sonix.h: No such file or directory
rel@Set:~/gspcav1-20071224$ gspcav1-20071224/utils/
bash: gspcav1-20071224/utils/: No such file or directory
rel@Set:~/gspcav1-20071224$ gspcav1-20071224/utils/spcagamma.h
bash: gspcav1-20071224/utils/spcagamma.h: No such file or directory
rel@Set:~/gspcav1-20071224$ gspcav1-20071224/utils/spcausb.h
bash: gspcav1-20071224/utils/spcausb.h: No such file or directory
rel@Set:~/gspcav1-20071224$ gspcav1-20071224/utils/spcaCompat.h
bash: gspcav1-20071224/utils/spcaCompat.h: No such file or directory
rel@Set:~/gspcav1-20071224$ gspcav1-20071224/Conexant/
bash: gspcav1-20071224/Conexant/: No such file or directory
rel@Set:~/gspcav1-20071224$ gspcav1-20071224/Conexant/cx11646.h
bash: gspcav1-20071224/Conexant/cx11646.h: No such file or directory
rel@Set:~/gspcav1-20071224$ gspcav1-20071224/Conexant/cxlib.h
bash: gspcav1-20071224/Conexant/cxlib.h: No such file or directory
rel@Set:~/gspcav1-20071224$ gspcav1-20071224/Pixart/
bash: gspcav1-20071224/Pixart/: No such file or directory
rel@Set:~/gspcav1-20071224$ gspcav1-20071224/Pixart/pac207-OSX.h
bash: gspcav1-20071224/Pixart/pac207-OSX.h: No such file or directory
rel@Set:~/gspcav1-20071224$ gspcav1-20071224/Pixart/pac7311.h
bash: gspcav1-20071224/Pixart/pac7311.h: No such file or directory
rel@Set:~/gspcav1-20071224$ gspcav1-20071224/Pixart/pac207.h
bash: gspcav1-20071224/Pixart/pac207.h: No such file or directory
rel@Set:~/gspcav1-20071224$ gspcav1-20071224/changelog
bash: gspcav1-20071224/changelog: No such file or directory
rel@Set:~/gspcav1-20071224$ gspcav1-20071224/license
bash: gspcav1-20071224/license: No such file or directory
rel@Set:~/gspcav1-20071224$ gspcav1-20071224/gspca_core.c
bash: gspcav1-20071224/gspca_core.c: No such file or directory
rel@Set:~/gspcav1-20071224$ gspcav1-20071224/Transvision/
bash: gspcav1-20071224/Transvision/: No such file or directory
rel@Set:~/gspcav1-20071224$ gspcav1-20071224/Transvision/tv8532.h
bash: gspcav1-20071224/Transvision/tv8532.h: No such file or directory
rel@Set:~/gspcav1-20071224$ gspcav1-20071224/Makefile.kld
bash: gspcav1-20071224/Makefile.kld: No such file or directory
rel@Set:~/gspcav1-20071224$ gspcav1-20071224/gspca.h
bash: gspcav1-20071224/gspca.h: No such file or directory
rel@Set:~/gspcav1-20071224$ gspcav1-20071224/Sunplus/
bash: gspcav1-20071224/Sunplus/: No such file or directory
rel@Set:~/gspcav1-20071224$ gspcav1-20071224/Sunplus/spca501.dat
bash: gspcav1-20071224/Sunplus/spca501.dat: No such file or directory
rel@Set:~/gspcav1-20071224$ gspcav1-20071224/Sunplus/spca505.dat
bash: gspcav1-20071224/Sunplus/spca505.dat: No such file or directory
rel@Set:~/gspcav1-20071224$ gspcav1-20071224/Sunplus/spca508.dat
bash: gspcav1-20071224/Sunplus/spca508.dat: No such file or directory
rel@Set:~/gspcav1-20071224$ gspcav1-20071224/Sunplus/spca561-OSX.h
bash: gspcav1-20071224/Sunplus/spca561-OSX.h: No such file or directory
rel@Set:~/gspcav1-20071224$ gspcav1-20071224/Sunplus/spca506.h
bash: gspcav1-20071224/Sunplus/spca506.h: No such file or directory
rel@Set:~/gspcav1-20071224$ gspcav1-20071224/Sunplus/spca561.h
bash: gspcav1-20071224/Sunplus/spca561.h: No such file or directory
rel@Set:~/gspcav1-20071224$ gspcav1-20071224/Sunplus/spca501_init.h
bash: gspcav1-20071224/Sunplus/spca501_init.h: No such file or directory
rel@Set:~/gspcav1-20071224$ gspcav1-20071224/Sunplus/spca508_init-OSX.h
bash: gspcav1-20071224/Sunplus/spca508_init-OSX.h: No such file or directory
rel@Set:~/gspcav1-20071224$ gspcav1-20071224/Sunplus/spca508_init.h
bash: gspcav1-20071224/Sunplus/spca508_init.h: No such file or directory
rel@Set:~/gspcav1-20071224$ gspcav1-20071224/Sunplus/spca501_init-OSX.h
bash: gspcav1-20071224/Sunplus/spca501_init-OSX.h: No such file or directory
rel@Set:~/gspcav1-20071224$ gspcav1-20071224/Sunplus/spca505_init.h
bash: gspcav1-20071224/Sunplus/spca505_init.h: No such file or directory
rel@Set:~/gspcav1-20071224$ gspcav1-20071224/Sunplus-jpeg/
bash: gspcav1-20071224/Sunplus-jpeg/: No such file or directory
rel@Set:~/gspcav1-20071224$ gspcav1-20071224/Sunplus-jpeg/spca500.dat
bash: gspcav1-20071224/Sunplus-jpeg/spca500.dat: No such file or directory
rel@Set:~/gspcav1-20071224$ gspcav1-20071224/Sunplus-jpeg/jpeg_qtables.h
bash: gspcav1-20071224/Sunplus-jpeg/jpeg_qtables.h: No such file or directory
rel@Set:~/gspcav1-20071224$ gspcav1-20071224/Sunplus-jpeg/sp5xxfw2.h
bash: gspcav1-20071224/Sunplus-jpeg/sp5xxfw2.h: No such file or directory
rel@Set:~/gspcav1-20071224$ gspcav1-20071224/Sunplus-jpeg/sp5xxfw2.dat
bash: gspcav1-20071224/Sunplus-jpeg/sp5xxfw2.dat: No such file or directory
rel@Set:~/gspcav1-20071224$ gspcav1-20071224/Sunplus-jpeg/spca500_init.h
bash: gspcav1-20071224/Sunplus-jpeg/spca500_init.h: No such file or directory
rel@Set:~/gspcav1-20071224$ gspcav1-20071224/gspca_build
bash: gspcav1-20071224/gspca_build: No such file or directory
rel@Set:~/gspcav1-20071224$ gspcav1-20071224/READ_AND_INSTALL
bash: gspcav1-20071224/READ_AND_INSTALL: No such file or directory
rel@Set:~/gspcav1-20071224$ gspcav1-20071224/Mars-Semi/
bash: gspcav1-20071224/Mars-Semi/: No such file or directory
rel@Set:~/gspcav1-20071224$ gspcav1-20071224/Mars-Semi/mr97311.h
bash: gspcav1-20071224/Mars-Semi/mr97311.h: No such file or directory
rel@Set:~/gspcav1-20071224$ gspcav1-20071224/cutlog.py
bash: gspcav1-20071224/cutlog.py: No such file or directory
rel@Set:~/gspcav1-20071224$ rel@Set:~$ cd gspcav1-20071224
bash: rel@Set:~$: command not found
rel@Set:~/gspcav1-20071224$ rel@Set:~/gspcav1-20071224$ make
bash: rel@Set:~/gspcav1-20071224$: No such file or directory
rel@Set:~/gspcav1-20071224$ make -C /lib/modules/`uname -r`/build SUBDIRS=/home/rel/gspcav1-20071224 CC=cc modules
make: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
  CC [M]  /home/rel/gspcav1-20071224/gspca_core.o
/home/rel/gspcav1-20071224/gspca_core.c:54:27: error: asm/semaphore.h: No such file or directory
/home/rel/gspcav1-20071224/gspca_core.c: In function ‘spca5xx_ioctl’:
/home/rel/gspcav1-20071224/gspca_core.c:2463: error: implicit declaration of function ‘video_usercopy’
/home/rel/gspcav1-20071224/gspca_core.c: At top level:
/home/rel/gspcav1-20071224/gspca_core.c:2609: error: unknown field ‘owner’ specified in initializer
/home/rel/gspcav1-20071224/gspca_core.c:2609: warning: initialization from incompatible pointer type
/home/rel/gspcav1-20071224/gspca_core.c:2611: error: unknown field ‘type’ specified in initializer
/home/rel/gspcav1-20071224/gspca_core.c: In function ‘spca50x_create_sysfs’:
/home/rel/gspcav1-20071224/gspca_core.c:2769: error: implicit declaration of function ‘video_device_create_file’
/home/rel/gspcav1-20071224/gspca_core.c:2780: error: implicit declaration of function ‘video_device_remove_file’
/home/rel/gspcav1-20071224/gspca_core.c: In function ‘spca5xx_probe’:
/home/rel/gspcav1-20071224/gspca_core.c:4301: error: incompatible types in assignment
make[1]: *** [/home/rel/gspcav1-20071224/gspca_core.o] Error 1
make: *** [_module_/home/rel/gspcav1-20071224] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
rel@Set:~/gspcav1-20071224$ make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
>   CC [M]  /home/rel/gspcav1-20071224/gspca_core.o
> /home/rel/gspcav1-20071224/gspca_core.c:54:27: error: asm/semaphore.h: No such file or directory
> /home/rel/gspcav1-20071224/gspca_core.c: In function ‘spca5xx_ioctl’:
> /home/rel/gspcav1-20071224/gspca_core.c:2463: erro
> /home/rel/gspcav1-20071224/g
> /home/rel/gspcav1-20071224/gspca_core.c:2609
> /home/rel/gspcav1-20071224/gsp
> /home/rel/gspcav1-20071224/gspca_core.c:2611: error: 
> /home/rel/gspca
> /home/rel/gspcav1-20071224/gspca_core.c:2769: error: implici
> /home/rel/gspcav1-20071224/gspca_co
> /home/rel/gspcav1-20071224/gspca
> /home/rel/gspcav1-20071224/gspca_core.c:4301: error: incompatible types in assignment
> make[2]: *** [/home/rel/gspcav1-20071224/gspca_core.o] Error 1
> make[1]: *** [_module_/home/rel/gspcav1-20071224] Error 2
> make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
> make: *** [default] Error 2
> rel@Set:~/gspcav1-20071224$ sudo modprobe -r spca5xx
> FATAL: Module spca5xx not found.
> rel@Set:~/gspcav1-20071224$ sudo rm -rf /lib/modules/`uname -r`/kernel/drivers/usb/media/gspcav1*
> rel@Set:~/gspcav1-20071224$ sudo make install
> mkdir -p /lib/modules/`uname -r`/kernel/drivers/usb/media/
> rm -f /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx.ko
> rm -f /lib/modules/`uname -r`/kernel/drivers/media/video/gspca.ko
> install -c -m 0644 gspca.ko /lib/modules/`uname -r`/kernel/drivers/usb/media/
> install: cannot stat `gspca.ko': No such file or directory
bash: command substitution: line 1: unexpected EOF while looking for matching `''
bash: command substitution: line 18: syntax error: unexpected end of file
bash: make[1]:: command not found
rel@Set:~/gspcav1-20071224$ make: *** [install] Error 1
bash: make:: command not found

```

I get the feeling I'm missing something rather simple... help me?

---

### Post by lng80 on 2009-06-06
I'm also having trouble getting this to work in Jaunty...bump.

---

