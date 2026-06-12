---
title: "problem with realtek driver after update"
date: 2012-12-02
forum: New to Ubuntu
---

### Post by Yannanael on 2012-12-02
Hello,
I had problems with my new Toshiba laptop, which, after installing Xubuntu 12.04, didn't have the Realtek 8723-driver necessary to make the wireless connection work.
I followed the suggestions of another thread and got the downloaded drivers installed.
But after each following update they are gone and I have to install them again.
Not a long job, but I should like to know how I can keep the drivers intact so they don't disappear during an update.
Thank for a solution,
Yann

---

### Post by Mark Phelps on 2012-12-02
How did you install the drivers in the first place?  Did you download a .deb file and use it? Or, did you download a source package and build the kernel module?

Also, how are you determining that the drivers are gone after each update?

---

### Post by Yannanael on 2012-12-03
Hello Mark,
I downloaded a tar.gz-file (rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012.tar.gz) that I extracted. I then cd'ed into the folder, opened a terminal there and did:
sudo su
make
make install
modprobe rtl8723e
exit
(I followed thread [http://ubuntuforums.org/showthread.php?t=2017622&highlight=toshiba+realtek](http://ubuntuforums.org/showthread.php?t=2017622&highlight=toshiba+realtek) 
especially reply by Chili555, july 6th)
This works fine, except for after an update.  Then, when I rightclick on the connection-icon in the upper toolbar, it shows only the wired connection, no wireless connections. And when I pull out the cable for wired connection, it doesn't change to wireless as it does normally.
When I repeat the *cd, sudo su, make etc*, everything works fine again, so I concluded that, one way or another, the driver has disappeared...
(By the way, I'm a newbie to Linux and I don't know where I should search for an installed driver.)
Any insight in what happens when I update?

Yann

---

