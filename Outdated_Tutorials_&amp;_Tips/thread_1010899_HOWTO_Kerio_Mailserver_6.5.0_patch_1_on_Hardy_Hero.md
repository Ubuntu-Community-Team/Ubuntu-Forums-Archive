---
title: "HOWTO Kerio Mailserver 6.5.0 patch 1 on Hardy Heron 8.04"
date: 2008-12-14
forum: Outdated Tutorials &amp; Tips
---

### Post by djieno on 2008-12-14
Hi Kerio mailserver fans! After succesfully using [Kerio on Dapper Drake]("http://ubuntuforums.org/showthread.php?t=460955") it's time to update to Hardy Heron 8.04 and 6.5.0 patch 1. It's a bit less generic but simpler since the Kerio mailserver package is already made into a .deb. 

[COLOR="Gray"]I've been trying to install Kerio mailserver on Ubuntu/Debian but somehow I coulnd't find a complete howto. It will start at bootup with a proper bootup script. Kerio Mailserver package isn't freeware but costs a fraction of mikey$oft Exchange. AND it is is build on rugged opensource Linux.

I really can't see why the most popular linux distribution isn't supported. [-o< Running a stripped down FC6 was still using 1.1 gig and 260 mb memory for a working KMS. I have Ubuntu server 6.06.1 running it in 600 mb and only 150 mb memory! I had no stability issues what so ever. Ubuntu Rocks![/COLOR]

This is meant to be a copy / paste howto. Starting from a clean installation of Ubuntu Hardy Heron 8.04 x86.

# Install openssh server for remote login. Now you copy paste the commands within a shell. 
```
sudo apt-get install ssh
```

# Ssh to your ubuntu/Debian to be Kerio mailserver machine from a desktop to be able to copy paste if from a console.
```
ssh your-keriomailserver-ip
```

# Grand console super user rights.
```
sudo -s
```

# install kerio dependencies libstdc++5
```
apt-get install libstdc++5
```

# Download the Kerio mailserver version kerio-kms_6.5.0-5341_i386.deb from my webserver. The kerio-kms_6.5.0-5341_i386.rpm cannot be converted to .deb using Alien. Since Kerio didn't comply with the officia Linux standards and it is unusable! A new .deb and startup script has been created from extracting the official .rpm. 
```
cd /tmp
wget [http://avore.nl/kerio-kms_6.5.0-5341_i386.deb]("http://avore.nl/kerio-kms_6.5.0-5341_i386.deb")

```

# Install the previously created kerio-kms_6.5.0-5341_i386.deb. If you have trouble installing the .deb file with "dpkg -i filename.deb" try "dpkg --unpack filename.deb". It worked fine for me.
```
dpkg -i kerio-kms_6.5.0-5341_i386.deb
```

# When it is finished installing set your preferences. You could also redo it by pressing going to the mailserer direcory (/opt/kerio/mailserver) and start the script by ./cfgwizard

#Set Kerio to start at bootup in rc.d. Do not forget the last dot!
```
update-rc.d keriomailserver start 99 2 3 4 5 . stop 20 0 1 6 .
```

Done! Do a reboot and see Kerio mailserver nicely start at boot.

I've tried to be as clear as I can. If you have any additions please pm me so I can alter this howto to prevent an unclear workflow. I really hate well intended but still bad/incomplete/absolete/unchecked howto's associated with Red Hat look-alikes. People using Ubuntu/Debian try to help out better!

Please do not forget to flare at Kerio for not having support for Ubuntu/Debian when buying the license!

Djieno! :popcorn:

---

