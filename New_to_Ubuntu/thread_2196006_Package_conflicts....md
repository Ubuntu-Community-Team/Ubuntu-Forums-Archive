---
title: "Package conflicts..."
date: 2013-12-27
forum: New to Ubuntu
---

### Post by Anaxagore on 2013-12-27
Hi,

I just reinstalled Ubuntu 13.10 a few days ago and have been setting up all my applications in the past few days.

However, I am now often encountering package conflicts and packages don't install anymore. For instance the Python-UNO bridge fails to install, with the following error:

> The following packages have unmet dependencies:

python-uno: Depends: libreoffice-core (= 1:4.0.2-0ubuntu1) but 1:4.1.3-0ubuntu1 is to be installed
            Depends: python (< 2.8) but 2.7.5-5ubuntu1 is to be installed
            Depends: libgcc1 (>= 1:4.1.1) but 1:4.8.1-10ubuntu9 is to be installed

(Ubuntu really is not clear on what the problem is, because installing  version x+1 when version x is required should not cause problems...)
Similarly, the older Picasa3 (wined up version that Google retired last year) fails to install with the error:

> dpkg: dependency problems prevent configuration of picasa:  picasa depends on lib32asound2; however:   Package lib32asound2 is not installed. 
 
dpkg: error processing picasa (--install): 
 dependency problems - leaving unconfigured 
Processing triggers for gconf2 ... 
 
(gconftool-2:24142): GConf-WARNING **: Client failed to connect to the D-BUS daemon: 
Unable to autolaunch a dbus-daemon without a $DISPLAY for X11 
Errors were encountered while processing:  picasa

Going further into the picasa error, apt-get install lib32asound2 returns:
> The following packages have unmet dependencies:
 lib32asound2 : Depends: libasound2 (= 1.0.25-4ubuntu3)

and apt-get install libasound2 returns:
> libasound2 is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 picasa : Depends: lib32asound2 but it is not going to be installed

apt-get -f install only proposes to remove picasa...


I  suppose this kind of error could be due to some x86 packages that still  required ia32-libs even though they should do without it, given that  13.10 uses multiarch and not ia32 anymore, but I really am no expert at  it, and just would like to solve this kind of recurring problem! Any idea (apart from reinstalling the whole system...)?

Thanks in advance for your suggestions!

---

### Post by ian-weisser on 2013-12-29
> **Anaxagore said:**
> For instance the Python-UNO bridge fails to install, with the following error:
```
The following packages have unmet dependencies:

python-uno: Depends: libreoffice-core (= [COLOR=#ff0000]1:4.0.2-0ubuntu1[/COLOR]) but [COLOR=#00ff00]1:4.1.3-0ubuntu1[/COLOR] is to be installed
            Depends: python (< 2.8) but 2.7.5-5ubuntu1 is to be installed
            Depends: libgcc1 (>= 1:4.1.1) but 1:4.8.1-10ubuntu9 is to be installed
```

You seems to have a version mismatch.
```
$ rmadison -u ubuntu libreoffice-core
 libreoffice-core | 1:3.5.2-2ubuntu1     | precise          | amd64, armel, armhf, i386, powerpc
 libreoffice-core | 1:3.5.4-0ubuntu1.1   | precise-security | amd64, armel, armhf, i386, powerpc
 libreoffice-core | 1:3.5.7-0ubuntu5     | precise-updates  | amd64, armel, armhf, i386, powerpc
 libreoffice-core | 1:3.6.2~rc2-0ubuntu3 | quantal          | amd64, armel, armhf, i386, powerpc
 libreoffice-core | 1:3.6.2~rc2-0ubuntu4 | quantal-updates  | amd64, armel, armhf, i386, powerpc
 libreoffice-core |[COLOR=#ff0000] 1:4.0.2-0ubuntu1[/COLOR]     | raring           | amd64, armhf, i386, powerpc
 libreoffice-core | 1:4.0.4-0ubuntu1     | raring-proposed  | amd64, armhf, i386, powerpc
 libreoffice-core | 1:4.1.2~rc3-0ubuntu1 | saucy            | amd64, armhf, i386, powerpc
 libreoffice-core |[COLOR=#00ff00] 1:4.1.3-0ubuntu1[/COLOR]     | saucy-updates    | amd64, armhf, i386, powerpc
 libreoffice-core | 1:4.1.3-0ubuntu2     | trusty           | amd64, armhf, i386, powerpc
 libreoffice-core | 1:4.1.3-0ubuntu3     | trusty-proposed  | amd64, armhf, i386, powerpc

```

Your recent installation of 13.10 may have been 13.04, or perhaps you installed a quite obsolete PPA.
Is your /etc/apt/sources.list all saucy? Or do you have some raring mixed in there?

---

