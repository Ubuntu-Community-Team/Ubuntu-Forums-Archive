---
title: "New install 14.04 server version"
date: 2015-04-01
forum: New to Ubuntu
---

### Post by aaron27 on 2015-04-01
I am having some issues with a new install of Ubuntu Server 14.04.2 LTS.

I originally had issues getting sudo apt-get update to work, however having searched around this is now fixed.
sudo apt-get upgrade informs me that after completion there are 3 not upgraded, 0 upgraded, 0 newly installed and 0 to remove.

The real issue though is that i cannot install any packages - gnome bought this to my attention as it wont let me install it, but it is not unique to this package i have tried a few others including gedit. Even with the sudo command they wont install.

I get a message stating:
Some packages could not be installed. This may mean that you have requested an impossible situation or that you are using the unstable distribution that some required packages have not yet been created or been moved out of incoming.

The following packages have unmet dependencies:
gnome: depends gnome-core (-1:3.8+4ubuntu3) but it is not going to be installed (there is a whole list with the same status)

E: unable to correct problems, you have held broken packages.

Can anyone advise?

KR aaron

---

### Post by sandyd on 2015-04-01
Please post the output of
```

cat /etc/apt/sources.list
tail -f /etc/apt/sources.list.d/*
sudo apt-get install gedit

```

---

### Post by aaron27 on 2015-04-01
Thank you for your reply:

cat /etc/apt/sources.list outputs:
```
deb cdrom:ubuntu:[ubuntu-server 14.04.2 LTS _trusty tahr_ -release amd64 (20150218.1)]/ trusty main restricted
deb cdrom:ubuntu:[ubuntu-server 14.04.2 LTS _trusty tahr_ -release amd64 (20150218.1)]/ trusty main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security multiverse

This software is not part of ubuntu, but is offered by canonical and the respective vendors as a service to ubuntu server.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner

This software is not part of ubuntu, but is offered by third-party developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty main universe restricted multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty main universe restricted multiverse
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
```
tail -f /etc/apt/sources.list.d outputs:
```
tail: error reading '/etc/apt/sources.list.d': is a directory
tail: /etc/apt/sources.list.d: cannot follow end of this type of file; giving up on this name
```

sudo apt-get install gedit outputs:
```
reading package lists... done
building dependency tree
reading state information... done
some packages could not be installed. this may mean that you have requested an impossible situation or if you are using unstable distribution that some required packages have not yet been created or been moved out of incoming.
the following information may help to resolve the situation:

the following packages have unmet dependencies:
gedit: depends: girl.2-peas-1.0 but it is not going to be installed
        recommends: girl.2-gtksource-3.0 but it is not going to be installed
E: unable to correct problems, you have held broken packages.
```

I feel i should add that this was an ISO image downloaded straight from the official ubuntu website and installed on a vmware virtual player. from the results of the first command it looks like the update server isnt actually ubuntu? or am i barking up the wrong tree?

---

### Post by sandyd on 2015-04-02
Fixed the second command - made a typo

Can you run it again please?

Thanks :)

Btw, before we continue, for some reason, you still have the CD in as a repo, run
```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.bak
sudo nano /etc/apt/sources.list
```

Paste:
```

#------------------------------------------------------------------------------#
#                            OFFICIAL UBUNTU REPOS                             #
#------------------------------------------------------------------------------#


###### Ubuntu Main Repos
deb http://us.archive.ubuntu.com/ubuntu/ trusty main restricted universe multiverse 
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty main restricted universe multiverse 

###### Ubuntu Update Repos
deb http://us.archive.ubuntu.com/ubuntu/ trusty-security main restricted universe multiverse 
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted universe multiverse 
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-security main restricted universe multiverse 
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted universe multiverse 
```

Press control +x, then 'y' at the next prompt, and then Enter key.

Run following command and post if there are any errors:
```

sudo apt-get update
```

---

### Post by aaron27 on 2015-04-02
Thank you for your help.
```

tail -f /etc/apt/sources.list.d/*

tail: cannot open '/etc/apt/sources.list.d/*' for reading: No such file or directory

```

I then copied the code you posted and ran the sudo apt-get update which downloaded alot of updates, so ran an sudo apt-get update aswell.

Then just out of interest ran the sudo apt-get install gnome - which now appears to be working (it is currently downloading/installing as i type this.

KR
Aaron

---

### Post by mastablasta on 2015-04-02
it's either a bug in wmware or you forgot to eject the virtual media (iso file).

btw why do you need gnome on server?

---

### Post by aaron27 on 2015-04-02
I'm using Gnome as I am installing Owncloud and prefer to have a GUI rather than use command line (plus if anything needs command line i can use terminal). 
I am new to linux after being a die hard windows user, however owncloud have dropped windows support so it was stop using it or learn linux

---

### Post by mastablasta on 2015-04-02
for installing owncloud all you need to do is copy two commands into command line if I am not mistaking. it can be done from windows using putty terminal.

if you need GUI to administer the server there are WebGUI out there that are light on resuorces. I find Ajenti quite easy to use and very light on resources. these webguis make it easy to administer the server while you are away from it. there are plenty of them out there (such as webmin and similar). some even have distributions based around them. like Open Media Vault, Nethserver...

Gnome is one of the heavier desktops. if you must have some sort of desktop then I suggest you use something lighter such as Lxde or maybe even just a windows manager will be more than enough (IceWM, jwm).

if server is doing something else besides owncloud then have a look at projects such as Zentyal (aims to replicate Microsoft small business server).

---

### Post by mastablasta on 2015-04-02
for installing owncloud all you need to do is copy two commands into command line if I am not mistaking. it can be done from windows using putty terminal.

if you need GUI to administer the server there are WebGUI out there that are light on resuorces. I find Ajenti quite easy to use and very light on resources. these webguis make it easy to administer the server while you are away from it. there are plenty of them out there (such as webmin and similar). some even have distributions based around them. like Open Media Vault, Nethserver...

Gnome is one of the heavier desktops. if you must have some sort of desktop then I suggest you use something lighter such as Lxde or maybe even just a windows manager will be more than enough (IceWM, jwm).

if server is doing something else besides owncloud then have a look at projects such as Zentyal (aims to replicate Microsoft small business server).

---

