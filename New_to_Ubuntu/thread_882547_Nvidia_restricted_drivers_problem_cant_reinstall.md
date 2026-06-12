---
title: "Nvidia restricted drivers problem cant reinstall"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by Justin EJ8 on 2008-08-07
I have just recently installed Ubuntu 8.04 Hardy Heron x64 on my laptop and am having an issue with the nvidia restricted drivers. 
When I first installed I enabled the restricted driver and it worked fine. Then, I installed the madwifi driver to get my atheros wireless card to work and the trouble began. The restricted drivers for the nvidia card were removed from the list and I cannot get them back. I have tried everything and cannot get any of the nvidia driver install methods to work. They all fail. At one point I got the driver to reappear, but when it was enabled, i restarted the computer and it crashed. 

Can someone point me in right direction?

Laptop is an HP Pavilion dv6707us. 
Video Card is an integrated Nvidia 7150m

---

### Post by Crafty Kisses on 2008-08-07
Try:
```
sudo apt-get install nvidia-glx
```
Can you also post the following output of:
```
glxinfo
```

---

### Post by Justin EJ8 on 2008-08-07
got this when running sudo apt-get install nvidia-glx
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  nvidia-kernel-source nvidia-settings
The following packages will be REMOVED:
  nvidia-glx-new
The following NEW packages will be installed:
  nvidia-glx
0 upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B/7333kB of archives.
After this operation, 5939kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 97303 files and directories currently installed.)
Removing nvidia-glx-new ...
dpkg-divert: error checking `/usr/lib32/libGL.so.1': No such file or directory
dpkg: error processing nvidia-glx-new (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 nvidia-glx-new
E: Sub-process /usr/bin/dpkg returned an error code (1)


And this from glxinfo
> justin@justin-laptop:~$ glxinfo
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x3a 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None


---

### Post by rogier.de.groot on 2008-08-07
How about trying "sudo apt-get remove --purge --force nvidia-glx-new" followed by either "sudo apt-get install nvidia-glx-new" or just trying the restricted driver manager (I'd recommend the latter). Note that the "--force" part of the first command is pure speculation on my part, you might want to check "man apt-get" to see what the correct option to force removal is.

Good luck

---

### Post by Justin EJ8 on 2008-08-07
got this 
> 
justin@justin-laptop:~$ sudo apt-get remove --purge --force-yes nvidia-glx-new
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  nvidia-glx-new
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 28.3MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 97254 files and directories currently installed.)
Removing nvidia-glx-new ...
dpkg-divert: error checking `/usr/lib32/libGL.so.1': No such file or directory
dpkg: error processing nvidia-glx-new (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 nvidia-glx-new
E: Sub-process /usr/bin/dpkg returned an error code (1)
justin@justin-laptop:~$ 


---

### Post by PmDematagoda on 2008-08-07
Try:-
```
sudo apt-get install --reinstall nvidia-glx-new
```
and then try and see if things work.

Also, in what ways did you try and install the Nvidia driver again?

---

### Post by nbayiha on 2008-08-07
@Justin EJ8

Sometime try to search first in the forum if your problem has been resolved before creating new post.

Follow the Tricky Tricky way in this post and you should have your card fixed .

[http://ubuntuforums.org/showthread.php?t=880787](http://ubuntuforums.org/showthread.php?t=880787)

---

### Post by Justin EJ8 on 2008-08-07
> **PmDematagoda said:**
> Try:-
```
sudo apt-get install --reinstall nvidia-glx-new
```
and then try and see if things work.

Also, in what ways did you try and install the Nvidia driver again?
I have tried all of the methods nbayiha's tutorial thread before making this post
> **nbayiha said:**
> @Justin EJ8

Sometime try to search first in the forum if your problem has been resolved before creating new post.

Follow the Tricky Tricky way in this post and you should have your card fixed .

[http://ubuntuforums.org/showthread.php?t=880787](http://ubuntuforums.org/showthread.php?t=880787)

anything involving uninstalling the nvidia-glx-new results in failure 

Maybe I should just format and try again. Everything happened when I installed madwifi and I've tried so many things I'm sure I had to have screwed something up somewhere. I may have made an epic fail noob mistake, lol.

---

### Post by KillerSponge on 2008-08-07
Have you tried installing the nVidia drivers using EnvyNG? It's in the repositories, and solves most problems automatically :)

---

### Post by nbayiha on 2008-08-07
> I think you have an and old install conflict problem, that's why you can't install the new one.
If either of nvidia-glx-legacy/nvidia-glx-new are installed a dotfile is created in /lib/linux-restricted-modules/ . Even after these packages are uninstalled the dotfile will remain and may frustrate efforts to use the nvidia-glx package

Try to do this.
go to your
```

cd /lib/linux-restricted-modules

```
then
```


ls -la

```
and there check if you have some hidden nvidia file something like

Quote:
.nvidia_new_installed file
If it's the case remove that file , and after that try again the tricky way .
Hope that will help you.

Try this one

---

