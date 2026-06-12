---
title: "Failed to load file after installing steam"
date: 2015-09-03
forum: New to Ubuntu
---

### Post by rob146 on 2015-09-03
Hello, everyone.

I just figured out how to install linux (finally) last night, and have since been installing everything I can think of.  I got most essential items down (coding and such), but I am having trouble with Steam.  I installed it through apt-get, after installing nvidia-352 drivers, and this is the error message that I receive.  Any help is very much welcome.  Thanks in advance.

```
$steam
ILocalize::AddFile() failed to load file "public/steambootstrapper_english.txt".
[2015-09-03 14:36:12] Startup - updater built Nov 25 2013 18:07:05
libGL error: No matching fbConfigs or visuals found
libGL error: failed to load driver: swrast
SteamUpdateUI: An X Error occurred
X Error of failed request:  BadValue (integer parameter out of range for operation)


```

NOTE: The following thread did not work for me.  GLXGears was able to run flawlessly. [http://askubuntu.com/questions/541343/problems-with-libgl-fbconfigs-swrast-through-each-update](http://askubuntu.com/questions/541343/problems-with-libgl-fbconfigs-swrast-through-each-update)

---

### Post by rob146 on 2015-09-03
UPDATE: I don't know what I did, but now the error message says the following:

```
$ steam
ILocalize::AddFile() failed to load file "public/steambootstrapper_english.txt".
[2015-09-03 14:47:14] Startup - updater built Nov 25 2013 18:07:05
libGL: screen 0 does not appear to be DRI2 capable
libGL: OpenDriver: trying /usr/lib/i386-linux-gnu/dri/tls/swrast_dri.so
libGL: OpenDriver: trying /usr/lib/i386-linux-gnu/dri/swrast_dri.so
libGL: Can't open configuration file /home/rob/.drirc: No such file or directory.
libGL: Can't open configuration file /home/rob/.drirc: No such file or directory.
libGL error: No matching fbConfigs or visuals found
libGL error: failed to load driver: swrast
SteamUpdateUI: An X Error occurred
X Error of failed request:  BadValue (integer parameter out of range for operation)
```

---

### Post by rob146 on 2015-09-03
SOLUTION:

Uninstall all Graphics Drivers except for the xorg one (COMPLETELY aka `sudo apt-get remove --purge nvidia*').
Uninstall steam (COMPLETELY aka `sudo apt-get remove --purge steam').
REBOOT (not sure if necessary, but doesn't hurt).
Install Steam
Install Drivers

---

### Post by tyler93 on 2016-02-28
> **rob146 said:**
> SOLUTION:

Uninstall all Graphics Drivers except for the xorg one (COMPLETELY aka `sudo apt-get remove --purge nvidia*').
Uninstall steam (COMPLETELY aka `sudo apt-get remove --purge steam').
REBOOT (not sure if necessary, but doesn't hurt).
Install Steam
Install Drivers

Hey, search engine users:

I had this same issue, but because I installed outside of the package manager, using the distributable hosted on NVIDIA's website, I couldn't use apt-get to uninstall my graphics driver.

Here's what I did to solve this problem (exact same error text as the OP):

1. uninstall steam (`apt-get remove --purge steam && rm ~/.steam -R')
2. download the newest relevant nvidia .run file from their website and `chmod +x' on that file to make it executable
3. stop the graphics manager (gdm3 by default for ubuntu, lightdm, kdm, xfdm, etc...) and switch to a tty (e.g. ctrl-alt-F1) to allow driver installation
4. nvidia's driver installer may require you to switch to runlevel 3 by using the command `init 3'
5. execute driver installer
6. **make sure to enable the 32-bit compatibility libraries** (I believe this is why it did not work in the first place. I initially thought I would be able to get away with a non-multi-arch installation, so I must have selected "no" on these before. However, steam is currently 32 bit only unfortunately)
7. add line `blacklist nouveau' to /etc/modprobe.d/blacklist.conf to ensure that the nvidia driver succeeds in loading
8. reboot
9. install steam

---

