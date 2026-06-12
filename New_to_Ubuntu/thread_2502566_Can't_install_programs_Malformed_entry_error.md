---
title: "Can't install programs: Malformed entry error"
date: 2024-11-19
forum: New to Ubuntu
---

### Post by snoylr on 2024-11-19
I am trying to install a program by using the terminal.

I am supposed to use the commands listed below.

su -
apt update
apt install -f ./softmaker-office-nx_1218-01_amd64.deb

When I try the commands, it get the following error message:

Malformed entry 1 in list file /etc/apt/sources.list.d/archive_uri-https_shop_softmaker_com_repo_apt-noble.list (Component)


The software updater and synaptic both error out with the same error message.

I am a novice in using Ubuntu so have little experience finding file paths or using the terminal



su -
apt update
apt install -f ./softmaker-office-nx_1218-01_amd64.deb

---

### Post by 1fallen on 2024-11-19
Dose that .deb file actually exist?
this is a correct install for softmaker:
```
sudo -i
mkdir -p /etc/apt/keyrings
wget -qO- https://shop.softmaker.com/repo/linux-repo-public.key | gpg --dearmor > /etc/apt/keyrings/softmaker.gpg
echo "deb [signed-by=/etc/apt/keyrings/softmaker.gpg] https://shop.softmaker.com/repo/apt stable non-free" > /etc/apt/sources.list.d/softmaker.list
apt update
apt install softmaker-office-nx
```
Run one line at a time.
Then Type "exit"
```
[FONT=monospace][COLOR=#000000]apt policy softmaker-office-nx [/COLOR]
softmaker-office-nx: 
  Installed: 3655 
  Candidate: 3655 
  Version table: 
 *** 3655 500 
        500 https://shop.softmaker.com/repo/apt stable/non-free amd64 Packages 
        100 /var/lib/dpkg/status


[/FONT]
```

---

### Post by snoylr on 2024-11-19
The terminal commands failed with the Malformed entry error.  Here is the readout from my terminal

ichard@Richard-DT-2024:~$ sudo -i
[sudo] password for richard: 
root@Richard-DT-2024:~# mkdir -p /etc/apt/keyrings
root@Richard-DT-2024:~# wget -qO- [https://shop.softmaker.com/repo/linux-repo-public.key](https://shop.softmaker.com/repo/linux-repo-public.key) | gpg --dearmor > /etc/apt/keyrings/softmaker.gpg
    
echo "deb [signed-by=/etc/apt/keyrings/softmaker.gpg] [https://shop.softmaker.com/repo/apt](https://shop.softmaker.com/repo/apt) stable non-free" > /etc/apt/sources.list.d/softmaker.list


root@Richard-DT-2024:~# 
root@Richard-DT-2024:~# echo "deb [signed-by=/etc/apt/keyrings/softmaker.gpg] [https://shop.softmaker.com/repo/apt](https://shop.softmaker.com/repo/apt) stable non-free" > /etc/apt/sources.list.d/softmaker.list
root@Richard-DT-2024:~# 
root@Richard-DT-2024:~# apt date
E: Invalid operation date
root@Richard-DT-2024:~# apt update
E: Malformed entry 1 in list file /etc/apt/sources.list.d/archive_uri-https_shop_softmaker_com_repo_apt-noble.list (Component)
E: The list of sources could not be read.
root@Richard-DT-2024:~#

---

### Post by 1fallen on 2024-11-19
Please show me this:
```
inxi -r
```
And wrap that return in CODE Tags...Like this [noparse]```
 your paste here
```[/noparse]
makes it easier to read.

---

### Post by snoylr on 2024-11-19
That was a dead end.  The system can't find inxi, and I can't install it because of Malformed entry

[CODE]


root@Richard-DT-2024:~# inxi -r
Command 'inxi' not found, but can be installed with:
apt install inxi
root@Richard-DT-2024:~# apt install inxi
E: Malformed entry 1 in list file /etc/apt/sources.list.d/archive_uri-https_shop_softmaker_com_repo_apt-noble.list (Component)
E: The list of sources could not be read.
root@Richard-DT-2024:~# 

[CODE]

---

### Post by 1fallen on 2024-11-19
Then this should help
```
[FONT=monospace][COLOR=#000000]ls -l  /etc/apt/sources.list.d/[/COLOR]

```
Your Last code box should look like this [/CODE] don't forget the leading slash "/"


[/FONT]

---

### Post by snoylr on 2024-11-19
That gave me some information

CODE:

root@Richard-DT-2024:~# ls -l  /etc/apt/sources.list.d/
total 28
-rw-r--r-- 1 root root  120 Nov 17 19:32 archive_uri-https_shop_softmaker_com_repo_apt-noble.list
-rw-r--r-- 1 root root  190 Nov 17 19:32 google-chrome.list
-rw-r--r-- 1 root root  190 Nov 17 19:32 google-chrome.list.save
-rw-r--r-- 1 root root  100 Nov 19 14:34 softmaker.list
-rw-r--r-- 1 root root  386 Nov 17 19:32 ubuntu.sources
-rw-r--r-- 1 root root 2552 Apr 24  2024 ubuntu.sources.curtin.orig
-rw-r--r-- 1 root root  386 Nov 17 19:32 ubuntu.sources.save

[/CODE]

---

### Post by 1fallen on 2024-11-19
Well that was not what I expected at all.
For now until I figure out what the hell is going on there:
Run:
```
exit
```
Then run
```
sudo rm -f  /etc/apt/sources.list.d/archive_uri-https_shop_softmaker_com_repo_apt-noble.list
```
Next run:
```
sudo apt update
```
I would like to see that please.

---

### Post by snoylr on 2024-11-19
Here goes:

```


richard@Richard-DT-2024:~$ sudo rm -f  /etc/apt/sources.list.d/archive_uri-https_shop_softmaker_com_repo_apt-noble.list
[sudo] password for richard: 
richard@Richard-DT-2024:~$ sudo apt update
Hit:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) noble InRelease
Get:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) noble-updates InRelease [126 kB]                                   
Get:3 [https://dl.google.com/linux/chrome/deb](https://dl.google.com/linux/chrome/deb) stable InRelease [1,825 B]                                      
Get:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) noble-security InRelease [126 kB]                                    
Get:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) noble-backports InRelease [126 kB]                                 
Get:6 [https://dl.google.com/linux/chrome/deb](https://dl.google.com/linux/chrome/deb) stable/main amd64 Packages [1,221 B]                            
Get:7 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) noble-updates/main i386 Packages [332 kB]                          
Get:8 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) noble-updates/main amd64 Packages [664 kB]    
Get:9 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) noble-updates/main Translation-en [156 kB]
Get:10 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) noble-updates/main amd64 Components [120 kB]                    
Get:11 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) noble-updates/restricted amd64 Packages [473 kB]                  
Get:12 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) noble-security/main i386 Packages [201 kB]                  
Get:13 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) noble-updates/restricted Translation-en [91.2 kB]                 
Get:14 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) noble-updates/restricted amd64 Components [212 B]                 
Get:15 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) noble-updates/universe amd64 Packages [718 kB]            
Get:16 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) noble-updates/universe i386 Packages [441 kB]                     
Get:17 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) noble-updates/universe amd64 Components [310 kB]                  
Get:18 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) noble-updates/multiverse amd64 Components [940 B]                 
Get:19 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) noble-backports/main amd64 Components [208 B]              
Get:20 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) noble-backports/restricted amd64 Components [212 B]        
Get:21 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) noble-backports/universe amd64 Components [21.1 kB]        
Get:22 [https://shop.softmaker.com/repo/apt](https://shop.softmaker.com/repo/apt) stable InRelease [2,348 B]                                        
Get:23 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) noble-backports/multiverse amd64 Components [212 B]               
Get:24 [https://shop.softmaker.com/repo/apt](https://shop.softmaker.com/repo/apt) stable/non-free amd64 Packages [1,153 B]              
Get:25 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) noble-security/main amd64 Packages [491 kB]
Get:26 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) noble-security/main Translation-en [101 kB]
Get:27 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) noble-security/main amd64 Components [7,192 B]
Get:28 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) noble-security/restricted amd64 Packages [473 kB]
Get:29 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) noble-security/restricted Translation-en [91.2 kB]
Get:30 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) noble-security/restricted amd64 Components [212 B]
Get:31 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) noble-security/universe i386 Packages [354 kB]
Get:32 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) noble-security/universe amd64 Packages [561 kB]
Get:33 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) noble-security/universe amd64 Components [51.9 kB]
Get:34 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) noble-security/multiverse amd64 Components [212 B]
Fetched 6,045 kB in 2s (3,016 kB/s)               
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
69 packages can be upgraded. Run 'apt list --upgradable' to see them.
richard@Richard-DT-2024:~$ apt list --upgradable
Listing... Done
acl/noble-updates 2.3.2-1build1.1 amd64 [upgradable from: 2.3.2-1build1]
file-roller/noble-updates 44.3-0ubuntu1 amd64 [upgradable from: 44.1-1]
gir1.2-glib-2.0/noble-updates,noble-security 2.80.0-6ubuntu3.2 amd64 [upgradable from: 2.80.0-6ubuntu3.1]
gir1.2-javascriptcoregtk-4.1/noble-updates,noble-security 2.46.3-0ubuntu0.24.04.1 amd64 [upgradable from: 2.46.1-0ubuntu0.24.04.1]
gir1.2-javascriptcoregtk-6.0/noble-updates,noble-security 2.46.3-0ubuntu0.24.04.1 amd64 [upgradable from: 2.46.1-0ubuntu0.24.04.1]
gir1.2-mutter-14/noble-updates 46.2-1ubuntu0.24.04.4 amd64 [upgradable from: 46.2-1ubuntu0.24.04.2]
gir1.2-webkit-6.0/noble-updates,noble-security 2.46.3-0ubuntu0.24.04.1 amd64 [upgradable from: 2.46.1-0ubuntu0.24.04.1]
gir1.2-webkit2-4.1/noble-updates,noble-security 2.46.3-0ubuntu0.24.04.1 amd64 [upgradable from: 2.46.1-0ubuntu0.24.04.1]
gnome-control-center-data/noble-updates,noble-updates 1:46.4-0ubuntu0.24.04.1 all [upgradable from: 1:46.0.1-1ubuntu7]
gnome-control-center-faces/noble-updates,noble-updates 1:46.4-0ubuntu0.24.04.1 all [upgradable from: 1:46.0.1-1ubuntu7]
gnome-control-center/noble-updates 1:46.4-0ubuntu0.24.04.1 amd64 [upgradable from: 1:46.0.1-1ubuntu7]
google-chrome-stable/stable 131.0.6778.85-1 amd64 [upgradable from: 130.0.6723.116-1]
gstreamer1.0-pipewire/noble-updates 1.0.5-1ubuntu2 amd64 [upgradable from: 1.0.5-1ubuntu1]
krb5-locales/noble-updates,noble-updates 1.20.1-6ubuntu2.2 all [upgradable from: 1.20.1-6ubuntu2.1]
ldap-utils/noble-updates 2.6.7+dfsg-1~exp1ubuntu8.1 amd64 [upgradable from: 2.6.7+dfsg-1~exp1ubuntu8]
libacl1/noble-updates 2.3.2-1build1.1 amd64 [upgradable from: 2.3.2-1build1]
libaudit-common/noble-updates,noble-updates 1:3.1.2-2.1build1.1 all [upgradable from: 1:3.1.2-2.1build1]
libaudit1/noble-updates 1:3.1.2-2.1build1.1 amd64 [upgradable from: 1:3.1.2-2.1build1]
libboost-iostreams1.83.0/noble-updates 1.83.0-2.1ubuntu3.1 amd64 [upgradable from: 1.83.0-2.1ubuntu3]
libboost-locale1.83.0/noble-updates 1.83.0-2.1ubuntu3.1 amd64 [upgradable from: 1.83.0-2.1ubuntu3]
libboost-thread1.83.0/noble-updates 1.83.0-2.1ubuntu3.1 amd64 [upgradable from: 1.83.0-2.1ubuntu3]
libcurl3t64-gnutls/noble-updates,noble-security 8.5.0-2ubuntu10.5 amd64 [upgradable from: 8.5.0-2ubuntu10.4]
libcurl4t64/noble-updates,noble-security 8.5.0-2ubuntu10.5 amd64 [upgradable from: 8.5.0-2ubuntu10.4]
libglib2.0-0t64/noble-updates,noble-security 2.80.0-6ubuntu3.2 amd64 [upgradable from: 2.80.0-6ubuntu3.1]
libglib2.0-bin/noble-updates,noble-security 2.80.0-6ubuntu3.2 amd64 [upgradable from: 2.80.0-6ubuntu3.1]
libglib2.0-data/noble-updates,noble-updates,noble-security,noble-security 2.80.0-6ubuntu3.2 all [upgradable from: 2.80.0-6ubuntu3.1]
libgssapi-krb5-2/noble-updates 1.20.1-6ubuntu2.2 amd64 [upgradable from: 1.20.1-6ubuntu2.1]
libjavascriptcoregtk-4.1-0/noble-updates,noble-security 2.46.3-0ubuntu0.24.04.1 amd64 [upgradable from: 2.46.1-0ubuntu0.24.04.1]
libjavascriptcoregtk-6.0-1/noble-updates,noble-security 2.46.3-0ubuntu0.24.04.1 amd64 [upgradable from: 2.46.1-0ubuntu0.24.04.1]
libk5crypto3/noble-updates 1.20.1-6ubuntu2.2 amd64 [upgradable from: 1.20.1-6ubuntu2.1]
libkrb5-3/noble-updates 1.20.1-6ubuntu2.2 amd64 [upgradable from: 1.20.1-6ubuntu2.1]
libkrb5support0/noble-updates 1.20.1-6ubuntu2.2 amd64 [upgradable from: 1.20.1-6ubuntu2.1]
libldap-common/noble-updates,noble-updates 2.6.7+dfsg-1~exp1ubuntu8.1 all [upgradable from: 2.6.7+dfsg-1~exp1ubuntu8]
libldap2/noble-updates 2.6.7+dfsg-1~exp1ubuntu8.1 amd64 [upgradable from: 2.6.7+dfsg-1~exp1ubuntu8]
libmutter-14-0/noble-updates 46.2-1ubuntu0.24.04.4 amd64 [upgradable from: 46.2-1ubuntu0.24.04.2]
libpipewire-0.3-0t64/noble-updates 1.0.5-1ubuntu2 amd64 [upgradable from: 1.0.5-1ubuntu1]
libpipewire-0.3-common/noble-updates,noble-updates 1.0.5-1ubuntu2 all [upgradable from: 1.0.5-1ubuntu1]
libpipewire-0.3-modules/noble-updates 1.0.5-1ubuntu2 amd64 [upgradable from: 1.0.5-1ubuntu1]
libpython3.12-minimal/noble-updates,noble-security 3.12.3-1ubuntu0.3 amd64 [upgradable from: 3.12.3-1ubuntu0.2]
libpython3.12-stdlib/noble-updates,noble-security 3.12.3-1ubuntu0.3 amd64 [upgradable from: 3.12.3-1ubuntu0.2]
libpython3.12t64/noble-updates,noble-security 3.12.3-1ubuntu0.3 amd64 [upgradable from: 3.12.3-1ubuntu0.2]
libspa-0.2-bluetooth/noble-updates 1.0.5-1ubuntu2 amd64 [upgradable from: 1.0.5-1ubuntu1]
libspa-0.2-modules/noble-updates 1.0.5-1ubuntu2 amd64 [upgradable from: 1.0.5-1ubuntu1]
libwebkit2gtk-4.1-0/noble-updates,noble-security 2.46.3-0ubuntu0.24.04.1 amd64 [upgradable from: 2.46.1-0ubuntu0.24.04.1]
libwebkitgtk-6.0-4/noble-updates,noble-security 2.46.3-0ubuntu0.24.04.1 amd64 [upgradable from: 2.46.1-0ubuntu0.24.04.1]
lintian/noble-updates,noble-updates 2.117.0ubuntu1.2 all [upgradable from: 2.117.0ubuntu1.1]
linux-generic-hwe-24.04/noble-updates,noble-security 6.8.0-49.49 amd64 [upgradable from: 6.8.0-48.48]
linux-headers-generic-hwe-24.04/noble-updates,noble-security 6.8.0-49.49 amd64 [upgradable from: 6.8.0-48.48]
linux-image-generic-hwe-24.04/noble-updates,noble-security 6.8.0-49.49 amd64 [upgradable from: 6.8.0-48.48]
linux-libc-dev/noble-updates,noble-security 6.8.0-49.49 amd64 [upgradable from: 6.8.0-48.48]
linux-tools-common/noble-updates,noble-updates,noble-security,noble-security 6.8.0-49.49 all [upgradable from: 6.8.0-48.48]
mtr-tiny/noble-updates 0.95-1.1ubuntu0.1 amd64 [upgradable from: 0.95-1.1build2]
mutter-common-bin/noble-updates 46.2-1ubuntu0.24.04.4 amd64 [upgradable from: 46.2-1ubuntu0.24.04.2]
mutter-common/noble-updates,noble-updates 46.2-1ubuntu0.24.04.4 all [upgradable from: 46.2-1ubuntu0.24.04.2]
pipewire-alsa/noble-updates 1.0.5-1ubuntu2 amd64 [upgradable from: 1.0.5-1ubuntu1]
pipewire-audio/noble-updates,noble-updates 1.0.5-1ubuntu2 all [upgradable from: 1.0.5-1ubuntu1]
pipewire-bin/noble-updates 1.0.5-1ubuntu2 amd64 [upgradable from: 1.0.5-1ubuntu1]
pipewire-pulse/noble-updates 1.0.5-1ubuntu2 amd64 [upgradable from: 1.0.5-1ubuntu1]
pipewire/noble-updates 1.0.5-1ubuntu2 amd64 [upgradable from: 1.0.5-1ubuntu1]
python3-distupgrade/noble-updates,noble-updates 1:24.04.23 all [upgradable from: 1:24.04.19]
python3.12-minimal/noble-updates,noble-security 3.12.3-1ubuntu0.3 amd64 [upgradable from: 3.12.3-1ubuntu0.2]
python3.12/noble-updates,noble-security 3.12.3-1ubuntu0.3 amd64 [upgradable from: 3.12.3-1ubuntu0.2]
shotwell-common/noble-updates,noble-updates 0.32.6-1ubuntu2 all [upgradable from: 0.32.6-1ubuntu1]
shotwell/noble-updates 0.32.6-1ubuntu2 amd64 [upgradable from: 0.32.6-1ubuntu1]
ubuntu-release-upgrader-core/noble-updates,noble-updates 1:24.04.23 all [upgradable from: 1:24.04.19]
ubuntu-release-upgrader-gtk/noble-updates,noble-updates 1:24.04.23 all [upgradable from: 1:24.04.19]
vim-common/noble-updates,noble-updates 2:9.1.0016-1ubuntu7.4 all [upgradable from: 2:9.1.0016-1ubuntu7.3]
vim-tiny/noble-updates 2:9.1.0016-1ubuntu7.4 amd64 [upgradable from: 2:9.1.0016-1ubuntu7.3]
xxd/noble-updates 2:9.1.0016-1ubuntu7.4 amd64 [upgradable from: 2:9.1.0016-1ubuntu7.3]
richard@Richard-DT-2024:~$ 


```

---

### Post by 1fallen on 2024-11-19
It did not remove it from the souces list, but please now run:
```
sudo apt upgrade
```
Post any errors it throws.
Your Code tags seem to be a challenge This is a bracket "[" this is not "{"  CODE goes with "[]" and Not " [}" your first box is "[CODE}" and should be "[CODE]" ;)

---

### Post by snoylr on 2024-11-19
This is what I got:

```


richard@Richard-DT-2024:~$ apt update
Reading package lists... Done
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock directory /var/lib/apt/lists/
W: Problem unlinking the file /var/cache/apt/pkgcache.bin - RemoveCaches (13: Permission denied)
W: Problem unlinking the file /var/cache/apt/srcpkgcache.bin - RemoveCaches (13: Permission denied)
richard@Richard-DT-2024:~$ sudo apt update
Hit:1 https://dl.google.com/linux/chrome/deb stable InRelease
Hit:2 https://shop.softmaker.com/repo/apt stable InRelease                                                   
Hit:3 http://us.archive.ubuntu.com/ubuntu noble InRelease                                                    
Hit:4 http://us.archive.ubuntu.com/ubuntu noble-updates InRelease                                            
Hit:5 http://security.ubuntu.com/ubuntu noble-security InRelease
Hit:6 http://us.archive.ubuntu.com/ubuntu noble-backports InRelease
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
69 packages can be upgraded. Run 'apt list --upgradable' to see them.
richard@Richard-DT-2024:~$ 


```

---

### Post by 1fallen on 2024-11-19
Good Job on the code tags :KS
This is what i want:
```
sudo apt upgrade
```

---

### Post by snoylr on 2024-11-19
At least some of my problems have been solved.  I have been able to install two free office applications from softmaker.

Here is the code I last got from my terminal:

```


richard@Richard-DT-2024:~$ apt update
Reading package lists... Done
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock directory /var/lib/apt/lists/
W: Problem unlinking the file /var/cache/apt/pkgcache.bin - RemoveCaches (13: Permission denied)
W: Problem unlinking the file /var/cache/apt/srcpkgcache.bin - RemoveCaches (13: Permission denied)
richard@Richard-DT-2024:~$ sudo apt update
Hit:1 https://dl.google.com/linux/chrome/deb stable InRelease
Hit:2 https://shop.softmaker.com/repo/apt stable InRelease                                                   
Hit:3 http://us.archive.ubuntu.com/ubuntu noble InRelease                                                    
Hit:4 http://us.archive.ubuntu.com/ubuntu noble-updates InRelease                                            
Hit:5 http://security.ubuntu.com/ubuntu noble-security InRelease
Hit:6 http://us.archive.ubuntu.com/ubuntu noble-backports InRelease
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
69 packages can be upgraded. Run 'apt list --upgradable' to see them.
richard@Richard-DT-2024:~$ 


```

So thank you very much.

---

### Post by 1fallen on 2024-11-19
Happy to help!
But your still not fully upgraded>>>"69 packages can be upgraded."
Finish if you have not done yet.
```
sudo apt upgrade
```

---

