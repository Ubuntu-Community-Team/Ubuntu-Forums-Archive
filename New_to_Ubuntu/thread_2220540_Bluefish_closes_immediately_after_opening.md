---
title: "Bluefish closes immediately after opening"
date: 2014-04-28
forum: New to Ubuntu
---

### Post by Santiago_Bayeta on 2014-04-28
Dear All,

I'm new to Ubuntu and Linux. I recently installed it (14.04 LTS) in order to develop web applications (comming from Windows).

I just installed Bluefish editor (first using the software center, then uninstalled and tried apt-get). Once installed, every time I try to launch the editor, it opens and after maybe half a second it closes.

I tried launching it from a terminal window and it does the same thing, except this time I can get some feedback in the terminal.

```
santiago@santiago-UX32VD:~$ bluefish 
error reading list 1 Error al abrir el archivo: No existe el archivo o el directorio


** (bluefish:8653): WARNING **: no configfile rcfile-2.0, try to convert config files from older versions


config file migration error 1:Error al abrir el archivo: No existe el archivo o el directorioerror reading list 1 Error al abrir el archivo: No existe el archivo o el directorio
error reading list 14 Error al abrir el archivo: Permiso denegado
cleanup_scanner, memory scancache 0(0Kb+0Kb) found 0(0Kb) fcontext 0(0Kb) = 0Kb


(bluefish:8653): Gtk-WARNING **: Attempting to read the recently used resources file at `/home/santiago/.local/share/recently-used.xbel', but the parser failed: Falló al abrir el archivo «/home/santiago/.local/share/recently-used.xbel»: Permiso denegado.
.gvfs: isdir=1 but mime type =application/octet-stream ???????????
**
ERROR:file_treemodel.c:463:fill_uri: code should not be reached
Abortado (`core' generado)
santiago@santiago-UX32VD:~$
``` 

If I run it from the terminal window using sudo it works (although I still get some errors.

```

santiago@santiago-UX32VD:~$ sudo bluefish 
[sudo] password for santiago: 
error reading list 1 Error al abrir el archivo: No existe el archivo o el directorio


** (bluefish:12363): WARNING **: no configfile rcfile-2.0, try to convert config files from older versions


config file migration error 1:Error al abrir el archivo: No existe el archivo o el directorioerror reading list 1 Error al abrir el archivo: No existe el archivo o el directorio
cleanup_scanner, memory scancache 0(0Kb+0Kb) found 0(0Kb) fcontext 0(0Kb) = 0Kb

```

Does anyone know what the problem is?

Thanks,
Santiago

---

### Post by Homayoun_Shahri on 2014-05-11
> **Santiago_Bayeta said:**
> Dear All,

I'm new to Ubuntu and Linux. I recently installed it (14.04 LTS) in order to develop web applications (comming from Windows).

I just installed Bluefish editor (first using the software center, then uninstalled and tried apt-get). Once installed, every time I try to launch the editor, it opens and after maybe half a second it closes.

I tried launching it from a terminal window and it does the same thing, except this time I can get some feedback in the terminal.

```
santiago@santiago-UX32VD:~$ bluefish 
error reading list 1 Error al abrir el archivo: No existe el archivo o el directorio


** (bluefish:8653): WARNING **: no configfile rcfile-2.0, try to convert config files from older versions


config file migration error 1:Error al abrir el archivo: No existe el archivo o el directorioerror reading list 1 Error al abrir el archivo: No existe el archivo o el directorio
error reading list 14 Error al abrir el archivo: Permiso denegado
cleanup_scanner, memory scancache 0(0Kb+0Kb) found 0(0Kb) fcontext 0(0Kb) = 0Kb


(bluefish:8653): Gtk-WARNING **: Attempting to read the recently used resources file at `/home/santiago/.local/share/recently-used.xbel', but the parser failed: Falló al abrir el archivo «/home/santiago/.local/share/recently-used.xbel»: Permiso denegado.
.gvfs: isdir=1 but mime type =application/octet-stream ???????????
**
ERROR:file_treemodel.c:463:fill_uri: code should not be reached
Abortado (`core' generado)
santiago@santiago-UX32VD:~$
``` 

If I run it from the terminal window using sudo it works (although I still get some errors.

```

santiago@santiago-UX32VD:~$ sudo bluefish 
[sudo] password for santiago: 
error reading list 1 Error al abrir el archivo: No existe el archivo o el directorio


** (bluefish:12363): WARNING **: no configfile rcfile-2.0, try to convert config files from older versions


config file migration error 1:Error al abrir el archivo: No existe el archivo o el directorioerror reading list 1 Error al abrir el archivo: No existe el archivo o el directorio
cleanup_scanner, memory scancache 0(0Kb+0Kb) found 0(0Kb) fcontext 0(0Kb) = 0Kb

```

Does anyone know what the problem is?

Thanks,
Santiago


I have the exact same issue. I noticed that if I run this with root privilege it runs perfectly, but if I run it with normal user ID it crashes immediately. Interestingly bluefish runs fine on a different computer which has the same version of UBUNTU (64 bit 14.04) installed.

---

### Post by Homayoun_Shahri on 2014-05-11
> **Homayoun_Shahri said:**
> I have the exact same issue. I noticed that if I run this with root privilege it runs perfectly, but if I run it with normal user ID it crashes immediately. Interestingly bluefish runs fine on a different computer which has the same version of UBUNTU (64 bit 14.04) installed.

I did a bit of searching, and the issue seems to be related to to ~/.gvfs. Which has a very strange permission:     [d????????? ? ? ? ? ? .gvfs]("http://www.devheads.net/linux/fedora/user/help-d-gvfs.htm#comment-79552") 
If you do mount | grep gvfs to see if this is running, and then unmount it: umount gvfsd-fuse then it all should work. It seems that after a reboot this file system does not get mounted! I can not run bluefish as myself with no problems or issues.

---

### Post by thombhitz on 2014-07-31
I had exact the same issue. Then installed bluefish via **ppa:klaus-vormweg/bluefish. **Link to launchpad: [https://launchpad.net/~klaus-vormweg/+archive/ubuntu/bluefish](https://launchpad.net/~klaus-vormweg/+archive/ubuntu/bluefish)

Now it's working without any problems. Hope this helps.

---

### Post by ian-weisser on 2014-07-31
> **Santiago_Bayeta said:**
> I just installed Bluefish editor (first using the software center, then uninstalled and tried apt-get).
Software Center and apt-get are different front ends to the *same* package manager. They both install exactly the same packages from exactly the same repositories. You installed a package, uninstalled it, then reinstalled exactly the same package.


> **Santiago_Bayeta said:**
> Once installed, every time I try to launch the editor, it opens and after maybe half a second it closes.
Yes, that's a crash, as you certainly suspected.
Look in /var/crash for the crashfile, which has a lot of useful information.


> **Santiago_Bayeta said:**
> ```
santiago@santiago-UX32VD:~$ bluefish 
error reading list 1 Error al abrir el archivo: No existe el archivo o el directorio

** (bluefish:8653): WARNING **: no configfile rcfile-2.0, try to convert config files from older versions

config file migration error 1:Error al abrir el archivo: No existe el archivo o el directorioerror reading list 1 Error al abrir el archivo: No existe el archivo o el directorio
error reading list 14 Error al abrir el archivo: Permiso denegado
cleanup_scanner, memory scancache 0(0Kb+0Kb) found 0(0Kb) fcontext 0(0Kb) = 0Kb


(bluefish:8653): Gtk-WARNING **: Attempting to read the recently used resources file at `/home/santiago/.local/share/recently-used.xbel', but the parser failed: Falló al abrir el archivo «/home/santiago/.local/share/recently-used.xbel»: Permiso denegado.
.gvfs: isdir=1 but mime type =application/octet-stream ???????????
**
ERROR:file_treemodel.c:463:fill_uri: code should not be reached
Abortado (`core' generado)
santiago@santiago-UX32VD:~$
``` 

Classic permissions problem. It even says so in the error messages. 
Usually that only happens if you did something ..clever.. during or after the install.
Is bluefish the _only_ application you need to run sudo to use? Are there others?
Have you run into _any_ other permission problems?

Please open a terminal and show us the output of the following command:
```
ls -l ~/.local/share/recently-used.xbel
```

---

### Post by vasa1 on 2014-07-31
> **ian-weisser said:**
> ... Please open a terminal and show us the output of the following command:
```
ls -l ~/.local/share/recently-used.xbel
```
Couldn't that output be quite voluminous? Maybe suggest a grep to clean things up?

---

### Post by ian-weisser on 2014-07-31
> **vasa1 said:**
> Couldn't that output be quite voluminous?
Well, let's find out. How long is your output?

---

### Post by hierro59 on 2014-11-14
Logré solucionar el problema eliminando la carpeta .bluefish de mi directorio personal.

---

### Post by ian-weisser on 2014-11-14
Glad you got it sorted.

---

