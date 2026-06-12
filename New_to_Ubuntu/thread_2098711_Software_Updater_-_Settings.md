---
title: "Software Updater - Settings"
date: 2012-12-27
forum: New to Ubuntu
---

### Post by seghele on 2012-12-27
Hello,
Greetings from Belgium.

 I'm using Ubuntu 12.10.
 I've a problem with the Software Updater.
 The button “settings” is not working/ not responding.
 What must I do? :confused:

---

### Post by howefield on 2012-12-27
Can you open Software Sources (it may take a while to load) ?

---

### Post by seghele on 2012-12-27
Yes

---

### Post by Laiquendi on 2012-12-27
So there you are, those are the same settings :)

Maybe it's a common issue and in such case it will be fixed with patch. If no - look for other errors you get (if any) and try to make out something from it.

---

### Post by seghele on 2012-12-27
Sorry, I thought it was the Software Center.
So, "Software Sources" v 0.92.9 will not open !!!

---

### Post by ibjsb4 on 2012-12-27
> **seghele said:**
> Hello,
Greetings from Belgium.

 I'm using Ubuntu 12.10.
 I've a problem with the Software Updater.
 The button “settings” is not working/ not responding.
 What must I do? :confused:

Try this

[open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

```
sudo apt-get update
```

Get any errors?

---

### Post by seghele on 2012-12-27
No change after update.

---

### Post by seghele on 2012-12-27
This is what I did:
~$ sudo apt-get clean && sudo apt-get autoremove
~$ sudo apt-get -f install
~$ sudo dpkg --configure -a
~$ sudo apt-get update
~$ sudo apt-get install --reinstall update-manager
~$ sudo apt-get update
Situation still the same !

---

### Post by seghele on 2012-12-28
No more HELP ???

---

### Post by howefield on 2012-12-28
Open a terminal and type

```
software-properties-gtk
```

Does it error ? If so, post the output.

---

### Post by seghele on 2012-12-28
:~$ software-properties-gtk
gpg: /tmp/tmpm1m133/trustdb.gpg: trustdb created
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/UbuntuDrivers/detect.py", line 162, in packages_for_modalias
    cache_map = packages_for_modalias.cache_maps[apt_cache_hash]
KeyError: -1062738956

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/usr/bin/software-properties-gtk", line 103, in <module>
    app = SoftwarePropertiesGtk(datadir=options.data_dir, options=options, file=file)
  File "/usr/lib/python3/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py", line 178, in __init__
    self.init_drivers()
  File "/usr/lib/python3/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py", line 1097, in init_drivers
    self.devices = detect.system_device_drivers()
  File "/usr/lib/python3/dist-packages/UbuntuDrivers/detect.py", line 415, in system_device_drivers
    for pkg, pkginfo in system_driver_packages(apt_cache).items():
  File "/usr/lib/python3/dist-packages/UbuntuDrivers/detect.py", line 319, in system_driver_packages
    for p in packages_for_modalias(apt_cache, alias):
  File "/usr/lib/python3/dist-packages/UbuntuDrivers/detect.py", line 164, in packages_for_modalias
    cache_map = _apt_cache_modalias_map(apt_cache)
  File "/usr/lib/python3/dist-packages/UbuntuDrivers/detect.py", line 129, in _apt_cache_modalias_map
    m = package.candidate.record['Modaliases']
  File "/usr/lib/python3/dist-packages/apt/package.py", line 429, in record
    return Record(self._records.record)
UnicodeDecodeError: 'utf-8' codec can't decode byte 0xeb in position 126: invalid continuation byte

I hope this can help!

---

### Post by howefield on 2012-12-28
Can't help you with that, but what I would do is take a line and stick it into a google search, eg this line..

> File "/usr/lib/python3/dist-packages/UbuntuDrivers/detect.py", line 162, in packages_for_modalias

which gives amongst others...

[https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/1053749](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/1053749)

which looks similar to your error, there is a fix in there that worked for more than one user. I'm not saying this is the answer for you, just how I would try to research it in the event no one else comes along here with anything better.

---

### Post by seghele on 2012-12-28
:D
There was an odd character " ë " in /var/lib/dpkg/status.
 
After changing it in " e " and saving, the problem was fixed.

Now when I do
:~$ software-properties-gtk
gpg: /tmp/tmpxm03zk/trustdb.gpg: trustdb created

And the window with "setting" was activated. 

;)  NO MORE ERRORS.
Thank you / thank you.

---

### Post by howefield on 2012-12-28
Excellent, well done. :)

Glad you nailed it.

---

