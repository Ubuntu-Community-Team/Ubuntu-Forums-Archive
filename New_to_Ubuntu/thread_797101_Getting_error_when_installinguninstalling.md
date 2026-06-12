---
title: "Getting error when installing/uninstalling"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by youtin on 2008-05-17
I've installed a bunch of apps before, but recently, this error comes up when I'm trying to uninstall/install something.

**msttcorefonts: subprocess post-installation script returned error exit status 1**

It makes the installation crash/unusable. What can I do about it? I even tried to remove msttcorefonts but the same error comes up.:confused:

I'm using Gutsy. Hope someone can help me figure it out!

---

### Post by nicedude on 2008-05-17
You will need to list more info. for starters what are you trying to install that is having a problem with MS True Type Core Fonts?

---

### Post by shadow-of-sin on 2008-05-17
This means that your msttcorefonts installation failed, do the following in the terminal to fix your problem:
```
sudo apt-get reinstall msttcorefonts
```

---

### Post by youtin on 2008-05-17
Thanks for the replies! :)

I tried installing MPlayer and also xfmedia when MPlayer didn't work. The same error came out for both of them and MPlayer crashed at startup.

However, when I tried
**sudo apt-get reinstall msttcorefonts**

This came up:
**E: Invalid operation reinstall**

What to do???

---

### Post by Oldsoldier2003 on 2008-05-17
> **youtin said:**
> Thanks for the replies! :)

I tried installing MPlayer and also xfmedia when MPlayer didn't work. The same error came out for both of them and MPlayer crashed at startup.

However, when I tried
**sudo apt-get reinstall msttcorefonts**

This came up:
**E: Invalid operation reinstall**

What to do???
```

sudo apt-get install --reinstall msttcorefonts
```

---

### Post by PatrickMoore on 2008-05-17
> **Oldsoldier2003 said:**
> ```

sudo apt-get install --reinstall msttcorefonts
```

when i did that i get this...

[PHP]Reading package lists... Done
Building dependency tree        
Reading state information... Done
The following packages were automatically installed and are no longer required:
  artsbuilder libtaglib2.0-cil libmono-cairo2.0-cil libtagc0
  python-gnome2-extras libavahi1.0-cil python-mutagen libtunepimp5
  libgtk2-ruby1.8 libfftw3-3 libgdl-gnome-1-0 libgdl-1-common
  libgconf2-ruby1.8 libmono-zeroconf1.0-cil libgconf2-ruby libgda3-common
  libifp4 libglib2-ruby1.8 libglade2-ruby1.8 libcairo-ruby1.8 libkarma0
  python-pyvorbis libatk1-ruby1.8 libpango1-ruby1.8 libgda3-3
  libgdk-pixbuf2-ruby1.8 python-pymad python-pyogg libnjb5 libgdl-1-0 libofa0
  libboo2.0-cil
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 57 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up msttcorefonts (2.4) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/PHP]

---

