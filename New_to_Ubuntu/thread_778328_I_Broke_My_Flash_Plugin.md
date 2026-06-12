---
title: "I Broke My Flash Plugin"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by deadfecesguy on 2008-05-02
Hi there, I did something (not sure what), but when I try to reinstall flashplugin-nonfree using Synaptic Package Manager, i get the following error. 

```
E: /var/cache/apt/archives/flashplugin-nonfree_9.0.124.0ubuntu2_i386.deb: subprocess new pre-removal script returned error exit status 127
```


If I try to remove the plugin using Synaptic Package Manager, I get this error:

```
E: flashplugin-nonfree: Package is in a very bad inconsistent state - you should reinstall it before attempting a removal.
```

---

### Post by tamoneya on 2008-05-02
```
sudo apt-get check
```Then attempt to reinstall like you were before.

---

### Post by deadfecesguy on 2008-05-02
I get the same error from before:

```
E: /var/cache/apt/archives/flashplugin-nonfree_9.0.124.0ubuntu2_i386.deb: subprocess new pre-removal script returned error exit status 127
```

---

### Post by Biggy on 2008-05-02
Synaptic Package Mnager > Custom Filters > Broken

---

### Post by deadfecesguy on 2008-05-02
> **Biggy said:**
> Synaptic Package Mnager > Custom Filters > Broken

What is that supposed to do? It didn't find anything.

---

### Post by Tom--d on 2008-05-02
install flash manualy. 

Download it from Abobe. the (tar.gz file) and run install_flashpayer in terminal (without sudo.. this will install it under .mozilla in your home directory) 

Or install Gnash in synpatic. (its a free and open source flash player. (not as good as flash player 9 but its getting there :) (I use it :D))

---

### Post by deadfecesguy on 2008-05-02
Is there a way I can physically remove the plugin?

---

### Post by Oldsoldier2003 on 2008-05-02
```
sudo apt-get clean
sudo apt-get install -f
```

then ```
sudo apt-update
sudo apt-get upgrade

```
try reinstalling your plugin after that. Please post any errors and we can help you work through it

---

### Post by Tom--d on 2008-05-02
my adobe flash player was in /usr/share/firefox/plugins

---

### Post by deadfecesguy on 2008-05-02
> **Oldsoldier2003 said:**
> ```
sudo apt-get clean
sudo apt-get install -f
```

then ```
sudo apt-update
sudo apt-get upgrade

```
try reinstalling your plugin after that. Please post any errors and we can help you work through it



After I did ```
sudo apt-get install -f
```
I get this error:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  apturl xulrunner-1.9-gnome-support
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 18.7kB of archives.
After this operation, 0B of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com hardy/multiverse flashplugin-nonfree 9.0.124.0ubuntu2 [18.7kB]
Fetched 18.7kB in 0s (34.6kB/s)            
Preconfiguring packages ...
Selecting previously deselected package flashplugin-nonfree.
(Reading database ... 152175 files and directories currently installed.)
Preparing to replace flashplugin-nonfree 9.0.124.0ubuntu2 (using .../flashplugin-nonfree_9.0.124.0ubuntu2_i386.deb) ...
update-alternatives: unable to make /usr/lib/mozilla/plugins/flashplugin-alternative.so.dpkg-tmp a symlink to /etc/alternatives/mozilla-flashplugin: No such file or directory
dpkg: warning - old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/prerm: 88: cho: not found
dpkg: error processing /var/cache/apt/archives/flashplugin-nonfree_9.0.124.0ubuntu2_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 127
postinst called with argument `abort-upgrade'
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/flashplugin-nonfree_9.0.124.0ubuntu2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by Tom--d on 2008-05-02
Maybe remove the' /var/cache/apt/archives/flashplugin-nonfree_9.0.124.0ubuntu2_i386.deb' file? that may do it.. but not 100% yet on it.

---

### Post by kansasnoob on 2008-05-02
This may be totally irrelevant, but I broke a lot of stuff (more than once) when I upgraded from Gutsy to Hardy until I upgraded the Medibuntu repo.

---

### Post by deadfecesguy on 2008-05-02
no that didn't help. any other ideas?

---

