---
title: "can't get repetier-host to run got terminal info coped in post"
date: 2016-09-07
forum: New to Ubuntu
---

### Post by imawesome on 2016-09-07
Hi I'm Jeff
I'm trying to install Repetier-Host i think i messed it up what happened is i down loaded the PPA i think thats what it's called and i unpacked it then opened the terminal did this  

```

jeff@dell:~$ '/home/jeff/Downloads/RepetierHost/configureFirst.sh' 
System: i686
Using 32 bit CuraEngine
cp: cannot stat 'plugins/CuraEngine/CuraEngine32': No such file or directory
chmod: cannot access 'plugins/CuraEngine/CuraEngine': No such file or directory
[sudo] password for jeff: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libmono-winforms2.0-cil is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  mono-reference-assemblies-2.0 mono-devel

E: Package 'libmono-winforms2.0-cil' has no installation candidate
chmod: cannot access '../RepetierHost': No such file or directory
chmod: cannot access 'data': No such file or directory
chmod: cannot access 'installDep*': No such file or directory
rm: cannot remove '/usr/bin/repetierHost': No such file or directory
Checking if you are in the dialout group.
0
Adding user jeff to the dialout group.
You need to login again in order to connect to your printer.
Compiling helper software to allow non ansi baud rates for some boards
depending on the used serial driver.
g++: error: SetBaudrate.cpp: No such file or directory
g++: fatal error: no input files
compilation terminated.
Configuration finished.
IMPORTANT: In addition to the bundled CuraEngine, the host also
supports Slic3r and Skeinforge. These slicers are not bundled, so
need to install them according to their docs and then set the path
to them in Repetier-Host.
For Slic3r simply unpack the tar you get on [http://slic3r.org](http://slic3r.org) in this directory.
The host will then register and add it automatically on next restart.

IMPORTANT: You need a recent mono version since the host uses .NET 4.0
If you see the following error message, your mono is too old!
>>> System.Windows.Forms.SplitContainer doesn't implement interface System.ComponentModel.ISupportInitialize <<<
bash: /home/jeff/createDesktopIcon.sh: No such file or directory
jeff@dell:~$ 


```

there seems to be something about .net that might be important not sure? don't know what a mono is :confused:  
anyway then i read the read me file should had done that first so i changed the directory 
this is what the read me file says 

```

Installation instructions

1. Open a terminal
2. Go to the directory, where you want to have the installation
3. tar -xzf repetierHostLinux.tgz
   change tar file accordingly.
4. cd RepetierHost
5. sh configureFirst.sh
6. Make sure your user has permission to use the serial port. On
   Debian and Fedora this requires membership in group dialout. The
   script will try to add you to dialout automatcally.
   To add a user into this group enter:
      usermod -a -G dialout yourUserName
7. This directory will now contain a Repetier-Host.desktop file, that you can copy to
   your desktop to have a icon to start the host with.
      
After that, you have a link in /usr/bin so you can start the host from
everywhere with

repetierHost

Known issues:
- You may see an OpenGL warning at startup. Ignore it.
- Sometimes the start fails. Just start again.
- Some mono versions seem to crash on exit. Ignore the messages as you are already leaving.
- You need a recent mono version like 3.2 or the host will crash sooner or later due to
  not implemented functions.



```

i guess this would be the reinstall

```
jeff@dell:~$ cd Repetierhost
bash: cd: Repetierhost: No such file or directory
jeff@dell:~$ ls
Desktop    Downloads         freecad  Pictures  repetier      Templates
Documents  examples.desktop  Music    Public    RepetierHost  Videos
jeff@dell:~$ cd RepetierHost
jeff@dell:~/RepetierHost$ sh configurefirst.sh
sh: 0: Can't open configurefirst.sh
jeff@dell:~/RepetierHost$ sudo sh configureFirst.sh
[sudo] password for jeff: 
System: i686
Using 32 bit CuraEngine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libmono-winforms2.0-cil is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  mono-reference-assemblies-2.0 mono-devel

E: Package 'libmono-winforms2.0-cil' has no installation candidate
Checking if you are in the dialout group.
0
Adding user root to the dialout group.
You need to login again in order to connect to your printer.
Compiling helper software to allow non ansi baud rates for some boards
depending on the used serial driver.
SetBaudrate.cpp:11:2: warning: #warning TCGETS2 [-Wcpp]
 #warning TCGETS2
  ^
SetBaudrate.cpp:40:2: warning: #warning TCGETS2 [-Wcpp]
 #warning TCGETS2
  ^
Configuration finished.
IMPORTANT: In addition to the bundled CuraEngine, the host also
supports Slic3r and Skeinforge. These slicers are not bundled, so
need to install them according to their docs and then set the path
to them in Repetier-Host.
For Slic3r simply unpack the tar you get on [http://slic3r.org](http://slic3r.org) in this directory.
The host will then register and add it automatically on next restart.

IMPORTANT: You need a recent mono version since the host uses .NET 4.0
If you see the following error message, your mono is too old!
>>> System.Windows.Forms.SplitContainer doesn't implement interface System.ComponentModel.ISupportInitialize <<<
This folder now contains a repetier-RepetierHost.desktop file
Copy it to your desktop to get a launch icon there
jeff@dell:~/RepetierHost$ 

[/QUOTE]

i moved the desktop file to the decktop but i got told that it was not safe so i changed the permissions 
then it started an error message so i opened the terminal and i seen that "/home/jeff/RepetierHost/RepetierHost.exe" 
was denied so i changed the permissions on that it seemed to help it changed the output to "wine: /home/jeff/.wine is not owned by you" I'm 
taking that as a positive maybe lol
 

[QUOTE]
jeff@dell:~/Desktop$ sudo repetier-RepetierHost.desktop
[sudo] password for jeff: 
sudo: repetier-RepetierHost.desktop: command not found
jeff@dell:~/Desktop$ sudo ./repetier-RepetierHost.desktop
./repetier-RepetierHost.desktop: 1: ./repetier-RepetierHost.desktop: [Desktop: not found
./repetier-RepetierHost.desktop: 3: ./repetier-RepetierHost.desktop: /home/jeff/RepetierHost/RepetierHost.exe: Permission denied
./repetier-RepetierHost.desktop: 6: ./repetier-RepetierHost.desktop: 3d: not found
./repetier-RepetierHost.desktop: 9: ./repetier-RepetierHost.desktop: text/gcode: not found
./repetier-RepetierHost.desktop: 9: ./repetier-RepetierHost.desktop: application/wavefront-obj: not found
./repetier-RepetierHost.desktop: 9: ./repetier-RepetierHost.desktop: application/x-amf: not found
jeff@dell:~/Desktop$ sudo ./repetier-RepetierHost.desktop
./repetier-RepetierHost.desktop: 1: ./repetier-RepetierHost.desktop: [Desktop: not found
wine: /home/jeff/.wine is not owned by you
./repetier-RepetierHost.desktop: 6: ./repetier-RepetierHost.desktop: 3d: not found
./repetier-RepetierHost.desktop: 9: ./repetier-RepetierHost.desktop: text/gcode: not found
./repetier-RepetierHost.desktop: 9: ./repetier-RepetierHost.desktop: application/wavefront-obj: not found
./repetier-RepetierHost.desktop: 9: ./repetier-RepetierHost.desktop: application/x-amf: not found
jeff@dell:~/Desktop$ 

```

I'm not sure i was doing that right or not? I'm straight up winging it at this point 
but hay I'm only on my second day of ubuntu what can i say

---

### Post by imawesome on 2016-09-08
ok it works if i use the link to shell script that is in user/bin/repetierhost
maybe what is on my desktop is not the right file the one that works reads 

#!/bin/sh
cd /home/jeff/RepetierHost
mono RepetierHost.exe -home /home/jeff/RepetierHost&

---

