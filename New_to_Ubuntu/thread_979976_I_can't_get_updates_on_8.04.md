---
title: "I can't get updates on 8.04"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by theamber on 2008-11-12
Hi I have installed 8.04 on a laptop compaq v5000. When I am downloading the first updates I get this message:
Please inform of this error and include the files:
 /var/log/dist-upgrade.log y /var/log/dist-upgrade-apt.log
Then I get a window like this:

Traceback (most recent call last):

  File "/usr/bin/update-manager", line 101, in <module>
    if not controler.doDistUpgrade():

  File "/usr/lib/python2.5/site-packages/DistUpgrade/DistUpgradeController.py", line 936, in doDistUpgrade
    self._rewriteAptPeriodic(self.apt_minAge)

how do I get this log files and who should I inform.

---

### Post by cariboo on 2008-11-12
All the log files are /var/log as it says in the meesage. you can either use a terminal and cd into /var/log/dist-upgrade or you can do it graphically using Nautilus. Places-->Home Folder-->File System-->var-->log-->dist-upgrade.

Jim

---

### Post by theamber on 2008-11-12
Yes but I cant get into de desktop now. I tried reinstalling it but It dos not get to the desktop anymore. I think I may need the 8.10 version, should that make a difference it is laptop a Compaq V5000 AMD 64 Turion.

---

### Post by theamber on 2008-11-12
I am downloading the 64 bits 8.10 version since I have teh AMD 64 Turion I think that may work better. I will post the results.

---

### Post by theamber on 2008-11-13
I have installed version 8.10 after several tries and with errors, It seems to work but I can't install flash I get this:
md5sum mismatch install_flash_player_10_linux.tar.gz
The Flash plugin is NOT installed.

Procesando activadores para libc6 ...
ldconfig deferred processing now taking place

I tried a couple times but the same I even did it for the terminal window.

---

### Post by zvacet on 2008-11-13
You can install flash from synaptic.be sure that you have partner repo  added to your source list.

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) interpid partner

```
sudo apt-get update
```

After this goto the synaptic and in search box type adobe and you should see adobe flash plugin.Click on white box on the left and install it.

---

