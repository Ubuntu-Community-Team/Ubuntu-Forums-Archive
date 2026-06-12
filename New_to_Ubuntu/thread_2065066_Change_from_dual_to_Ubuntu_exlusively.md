---
title: "Change from dual to Ubuntu exlusively"
date: 2012-10-01
forum: New to Ubuntu
---

### Post by jaspenhof on 2012-10-01
I currently have Ubuntu 12.04 installed along with Win XP.  I installed it using the windows installer.

I'm ready to get rid of Win XP and use Ubuntu by itself.

I am using a 6 y/o Dell Dimension with 1 gb memory.  My HD is only 35 gigs.  But I have a 500 gig external HD attached via USB.

I don't know how to get this done and I need your help.  I also need your instructions to be as simple as possible.  I'm not that computer literate.

Thanks for your time and assistance

Spence

---

### Post by 2F4U on 2012-10-01
From what you are saying I guess you installed Ubuntu "inside" Windows using Wubi? If this is true, since Ubuntu is installed using Windows XP, you can't get rid of XP easily, since that would also destroy the Ubuntu installation. To use Ubuntu exclusively, you would have to do a clean installation using the Ubuntu liveCD.

---

### Post by HiImTye on 2012-10-01
copy the '/home/<user>' folder from inside your WUBI install to your external drive, along with any other data folders you want to keep on your main drive (music, videos, etc). after this, just use a liveCD/USB and install as per normal. once it's completed, copy your the folders you backed up earlier to the folders you want them in, and viola! you may need to log out and then back in for some changes in your /home/ folder to take effect

other than this, you will just need to install any programs you had installed, but your settings for those should remain, assuming they weren't in system folders

let us know if you need any specific instructions

---

### Post by deadflowr on 2012-10-01
First thing you'd probably want to do is backup any personal files you have. Then go to Ubuntu.com and download the ISO:

[http://www.ubuntu.com/download/desktop]("http://www.ubuntu.com/download/desktop")

Please read the installation instructions 

[http://www.ubuntu.com/download/help/install-ubuntu-desktop]("http://www.ubuntu.com/download/help/install-ubuntu-desktop")

Then when it's time to install, since you want to erase XP, install over everything(later on, when you've gained more knowledge, you can try setting up various partition schemes).

---

### Post by Elfy on 2012-10-01
You can migrate it to a partition - then you can remove XP

[https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)

---

