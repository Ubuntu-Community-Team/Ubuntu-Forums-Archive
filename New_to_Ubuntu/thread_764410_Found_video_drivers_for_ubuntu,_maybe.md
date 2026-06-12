---
title: "Found video drivers for ubuntu, maybe"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by Universal344 on 2008-04-23
OK, I can't enable advanced desktop effects and the restricted drivers frag my graphics.  I posted asking for help and was directed to this page: [http://ati.amd.com/support/drivers/linux/linux-radeon.html]("http://ati.amd.com/support/drivers/linux/linux-radeon.html").  I was about to download linux drivers when I realized the text in the far right column.  I am running 7.10 or gutsy gibbon, will these drivers support it?

---

### Post by SOULRiDER on 2008-04-23
This:
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8-4-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8-4-x86.x86_64.run)

Also, their wiki can be helpful if you come across any errors or problems:
[http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page) and especially **[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)**

---

### Post by rouge568 on 2008-04-23
They should. All xorg is is the core graphics backend for Ubuntu (and many other linux distros). Hardy comes with 7.3, and Gutsy is a generation or so behind. Judging by the range these drivers support, you should be all set to go to install these. I cannot guarantee they will work, but the xorg dependency is satisfied.

---

### Post by Tatty on 2008-04-23
> **Universal344 said:**
> OK, I can't enable advanced desktop effects and the restricted drivers frag my graphics.  I posted asking for help and was directed to this page: [http://ati.amd.com/support/drivers/linux/linux-radeon.html]("http://ati.amd.com/support/drivers/linux/linux-radeon.html").  I was about to download linux drivers when I realized the text in the far right column.  I am running 7.10 or gutsy gibbon, will these drivers support it?

It should do, Gutsy uses Xorg 7.2 i believe.

---

### Post by Universal344 on 2008-04-23
OK, i tried downloading the drivers, but now when I double click the desktop link or click open in the download manager he opens the code in open office. How do I run the drivers??????

---

### Post by Tatty on 2008-04-23
> **Universal344 said:**
> OK, i tried downloading the drivers, but now when I double click the desktop link or click open in the download manager he opens the code in open office. How do I run the drivers??????

Right click on the file, Properties->Permissions->Allow executing file as program.  That makes it executable.

Try the installation page in the link from soulrider... [http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)

---

