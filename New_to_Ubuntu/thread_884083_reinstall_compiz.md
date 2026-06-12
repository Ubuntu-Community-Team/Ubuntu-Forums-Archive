---
title: "reinstall compiz"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by okey666 on 2008-08-08
After having various problems with compiz, I managed to completely mess it up. Now I want to get rid of it and start again.

Could somebody please advise me of which packages to remove and install and what config to set (I have removed some packages and reinstalled the whole thing but I seem to keep the same broken compiz???). I would like it to be just how it was when I installed Hardy.

---

### Post by northern lights on 2008-08-08
Navigate to "System > Preferences > Advanced Desktop Effects Settings". At the bottom of the left column, you'll find "Preferences". Under the "Profile & Backend" tab, there's a "Reset to defaults" button.

I think that might just be what you're looking for.

---

### Post by okey666 on 2008-08-08
That has started compiz working... BUT it has left me with the same config problems that I had on thread:
[http://ubuntuforums.org/showthread.php?t=882652](http://ubuntuforums.org/showthread.php?t=882652)

With those problems I decided it might be best to reinstall compiz.

---

### Post by nothingspecial on 2008-08-08
Go to your home folder.
Press ctrl + H
Delete your .compiz file
reboot

---

### Post by nothingspecial on 2008-08-08
Sorry, click on .config and delete the compiz file in there.

---

### Post by okey666 on 2008-08-08
I dont't have a compix file in my .compiz folder. I have only 4 folders

/images
/metadata
/plugins
/session

---

### Post by okey666 on 2008-08-08
oh, sorry, read you wrong. Trying it.

---

### Post by okey666 on 2008-08-08
Well... compiz works well, but the configuration does not. As before, sometimes, when I check a box to enable a plugin, I come back a few minutes later and it has been unchecked. Then, when I change a key binding it will just revert to the default. Finally, in the appearance dialogue, custom configuration is not displayed, even though ccsm is installed.

---

### Post by nothingspecial on 2008-08-08
To finish what I should have said in my first post (long day/too much ...)

There is also a file in .gconf > apps called compiz. Delete that aswell. Log out and back in and compiz should be in its original state.

Have fun reconfiguring it.:)

---

### Post by InfinityCircuit on 2008-08-08
Open up a terminal.

rm -rf ~/.compiz
sudo apt-get install --reinstall -o DPkg::Options::"--force-confmiss" -o DPkg::Options::"--force-confnew" "compiz*"

---

### Post by okey666 on 2008-08-08
After remove of second folder everything is reset, but config problems remain.

After I ran the commands I get:
```
oscar@oscar-desktop:~$ rm -rf ~/.compiz
oscar@oscar-desktop:~$ sudo apt-get install --reinstall -o DPkg::Options::"--force-confmiss" -o DPkg::Options::"--force-confnew" "compiz*"
[sudo] password for oscar: 
E: Option DPkg::Options::--force-confmiss: Configuration item specification must have an =<val>.

```

I'm not to good with long commands...

---

### Post by nothingspecial on 2008-08-08
Ok try something else. Try opening up synaptic and marking compizconfig-settings-manager for complete removal and then reinstalling it.

---

### Post by InfinityCircuit on 2008-08-08
Sorry my memory failed me I gave you the wrong command.  It should be:

apt-get install --reinstall -o Dpkg::Options::force=--force-confnew,confmiss "compiz*"

---

### Post by okey666 on 2008-08-08
Very strange...

even after complete removal, ccsm is still on the menu and still works! I have even restarted. I have a similar situation with "compiz fusion icon" it is uninstalled but still works.

---

### Post by okey666 on 2008-08-08
After running the reinstall command I get this:
> Unpacking replacement python-compizconfig ...
Errors were encountered while processing:
 /var/cache/apt/archives/compiz-fusion-bcop_0.6.0-1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

edit:
and although compiz lost all the extra plug ins and everything the old problems still remain. It is like the packages are stuck on my system.

---

### Post by okey666 on 2008-08-08
Whoah, I tried to remove the fusion-icon and this is what happened:

> oscar@oscar-desktop:~$ sudo apt-get remove fusion-icon
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package fusion-icon is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libnl1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
43 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up fp-units-rtl (2.2.0-dfsg1-5) ...
Setting up fp-compiler (2.2.0-dfsg1-5) ...

Setting up compiz-core (1:0.7.4-0ubuntu7) ...
Setting up compiz-fusion-plugins-extra (0.7.4-0ubuntu1) ...

Setting up compiz-fusion-plugins-main (0.7.4-0ubuntu6) ...

Setting up compiz-plugins (1:0.7.4-0ubuntu7) ...
Setting up libcompizconfig0 (0.7.4-0ubuntu1) ...

Setting up compizconfig-backend-gconf (0.7.4-0ubuntu1) ...
Setting up compiz-gnome (1:0.7.4-0ubuntu7) ...

Setting up compiz (1:0.7.4-0ubuntu7) ...
Setting up compiz-dev (1:0.7.4-0ubuntu7) ...
Setting up compizconfig-backend-kconfig (0.7.4-0ubuntu1) ...
Setting up kwin (4:3.5.9-0ubuntu7.3) ...

Setting up compiz-kde (1:0.7.4-0ubuntu7) ...
Setting up libemeraldengine0 (0.7.2-0ubuntu2) ...

Setting up emerald (0.7.2-0ubuntu2) ...

Setting up gdc-4.1 (0.25-4.1.2-16ubuntu1) ...
Setting up libgmp3c2 (2:4.2.2+dfsg-1ubuntu2) ...

Setting up haskell-utils (1.10ubuntu3) ...
Setting up libgmpxx4ldbl (2:4.2.2+dfsg-1ubuntu2) ...

Setting up libgmp3-dev (2:4.2.2+dfsg-1ubuntu2) ...
Setting up libncurses5-dev (5.6+20071124-1ubuntu2) ...
Setting up libreadline5-dev (5.2-3build1) ...

Setting up ghc6 (6.8.2-2ubuntu1) ...

Setting up kicker (4:3.5.9-0ubuntu7.3) ...

Setting up kicker-compiz (3.5.4-0ubuntu1) ...
Setting up kicker-taskbar-compiz (0.1-0ubuntu1) ...

Setting up libsnmp-mib-compiler-perl (0.06-2) ...
Setting up mono-gmcs (1.2.6+dfsg-6ubuntu3) ...
Setting up ocaml-base-nox (3.10.0-8) ...

Setting up ocaml-interp (3.10.0-8) ...

Setting up ocaml-nox (3.10.0-8) ...

Setting up ocaml-compiler-libs (3.10.0-8) ...

Setting up ocaml-native-compilers (3.10.0-8) ...
Setting up pnet-compiler (0.7.4-1build1) ...

Setting up binutils-avr (2.18-3) ...
Setting up binutils-m68hc1x (1:2.18-2) ...
Setting up compiz-bcop (0.7.4-0ubuntu1) ...
Setting up python-compizconfig (0.7.4-0ubuntu1) ...
Setting up compizconfig-settings-manager (0.7.4-0ubuntu2) ...
gtk-update-icon-cache: The generated cache was invalid.
WARNING: icon cache generation failed for /usr/share/icons/hicolor

Setting up gcc-avr (1:4.2.2-1) ...
Setting up gcc-m68hc1x (1:3.3.6+3.1+dfsg-1) ...
Setting up libcompizconfig0-dev (0.7.4-0ubuntu1) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
oscar@oscar-desktop:~$ 


What is going on???

---

### Post by okey666 on 2008-08-08
I tried to reinstall fusion-icon and I got this:
> Setting up fusion-icon (0.0.0+git20071028-2ubuntu2) ...
pycentral: pycentral pkginstall: not overwriting local files
pycentral pkginstall: not overwriting local files
dpkg: error processing fusion-icon (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 fusion-icon
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by okey666 on 2008-08-08
I hate to paste out more output, BUT when I run ccsm in the terminal and edit a binding I get the error:
> oscar@oscar-desktop:~$ ccsm
Traceback (most recent call last):
  File "/usr/local/lib/python2.5/site-packages/ccm/Settings.py", line 942, in RunKeySelector
    self.BindingEdited (new)
  File "/usr/local/lib/python2.5/site-packages/ccm/Settings.py", line 947, in BindingEdited
    conflict = KeyConflict (self.Setting, accel)
  File "/usr/local/lib/python2.5/site-packages/ccm/Conflicts.py", line 134, in __init__
    ActionConflict.__init__(self, setting, settings, autoResolve)
  File "/usr/local/lib/python2.5/site-packages/ccm/Conflicts.py", line 94, in __init__
    if setting.Info[0] and plugin is not setting.Plugin:
IndexError: tuple index out of range
Traceback (most recent call last):
  File "/usr/local/bin/ccsm", line 71, in <module>
    gtk.main()


Is that any help?

---

