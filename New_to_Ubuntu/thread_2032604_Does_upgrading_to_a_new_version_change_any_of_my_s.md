---
title: "Does upgrading to a new version change any of my settings?"
date: 2012-07-24
forum: New to Ubuntu
---

### Post by Bufeu on 2012-07-24
As the topic says, does an upgrade to a new version change my settings/my configurations?
For example, I have added my own desktop backgrounds in /use/share/backgrounds, will these files be deleted and replaced? I have also done a lot of modifications in /etc/xdg, /usr/share/applications and on Unity (via dconf), will this also be lost?  Is there no way to update only the most necessary, without taking the risk of a broken installation (provided the computer is not disconnected from the power outlet, of course)?

---

### Post by raja.genupula on 2012-07-24
No its not going to change any of your settings and installed applications . But always its a good habit of taking Backup of your system before upgrading .

one more good thing is to check your system performance by a LIVE CD , Here you have to check the hardware like Audio,Video,Wifi,Sound etc.

If everything is fine you can go happily . If any problems faced , google that problem have solutions or not . I hope maximum problems are fixed so you will find solutions . 

all the best .:)

---

### Post by Bufeu on 2012-07-24
Sp, if I use KDE (just as an example), a upgrading will not install and "active" Unity (as I know is the standard shell interface in Ubuntu since 11.04)?

---

### Post by audiomick on 2012-07-24
As already mentioned, a problem free upgrade will not affect any of your settings. 

If you have done a lot of tweaking, you might be interested in reading this.

[https://help.ubuntu.com/community/Partitioning/Home/Moving]("https://help.ubuntu.com/community/Partitioning/Home/Moving")

The gist of it is that all your config stuff is in your /home/user folder. If you put /home on a separate partition, you can even do a fresh install without losing your setting. You re-use the existing /home in the new install, thereby retaining all your data and all your settings.

---

### Post by Bufeu on 2012-07-24
> **audiomick said:**
> As already mentioned, a problem free upgrade will not affect any of your settings. 

If you have done a lot of tweaking, you might be interested in reading this.

[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

The gist of it is that all your config stuff is in your /home/user folder. If you put /home on a separate partition, you can even do a fresh install without losing your setting. You re-use the existing /home in the new install, thereby retaining all your data and all your settings.
But the settings I have done OUTSIDE /home then? Will THEY be lost during a upgrade of the system?

---

### Post by audiomick on 2012-07-24
> **Bufeu said:**
> But the settings I have done OUTSIDE /home then? Will THEY be lost during a upgrade of the system?
What settings would that be? As far as I know, Ubuntu stores all user related config files in hidden files/folders in the /home/user folder of the user that made the settings. 

If you know of a config file that is stored elsewhere, then you already know which file you need to backup in order to re-use it in a new install... ;)

---

### Post by Bufeu on 2012-07-24
> **audiomick said:**
> What settings would that be? As far as I know, Ubuntu stores all user related config files in hidden files/folders in the /home/user folder of the user that made the settings. 

If you know of a config file that is stored elsewhere, then you already know which file you need to backup in order to re-use it in a new install... ;)
The problem is that I don't know exactly which files I have modified, that's why I am asking IF some files  will be "restored"/deleted/lost.

---

### Post by oldfred on 2012-07-24
I found it worthwhile to backup /etc. And any other folder in / that you may have added custom settings. I learned to make a copy of any system file I edited into a folder in /home so my backup of /home includes all my settings.

 I only do clean installs to another 25GB / partition so I have old install (just in case I missed something), but when I used to do upgrades it would always ask if I wanted to keep old config. 
If you keep old config, it may not work with new version or if you overwrite old version you may lose your custom settings. So best to backup, let system update to current settings and re-add those settings you need (often a lot fewer).

---

### Post by Bufeu on 2012-07-24
oldfred, so does a upgrade means lost customized settings/files?

---

### Post by oldfred on 2012-07-24
I have not done an upgrade since 9.04. But then it always asked if you wanted to overwrite configuration files. I do not think it backed them up. But I tried using my files and had issues as old settings did not work. And I tried accepting new files and lost old settings. Back then it also offered to compare configurations, but that did not help me much as I was not sure what I was seeing.

Backup is best.

---

### Post by Bufeu on 2012-07-24
> **oldfred said:**
> I have not done an upgrade since 9.04. But then it always asked if you wanted to overwrite configuration files. I do not think it backed them up. But I tried using my files and had issues as old settings did not work. And I tried accepting new files and lost old settings. Back then it also offered to compare configurations, but that did not help me much as I was not sure what I was seeing.

Backup is best.Since you have not upgraded, I hope someone else an answer my question... But I'll backup before upgrading. :)

---

