---
title: "How do I get output from command line"
date: 2008-08-05
forum: New to Ubuntu
---

### Post by winsane on 2008-08-05
I want to post the output I am getting when I try to install packages on my Ubuntu server but all I have is the command line. Is there a way to pipe my output to a file and post it on the forum?

---

### Post by hyper_ch on 2008-08-05
```

COMMAND > ~/Desktop/output.txt

```

---

### Post by decoherence on 2008-08-05
also *COMMAND | tee file* for example
```

apt-get install something | tee ~/Desktop/output.txt
```

which allows you to watch the output and saves it to a file.

---

### Post by winsane on 2008-08-05
First, I try to install util-linux


Reading package lists...
Building dependency tree...
Reading extended state information...
Initializing package states...
Building tag database...
The following packages are BROKEN:
  util-linux 
The following packages have been kept back:
  bash bind9-host bsdutils dnsutils dpkg dselect file initramfs-tools 
  iproute libmagic1 libpam-modules libpam0g libssl0.9.8 linux-image-server 
  linux-server lshw mount openssh-client openssh-server parted pciutils 
  procps python2.4 python2.4-minimal samba samba-common sudo winbind 
1 packages upgraded, 0 newly installed, 0 to remove and 28 not upgraded.
Need to get 0B/440kB of archives. After unpacking 664kB will be used.
The following packages have unmet dependencies:
  util-linux: PreDepends: libc6 (>= 2.4) but 2.3.6-0ubuntu20.5 is installed.
              PreDepends: libncurses5 (>= 5.6+20071006-3) but 5.5-1ubuntu3 is installed.
              PreDepends: libslang2 (>= 2.0.7-1) but 2.0.5-1build2 is installed.
              PreDepends: zlib1g (>= 1:1.2.3.3.dfsg-1) but 1:1.2.3-6ubuntu4 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
console-common
console-data
console-tools
initscripts
sysvinit
ubuntu-minimal
util-linux

Score is -202428

Accept this solution? [Y/n/q/?] The following ESSENTIAL packages will be REMOVED!
  util-linux sysvinit 

WARNING: Performing this action will probably cause your system to break!
         Do NOT continue unless you know EXACTLY what you are doing!
To continue, type the phrase "I am aware that this is a very bad idea":
Abort.

********And then the other (libcupsys2):
Reading package lists...
Building dependency tree...
Reading extended state information...
Initializing package states...
Building tag database...
The following packages have been kept back:
  bash bind9-host bsdutils dnsutils dpkg dselect file initramfs-tools 
  iproute libmagic1 libpam-modules libpam0g libssl0.9.8 linux-image-server 
  linux-server lshw mount openssh-client openssh-server parted pciutils 
  procps python2.4 python2.4-minimal samba samba-common sudo util-linux 
  winbind 
0 packages upgraded, 0 newly installed, 0 to remove and 29 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information...

I actually have weird dependency issues like this all over the place.  What I want to do is get a gnome desktop up and running on my ubuntu server.  What packages do I need to download and how do I resolve these dependencies!!?:confused:

---

### Post by decoherence on 2008-08-06
i want to confirm that your installed system and your sources.list match up. please post the following output

```
lsb_release -a

cat /etc/apt/sources.list
```

the version reported in lsb_release should jive with the version referred to in sources.list (hardy, gutsy, etc)

if they do match up you can try the following without fear of further damaging your system

```
sudo apt-get update
sudo apt-get -f install
```

if they don't match up (for instance if lsb_release reports Gutsy but sources.list refers to hardy) you should first change your sources.list to match what lsb_release reports, then run the above two apt-get commands. if you wish to upgrade after that, first run

```
sudo apt-get upgrade
```

then change your sources.list back so it refers to hardy again and run
```

sudo apt-get dist-upgrade
```

hth

---

### Post by kpkeerthi on 2008-08-06
> **winsane said:**
> I want to post the output I am getting when I try to install packages on my Ubuntu server but all I have is the command line. Is there a way to pipe my output to a file and post it on the forum?

[http://www.devdaily.com/blog/post/linux-unix/use-unix-linux-script-command-record-your-command-line-i-o/](http://www.devdaily.com/blog/post/linux-unix/use-unix-linux-script-command-record-your-command-line-i-o/)

---

### Post by decoherence on 2008-08-06
kpkeerthi, that's handy! :)

---

### Post by kpkeerthi on 2008-08-06
> **decoherence said:**
> kpkeerthi, that's handy! :)

You are welcome. I use that everytime I run package updates so I can go back and do post-mortem should something go wrong.

---

### Post by finer recliner on 2008-08-06
ctrl+shift+c will copy from a terminal window. you can then paste it in another window using the normal ctrl+v (or middle click)

---

### Post by winsane on 2008-08-08
Sources.list and lsb_release -a are both showing Ubuntu 8.04. When I ran apt-get install upgrade, there was a great deal of installing and it appear to end successfully.  

However, typing 'startx' does not launch anything but an error message.:)

---

### Post by winsane on 2008-08-11
What about this....
Can I install a simple GUI of some sort? Maybe a very basic GUI that does not require high resolution or special drivers or anything. Like a "safe mode" kind of thing.  Is there anything like that?

---

### Post by cariboo on 2008-08-11
You could always install webmin. Webmin is a web based server administration suite. Have a look here:

[http://www.webmin.com/](http://www.webmin.com/)

If you look under Webmin Links, there is a link to a demo, you can check it out and see if it fits your needs.

Jim

---

