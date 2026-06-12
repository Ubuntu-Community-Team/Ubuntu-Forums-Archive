---
title: "Pangolin ... Update Manager ... internet stop ... stuck"
date: 2014-01-15
forum: New to Ubuntu
---

### Post by czgirb on 2014-01-15
Currently, I using a **Pangolin** and I do an **Update Manager**, while in the halfway, the internet connection stuck for a long time ... and so the process.
So, I use **xkill** command to end the process and I think to start the process if connection is back to normal.
But when I repeat the process, it recommends me to do a **Partial Upgrade** and I follow the instruction, in the halfway it stop and pop-up:
> **Unable to get exclusive lock**
*This  usually means that another package management application (like apt-get  or aptitude) already running. Please close that application first.*




in googling i found: (so I follow the instruction too)
```
czgirb@czgirb:~$ sudo killall dpkg
[sudo] password for czgirb: 
czgirb@czgirb:~$ sudo rm /var/cache/apt/archives/lock
czgirb@czgirb:~$ sudo rm /var/lib/dpkg/lock
czgirb@czgirb:~$ sudo apt-get -f install
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
czgirb@czgirb:~$ sudo dpkg --configure -a
Processing triggers for menu ...
Setting up update-notifier-common (0.119ubuntu8.6) ...
flashplugin-installer: downloading [http://archive.canonical.com/pool/partne...335.orig.tar.gz]("http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.335.orig.tar.gz")
Installing from local file /tmp/tmpLyZ8qQ.gz
Flash Plugin installed.
Setting up flashplugin-installer (11.2.202.335ubuntu0.12.04.1) ...
Setting up language-pack-zh-hant (1:12.04+20140106) ...
Setting up language-pack-zh-hans (1:12.04+20140106) ...
Setting up language-pack-en (1:12.04+20140106) ...
Setting up language-pack-zh-hant-base (1:12.04+20140106) ...
Generating locales...
  zh_HK.UTF-8... done
  zh_TW.UTF-8... done
Generation complete.
Setting up language-pack-gnome-zh-hant (1:12.04+20140106) ...
Setting up language-pack-gnome-zh-hans (1:12.04+20140106) ...
Setting up language-pack-zh-hans-base (1:12.04+20140106) ...
Generating locales...
  zh_CN.UTF-8... done
  zh_SG.UTF-8... done
Generation complete.
Setting up language-pack-en-base (1:12.04+20140106) ...
Generating locales...
  en_AG.UTF-8... done
  en_AU.UTF-8... done
  en_BW.UTF-8... done
  en_CA.UTF-8... done
  en_DK.UTF-8... done
  en_GB.UTF-8... done
  en_HK.UTF-8... hash collision (1688509771) en_HK.utf8, de_CH.utf8
failed
  en_IE.UTF-8... done
  en_IN.UTF-8... done
  en_NG.UTF-8... done
  en_NZ.UTF-8... done
  en_PH.UTF-8... done
  en_SG.UTF-8... done
  en_US.UTF-8... done
  en_ZA.UTF-8... done
  en_ZM.UTF-8... done
  en_ZW.UTF-8... done
Generation complete.
Setting up language-pack-gnome-en (1:12.04+20140106) ...
Setting up language-pack-gnome-zh-hant-base (1:12.04+20140106) ...
Setting up language-pack-gnome-en-base (1:12.04+20140106) ...
Setting up language-pack-gnome-zh-hans-base (1:12.04+20140106) ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
dpkg: error: failed to remove my own update file /var/lib/dpkg/updates/0000: No such file or directory
czgirb@czgirb:~$



```

After that I repeat the process (**Partial Upgrade**), but it stop with the following information:
> dpkg: error: parsing file '/var/lib/dpkg/updates/0003' near line 0: newline in fireld name '#padding'




Now ... what should I do? Please guide me ...

---

### Post by czgirb on 2014-01-15
czgirb@czgirb:~$ sudo apt-get install -f
[sudo] password for czgirb: 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
czgirb@czgirb:~$ sudo dpkg --configure -a
dpkg: error: parsing file '/var/lib/dpkg/updates/0003' near line 0:
 newline in field name `#padding'
czgirb@czgirb:~$

---

### Post by plucky on 2014-01-15
> **czgirb said:**
> czgirb@czgirb:~$ sudo apt-get install -f
[sudo] password for czgirb: 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
czgirb@czgirb:~$ sudo dpkg --configure -a
dpkg: error: parsing file '/var/lib/dpkg/updates/0003' near line 0:
 newline in field name `#padding'
czgirb@czgirb:~$

That directory should be empty.Open a terminal and:

Post output for ```
ls /var/lib/dpkg/updates/*
```

To clear the directory,use ```
sudo rm -r /var/lib/dpkg/updates/*
```

Then run [code]sudo apt-get update && sudo apt-get dist-upgrade[code] and see if that runs without errors.

Good Luck

---

