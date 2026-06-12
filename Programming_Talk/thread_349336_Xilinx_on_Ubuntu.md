---
title: "Xilinx on Ubuntu?"
date: 2007-01-30
forum: Programming Talk
---

### Post by Jonas_Henricsson on 2007-01-30
I've been trying to get Xilinx (Webpack) to work on my Ubuntu system but I have been unsuccessful. It's supposed to work for linux system. I've installed it, but I can't find any .exe-file or corresponding file. Does anyone know anything about this?

Downloaded this: [http://www.xilinx.com/ise/logic_design_prod/webpack.htm](http://www.xilinx.com/ise/logic_design_prod/webpack.htm)

---

### Post by regomodo on 2007-05-05
hi, any luck?

I have tried to install it before as well. I did it through terminal but it died halfway through.

I used the xilinx7.1 from the classics download.


Just redownloading it now and will let you know if i have any success

---

### Post by regomodo on 2007-05-05
so far, so bad.

```
root@jon-ubuntu:/home/jon# sh '/home/jon/Desktop/WebPACK_71_fcfull_i.sh' 
Verifying archive integrity... All good.
Uncompressing Xilinx ISE WebPACK Installer.............................................................................................................................................................................
/tmp/selfgz10805/platform/lin/bin/lin
/tmp/selfgz10805/platform/lin/xilsetup: error while loading shared libraries: libXm.so.3: cannot open shared object file: No such file or directory


************ setup done! ***************

/usr/bin/nohup: cannot run command `./windu_registryd50': No such file or directory
root@jon-ubuntu:/home/jon# 
```

---

### Post by biovore on 2007-05-20
I have ISE 9.1i and the EDK working here on Kubuntu..  It is not a run the installer and go install though.  You will need to install libstc++5 (gcc-3.3) to get all the correct libs.  After install you will have to manualy add some enviroment vars.  (watch when it installs. It give you the vars you have to add..  but it fails to add them for some reason)  So in sumation it works, but you will have to use a large hammer.  Also note that the Xilinx USB tag also work, but requires you to setup the usb driver.    This tools tagets redhat 9 so you have to provide all that compatiblity crap.  
Some usefull links: [http://www.itee.uq.edu.au/~listarch/microblaze-uclinux/archive/2007/03/msg00101.html](http://www.itee.uq.edu.au/~listarch/microblaze-uclinux/archive/2007/03/msg00101.html)    [http://stefan.endrullis.de/en/xilinx_ise_7.1.html](http://stefan.endrullis.de/en/xilinx_ise_7.1.html)

---

### Post by mbmsv on 2007-06-01
> **biovore said:**
> I have ISE 9.1i and the EDK working here on Kubuntu..  It is not a run the installer and go install though.  You will need to install libstc++5 (gcc-3.3) to get all the correct libs.  

Hi! I am having difficulty with getting the EDK91 to work on Kubuntu 7.04. When I try to start it I get  the following:

_xps: error while loading shared libraries: libPortability.so : cannot open  shared object file : no such file or directory.

If I set LD_ASSUME_KERNEL=2.4.7 (or 2.4.1) then it seems to break something  severely in bash so that I can't even do printenv and xps doesn't start  either... I suspect that the problem might have something to do with the  fact that I have both libstdc++5 and libstdc++6 installed. I am not sure now at which point libstdc++6 was installed  and what will I break if I try uninstalling it...

All other environment variables seem to be set correctly, at least in the  bash session I am using to launch the app...ISE launches fine as well as  Impact does...

Thanks,
/Mikhail

---

### Post by mbmsv on 2007-06-01
> **mbmsv said:**
> Hi! I am having difficulty with getting the EDK91 to work on Kubuntu 7.04. When I try to start it I get  the following:

_xps: error while loading shared libraries: libPortability.so : cannot open  shared object file : no such file or directory.

/Mikhail

I have found that the library in question is in fact in the ISE directory $XILINX/bin/lin. I copied it into $XILINX_EDK/bin/lin (which is set to LD_LIBRARY_PATH) and it complained about another library, which I also found in the ISE tree. After I copied a few dozens of these libraries xps finally started, but with a blank window :( 

Arghh... What am I missing here?...

Thanks,
/Mikhail

---

### Post by mbmsv on 2007-06-01
The problem has been solved:

$ export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$XILINX/bin/lin


/Mikhail

---

### Post by regomodo on 2007-06-04
Hi, i couldn't get it to work using the .bin file so i installed in wine.

Seems to be ok atm but 1 thing i have noticed is it gets the layou/fonts all a bit wrong when zoomed out from 100%.

Here are 2 screengrabs to show what i mean

---

### Post by kunal_noob on 2007-08-30
Hi 
I'm trying to install ISE Webpack 9.1i on my AMD64 Ubuntu Feisty. 

After starting the installation, at one point it gives out the message:



```
kunal@Flanker:~/inst$ sudo ./setup
/home/kunal/inst/bin/lin/_setup: error while loading shared libraries: 
libXcursor.so.1: cannot open shared object file: No such file or directory
```


I can't figure out where this library comes from! Help!

cheers,
Kunal

---

### Post by xylometazolin on 2007-11-28
I'm also using Ubuntu on an AMD64 architecture and Xilinx is running well.

In case of missing libraries, an easy solution is to search for the missing file (libXcursor.so.1) on [http://packages.ubuntu.com/](http://packages.ubuntu.com/). Use the second input field and don't forget to set distribution and architecture.

In your case there are 2 packages containing the file.
- package libxcursor1 contains /usr/lib/libXcursor.so.1
- package ia32-libs contains /usr/lib32/libXcursor.so.1

So you need to install:
- libxcursor1 if you are using a 64 bit version of Xilinx
- ia32-libs if you are using a 32 bit version of Xilinx

Sometimes you have the problem that you cannot find a package with the 32 bit library you are missing. Then you need to choose "Intel x86" as architecture, download the package manually and extract the content to a temporary directory and copy the files located in $unpacked/lib/ to /lib32/ and the files located in $unpacked/usr/lib/ to /usr/lib32/.

There is no problem to get a 32 bit programm running on a 64 bit operating system. The only problem is, that in some cases you cannot install the necessary packages via apt-get.

---

### Post by t.rain on 2008-04-21
> **mbmsv said:**
> Hi! I am having difficulty with getting the EDK91 to work on Kubuntu 7.04. When I try to start it I get  the following:

_xps: error while loading shared libraries: libPortability.so : cannot open  shared object file : no such file or directory.

If I set LD_ASSUME_KERNEL=2.4.7 (or 2.4.1) then it seems to break something  severely in bash so that I can't even do printenv and xps doesn't start  either... I suspect that the problem might have something to do with the  fact that I have both libstdc++5 and libstdc++6 installed. I am not sure now at which point libstdc++6 was installed  and what will I break if I try uninstalling it...

All other environment variables seem to be set correctly, at least in the  bash session I am using to launch the app...ISE launches fine as well as  Impact does...

Thanks,
/Mikhail

Hi everybody,

I **encountered exactly the same** problems on OpenSUSE. I posted a HOW-TO to get rid of it at my homepage:

[COLOR="DarkRed"][http://thomasreinbacher.wasner.it](http://thomasreinbacher.wasner.it)[/COLOR]

greetings,
Thomas

---

### Post by josheeg on 2009-10-30
I think I installed it but didn't expect problems. I didn't get any everything installed fine. 

Except I did not install the programmer stuff & I see no icons is their some command I type in the command prompt or a whereis to find the files I installed?

I should have paid more attention to the installation.:popcorn:

---

### Post by ole2 on 2010-08-06
> **mbmsv said:**
> I have found that the library in question is in fact in the ISE directory $XILINX/bin/lin. I copied it into $XILINX_EDK/bin/lin (which is set to LD_LIBRARY_PATH) and it complained about another library, which I also found in the ISE tree. After I copied a few dozens of these libraries xps finally started, but with a blank window :( 

Arghh... What am I missing here?...

Thanks,
/Mikhail

blank window inside Xilinx XPS remain until following missing libraries aren't installed:
libqt3-mt and libqt3-mt-dev

---

