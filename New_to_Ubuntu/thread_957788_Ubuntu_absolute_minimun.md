---
title: "Ubuntu absolute minimun"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by Konstabel on 2008-10-24
If I want to install Ubuntu and really start from scratch to add packages as needed, what is the absolute minimum I have to install?

---

### Post by Coreigh on 2008-10-24
The *easiest* is to start with Ubuntu Server. However that is probably not absulute minimum. I am currently running a test install of 8.04 server to which I added a GUI and a couple things it is using 564MB of hard disk. Below is what I did.

> Ubuntu Server 8.04 - log book
Starting point is a minimal installation of Ubuntu Server 8.04 LTS. NO options were selected during the installation, only the bare minimum was installed. The hardware for this system is an older HP Vectra VL400SF - 900mhz PIII, 256MB RAM, 10GB IDE disk, CD-ROM and floppy. To get Ubuntu newer than 6.10 to install or run in liveCD mode the option "NOAPIC" had to be added to the boot script.



July 31, 2008
Edit /etc/apt/sources.list, deselect the CDROM sources and select the universe/multi-verse sources.
apt-get update
apt-get upgrade
reboot
install a minimal xwindows: apt-get install icewm xdm numlockx xterm xserver-xorg-core xfonts-base
startx should start the GUI, may need to apt-get install --reinstall icewm
light browser with apt-get install dillo

August 1, 2008
A light GUI text editor, about 4MB of dependancies: apt-get install leafpad
Install components to allow joining Windows domain: apt-get install samba samba-common smbfs smbclient smbldap-tools winbind krb5-config krb5-user openbsd-inetd
Kerberos realm hostname for MYDOMAIN.COM is "UBserver"
Customize; /etc/samba/smb.conf, /etc/krb5.conf, and /etc/nsswitch.conf. Copy the original files and append .DEFAULT, to have back-ups
/etc/samba/smb.conf
/etc/krb5.conf
/etc/nsswitch.conf
Add entries to HOSTS file for UBserver, nas and web.
Restart the services: /etc/init.d/samba restart &
/etc/init.d/winbind restart
Join domain: net ads join -U administrator If this doesn’t work, check the logs in Linux (/var/log/samba/*) and Windows.
Add mount points to MNT folder F, G, R (mkdir F ... etc.)


---

### Post by jamesrfla on 2008-10-24
You can get Ubuntu Minimal here. [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by hyper_ch on 2008-10-24
or get the alternate cd and use F6 (I think) to select what install you want.

---

### Post by _sAm_ on 2008-10-24
> **Konstabel said:**
> If I want to install Ubuntu and really start from scratch to add packages as needed, what is the absolute minimum I have to install?

Follow one of these two guides and pick what you want to install;
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)
[http://wiki.dennyhalim.com/ubuntu-minimal-desktop](http://wiki.dennyhalim.com/ubuntu-minimal-desktop)

---

### Post by em4r1z on 2008-10-24
Why are you trying to build a minimal system? Depending on your answer we'll be able to provide better advices.
If you're building a minimal system because you want control and not due to scarce resources, I'd suggest:

1. Use the minimal (net) installation CD.
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

2. Edit your sources list to fit your needs and update.
```
sudo nano /etc/apt/sources.list
sudo apt-get update
```

3. Install a windowing sytem, a desktop environment and a login manager.
```
sudo apt-get install xorg gnome-core gdm
```

4. Install a web browser and a network manager.
```
sudo apt-get install firefox network-manager-gnome
```

5. Restart and keep on building your system.
Use the distribution's package list and Synaptic to know more about the applications and their dependencies.
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

