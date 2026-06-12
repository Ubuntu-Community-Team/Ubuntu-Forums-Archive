---
title: "SFTP via lftp"
date: 2013-04-13
forum: New to Ubuntu
---

### Post by GrouchyGaijin on 2013-04-13
Hi Guys,

I'm trying to ftp into my hosting account using lftp, but am not able to do so using sftp.
I think I've followed the instructions yet still can't connect.  Then it occurred to me that perhaps lftp was not compiled with sftp enabled.
I want to use this in a script to upload some files automatically.

My questions are:

1. Is anyone else using lftp to connect securely? 

2. Based on the version information, is my version compiled with sftp enabled? (Stupid question I know, does TLS = SFTP?).

```
LFTP | Version 4.4.5 | Copyright (c) 1996-2013 Alexander V. Lukyanov



Libraries used: Readline 6.2, Expat 2.0.1, GnuTLS 2.12.14, zlib 1.2.3.4



```

---

### Post by TheFu on 2013-04-14
I've never heard of lftp.  Most of the time, having sftp access to a webhost requires having shell access via ssh. For my hosts, this means faxing a copy of a government ID since shell access on a shared host is extremely powerful. Can you ssh into the machine?  If you can't, I wouldn't expect sftp to work either.  On my hosts, the sftp port is not the default - the hosting provider had to tell me which port to use and I had to install keys - no password-based access is allowed.

ssh, scp and sftp are all connected. They use the same port.

---

### Post by GrouchyGaijin on 2013-04-14
lftp is in the Ubuntu repository and from what I've gathered from Google it is pretty common.

[Quote=Ubuntu Repository]
Lftp is a file retrieving tool that supports FTP, HTTP, FISH, SFTP, HTTPS
and FTPS protocols under both IPv4 and IPv6. Lftp has an amazing set of
features, while preserving its interface as simple and easy as possible.


The main two advantages over other ftp clients are reliability and ability
to perform tasks in background. It will reconnect and reget the file being
transferred if the connection broke. You can start a transfer in background
and continue browsing on the ftp site. It does this all in one process. When
you have started background jobs and feel you are done, you can just exit
lftp and it automatically moves to nohup mode and completes the transfers.
It has also such nice features as reput and mirror. It can also download a
file as soon as possible by using several connections at the same time.


Lftp can also be scriptable, it can be used to mirror sites, it lets you
copy files among remote servers (even between FTP and HTTP). It has an
extensive online help. It supports bookmarks, and connecting to several
ftp/http sites at the same time.


This package also includes lftpget - A simple non-interactive
tool for downloading files.[/Quote]

The main problem was that the version in the repository isn't compiled with libssl so I recompiled the latest version to include ssl support.

The usage is:
```
ftp -u username,password-placeholder -p alt port number sftp://isp.com
```
The password-placeholder can be anything, this just tells lftp to pull your key from the ~/.ssh folder.

---

### Post by Lars Noodén on 2013-04-14
The [sftp client](http://manpages.ubuntu.com/manpages/quantal/en/man1/sftp.1.html) is provided by your basic Ubuntu installation.  Why not use that for SFTP?

---

### Post by GrouchyGaijin on 2013-04-14
Only because I want to run this from a script and upload all of the sub-directories and their files from a particular source directory without uploading the source directory itself and based on what I've read the easiest way to do this is via lftp's reverse mirror feature.

---

### Post by Lars Noodén on 2013-04-14
rsync works very well for copying whole directories with their component subdirectories, too.

---

### Post by GrouchyGaijin on 2013-04-14
Right, but I didn't see how to exclude the main source directory with rysnyc and only copy the subdirectories

---

### Post by Lars Noodén on 2013-04-14
That should be doable with rsync using --exclude or --include.  Those will keep rsync from copying other files or directories.

---

### Post by TheFu on 2013-04-14
> **GrouchyGaijin said:**
> Right, but I didn't see how to exclude the main source directory with rysnyc and only copy the subdirectories

Mirroring directories is exactly what rsync is for.  It can do anything ... almost and is very well designed to handle anything that you or I could ask.  The man page for rsync is extremely complete too.  rsync works over ssh by default and honors .ssh/config settings as well as keys.

If you want to mirror directories, rsync is THE tool of choice.

I've been a Linux/UNIX user for over 20 yrs, never heard of lftp.

---

### Post by GrouchyGaijin on 2013-04-14
You know I'm detecting more than a bit of condescension in your tone.
I'll tell you something "Dad", it really does not matter one bit to me if you have heard of a piece of software or not.
I'm sure rsync is fine, I have lftp set up using my keys and it is working for me - hence thread solved.

---

### Post by Mopar1973Man on 2013-04-14
I've got a network of 4 computer here at home. What I've done is given myself a internal domain name and I can sFTP across my LAN to any machine. I've installed openssh-server on all of them.

```
sudo apt-get install openssh-server
```

Now I can either work through terminal on SSH or just sFTP them with Filezilla

```
sudo apt-get install filezilla
```

Then if you want to go the extra mile to can tweak the SSH.

[https://help.ubuntu.com/community/SSH/OpenSSH/Configuring]("https://help.ubuntu.com/community/SSH/OpenSSH/Configuring")

I tried it just for the sake of saying I did it.  I got me a free domain name from no-ip.com and port forward 22 on my DSL modem and was able at anytime login to the machine I had setup to the outside world.

---

