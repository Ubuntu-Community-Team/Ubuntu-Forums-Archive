---
title: "Configure File Sharing, what's next?"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by fester225 on 2008-11-09
I'm trying to configure a couple of Kubuntu directories for sharing. I click on SHARE, and then CONFIGURE FILE SHARING. At CONFIGURE FILE SHARING I enter my password, then nothing happens. Am I supposed to get a dialog box to configure the directories?

---

### Post by jhahoneyk on 2008-12-05
try installing the gui tool-
sudo apt-get install system-config-samba

---

### Post by mugginz on 2009-04-20
Kubuntu ships with file sharing in a broken state but it easy to fix.

I've made a how-to on how to fix it though.

[http://mugginix.com/articles/2009/Apr/19/Broken-File-Sharing/]("http://mugginix.com/articles/2009/Apr/19/Broken-File-Sharing/")

---

### Post by olingerc on 2009-09-30
I think it's still broken in karmic. Somebody has time to file bug?

---

### Post by cariboo on 2009-09-30
@olingerc

If you have a problem with Karmic, you should ask you questions in [Karmic Testing & Development]("http://ubuntuforums.org/forumdisplay.php?f=359"). If you don't create a bug report yourself, the devs won't be able to fix it.

---

### Post by araknyd on 2009-12-08
mugginz: i didnt need all of the steps you provided to get the "configure file sharing" button to work in the folder properties dialogue box. however, im sure i will have to adjust the vista OS in order for it to find my folders over the network.

NFS (nautilus??) is only used for unix to unix sharing right? as long as thats the case then samba should be sufficient.

thanks for the help.

BTW, using Karmic Kubuntu with the most recent kernel updates.

---

