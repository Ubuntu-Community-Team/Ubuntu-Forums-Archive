---
title: "How do I Un-Install Ubuntu?"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by jbocean on 2008-08-04
Want to uninstall Ubuntu Studio 8.04?
How do I do that?

---

### Post by beanhead on 2008-08-04
what do you want to put in it's place. I would say just use a live linux cd 

and use the gparted program, like a puppy live cd. are you trying to keep a regular install of ubuntu ?

---

### Post by LowSky on 2008-08-04
Ubuntu Live CD has Gparted on it that can erase partitions, or if you just want Studio gone and want to use regular ubuntu, just type this command in a terminal
```
sudo aptitude remove ubuntustudio-desktop && sudo aptitude update && sudo aptitude install ubuntu-desktop
```

NOTE: it will not uninstall the the audio, graphics or video. use the following command if you did a complete install and want it all gone and want a vanilla ubuntu install

```
sudo aptitude remove ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video && sudo aptitude update && sudo aptitude install ubuntu-desktop
```

---

### Post by jbocean on 2008-08-05
I want to replace Ubuntu Studio w/ Regular Ubuntu 8.04.

---

### Post by stevoo on 2008-08-05
Studio is nothing more than a theme installed on Ubuntu.

So just follow the details here and here you have Studio
[http://www.ubustu.com/globe/2007/05/23/add-ubuntu-studio-to-an-existing-ubuntu-install/](http://www.ubustu.com/globe/2007/05/23/add-ubuntu-studio-to-an-existing-ubuntu-install/)

---

### Post by WRDN on 2008-08-05
> **jbocean said:**
> I want to replace Ubuntu Studio w/ Regular Ubuntu 8.04.

If you wish to do this, just follow the Ubuntu 8.04 installation process, and when you arrive at the partitioning stage, select Manual partitioning. Then, select the partition Ubuntu Studio is currently installed on, and select to Format the partition.

---

### Post by LowSky on 2008-08-05
just follow my commands, or just install the ubuntu desktop

sudo aptitude install ubuntu-desktop

---

### Post by jbocean on 2008-08-05
Thanks everyone, I will give it a try.

---

### Post by jbocean on 2008-08-06
I need some clarification ...

A.  If I use terminal commands (per LowSky's post) and install 'ubuntu-desktop', will that give me the install of Open Office? (which is really what I need the most-to do my work) 

OR

B.  If I use the Ubuntu install interface (per WRDN's post), How will I know which partition has Ubuntu Studio part in it? 

I tried this last night, went to manual partition and couldn't determine which partition had Ubuntu Studio bc I just saw a bunch of numbers (Machine dual boots w/ Win XP - which my wife wants to keep).

We don't have our ISP back up yet to download Open Office, bc our house hit by lightning ... the computer w/ Win XP & Ubuntu Studio survived, but the DSL line/wireless router, didn't.

Thanks again.

---

### Post by maybeway36 on 2008-08-06
The Ubuntu partition is probably ext3. The Windows XP partition is fat32 or ntfs, and the linux-swap partition also belongs to Ubuntu.
You can just erase Ubuntu Studio and install Ubuntu by telling it to only format the ext3 partition and use it as root - /

---

