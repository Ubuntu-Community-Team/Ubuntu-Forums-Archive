---
title: "Problem in downloading and updating files"
date: 2012-03-31
forum: New to Ubuntu
---

### Post by mgrameshbabu on 2012-03-31
Hi all,
I am new user for Ubuntu11.10. I am using 64bit windows-7 OS with 4GB ram and AMD processor.  I installed UBUNTU through wubi windows installer. At office I am using proxy server and at home I am using direct broadband connection. With default browser Mozilla firefox, I could able to to browse and download softwares. But when i use ubuntu software centre I could not able to download any software and could not able to update Ubuntu. I tried to download synaptic by using terminal. But got some error report which I have given below.Please go through it and give a solution.

And also I want to learn how to install file packages and tar.gp files manually. Please send me some documents if you have.

Thanks in advance.
Ramesh

Error report:


faculty@ubuntu:~$ sudo get-apt install tcl8.5.11
[sudo] password for faculty: 
sudo: get-apt: command not found
faculty@ubuntu:~$ sudo apt-get install synaptic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libept1
Suggested packages:
  dwww menu deborphan
The following NEW packages will be installed:
  libept1 synaptic
0 upgraded, 2 newly installed, 0 to remove and 400 not upgraded.
2 not fully installed or removed.
Need to get 2,282 kB of archives.
After this operation, 7,574 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libept1 synaptic
Install these packages without verification [y/N]? y
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric/main libept1 amd64 1.0.5build1 [134 kB]
Get:2 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric/universe synaptic amd64 0.75.2ubuntu8 [2,148 kB]
Fetched 2,282 kB in 1min 9s (32.9 kB/s)                                        
Selecting previously deselected package libept1.
(Reading database ... 123706 files and directories currently installed.)
Unpacking libept1 (from .../libept1_1.0.5build1_amd64.deb) ...
Selecting previously deselected package synaptic.
Unpacking synaptic (from .../synaptic_0.75.2ubuntu8_amd64.deb) ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for gnome-menus ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for man-db ...
Setting up flashplugin-downloader:i386 (11.0.1.152ubuntu1) ...
Downloading...
--2012-03-31 10:52:17--  [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.0.1.152.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.0.1.152.orig.tar.gz)
Connecting to 172.16.19.11:80... connected.
Proxy request sent, awaiting response... 404 Not Found
2012-03-31 10:52:17 ERROR 404: Not Found.

download failed
The Flash plugin is NOT installed.
dpkg: error processing flashplugin-downloader:i386 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of flashplugin-installer:
 flashplugin-installer depends on flashplugin-downloader (>= 11.0.1.152ubuntu1); however:
  Package flashplugin-downloader is not installed.
  Package flashplugin-downloader:i386 is not configured yet.
dpkg: error processing flashplugin-installer (--configure):
 dependency problems - leaving unconfigured
Setting up libept1 (1.0.5build1) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          Setting up synaptic (0.75.2ubuntu8) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 flashplugin-downloader:i386
 flashplugin-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by winh8r on 2012-03-31
> **mgrameshbabu said:**
> Hi all,
I am new user for Ubuntu11.10. I am using 64bit windows-7 OS with 4GB ram and AMD processor.  I installed UBUNTU through wubi windows installer. At office I am using proxy server and at home I am using direct broadband connection. With default browser Mozilla firefox, I could able to to browse and download softwares. But when i use ubuntu software centre I could not able to download any software and could not able to update Ubuntu. I tried to download synaptic by using terminal. But got some error report which I have given below.Please go through it and give a solution.

And also I want to learn how to install file packages and tar.gp files manually. Please send me some documents if you have.

Thanks in advance.
Ramesh

Error report:


faculty@ubuntu:~$ sudo**[COLOR="Red"] get-apt[/COLOR]** install tcl8.5.11
[sudo] password for faculty: 
sudo: get-apt: command not found
faculty@ubuntu:~$ sudo apt-get install synaptic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libept1
Suggested packages:
  dwww menu deborphan
The following NEW packages will be installed:
  libept1 synaptic
0 upgraded, 2 newly installed, 0 to remove and 400 not upgraded.
2 not fully installed or removed.
Need to get 2,282 kB of archives.
After this operation, 7,574 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libept1 synaptic
Install these packages without verification [y/N]? y
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric/main libept1 amd64 1.0.5build1 [134 kB]
Get:2 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric/universe synaptic amd64 0.75.2ubuntu8 [2,148 kB]
Fetched 2,282 kB in 1min 9s (32.9 kB/s)                                        
Selecting previously deselected package libept1.
(Reading database ... 123706 files and directories currently installed.)
Unpacking libept1 (from .../libept1_1.0.5build1_amd64.deb) ...
Selecting previously deselected package synaptic.
Unpacking synaptic (from .../synaptic_0.75.2ubuntu8_amd64.deb) ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for gnome-menus ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for man-db ...
Setting up flashplugin-downloader:i386 (11.0.1.152ubuntu1) ...
Downloading...
--2012-03-31 10:52:17--  [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.0.1.152.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.0.1.152.orig.tar.gz)
Connecting to 172.16.19.11:80... connected.
Proxy request sent, awaiting response... 404 Not Found
2012-03-31 10:52:17 ERROR 404: Not Found.

download failed
The Flash plugin is NOT installed.
dpkg: error processing flashplugin-downloader:i386 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of flashplugin-installer:
 flashplugin-installer depends on flashplugin-downloader (>= 11.0.1.152ubuntu1); however:
  Package flashplugin-downloader is not installed.
  Package flashplugin-downloader:i386 is not configured yet.
dpkg: error processing flashplugin-installer (--configure):
 dependency problems - leaving unconfigured
Setting up libept1 (1.0.5build1) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          Setting up synaptic (0.75.2ubuntu8) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 flashplugin-downloader:i386
 flashplugin-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)

Hi,

Your first error was caused by using get-apt rather than the correct apt-get.

try running this command

```
sudo apt-get update && sudo apt-get upgrade
```

In order to try and resolve the flash problem, click on the link in my sig below "Help with Flash" and install FlashAid then run the wizard and it will check your system and offer you the best option.

Try this and report back any problems.

---

### Post by codemaniac on 2012-03-31
Hello mgrameshbabu ,

Welcome to Ubuntuforums .!!!
Seems like the package you are trying to install needs flash plugin .
if you want to install Flash, Java, MP3 playback, and a lot of other popular proprietary codecs all at once, install the **ubuntu-restricted-extras** package instead.Try the below in your terminal .
```
sudo apt-get install ubuntu-restricted-extras
```
The below link should help .
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by santosh83 on 2012-03-31
> **mgrameshbabu said:**
> 
faculty@ubuntu:~$ sudo apt-get install synaptic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libept1
Suggested packages:
  dwww menu deborphan
The following NEW packages will be installed:
  libept1 synaptic
0 upgraded, 2 newly installed, 0 to remove and 400 not upgraded.
2 not fully installed or removed.
Need to get 2,282 kB of archives.
After this operation, 7,574 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libept1 synaptic
Install these packages without verification [y/N]? y
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric/main libept1 amd64 1.0.5build1 [134 kB]
Get:2 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric/universe synaptic amd64 0.75.2ubuntu8 [2,148 kB]
Fetched 2,282 kB in 1min 9s (32.9 kB/s)                                        


Others have you given you suggestions as to what to do, but I just want to note something here.

From your command output above, I'm surprised that libept1 and synaptic cannot be authenticated! 

I was under the impression that the official canonical repositories (main channel) were automatically authenticated, since the necessary keys are supplied as a part of the system...

Perhaps your package system itself is somehow broken?

---

### Post by mgrameshbabu on 2012-04-02
Thank you Shantosh
I completely formated and reinstalled the latest version of Ubuntu. Now it is working well.

Thanks
Ramesh

---

