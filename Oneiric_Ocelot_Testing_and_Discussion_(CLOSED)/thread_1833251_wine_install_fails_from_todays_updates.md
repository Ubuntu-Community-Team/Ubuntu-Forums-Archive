---
title: "wine install fails from todays updates"
date: 2011-08-25
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by buzzmandt on 2011-08-25
prob something about multiarch stuff, but this was an install from daily live only 3 days ago.  should be multiarch enabled already.
todays update remove wine and ia32-libs, not a big deal and don't really use it much but would like to know if anyone knows if this is being addressed.  perhaps they will build wine for oneiric without ia32?

```
buzzmandt@buzzmandt-Compaq-Presario-CQ60-Notebook-PC:~$ sudo apt-get install wine
[sudo] password for buzzmandt: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine : Depends: wine1.2 but it is not going to be installed
        Depends: ia32-libs (>= 1.6) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
buzzmandt@buzzmandt-Compaq-Presario-CQ60-Notebook-PC:~$ 

```

---

### Post by lvalen18 on 2011-08-26
I second this :(

I've tried using Synaptic and all the wine version (1.0 > 1.3) give the same error
I tried "ia32-libs" says it depends on "lib32v41-o" but then that causes an error about not being installed due to broken packages :mad:

---

### Post by sumski on 2011-08-26
No more lib32v4l
> v4l-utils (0.8.5-3ubuntu1) oneiric; urgency=low

  * Stop building the lib32* packages on amd64. LP: #808064.
  * Package requires symbols jpeg_mem_src and jpeg_mem_dest from jpeg8.
    Build-depend on libjpeg8-dev. 

---

### Post by jucas_lo on 2011-08-26
Hi I am facing the same problem, but I need ia32-libs to run the android-sdk which is only compiled for i386 and depends on ncurses:i386, what can I do???

---

### Post by vhaarr on 2011-08-26
> **jucas_lo said:**
> Hi I am facing the same problem, but I need ia32-libs to run the android-sdk which is only compiled for i386 and depends on ncurses:i386, what can I do???
Just downgrade libv4l again from the old packages found in /var/cache/apt/archives with dpkg -i.

Reinstall ia32-libs.

Then everything works fine :)

---

### Post by drodiger on 2011-08-27
Few days ago, when doing upgrade, it removed googleearth ia32-crossover-pro picasa skype and wine1.3.

How can I reinstall this packages. Some of them are not available in partners section anymore.

I can't also install acroread. I had to install flashplugin from adobe's site. I used 64-bit which is working better then 32bit which was deleted during upgrade.

Thanks

---

### Post by drodiger on 2011-08-27
Another update: wine (ia32-libs also) can be installed now. Just do sudo apt-get update and install wine1.3

---

### Post by P-I H on 2011-08-27
It worked for me to install wine 1.3 by use of synaptic on a fully updated installation with daily build 26/8.

It also worked to install Steam by use of Winetricks and to run Torchlight in resolution 1680*1050. However, after quitting Torchlight the desktop was coruupt and a reboot was required.

---

