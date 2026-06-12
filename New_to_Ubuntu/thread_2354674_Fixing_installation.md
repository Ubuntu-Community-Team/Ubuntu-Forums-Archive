---
title: "Fixing installation"
date: 2017-03-05
forum: New to Ubuntu
---

### Post by charlie102 on 2017-03-05
I removed some files by typing 'sodo apt-get --purge wireshark autoremove'. The command removed more files than I wanted (the command was running for over a minute, then I reseted my comp, I got scared). Now I get a message after booting my computer: "system program problem detected". 

I have run
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```
but I keep getteing this popup message after booting up. Shall I worry about it or ignore it? I don't know if some security-related files were deleted. Is there some simple way to fix it. I dont want to reinstall my system. I am using

 Lubuntu 16.04

---

### Post by Autodave on 2017-03-05
Go into it and read what it says. A lot of times, you will see a program listed there as what the problem is. You can usually go into Synaptic, find that programs, and tell Synaptic to re-install it.

---

### Post by ajgreeny on 2017-03-05
You should have noted in the output of that remove command what the packages were that wireshark wanted to take with it and then hit "n" to abort the removal.  It's always worth taking note of that sort of thing when adding or removing packages, and both the command line and synaptic will tell you all, so whichever way you had chosen in your Lubuntu you could have avoided the problem that has now appeared.
```
grep -i " remove " /var/log/dpkg.log.1 /var/log/dpkg.log
```
will show you all the packages that were removed and by looking at the times shown in the lines of output you will be able to see what was removed at the same time as wireshark. Make a note of all those packages and reinstall them.

If my system (Xubuntu 16.04) is anything to go by, the list of dependency packages added when installing wireshark is not too long, the full list being:-

geoip-database-extra libc-ares2, libjs-openlayers, libqgsttools-p1, libqt5multimedia5-plugins, libqt5multimediawidgets5, libsmi2ldbl, ibwireshark-data, libwireshark6, libwiretap5, libwsutil6, wireshark, wireshark-common, and wireshark-qt.

It is difficult to see why very many packages other than those would have been removed along with the **purge autoremove** command you used, but you should soon be able to see with that first grep command I showed, and then reinstall any of those in your own list that you know you still want.

---

