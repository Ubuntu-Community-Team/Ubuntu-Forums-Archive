---
title: "apt-"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by viswanathan on 2008-05-14
guys well this may sound crazy but where are the packages installed in hard disk when apt-get install ___________ command is used i wanna know d location in d hard disk where these files r present :KS

---

### Post by bjm1904 on 2008-05-14
I've found from experience that it varies from app to app. Some install in /opt, others in /sbin, or in /etc, others in /usr/local - if you take a look at simple backup config (downloadable through synaptic) it will show you the folders it excludes (and lists the folders generally used for programs)

---

### Post by Oldsoldier2003 on 2008-05-14
> **viswanathan said:**
> guys well this may sound crazy but where are the packages installed in hard disk when apt-get install ___________ command is used i wanna know d location in d hard disk where these files r present :KS

which <packagname> will give you the path to where the package is installed. for example:

```
chuck@chuck-desktop:~$ which gparted
/usr/local/sbin/gparted
```

the sharp eyed ones can tell thats not where gparted is usually installed  :)

---

### Post by oedha on 2008-05-14
the downloaded files (*deb) ==> /var/cache/apt/archives

---

### Post by dje on 2008-05-14
Or in a terminal you could use:
```
whereis *program_name*
```

hope that helps,
dje

---

### Post by Oldsoldier2003 on 2008-05-14
> **oedha said:**
> the downloaded files (*deb) ==> /var/cache/apt/archives

```
sudo apt-get clean
``` will remove these saved packages, freeing up disk space. Once the packages are installed you wont need them, if you ever do... apt will re download them.

---

### Post by sunstriker on 2008-05-14
A program in linux is not installed with all his files in the same directory (like in windows) but they are spread out across various directories. Most programs will put their main files in /usr/share (ex. Firefox). Desktop managers like gnome and KDE install in /opt. Much programs will put config files in /etc, such as apache2.
Via synaptic you can see the properties of a package and it will list all the files the program installs and their location on your drive.
if you remove a program with apt-get remove, most programs leave their config files (for later use). If you want to remove them to, remove the program with the --purge option. Like ```
sudo apt-get remove apache2 --purge
```

---

### Post by Michael.Godawski on 2008-05-14
If you want to check where all the files of a specific application are, open up synaptic package manager, right-click on an installed application, select properties and go to installed files.
You will see many directories containing the scattered files of the one application.

---

