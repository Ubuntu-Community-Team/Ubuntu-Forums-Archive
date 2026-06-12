---
title: "Problems with wireless and files on eeeXubuntu"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by XubuNoobie on 2008-04-22
Hi.

I have an Asus EEE 4g and recently installed eeeXubuntu on it. At first everything seemed ok, but now I'm having troubles.

Problems started when I tried to connect a wireless router. The router works ok on my table computer, but not on eee. Eees blue wifi-light is on, but it can't connect. When I looked at terminal, it couldn't find wifi at all.

Also, when I start or restart my computer, i get an error message, that says it can't find or warrify my internet connection and that I should add my username to etc/hosts. Well the problem is that yesterday I get permission denied, when I tried to access etc/hosts. Today it shows, that no such file even exists.

My internet connection options seem to disappear as well. Yesterday I couldn't find the options to start wireless, today I can't find wireless connction even in manual configurations.

Any ideas gays? I'm thinking of giving up and installing the whole OS again...

---

### Post by aeiah on 2008-04-22
you should probably check out the eeexubuntu community. they should be able to help you a lot better since all eeepcs are pretty much the same

---

### Post by XubuNoobie on 2008-04-22
> **aeiah said:**
> you should probably check out the eeexubuntu community. they should be able to help you a lot better since all eeepcs are pretty much the same

I've tried there too. :) So far, no luck.

---

### Post by merwizard on 2008-04-22
I tried eeexubuntu. Enjoyed it, but it has its shortcomings. Then I stumbled upon this project:

[http://www.eeepclinuxos.com](http://www.eeepclinuxos.com)

They are far more advanced than eeexubuntu as far as I know, considering that last time I tried eeexubuntu was by Christmas. They are still testing this stuff, but I use it on a daily basis and it's stable enough for me.

The advantages of trying it are as follows:

It can be installed both on a USB stick and the internal SSD. Iti uses the same mechanism on both (compressed install + changes file + unionfs). That dramatically reduces the size of a typical install to only 700 MB, leaving  the rest of the disk space available to be used for any purpose. The Live USB install also keeps the changes you've made, so, you can use it exactly the way you would use a "hard disk" install.

Full KDE experience, full OSD, working overclocking (via GUI!), everything else works (notable exception, Fn+F2, but they're working on it).

They use Synaptic too, and they have good package repositories.

Most system configuration done via GUI (the PCLinuxOS Control Center is quite nice)

Download the current beta at

[http://www.eeepclinuxos.com/iso/EeePCLinuxOS-Beta3.iso](http://www.eeepclinuxos.com/iso/EeePCLinuxOS-Beta3.iso)

---

