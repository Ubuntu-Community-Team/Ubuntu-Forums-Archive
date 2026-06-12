---
title: "Synaptic error"
date: 2012-03-14
forum: New to Ubuntu
---

### Post by borger live on 2012-03-14
I made a big goof and tried to add something to the source list
deb [http://*ftp.de.debian.org/debian*]("http://%3Ci%3Eftp.de.debian.org/debian%3C/i%3E") sid main
and did it really wrong, now I get this message error and synaptic shuts down.
> E: Dynamic MMap ran out of room. Please increase the size of APT::Cache-Limit. Current value: 25165824. (man 5 apt.conf)
E: Error occurred while processing pavucontrol (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/ftp.de.debian.org_debian_dists_sid_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

W: Unable to munmapHow can I get that line out of the sources list in Synaptic?
Thank you

---

### Post by dmouck on 2012-03-14
Sudo edit /etc/apt/sources.list with your editor of choice (gedit, vi, etc.) and remove it from there. Then run sudo apt-get update and you should be good.

---

### Post by jerrrys on 2012-03-14
open a terminal and enter

sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

---

### Post by matt_symes on 2012-03-14
Hi

Normally i would say type

```
sudo rm -r /var/lib/apt/lists/*
```

to clean your lists cache, and then type

```
sudo apt-get update
```

But this is a debian package

> ftp.de.debian.org_debian_dists_sid_main_binary-i386_Packages

Are you sure you want this in your sources ? Debian packages can cause problems.

As the previous poster said, maybe remove it from your sources file ?

To remove it

```
sudo sed -i '/sid/d' /etc/apt/sources.list
```

Kind regards

---

### Post by borger live on 2012-03-14
Thanks!  You guys are awesome!):P

---

### Post by jerrrys on 2012-03-14
@matt

our commands are slightly different.

sudo rm -r /var/lib/apt/lists/*
sudo rm /var/lib/apt/lists/* -vf

wonder which one has the advantage

---

### Post by jerrrys on 2012-03-14
and welcome to the forum [borger live]("http://ubuntuforums.org/member.php?u=1579874") :D

---

### Post by borger live on 2012-03-14
Is removed from the list.  Trying to install the ImageShack uploader
>  If you are running Debian, it is strongly suggested to use a package manager like [aptitude]("http://packages.debian.org/sid/aptitude") or [synaptic]("http://packages.debian.org/sid/synaptic") to download and install packages, instead of doing so manually via this website.
 You should be able to use any of the listed mirrors by adding a line to your /etc/apt/sources.list like this:
  deb [http://*ftp.de.debian.org/debian*]("http://%3Ci%3Eftp.de.debian.org/debian%3C/i%3E") sid main   Replacing *ftp.de.debian.org/debian* with the mirror in question.   

so I tried to insert it into Synaptic.
There is a .deb file  to downloadbut maybe I'll just leave it alone?
Thanks again!

PS  it even says [URL="http://packages.debian.org/sid/imageshack-uploader"]Download latest version of Imageshack Uploader
[/URL]for Ubuntu/Debian Linux

---

### Post by matt_symes on 2012-03-14
Hi jerrrys

> **jerrrys said:**
> @matt

our commands are slightly different.

sudo rm -r /var/lib/apt/lists/*
sudo rm /var/lib/apt/lists/* -vf

wonder which one has the advantage

Neither really. 

Mine will also delete the partial directory as well and any files contained within. That directory should be recreated, but sometimes it's not and it has to be recreated manually; however sometimes the problem is in the partial directory. 

Yours gives more user feedback as it will tell you what it deletes (the verbose switch). It will just delete everything in the lists directory and not in the partial directory.

The -f switch may not be required though, as it is run with sudo.

They should both work and your advice is good :)

Kind regards

---

### Post by jerrrys on 2012-03-14
thanks matt

---

### Post by matt_symes on 2012-03-14
Hi

> **borger live said:**
> Is removed from the list.  Trying to install the ImageShack uploader
so I tried to insert it into Synaptic.
There is a .deb file  to downloadbut maybe I'll just leave it alone?
Thanks again!

PS  it even says [URL="http://packages.debian.org/sid/imageshack-uploader"]Download latest version of Imageshack Uploader
[/URL]for Ubuntu/Debian Linux

It's in the Ubuntu repositories.

```
matthew@matthew-Aspire-7540:~/my_documents/router/dlink_dir_615$ apt-cache search imageshack
imageshack-uploader - a image and video upload utility for the ImageShack hosting service
imageshack-uploader-common - a image and video upload utility - common files
matthew@matthew-Aspire-7540:~/my_documents/router/dlink_dir_615$
```

It's in the universe repository so you will have to enable that.

```
matthew@matthew-Aspire-7540:~/my_documents/router/dlink_dir_615$ apt-cache show imageshack-uploader | grep Section
Section: universe/utils
matthew@matthew-Aspire-7540:~/my_documents/router/dlink_dir_615$
```

Kind regards

---

### Post by borger live on 2012-03-14
Hi Matt,  I don't have imageshack-uploader anywhere I can find.
I have
> plasma-widget-droptoimagessl
photo-uploadI'm using 10.04 and have all repositories enables.
```
medion@Medion:~$ apt-cache search imageshack
photo-uploader - Command line photo uploader
plasma-widget-droptoimageshack - plasma widget which can upload images to Imageshack.us
medion@Medion:~$ imageshack-uploader
```

---

### Post by matt_symes on 2012-03-14
Hi

> **borger live said:**
> Hi Matt,  I don't have imageshack-uploader anywhere I can find.
I have
I'm using 10.04 and have all repositories enables.
```
medion@Medion:~$ apt-cache search imageshack
photo-uploader - Command line photo uploader
plasma-widget-droptoimageshack - plasma widget which can upload images to Imageshack.us
medion@Medion:~$ imageshack-uploader
```

You're right. It's not in the repos for 10.04

Here is a PPA for it.

[https://launchpad.net/~lfaraone/+archive/ppa](https://launchpad.net/~lfaraone/+archive/ppa)

Linked from here (at the bottom)

[https://launchpad.net/ubuntu/+source/imageshack-uploader](https://launchpad.net/ubuntu/+source/imageshack-uploader)

Kind regards

---

### Post by borger live on 2012-03-14
Thanks matt mate!  In good shape now! =D>

---

