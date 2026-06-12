---
title: "[SOLVED] &amp;quot;sudo&amp;quot; problems"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by ans5685 on 2008-07-01
hello everybody 
every time I use sudo anything this happens e.g.

> sudo apt-get install -f
sudo: must be setuid root

and the command fails to work

however if i ignore the sudo 

 > apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libavahi-qt3-1 python-pylibacl libxine1-x libxcb-xv0 libsmokeqt1 libmp4v2-0
  libtunepimp5 libpoppler-qt2 libflac++6 rdiff-backup openvpn-blacklist
  libxine1-plugins libqt-perl network-manager-pptp pptp-linux cryptsetup
  procmail libpythonize0 libgmp3c2 network-manager-openvpn perl-suid libept0
  gtk2-engines-qtcurve libksba8 gnupg-agent libxapian15 poster
  libxine1-console ocrad libifp4 debtags libdbus-qt-1-1c2 vpnc pykdeextensions
  libxine1-misc-plugins network-manager-vpnc zoo mpg123 libmimelib1c2a
  libstrigihtmlgui0 resolvconf openvpn libxcb-shape0 libxcb-shm0 pinentry-qt
  libsearchclient0 librsync1 gpgsm libnjb5 libxine1-bin python-pyxattr
  libxine1-ffmpeg libxine1
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  kio-umountwrapper
0 upgraded, 0 newly installed, 1 to remove and 24 not upgraded.
1 not fully installed or removed.
After this operation, 115kB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: requested operation requires superuser privilege
E: Sub-process /usr/bin/dpkg returned an error code (2)


the problem started after I installed kubuntu-desktop to get kde for some experimentation and then removed all the kde packages manually (using Synaptic) as "sudo aptitude remove kubuntu-desktop" removed only the metapackage.
As of now I can't install or uninstall anything :confused::confused::confused::confused:
Please help1!!!!

---

### Post by ibutho on 2008-07-01
You can run the livecd, mount your root partition and navigate to /usr/bin, then run
```
sudo chmod u+s /usr/bin/sudo
```

---

### Post by Vishal Agarwal on 2008-07-01
I hope this > sudo apt-get autoclean will help you in removing prolem

---

### Post by iaculallad on 2008-07-01
Boot on Recovery mode:

```
chown root:root /usr/bin/sudo
chmod 4755 /usr/bin/sudo
reboot
```

---

### Post by ans5685 on 2008-07-01
I'll try that and reply in 15 mins.

---

### Post by ans5685 on 2008-07-02
Sorry guys i still have a problem
i followed iaculallad's instructions and this is what happened

 > sudo apt-get install -f
sudo: /etc/sudoers is mode 0666, should be 0440

What do I do now?

---

### Post by ibuclaw on 2008-07-02
Reboot into Ubuntu Recovery Mode and enter the "**root shell**".
Then type in
```
chmod 0440 /etc/sudoers
exit
```

Then continue with the normal boot.

Regards
Iain

---

### Post by ans5685 on 2008-07-02
Thank's tinivole
but I already did as u said and now I am getting

>  sudo apt-get install -f
bash: /usr/bin/sudo: Permission denied


Now what do I do???????
 (Feel like slapping myself silly)

---

### Post by ibutho on 2008-07-02
Take a look at this [article]("http://www.psychocats.net/ubuntu/fixsudo"). It may help resolve your problem.

---

### Post by ans5685 on 2008-07-02
Thanks guys!!!
I did as iaculallad said immediately followed by tinivole's instructions and the sudo problem is SOLVED but I still can't resolve i.e. remove  kio-umountwrapper using apt-get or synaptic :( :(
P.S. I am marking this thread solved in a few mins.
Thanks again

---

### Post by iaculallad on 2008-07-02
> **ans5685 said:**
> but I still can't resolve i.e. remove  kio-umountwrapper using apt-get or synaptic :( :(


Drop to your terminal and issue the command below:

```
sudo apt-get remove --purge kio-umountwrapper
```

---

### Post by ans5685 on 2008-07-02
> **iaculallad said:**
> Drop to your terminal and issue the command below:

```
sudo apt-get remove --purge kio-umountwrapper
```

Tried it and 

> The following packages will be REMOVED:
  kio-umountwrapper
0 upgraded, 0 newly installed, 1 to remove and 24 not upgraded.
1 not fully installed or removed.
After this operation, 115kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 194478 files and directories currently installed.)
Removing kio-umountwrapper ...
No diversion `diversion of /usr/share/apps/konqueror/servicemenus/media_safelyremove.desktop by kio-umountwrapper', none removed
No diversion `diversion of /usr/share/apps/dolphin/servicemenus/media_safelyremove.desktop by kio-umountwrapper', none removed
Removing `diversion of /usr/share/apps/d3lphin/servicemenus/media_safelyremove.desktop to /usr/share/apps/d3lphin/servicemenus/media_safelyremove.desktop.distrib by kio-umountwrapper'
dpkg-divert: error checking `/usr/share/apps/d3lphin/servicemenus/media_safelyremove.desktop': No such file or directory
dpkg: error processing kio-umountwrapper (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 kio-umountwrapper
E: Sub-process /usr/bin/dpkg returned an error code (1)


:(:(:(:(:
 
Maybe I'll learn to live with it.
Thanks again.

---

### Post by ChameleonDave on 2008-07-04
> **ans5685 said:**
> Thanks guys!!!
I did as iaculallad said immediately followed by tinivole's instructions and the sudo problem is SOLVED but I still can't resolve i.e. remove  kio-umountwrapper using apt-get or synaptic :( :(
Thanks again

For that one, just look up "kio-umountwrapper" in the forum.

---

