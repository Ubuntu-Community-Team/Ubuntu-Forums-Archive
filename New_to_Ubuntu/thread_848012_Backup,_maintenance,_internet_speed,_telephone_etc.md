---
title: "Backup, maintenance, internet speed, telephone etc."
date: 2008-07-03
forum: New to Ubuntu
---

### Post by mainak_sen on 2008-07-03
Hi,

I am new to Ubuntu and Linux, having migrated from Win XP recently. I have the following questions:

1. What do I need to do, if anything at all, to maintain my computer on a regular basis? I mean, things like clearing the various caches, temporary  files, redundant/obsolete files, etc. Is there a simple program (like we have for Windows) that will do this?

2. I checked in the forum and found a number of programs for taking backups. Now, apart from my 'Home' folder, where I keep all my documents and stuff, which all SYSTEM FOLDERS do I need to backup? Clearly one option is to backup the entire HDD (i.e. take a disk image) but that I feel is overkill, taking way too much time and space. What is a the subset of the system files that I absolutely need in order to recover my system if something bad is to happen. Coming over from Windows, I am looking for something equivalent to System Restore

3. I use a Broadband Internet connection from my ISP. Is there a utility which allows me to measure the download/upload speed that I am actually getting?

4. I also have a dial-up modem connected to my computer, which can be linked to my telephone (ordinary land-line phone from the local utility company). Is there a program that I can use to make/receive telephone calls  from my computer using my telephone connection? Note: I am NOT looking for VOIP; I just want to use conventional telephony, only substituting the functions of my telephone handset by the computer, so that I can dial/receive calls, maintain a telephone directory, may be get Caller ID etc.

Any help from anybody on any of the above will be appreciated. Thanks in advance.

---

### Post by hyper_ch on 2008-07-03
(1) it is adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

(2) > **mainak_sen said:**
> I am new to Ubuntu and Linux, having migrated from Win XP recently.
good choice ;)

(3) > **mainak_sen said:**
> 1. What do I need to do, if anything at all, to maintain my computer on a regular basis?
Just keep the software up-to-date ;) luckily there is one centralized process for that ;)

(4) > **mainak_sen said:**
> 2. I checked in the forum and found a number of programs for taking backups. Now, apart from my 'Home' folder, where I keep all my documents and stuff, which all SYSTEM FOLDERS do I need to backup?
It depends... you also might want to backup /etc folder as it contains system-wide configuration files... if you run apache and a locla website you want to backup /var/www... if you run mysql you should also backup the databases either with mysqldump or (not recommended) shutting down mysql and copy the database binary files from /var/lib/mysql... you may want to backup log files also /var/log....

(5) > **mainak_sen said:**
> 3. I use a Broadband Internet connection from my ISP. Is there a utility which allows me to measure the download/upload speed that I am actually getting?
Doesn't your router show current transfer rates?

(5) > **mainak_sen said:**
> Is there a program that I can use to make/receive telephone calls  from my computer using my telephone connection?
I think with Asterisk this might be possible: [http://en.wikipedia.org/wiki/Asterisk_(PBX](http://en.wikipedia.org/wiki/Asterisk_(PBX))

---

### Post by iaculallad on 2008-07-03
> **mainak_sen said:**
> 

2. I checked in the forum and found a number of programs for taking backups. Now, apart from my 'Home' folder, where I keep all my documents and stuff, which all SYSTEM FOLDERS do I need to backup? Clearly one option is to backup the entire HDD (i.e. take a disk image) but that I feel is overkill, taking way too much time and space. What is a the subset of the system files that I absolutely need in order to recover my system if something bad is to happen. Coming over from Windows, I am looking for something equivalent to System Restore



Try to use the **sbackup** restore/backup utility. It's available in the repository:

```
sudo apt-get install sbackup
```

and to access it after your successful install:

Navigate to System->Administration->Simple Backup Config

---

### Post by AtrejuT on 2008-07-03
> **mainak_sen said:**
> Hi,

I am new to Ubuntu and Linux, having migrated from Win XP recently. I have the following questions:

1. What do I need to do, if anything at all, to maintain my computer on a regular basis? I mean, things like clearing the various caches, temporary  files, redundant/obsolete files, etc. Is there a simple program (like we have for Windows) that will do this?

2. I checked in the forum and found a number of programs for taking backups. Now, apart from my 'Home' folder, where I keep all my documents and stuff, which all SYSTEM FOLDERS do I need to backup? Clearly one option is to backup the entire HDD (i.e. take a disk image) but that I feel is overkill, taking way too much time and space. What is a the subset of the system files that I absolutely need in order to recover my system if something bad is to happen. Coming over from Windows, I am looking for something equivalent to System Restore

3. I use a Broadband Internet connection from my ISP. Is there a utility which allows me to measure the download/upload speed that I am actually getting?

4. I also have a dial-up modem connected to my computer, which can be linked to my telephone (ordinary land-line phone from the local utility company). Is there a program that I can use to make/receive telephone calls  from my computer using my telephone connection? Note: I am NOT looking for VOIP; I just want to use conventional telephony, only substituting the functions of my telephone handset by the computer, so that I can dial/receive calls, maintain a telephone directory, may be get Caller ID etc.

Any help from anybody on any of the above will be appreciated. Thanks in advance.


Alright, lets see if I can help there:
1. I don't think you need to do anything. Of course you can clean out browser caches if you want to, but I don't think that makes a lot of sense. Temporary files are stored in /tmp and deleted with every reboot.

2. Depends a little on what you want. I personally only take backups of my home folder. Not only is all my data stored there (and that's the only _seriously_ important thing to back up), but all program settins are also stored in /home/yourusername. So in case of a seriously busted system (and I didn't have that yet, using Ubuntu already for 3 years) you can just reinstall. Only takes say 40 minutes or so, including all your programs. and all your settings are backed up, after all.

If you want to know all your installed programs for easy reinstallation you can run
```

dpkg -l > list.txt

```
in a terminal. That prints a list of all packages installed on your system and saves that list in the file list.txt

3. I guess system monitor (system-administration-system monitor) shows your current upspeed/downspeed. but that's just what you're currently using. you could also have a look here:
[http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-linux.html](http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-linux.html)

4. sorry - no idea. any other takers?

welcome to ubuntu!

atreju

---

### Post by saratchandra on 2008-07-03
> **mainak_sen said:**
> Hi,

I am new to Ubuntu and Linux, having migrated from Win XP recently. I have the following questions:

1. What do I need to do, if anything at all, to maintain my computer on a regular basis? I mean, things like clearing the various caches, temporary  files, redundant/obsolete files, etc. Is there a simple program (like we have for Windows) that will do this?

2. I checked in the forum and found a number of programs for taking backups. Now, apart from my 'Home' folder, where I keep all my documents and stuff, which all SYSTEM FOLDERS do I need to backup? Clearly one option is to backup the entire HDD (i.e. take a disk image) but that I feel is overkill, taking way too much time and space. What is a the subset of the system files that I absolutely need in order to recover my system if something bad is to happen. Coming over from Windows, I am looking for something equivalent to System Restore

3. I use a Broadband Internet connection from my ISP. Is there a utility which allows me to measure the download/upload speed that I am actually getting?

4. I also have a dial-up modem connected to my computer, which can be linked to my telephone (ordinary land-line phone from the local utility company). Is there a program that I can use to make/receive telephone calls  from my computer using my telephone connection? Note: I am NOT looking for VOIP; I just want to use conventional telephony, only substituting the functions of my telephone handset by the computer, so that I can dial/receive calls, maintain a telephone directory, may be get Caller ID etc.

Any help from anybody on any of the above will be appreciated. Thanks in advance.

You can use the netspeed applet for gnome-panel to measure internet speed. Check for netspeed in synaptic.

---

