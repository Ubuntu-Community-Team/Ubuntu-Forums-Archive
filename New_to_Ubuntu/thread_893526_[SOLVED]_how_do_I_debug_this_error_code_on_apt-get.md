---
title: "[SOLVED] how do I debug this? error code on apt-get upgrade"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by mdecler2 on 2008-08-18
Hello! I recently installed Hardy Heron, and there was an error during the install. The error is when installing gnome-themes and gnome-accessibility-themes. I am now trying to install them from the repository upgrade (used apt-get upgrade).

I really just want to have more verbose output on the error since I have no idea what the problem is or how to diagnose it. But if you have knowledge of the problem, that would be helpful as well.

```
Setting up gnome-accessibility-themes (2.22.0-0ubuntu1) ...
gtk-update-icon-cache: symbol lookup error: /usr/lib/libgdk_pixbuf-2.0.so.0: undefined symbol: g_once_init_enter_impl
dpkg: error processing gnome-accessibility-themes (--configure):
 subprocess post-installation script returned error exit status 127
Setting up gnome-themes (2.22.0-0ubuntu1) ...
gtk-update-icon-cache: symbol lookup error: /usr/lib/libgdk_pixbuf-2.0.so.0: undefined symbol: g_once_init_enter_impl
dpkg: error processing gnome-themes (--configure):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 gnome-accessibility-themes
 gnome-themes
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Any sort of help is appreciated!

---

### Post by markjensen on 2008-08-18
Not sure what error "127" is, but if you had some unspecified problems during the upgrade, perhaps doing a **sudo apt-get clean** then a **sudo apt-get update** will help clean up the package manager.

I may be on the wrong trail with this, but worth a try.

---

### Post by mdecler2 on 2008-08-18
Thank you for the response! Unfortunately, that did not solve the problem.

I have been trying to reinstall libgdk-pixbuf-dev and libgdk-pixbuf2, but I receive the same error! In fact, anything that I have tried to install I fail due to the gnome-themes and gnome-accessibilty-themes error (127).

I think that apt is trying to install what it thinks the most important updates are before what I am specifying, so I am going to try an override apt and get libgdk-pixbuf reinstalled.

Any other help or advice is appreciated!

---

### Post by markjensen on 2008-08-18
Well, let's look at this error:
dpkg: error processing gnome-accessibility-themes (--configure):
and this one:
dpkg: error processing gnome-themes (--configure):

Is it telling you that these packages are not configured, and maybe you can run them with a --configure option to remedy it?

That's about my last guess, I am afraid. :(

---

### Post by Ryadt on 2008-08-18
Try```
sudo dpkg --configure -a
```

---

### Post by mdecler2 on 2008-08-18
Well, this error message is too vague:
```
gtk-update-icon-cache: symbol lookup error: /usr/lib/libgdk_pixbuf-2.0.so.0: undefined symbol: g_once_init_enter_impl

```

I am not sure what to do, and I haven't been able to get around aptitudes fascination with gnome-themes. I am not even using gdm, and I can't seem to install anything without first correcting this problem.

---

### Post by mdecler2 on 2008-08-18
> **Ryadt said:**
> Try```
sudo dpkg --configure -a
```

The problem with this is that apt has actually been trying to configure the two packages all along.

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y

```

---

### Post by Ryadt on 2008-08-18
Have a look here [http://ubuntuforums.org/showthread.php?t=583537](http://ubuntuforums.org/showthread.php?t=583537)

---

### Post by mdecler2 on 2008-08-18
SOLUTION:
> **Ryadt said:**
> Have a look here [http://ubuntuforums.org/showthread.php?t=583537](http://ubuntuforums.org/showthread.php?t=583537)

I followed the link to the above and followed the steps. I will copy and paste the solution here for your convenience:
> **DalaiDakkar said:**
> My problem was fixed with this steps

No, don't delete /usr/lib/libgdk_pixbuf-2.0.so.0... You definetely need that! You can get it back by doing apt-get --reinstall install libgtk2.0-0.

Then run: ldd /usr/lib/libgdk_pixbuf-2.0.so.0 and it will list all libraries that it's trying to load. Look for /usr/local/lib/<<Some file>> the local part is key as this is where most make install's put libraries. Any file in /usr/local/lib is in your way and I suggest moving it somewhere else not deleting it.


However, I still do not understand the problem, or how to avoid it in the future. I am guessing that it has something to do with synaptic upgrading issues with libgtk libraries?

---

### Post by mdecler2 on 2008-08-18
I am having similar library issues with libgtk-2.0 installing brasero and gtk-chtheme applications.

I think I am going to try doing a clean install with an install CD. Wish me luck!

---

### Post by mdecler2 on 2008-09-04
I am not sure why the problem continued to happen on other sources, but I have done a clean install, and I am finally where I need to be (several days later). I was able to keep my home directory intact, and I stored all my personal information there, so I am just filling in the cracks here and there. My printer was detected too, which was nice.

I didn't know any other way to solve the problem.

---

