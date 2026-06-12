---
title: "Ubuntu or Kubuntu 8.10?"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by diplomat.x on 2008-10-30
I know this subject is quite controversial. But i have experienced ubuntu for quite a while now and want to try something new. Should i go for kubuntu this time? I have limited bandwidth so i cannot waste it just like that.
Please suggest one. 

My synaptics is messed up big time. I had only provided 50 Mb to /boot and so its stuck now. I cannot upgrade or install packages. So i have to do a clean install.

Thank You :)

---

### Post by lisati on 2008-10-30
One thing you might want to check out if you have limited bandwidth is the "minimal install" cd at [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by hellion0 on 2008-10-30
It's all a matter of personal preference. If you like Gnome, just stick with Ubuntu. If you like KDE (or want to give it a try), give Kubuntu a whirl.

Either way you go, you can always convert one to the other down the line:

(From Ubuntu to Kubuntu)
```
sudo aptitude install kubuntu-desktop
```
(From Kubuntu to Ubuntu)
```
sudo aptitude install ubuntu-desktop
```

---

### Post by Yashiro on 2008-10-30
I'd download and install the default Gnome image.
Once it is installed, consider trying Kubuntu.

Or you could boot from a LiveCD and fix your partitions.

---

### Post by Kevbert on 2008-10-30
> **diplomat.x said:**
> I know this subject is quite controversial. But i have experienced ubuntu for quite a while now and want to try something new. Should i go for kubuntu this time? I have limited bandwidth so i cannot waste it just like that.
Please suggest one. 

My synaptics is messed up big time. I had only provided 50 Mb to /boot and so its stuck now. I cannot upgrade or install packages. So i have to do a clean install.

Thank You :)

Why not have Ubuntu Intrepid and add the KDE front end as a sessions option ?  You can then start in either via the options in the log-in screen.  You need to find out what version of KDE is available (4.0 is a disappointment, but 4.1 is fine). You can do this via Synaptic. I've tried this is Hardy, but it is KDE4.0:( See my thread [[COLOR="Red"]here.[/COLOR]]("http://ubuntuforums.org/showthread.php?t=961577")
Regarding boot menu and the boot partition being full. Have you removed all the old kernels from this. You can check to see what kernels are there via terminal with
```
cd /boot
ls -l
```
Having found out what you have go to Synaptic and search for 'linux-image'. You then want to remove all linux-image...-generic images which you are no longer using (apart from the current working one).  This will also remove the unused kernels from you menu.lst file (providing that the current OS is the one that you are running).

---

### Post by billgoldberg on 2008-10-30
> **diplomat.x said:**
> I know this subject is quite controversial. But i have experienced ubuntu for quite a while now and want to try something new. Should i go for kubuntu this time? I have limited bandwidth so i cannot waste it just like that.
Please suggest one. 

My synaptics is messed up big time. I had only provided 50 Mb to /boot and so its stuck now. I cannot upgrade or install packages. So i have to do a clean install.

Thank You :)

Ubuntu, hands down the better distro.

---

### Post by kernelhaxor on 2008-10-30
My choice: Kubuntu FTW!

Its not like one is good, the other bad.  It being a personal choice, you are the better judge.
Ubuntu is more lightweight than Kubuntu.  Some ppl say KDE is bloated but I think it is a very rich desktop environment ..

---

### Post by duki3003 on 2008-10-31
> **kernelhaxor said:**
> 
Ubuntu is more lightweight than Kubuntu.  Some ppl say KDE is bloated but I think it is a very rich desktop environment ..

Yes but some people also say that ubuntu is too simplefied, but it all depends...

Depending on do you perfer elegant an simple - go for ubuntu
Or if you perfer bling bling elegant - go for kubuntu.

My recomendation is install ubuntu, and add kubuntu desktop with ```
sudo aptitude install kubuntu-desktop
```
It's only 150 MB extra download (probably)
and if you're not pleased just remove it
```
sudo aptitude remove kubuntu-desktop
```
I'm asuming you know how to set root password....
:guitar:

---

### Post by Sailorcancer on 2008-10-31
Duki what exactly happens when you install the Kubuntu desktop?

---

### Post by frunns on 2008-11-04
> **duki3003 said:**
> and if you're not pleased just remove it
```
sudo aptitude remove kubuntu-desktop
```


Yeaaahh... Doesn't really work that way though. How do you really remove kubuntu-desktop? With all the stuff it installs that you don't want? And for some reason I got Kubuntu-stuff starting in gnome too, that thing really messed up my installation... ><

---

### Post by deearar on 2008-11-04
I just went through this. I thought I'd try KDE but I found it pretty inconsistent in its interface and went back to Gnome.

As far as removing it, I removed a lot of stuff manually through Synaptic and in the end reinstalled Gnome and GDM for good measure. It is not a simple uninstall.

---

