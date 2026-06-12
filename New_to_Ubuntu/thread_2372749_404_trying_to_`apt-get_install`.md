---
title: "404 trying to `apt-get install`"
date: 2017-09-28
forum: New to Ubuntu
---

### Post by UTAN_dev on 2017-09-28
On Ubuntu 16.04.1 LTS I'm trying to install a newer version of gitg (3.26) than provided by apt (3.17). I downloaded the archive and followed the instructions, and need to install a bunch of dependencies.

Trying to install libgtk-3-dev, I got several 404s:


```
$ sudo apt-get install build-essential libgtk-3-dev --fix-missing
Get:8 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) xenial-security/main amd64 libexpat1-dev amd64 2.1.0-7ubuntu0.16.04.3 [115 kB]
Get:9 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) xenial-security/main amd64 libfreetype6-dev amd64 2.6.1-0.1ubuntu2.3 [956 kB]
Err:10 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 libdrm-dev amd64 2.4.67-1ubuntu0.16.04.2 404  Not Found [IP: 91.189.88.161 80]
Err:11 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 libegl1-mesa-dev amd64 11.2.0-1ubuntu2.2 404  Not Found [IP: 91.189.88.161 80]
Get:12 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) xenial-security/main amd64 libgdk-pixbuf2.0-dev amd64 2.32.2-1ubuntu1.3 [44.3 kB]
Get:13 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) xenial-security/main amd64 nettle-dev amd64 3.2-1ubuntu0.16.04.1 [939 kB]
Err:14 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 libgtk-3-dev amd64 3.18.9-1ubuntu3.1 404  Not Found [IP: 91.189.88.161 80]
Fetched 2,848 kB in 1s (2,358 kB/s)
Unable to correct missing packages.
E: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/libd/libdrm/libdrm-dev_2.4.67-1ubuntu0.16.04.2_amd64.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/libd/libdrm/libdrm-dev_2.4.67-1ubuntu0.16.04.2_amd64.deb) 404  Not Found [IP: 91.189.88.161 80]
E: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/m/mesa/libegl1-mesa-dev_11.2.0-1ubuntu2.2_amd64.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/m/mesa/libegl1-mesa-dev_11.2.0-1ubuntu2.2_amd64.deb) 404  Not Found [IP: 91.189.88.161 80]
E: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/g/gtk+3.0/libgtk-3-dev_3.18.9-1ubuntu3.1_amd64.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/g/gtk+3.0/libgtk-3-dev_3.18.9-1ubuntu3.1_amd64.deb) 404  Not Found [IP: 91.189.88.161 80]
E: Aborting install
```

(Full output at [https://pastebin.com/s81mRns3](https://pastebin.com/s81mRns3))

Googling libgtk-3-dev_3.18.9-1ubuntu3.1_amd64.deb, I didn't get any hits on that specific version, but did get the [download page]("https://packages.ubuntu.com/xenial-updates/amd64/libgtk-3-bin/download") for libgtk-3-bin_3.18.9-1ubuntu3.3_amd64.deb, a newer version (3.3 vs. 3.1), listing mirrors I could add to my apt sources list.

[LIST=1]
[*]Why would ca.archive.ubuntu.com not have the file I need? (See? This is a newbie question. ;))
[*]Since gitg requires libgtk 3.3, will the install fail after I add one of the listed mirrors (e.g. mirrors.kernel.org/ubuntu)?
[/LIST]
Thanks!

---

### Post by &amp;KyT$0P# on 2017-09-28
Does running [FONT=Courier New]sudo apt-get update[/FONT] fix it?

---

### Post by UTAN_dev on 2017-09-28
I did both `sudo apt-get update` and `sudo apt-get install build-essential libgtk-3-dev --fix-missing`, to no avail.

---

### Post by slickymaster on 2017-09-28
@UTAN_dev:

Please [use code tags]("https://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") when posting output. Output posted as plain text loses its formatting and parts of it sometimes turn into smileys making it difficult to read and understand.

---

### Post by mc4man on 2017-09-28
Open up Software & Updates & pick a new server from the Download from dropdown
Assuming canada you could try another canadian mirror or use either a US server or just use the Main server.
The main us server which is very reliable  is down in the list, see screen

---

### Post by UTAN_dev on 2017-09-28
[LIST]
[*]Software & Updates > Download from: = "Other…"
[*]Choose a download server: select us.archive.ubuntu.com, Choose Server
[*]Back at Software & Updates: Download from: "Other… "
[*]I try `sudo apt-get install build-essential libgtk-3-dev --fix-missing` again. Same 404s. I notice apt is still trying to get those files from ca.archive.ubuntu.com.
[/LIST]

It seems us.archive.ubuntu.com didn't stick. How can I verify which source is used? BTW, here's my /etc/apt/sources.list :
```
#------------------------------------------------------------------------------#
#                            OFFICIAL UBUNTU REPOS                             #
#------------------------------------------------------------------------------#




###### Ubuntu Main Repos
deb http://ca.archive.ubuntu.com/ubuntu/ xenial main restricted universe multiverse 
deb-src http://ca.archive.ubuntu.com/ubuntu/ xenial main restricted universe multiverse 


###### Ubuntu Update Repos
deb http://ca.archive.ubuntu.com/ubuntu/ xenial-security main restricted universe multiverse 
deb http://ca.archive.ubuntu.com/ubuntu/ xenial-updates main restricted universe multiverse 
deb-src http://ca.archive.ubuntu.com/ubuntu/ xenial-security main restricted universe multiverse 
deb-src http://ca.archive.ubuntu.com/ubuntu/ xenial-updates main restricted universe multiverse


```

---

