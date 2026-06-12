---
title: "Deleting files and permission problems"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by Dalston on 2008-05-14
Hello I have a folder in my wastebasket that wont delete,  can someone help me out please?  I click on permissions and it says the owner can create and delete files, but group and others only lets me access them.  If I try and change them it says "Sorry, couldn't change the permissions of "folder": Operation not supported by backend.  Im using 8.04 updated from 7.10 updated from 7.04.  Thanks

---

### Post by shifty_powers on 2008-05-14
> **Dalston said:**
> Hello I have a folder in my wastebasket that wont delete,  can someone help me out please?  I click on permissions and it says the owner can create and delete files, but group and others only lets me access them.  If I try and change them it says "Sorry, couldn't change the permissions of "folder": Operation not supported by backend.  Im using 8.04 updated from 7.10 updated from 7.04.  Thanks
```
gksudo nautilus
```

just go to your home folder and find the trash folder ;)

(if that doesn't work there is something else you can do, but i'd try that first ;))

---

### Post by Tart on 2008-05-14
I had the same problem yestrday
You can check [http://ubuntuforums.org/showthread.php?t=793496](http://ubuntuforums.org/showthread.php?t=793496) for solution.
You really need to know where trash hides with nautilus.

---

### Post by Dalston on 2008-05-14
I tried to do that but the folder wasnt in the trash folder.   But it is there when I click on the wastebasket on my desktop.

---

### Post by Dalston on 2008-05-14
Ok it worked , I just had to find the trash folder in the .local folder.
Thanks to both of you for your help.

> **shifty_powers said:**
> ```
gksudo nautilus
```

just go to your home folder and find the trash folder ;)

(if that doesn't work there is something else you can do, but i'd try that first ;))

> **Tart said:**
> I had the same problem yestrday
You can check [http://ubuntuforums.org/showthread.php?t=793496](http://ubuntuforums.org/showthread.php?t=793496) for solution.
You really need to know where trash hides with nautilus.

---

### Post by kc8hr on 2008-05-15
> **shifty_powers said:**
> ```
gksudo nautilus
```

just go to your home folder and find the trash folder ;)

(if that doesn't work there is something else you can do, but i'd try that first ;))

Why should I have to gksudo or sudo to delete files in my own home directory? That's nuts!

I have been using Linux for 10 years, and I have never had to sudo to delete my own files, nor modify my own config files before. 

When I tried to activate a plugin in gkrellm, I get another permission denied error.

Is there a way to fix this problem?

I had a perfectly-functioning Gutsy install before I went wacko and decided to upgrade!

---

### Post by shifty_powers on 2008-05-16
heh, well, theres the rub.

the upgrade feature is a good idea. the ability to upgrade from one version to another could be really good, and i'm sure in time it will work well.

Tbh though, if you want to change version, you're better off to backup your data and do a completely fresh install.

Or have a /home partition of course ;)

---

### Post by hyper_ch on 2008-05-16
what permissions do the files have?

shifty_powers: There are also rolling distros... that means that gradually applications will be upgraded... so you have no versions at all anymore...

---

### Post by shifty_powers on 2008-05-16
well yes i know, but i was talking about ubuntu.

and upgrading CAN work in ubuntu, but it also seems to go wrong for enough people for me to prefer to do a clean install.

i wasn't suggesting that the op should reinstall just because of a permission problem, don't get me wrong, just making a point ;)

---

### Post by hyper_ch on 2008-05-16
I prefer a clean install as it's always a good time for me to get rid of unused stuff... I've written myself a small install script that will download and install and copy configuration back of my usual applications and stuff...

---

### Post by shifty_powers on 2008-05-16
sounds very useful. care to share with us ;)

(really don't have time to ge to to grips with that side of linux right now. Maybe when i've finished my mental health nursing degree ;))

---

### Post by hyper_ch on 2008-05-16
it's a simple shell script... something like:

```

#!/bin/bash

################ RESTORE SOURCES.LIST ###############

cp -f /backup/backup_files/sources.list /etc/apt/sources.list
cp -f /backup/backup_files/secring.gpg /etc/apt/secring.gpg
cp -f /backup/backup_files/trustdb.gpg /etc/apt/trustdb.gpg
cp -f /backup/backup_files/trusted.gpg /etc/apt/trusted.gpg

#####################################################

# Update & uprade
sudo apt-get -y update
sudo apt-get -y upgrade
sudo apt-get -y dist-upgrade

# Add packages with required user interaction
sudo apt-get -y install skype sun-java6-jre sun-java5-jre postfix

# Remove unwanted packages
apt-get -y remove mozilla-thunderbird

#KDE Appz
aptitude -y install kopete konversation konqueror k3b amarok krfb kate kontact kdepim-kio-plugins kgpg akregator gdb

# Chat
aptitude -y install amsn irssi

# OpenSSH / Browsers Tools
aptitude -y install openssh-server kazehakase opera flashplugin-nonfree vlc mc unrar gparted openoffice.org openoffice.org-gtk imagemagick numlockx msttcorefonts whois phpmyadmin mysql-server mysql-client libmysqlclient15-dev adesklets d4x googleearth htop traceroute libjack0.100.0-dev

# Codecs
aptitude -y install xubuntu-restricted-extras libdvdcss2 gstreamer0.10-ffmpeg gstreamer0.10-pitfdll gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui w32codecs mplayer

# Timeserver
aptitude -y install ntp ntpdate

#######################
#######################

# Restore other files

cp -f /backup/backup_files/sysinfo /usr/share/apps/konversation/scripts/sysinfo
cp -f /backup/backup_files/screenshot /usr/bin/screenshot

# Restore files/directories contained in the restore.txt file
for DIR in $(cat restore.txt);

do

        echo "Restoring $DIR"
        cp -Rfp /backup/current/$DIR $DIR
        echo "$DIR done";

done

```

---

### Post by shifty_powers on 2008-05-16
cheers, will have to look through that when i get a chance ;)

---

### Post by AmpersUK on 2010-02-05
> **Dalston said:**
> Hello I have a folder in my wastebasket that wont delete,  can someone help me out please?  I click on permissions and it says the owner can create and delete files, but group and others only lets me access them.  If I try and change them it says "Sorry, couldn't change the permissions of "folder": Operation not supported by backend.  Im using 8.04 updated from 7.10 updated from 7.04.  Thanks

Yes this can be a pain. I have a network backup box (1Terabyte) with two Windows machines accessing it perfectly. I have two Ubuntu machines that can see it under Samba, but when I try to copy files over, I get "Operation not supported by backend"

I tried to ensure I have permission by using gksu nautilus, but when I click on network, I am told that under gksu, Nautilus cannot access Network.

Ubuntu 9.10 is still a fledgling operating system but I am sure they will make the mainstream, but they are going to have to do a lot better.

Ampers

---

