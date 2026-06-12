---
title: "Problem instaling ATI Catalyst Video Driver"
date: 2014-03-25
forum: New to Ubuntu
---

### Post by we-are-the-forsaken on 2014-03-25
HI ! 

I am a new user to Linux and i get a problem while i try to install the ATI Catalyst driver. I got Linux Ubuntu 12.04 LTS 32 bit and 
graphic card Mobility Radeon HD 5430
I found guide and tryed to do it like they say :
[http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-ati-catalyst-video-drivers-fglrx/126513#126513](http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-ati-catalyst-video-drivers-fglrx/126513#126513)

1.) I started with the terminall command :
```

sudo apt-get install build-essential cdbs fakeroot dh-make debhelper debconf libstdc++6 dkms libqtgui4 wget execstack libelfg0 dh-modaliases
(no problems)

```
2.) I downloadet the Ati Catalyst driver from the officall Ati site and extract it under :
FOLDER : clawfingaz@ClawFingaS:~/ati$ FILE NAME :amd-catalyst-13.12-linux-x86.x86_64.run

3.) Next i did the terminal command :
```

sudo sh *.run --buildpkg Ubuntu/precise 
This created me 4 files :
fglrx_8.961-0ubuntu1_amd64.deb
fglrx-amdcccle_8.961-0ubuntu1_amd64.deb
fglrx-dev_8.961-0ubuntu1_amd64.deb
fglrx-installer_13.251-0ubuntu1_i386.changes
```

4.) Here is the problem . When i try to install the driver with the terinal command :

```
sudo dpkg -i *.deb
```
i get this error ( i copy - pasted it from the terminal ) :

```
clawfingaz@ClawFingaS:~/ati$ sudo dpkg -i *.deb
Selecting previously unselected package fglrx.
(Reading database ... 148899 files and directories currently installed.)
Unpacking fglrx (from fglrx_13.251-0ubuntu1_i386.deb) ...
Selecting previously unselected package fglrx-amdcccle.
Unpacking fglrx-amdcccle (from fglrx-amdcccle_13.251-0ubuntu1_i386.deb) ...
Selecting previously unselected package fglrx-dev.
Unpacking fglrx-dev (from fglrx-dev_13.251-0ubuntu1_i386.deb) ...
dpkg: dependency problems prevent configuration of fglrx:
fglrx depends on linux-headers-generic | linux-headers-generic-lts-quantal | linux-headers; however:
  Package linux-headers-generic is not installed.
  Package linux-headers-generic-lts-quantal is not installed.
  Package linux-headers is not installed.
dpkg: error processing fglrx (--install):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of fglrx-amdcccle:
fglrx-amdcccle depends on fglrx; however:
  Package fglrx is not configured yet.
dpkg: error processing fglrx-amdcccle (--install):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of fglrx-dev:
fglrx-dev depends on fglrx; however:
  Package fglrx is not configured yet.
dpkg: error processing fglrx-dev (--install):
dependency problems - leaving unconfigured
Processing triggers for ureadahead ...
Errors were encountered while processing: 
fglrx 
fglrx-amdcccle
fglrx-dev
```
Can someone help me ? =)

---

### Post by bshatt1987 on 2014-03-25
I think you might try 
```
sudo apt-get -f install
```
Then try installing the driver packages again.

If not, go through and try to install the headers that it says are missing, so:
```
sudo apt-get install [COLOR=#333333][FONT=Ubuntu]linux-headers-generic linux-headers-generic-lts-quantal linux-headers[/FONT][/COLOR]
```
Then try installing the driver packages.

---

### Post by we-are-the-forsaken on 2014-03-25
This helped after i did
 sodu apt-get -f install  
I was able to run 
```
sudo dpkg -i *.deb
```
And this is what i get :```

clawfingaz@ClawFingaS:~/ati$ sudo dpkg -i *.deb
(Reading database ... 171479 files and directories currently installed.)
Preparing to replace fglrx 2:13.251-0ubuntu1 (using fglrx_13.251-0ubuntu1_i386.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement fglrx ...
Preparing to replace fglrx-amdcccle 2:13.251-0ubuntu1 (using fglrx-amdcccle_13.251-0ubuntu1_i386.deb) ...
Unpacking replacement fglrx-amdcccle ...
Preparing to replace fglrx-dev 2:13.251-0ubuntu1 (using fglrx-dev_13.251-0ubuntu1_i386.deb) ...
Unpacking replacement fglrx-dev ...
Setting up fglrx (2:13.251-0ubuntu1) ...
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group i386-linux-gnu_gl_conf is broken.
update-alternatives: warning: skip creation of /usr/lib32/libaticalcl.so because associated file /usr/lib32/fglrx/libaticalcl.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalrt.so because associated file /usr/lib32/fglrx/libaticalrt.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group i386-linux-gnu_gl_conf is broken.
update-alternatives: warning: skip creation of /usr/lib32/libaticalcl.so because associated file /usr/lib32/fglrx/libaticalcl.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalrt.so because associated file /usr/lib32/fglrx/libaticalrt.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-initramfs: deferring update (trigger activated)
Loading new fglrx-13.251 DKMS files...
Building only for 3.11.0-15-generic
Building for architecture i686
Building initial module for 3.11.0-15-generic
Error! Bad return status for module build on kernel: 3.11.0-15-generic (i686)
Consult /var/lib/dkms/fglrx/13.251/build/make.log for more information.
update-initramfs: deferring update (trigger activated)
Processing triggers for ureadahead ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Setting up fglrx-amdcccle (2:13.251-0ubuntu1) ...
Setting up fglrx-dev (2:13.251-0ubuntu1) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.11.0-15-generic
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

```
there is and error inside .. i dont know is this good or not but i was going ahed true the instalation guid and typed :
[h=3]Continuing with the installation, type:[/h]sudo aticonfig --initial

this is from terminal :
```

[/FONT][/COLOR]clawfingaz@ClawFingaS:~/ati$ sudo aticonfig --initial
Found fglrx primary device section
Using /etc/X11/xorg.conf
Saving back-up to /etc/X11/xorg.conf.fglrx-0
```

after this i rebooted the computer as the guide say  and after this i tryed :
```
**Now go ahead and reboot your computer.**
If all is right, the fglrx driver that corresponds to AMD/ATI Catalyst will be installed and working on your system. To confirm the drivers are working open a terminal and type:
fglrxinfo
You should get an output similar to the following:
display: :0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: ATI Radeon HD 4300/4500 Series
OpenGL version string: 3.3.11631 Compatibility Profile Context
but i get :

X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  155 (ATIFGLEXTENSION)
  Minor opcode of failed request:  66 ()
  Serial number of failed request:  13
  Current serial number in output stream:  13
```


You maybe know ehat i did wrong again =) ?

---

### Post by bshatt1987 on 2014-03-25
I'm not going to lie to you, I honestly have no idea. 
Did you try just running the [COLOR=#333333][FONT=Ubuntu]amd-catalyst-13.12-linux-x86.x86_64.run file in the terminal?
Like, navigate to the directory where [COLOR=#333333][FONT=Ubuntu]amd-catalyst-13.12-linux-x86.x86_64.run is located and type
```
[COLOR=#333333][FONT=Ubuntu]./[COLOR=#333333][FONT=Ubuntu]amd-catalyst-13.12-linux-x86.x86_64.run[/FONT][/COLOR][/FONT][/COLOR]
```[COLOR=#333333][FONT=Ubuntu][COLOR=#333333][FONT=Ubuntu]
Then that will pop up with a dialog box and you can choose to install the driver directly or you can "generate distribution specific driver package".  
It seems that the commands you did created the packages, so you might try just clicking the first option that installs the driver directly.  
Otherwise I have absolutely no idea.  [/FONT][/COLOR][/FONT][/COLOR][/FONT][/COLOR]

Edit -  Or, what about the "Additional Drivers" utility that should be available.  That's how I installed my driver.  
I tried the driver from AMD website but didn't like the results as much so I went back to the driver that was available via the "Additional Drivers" utility.  
[/FONT][/COLOR]

---

### Post by we-are-the-forsaken on 2014-03-25
I found the solution on this site and it worked for me =) :
[https://gist.github.com/moldcraft/8116528](https://gist.github.com/moldcraft/8116528)

i just edited this last terminal command : 
[COLOR=#000000][FONT=Consolas]sudo ./ati-installer.sh 13.251 --buildpkg Ubuntu/saucy  -----> [/FONT][/COLOR][COLOR=#000000][FONT=Consolas]sudo ./ati-installer.sh 13.251 --buildpkg Ubuntu/precise ( coz i got ubuntu 12.04 )
and followed all other step exactly 

Thx for your time and for your help .

[/FONT][/COLOR]

---

### Post by bshatt1987 on 2014-03-25
Oh, awesome!  I'm glad you got it all worked out. :D

---

