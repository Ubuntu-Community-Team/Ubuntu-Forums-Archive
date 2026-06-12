---
title: "Guitar Pro 6 on 64bit"
date: 2011-09-15
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by sonicb00m on 2011-09-15
Anyone had any luck getting this program to install? I was hoping with these i386 packages being installed as needed that Gp6 would be easy to run under x64 but it doesn't install :(

```


~$ sudo dpkg -i gp6-full-linux-demo-r9980.deb 
Selecting previously deselected package guitarpro6:i386.
(Reading database ... 170310 files and directories currently installed.)
Unpacking guitarpro6:i386 (from gp6-full-linux-demo-r9980.deb) ...
dpkg: dependency problems prevent configuration of guitarpro6:i386:
 guitarpro6:i386 depends on libstdc++6.
 guitarpro6:i386 depends on libasound2; however:
  Package libasound2:i386 is not installed.
 guitarpro6:i386 depends on libxml2; however:
 guitarpro6:i386 depends on libxslt1.1; however:
 guitarpro6:i386 depends on libportaudio0; however:
 guitarpro6:i386 depends on libportaudio2; however:
 guitarpro6:i386 depends on libglu1-mesa; however:
 guitarpro6:i386 depends on gksu; however:
dpkg: error processing guitarpro6:i386 (--install):
 dependency problems - leaving unconfigured
Processing triggers for gnome-menus ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Errors were encountered while processing:
 guitarpro6:i386
adam@main:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libc6-i386 lib32gcc1 libasound2:i386 libstdc++6:i386 libglu1-mesa:i386 libgl1-mesa-glx:i386 libx11-6:i386 libxext6:i386 libxxf86vm1:i386 libxdamage1:i386 libxfixes3:i386 libdrm2:i386 libxcb1:i386
  libxau6:i386 libxdmcp6:i386 libglapi-mesa:i386 libportaudio0:i386
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libasound2:i386 libdrm2:i386 libgl1-mesa-glx:i386 libglapi-mesa:i386 libglu1-mesa:i386 libportaudio0:i386 libstdc++6:i386 libx11-6:i386 libxau6:i386 libxcb1:i386 libxdamage1:i386 libxdmcp6:i386
  libxext6:i386 libxfixes3:i386 libxxf86vm1:i386
Suggested packages:
  libasound2-plugins:i386 libasound2-python:i386
Recommended packages:
  libgl1-mesa-dri:i386
The following packages will be REMOVED:
  guitarpro6:i386 libgksu2-0 sudo xauth xinit
The following NEW packages will be installed:
  libasound2:i386 libdrm2:i386 libgl1-mesa-glx:i386 libglapi-mesa:i386 libglu1-mesa:i386 libportaudio0:i386 libstdc++6:i386 libx11-6:i386 libxau6:i386 libxcb1:i386 libxdamage1:i386 libxdmcp6:i386
  libxext6:i386 libxfixes3:i386 libxxf86vm1:i386
0 upgraded, 15 newly installed, 5 to remove and 0 not upgraded.
50 not fully installed or removed.
Need to get 0 B/1,995 kB of archives.
After this operation, 198 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 173190 files and directories currently installed.)
Removing guitarpro6:i386 ...
Removing libgksu2-0 ...
update-alternatives: removing manually selected alternative - switching libgksu-gconf-defaults to auto mode
Removing sudo ...
You have asked that the sudo package be removed,
but no root password has been set.
Without sudo, you may not be able to gain administrative privileges.

If you would prefer to access the root account with su(1)
or by logging in directly,
you must set a root password with "sudo passwd".

If you have arranged other means to access the root account,
and you are sure this is what you want,
you may bypass this check by setting an environment variable 
(export SUDO_FORCE_REMOVE=yes).

Refusing to remove sudo.
dpkg: error processing sudo (--remove):
 subprocess installed pre-removal script returned error exit status 1
Removing xinit ...
Removing xauth ...
Processing triggers for gnome-menus ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for man-db ...
Processing triggers for gconf2 ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 sudo
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

For some reason it wants to remove sudo as well!

---

### Post by dino99 on 2011-09-15
dont know what you have done: you says 64 bits system but apt tell you to remove i386 packages !!!

by the way this thread is unrelated with Oneiric subforum.

---

### Post by uRock on 2011-09-15
Moved to *general help*.

---

### Post by sonicb00m on 2011-09-15
The reason I posted in the Oneiric forum is because it works fine on Natty and it's Oneiric I am having trouble installing it with.

The confusion with the i386 packages confirms that the correct forum for this is Oneiric. 

Please put it back.

---

### Post by 3rdalbum on 2011-09-15
> sudo dpkg -i gp6-full-linux-demo-r9980.deb

...

> guitarpro6:i386 depends on libasound2; however:
  Package libasound2:i386 is not installed.

Is there any reason you're not just double-clicking on the package to install it in Software Center or Gdebi? The reason I ask is because the 'dpkg' utility does not resolve dependencies, and it's basically telling you that you are missing a dependency. If you install the package using Software Center or Gdebi, the dependencies will be resolved for you automatically.

---

### Post by sonicb00m on 2011-09-15
Software center reports "Wrong architecture" and won't install.

Shouldn't "apt-get install -f" fix dependencies though?

---

