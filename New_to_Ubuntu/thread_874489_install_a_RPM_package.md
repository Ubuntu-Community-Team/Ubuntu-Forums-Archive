---
title: "install a RPM package ?"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by smooth3006 on 2008-07-30
i downloaded a bitdefender antivirus program for linux  but it came as a rpm.run type of file. how do i install this in my ubuntu system? ive read about converting it into a deb package ? i know the file i downloaded has a rpm.run at the end. any help would be appreciated.

---

### Post by Oldsoldier2003 on 2008-07-30
> **smooth3006 said:**
> i downloaded a bitdefender antivirus program for linux  but it came as a rpm.run type of file. how do i install this in my ubuntu system? ive read about converting it into a deb package ? i know the file i downloaded has a rpm.run at the end. any help would be appreciated.

You can use alien to convert and install the rpm package. But before you do that you should see if there is a debian binary (.deb) available or consider compiling it from source. If you do decide to use alien you can get it from the repos:

```
sudo apt-get install alien
```

---

### Post by tinny on 2008-07-30
This is what you want!

They have their own repository.

Here are some instructions for how to set this up. (how to point your machine to this repository)
[http://download.bitdefender.com/repos/#](http://download.bitdefender.com/repos/#)

Then its just standard apt-get :)

---

### Post by smooth3006 on 2008-07-30
> **tinny said:**
> This is what you want!

They have their own repository.

Here are some instructions for how to set this up. (how to point your machine to this repository)
[http://download.bitdefender.com/repos/#](http://download.bitdefender.com/repos/#)

Then its just standard apt-get :)

thanks for this but i guess it won't work because i have a x64 install of ubuntu. this says it's for i386. :(

i thought bitdefender could work on x64 systems ?

---

### Post by hyper_ch on 2008-07-30
why do you want to run antivirus anyway?

---

### Post by sstusick on 2008-07-30
Another great site for debian files, [http://www.getdeb.net/](http://www.getdeb.net/)

---

### Post by gjoellee on 2008-07-30
you should check out this site as well: [http://www.debian.org/distrib/packages](http://www.debian.org/distrib/packages)

---

### Post by tinny on 2008-07-30
> **hyper_ch said:**
> why do you want to run antivirus anyway?

Yep! 

Linux will not be effected by the Viruses you are probably thinking of. (this is a windows mind set)

However if you are trying to protect other machines on your network that run Windows then there may be some value in what you are trying to do. (Linux machines can be carriers of these viruses but wont be effected)

---

### Post by SunnyRabbiera on 2008-07-30
right you really dont need antivirus in linux...

---

### Post by smooth3006 on 2008-07-30
> **tinny said:**
> Yep! 

Linux will not be effected by the Viruses you are probably thinking of. (this is a windows mind set)

However if you are trying to protect other machines on your network that run Windows then there may be some value in what you are trying to do. (Linux machines can be carriers of these viruses but wont be effected)

i know i dont technically need one but since im dual booting with vista and have a removable drive id at least like a av scanner. ive heard of clamav but I want a graphical interface scanner. I heard bitdefender was good.  I just need to find out if it will work under x64 ubuntu or not ? and how to instll ?

---

### Post by tinny on 2008-07-30
> **smooth3006 said:**
> i know i dont technically need one but since im dual booting with vista and have a removable drive id at least like a av scanner. ive heard of clamav but I want a graphical interface scanner. I heard bitdefender was good.  I just need to find out if it will work under x64 ubuntu or not ? and how to instll ?

ClamTk is a GUI front end for clamav. (clamav is pretty good)

It available in "Add / Remove applications" search for "ClamTk".

---

### Post by angry_johnnie on 2008-07-30
Well, you don't really need an antivirus, but if you want one, there's ClamAV in the repositories, and clamtk as the graphical frontend to clamav.

If you don't want clamav, and would rather use the rpm package, you must convert it, using alien.
```

sudo apt-get install alien
```

and then

```
cd /location/of/rpm/package
sudo alien -d name-of-the-package.rpm
```

---

### Post by gandaran on 2008-07-30
no need to convert the rpm package, there's also a .deb package of the same free bitdefender antivirus, you just have to look for it.
I'm using bitdefender, I think it's the best linux antivirus, it's the only one that includes adware, spyware and antivirus updates but I believe only works on 32-bits systems, and it's only a command line scanner, there is a third party gui for it for those that want one, I don't need it, I just made a nautilus menu options with nautilus actions utility, this way you just right click the file and select the option to scan the file or folder.
F-prot has a free linux 64-bits antivirus (fprot version 6 works on both 32-bits and 64-bits) no gui, only command line scanner.

---

### Post by smooth3006 on 2008-07-30
thanks guys i went with clamav, but it says i need to be root to update the signatures ? also i notice this is not the current version of clamav, how can i upgrade it ?

---

### Post by DirtDawg on 2008-07-30
> **tinny said:**
> ClamTk is a GUI front end for clamav. (clamav is pretty good)

It available in "Add / Remove applications" search for "ClamTk".

I would recommend [Avast]("http://www.avast.com/eng/download-avast-for-linux-edition.html") or [AVG]("http://free.avg.com/ww.download?prd=afl") over Clam.

In my experience, Clam AV is really, *really* slow. In addition, because Clam AV has no paid staff, it's been said their virus definitions are sometimes less up-to-date than others. I'm not sure if that's true or not, but the slowness alone is a deal killer for me.

---

### Post by smooth3006 on 2008-07-30
> **DirtDawg said:**
> I would recommend [Avast]("http://www.avast.com/eng/download-avast-for-linux-edition.html") or [AVG]("http://free.avg.com/ww.download?prd=afl") over Clam.

In my experience, Clam AV is really, *really* slow. In addition, because Clam AV has no paid staff, it's been said their virus definitions are sometimes less up-to-date than others. I'm not sure if that's true or not, but the slowness alone is a deal killer for me.

thanks but neither of those above will work on a x64 bit ubuntu version.

---

### Post by philinux on 2008-07-30
[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

Check this out.

---

### Post by gjoellee on 2008-07-30
the viruses...I managed to get a trojan via WINE so be careful downloading bad stuff with windows emulators (i discovered this with a Anti Virus scanner) I did remove it self by removing the programs folder...(the folder the program was in)

---

### Post by smooth3006 on 2008-07-30
thanks guys i was able to get avg on my x64 install following a guide i found on here. :)

---

