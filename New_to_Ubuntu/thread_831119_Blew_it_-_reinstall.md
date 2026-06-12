---
title: "Blew it - reinstall?"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by pablote on 2008-06-16
Hi again! As i've been having a lot of troubles with synaptic triying to install some packages i need to get my usb modem working, and i figured that maybe if i reinstall ubuntu i can get the installation to install those packages i need. Is that posible? I don't remember if Ubuntu Installation let's you do that, though =S. Any ideas on that?

Besides, i think messed something up because when i try to install some deb packages manually i get somekind of error. 
The last idea i had was to try to create a local repository for Synaptic (as i dont have access to internet and synaptic doesn't let me install packages from the installation cd). I found a thread ( [http://ubuntuforums.org/showthread.php?t=42862](http://ubuntuforums.org/showthread.php?t=42862)) with information about it, but, once again, i need a few packages i *don't* have (dpkg-dev, etc.), so i'm back where i started. 

Thanks in advance!!!, once again, this is my third thread in 2 days, and as most of you guessed, I'M A NEWBIE jejej

pablo

---

### Post by rraj.be on 2008-06-16
To configure usb modem just type this in terminal

```
wvdialconf
```

then you have to edit this file to fill your diallup number ,user name and password.

to edit:

```
sudo gedit /etc/wvdial.conf
```

to dial usb modem connection 

type ```
wvdial
```

To make a local repositary there is one easy way than shown in thread.

Just install aptoncd

```

sudo apt-get install aptoncd
```


This can be used to create local repositariers on your dvd or cd.

Here you can add packages in any folder and even all installed packages.

May i know if you need any further help.
Feel free to contact.

---

### Post by pablote on 2008-06-16
Thanks for your answer!
The thing is that my usb wireless modem is for conecting to a router, i mean i have a wireless connection. Ubuntu "connects" but i can't enter any websites and most certainly can't download any packages.
About aptoncd, won't i need to download the package when i call apt-get install ?? remember i dont have internet access nor access to the packages from the installation cd =(( .

Do you have any idea if i can choose which extra packages i want to install DURING the installation? if i can, i think i'm going to reinstall ubuntu

---

### Post by rraj.be on 2008-06-16
> **pablote said:**
> 
Do you have any idea if i can choose which extra packages i want to install DURING the installation? if i can, i think i'm going to reinstall ubuntu

I have no idea about wirless routers as i havn't used it.

hope someone will help you.

Regarding aptoncd if you created the aptoncd after downloading all your required installation packages,
then you can just insert the disk,

and ubuntu will automatically recognize it as a repository and starts synaptic package manager.

```
 You can install all the contents of that cd.
```

Even if you use spt-get install you can install from cd.

---

### Post by cariboo on 2008-06-16
Maybe your terminology is off a little what type of wirelss access device are you trying to set up, and if you do have a router wouldn't it be easier just to get a network cable to connect to the router so that you can download whatever files you need to get your network device working?

If you were to paste the result of lsusb  in you next post maybe we ccould help you solve your problem. In Applications-->Accessories-->Terminal type:

```
lsusb
```

Jim

---

