---
title: "Can't install HPLIP -- missing dependencies"
date: 2012-07-09
forum: New to Ubuntu
---

### Post by Luke3535 on 2012-07-09
Hi,

I'm using 10.04. I've tried to install HPLIP both using the [automatic install]("http://hplipopensource.com/hplip-web/downloads.html") and the [manual install]("http://hplipopensource.com/hplip-web/install/manual/distros/ubuntu.html").

The automatic install runs for a while and then says:
[INDENT]There are 5 missing REQUIRED dependencies[/INDENT]
(cups-devel, libusb, libtool, cups-image, and libjpeg)

and,

[INDENT]There are 9 missing OPTIONAL dependencies.[/INDENT]

The DEPENDENCY AND CONFLICT RESOLUTION fails with:
[INDENT]error: Package install command failed with error code 100[/INDENT]

With the manual install I get stuck at step 5, which returns:
[INDENT]make: *** No targets specified and no makefile found.  Stop.[/INDENT]

Can you help?

Thanks,


Luke

---

### Post by afixane on 2012-07-09
Open terminal, then write this
```
sudo nano /etc/apt/sources.list
```
Then paste the result here. Maybe I can help you

---

### Post by Luke3535 on 2012-07-09
> **afixane said:**
> Open terminal, then write this
```
sudo nano /etc/apt/sources.list
```
Then paste the result here. Maybe I can help you

Thanks! Here it is:

# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multive$
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe mul$

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.

---

### Post by afixane on 2012-07-09
uncoment, by removing the "#" on nano, so you'll get this line
```
deb http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multive$
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe mul$
```

And if you see this line on nano ( you must scroll down using your keyboard arrow )
```
#deb http://extras.ubuntu.com/ubuntu lucid main
#deb-src http://extras.ubuntu.com/ubuntu lucid main

```
uncomment them into this
```
deb http://extras.ubuntu.com/ubuntu lucid main
deb-src http://extras.ubuntu.com/ubuntu lucid main

```
then, exit nano (ctr+O, then ctrl+x), and type
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by mapes12 on 2012-07-10
If you install HPLIP from the Repos you will be getting an out of date driver. Go to the **HPLIP** website and follow the instructions to download and install the latest driver. The driver will more than likely download to your **Download** folder. Drag it to your Desktop then the installation instruction will work exactly as described on the site.

I did this the other w/e on 2 machines and both of them are now printing/scanning perfectly.

---

### Post by Luke3535 on 2012-07-10
> **mapes12 said:**
> If you install HPLIP from the Repos you will be getting an out of date driver. Go to the **HPLIP** website and follow the instructions to download and install the latest driver. The driver will more than likely download to your **Download** folder. Drag it to your Desktop then the installation instruction will work exactly as described on the site.

I did this the other w/e on 2 machines and both of them are now printing/scanning perfectly.

That's what I tried, giving the unsuccessful results documented in the original post. Thanks, though.

---

### Post by Luke3535 on 2012-07-10
Thanks very much for your reply. I didn't make it very far, though. Both of the first commands below returned "command not found", as quoted below.

[FONT="Fixedsys"]luke@ElijahOne:~$ deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multive$
No command 'deb' found, did you mean:
 Command 'debc' from package 'devscripts' (main)
 Command 'derb' from package 'libicu-dev' (main)
 Command 'dab' from package 'bsdgames' (universe)
 Command 'debi' from package 'devscripts' (main)
deb: command not found
luke@ElijahOne:~$ deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe mul$
deb-src: command not found
[/FONT]

I did confirm that the next two lines are not in the nano output.

Thanks,


Luke


> **afixane said:**
> uncoment, by removing the "#" on nano, so you'll get this line
```
deb http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multive$
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe mul$
```

And if you see this line on nano ( you must scroll down using your keyboard arrow )
```
#deb http://extras.ubuntu.com/ubuntu lucid main
#deb-src http://extras.ubuntu.com/ubuntu lucid main

```
uncomment them into this
```
deb http://extras.ubuntu.com/ubuntu lucid main
deb-src http://extras.ubuntu.com/ubuntu lucid main

```
then, exit nano (ctr+O, then ctrl+x), and type
```
sudo apt-get update
sudo apt-get upgrade
```

---

