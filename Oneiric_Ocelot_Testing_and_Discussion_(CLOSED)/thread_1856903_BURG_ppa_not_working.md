---
title: "BURG ppa not working"
date: 2011-10-09
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by fantab on 2011-10-09
I am trying to install BURG but the ppa for Oneiric doesn't seem to work... 

I have used _[http://ppa.launchpad.net/n-muench/burg/ubuntu](http://ppa.launchpad.net/n-muench/burg/ubuntu) oneiric main_ which I have found [here]("http://www.unixmen.com/linux-tutorials/linux-distributions/linux-distributions4-ubuntu/1679-how-to-install-burg-in-ubuntu-")

I get the following when I try to install:

```
sudo apt-get install burg burg-themes
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package burg
E: Unable to locate package burg-themes

```

Has anyone else installed BURG using the above ppa? Is there any other source I can use?

Thanks...

---

### Post by cariboo on 2011-10-09
There is no Oneiric repository for Burg, if you click the link you provided, then click Dists, you will see that there is only a Natty repository. Change the oneiric to natty, in your sources list, and you should be able to install Burg.

BTW it looks like Burg is no longer maintained, the last update was in April.

---

### Post by fantab on 2011-10-10
> **cariboo907 said:**
> There is no Oneiric repository for Burg, if you click the link you provided, then click Dists, you will see that there is only a Natty repository. Change the oneiric to natty, in your sources list, and you should be able to install Burg.

**BTW it looks like Burg is no longer maintained, the last update was in April**.

That is sad. I will just wait for the Burg-Oneiric ppa...

Thanks.

---

### Post by effenberg0x0 on 2011-10-10
I have tested super-boot-manager from repo... 
**[B]sudo add-apt-repository ppa:ingalex/super-boot-manager**[/B]...and it worked for grub, burg, plymouth (enable, disable, resolution, colors, default_cmd, themes, etc). You can check for updates from inside the application.

Regards,
Effenberg

---

