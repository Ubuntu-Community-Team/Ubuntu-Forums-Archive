---
title: "I Need build-essential Package, But An Offline Installer"
date: 2006-09-05
forum: Programming Talk
---

### Post by ZuLuuuuuu on 2006-09-05
Hi, I have a problem about installing softwares via internet. I have two computers, actually one is mine and one is my father's. Because of a "cable" problem only my father's computer is connected to internet. But Ubuntu is only installed on "my" computer. I need to get the build-essential package to be able to install other .deb files or source codes that I downloaded via my father's computer. But I cannot install build-essential package because my computer is not connected to internet and synaptic cannot find that package.

It surprised me that Ubuntu has not any installed C compiler by default. Anyone here have an advice for me?

---

### Post by ciscosurfer on 2006-09-05
Go to [http://packages.ubuntu.com/](http://packages.ubuntu.com/) on your father's computer, download the .deb file, burn it to a disc, pop that disc in your drive, copy the .deb file over to your desktop, and then install it by clicking the icon.

---

### Post by toojays on 2006-09-06
If you follow ciscosurfer's advice, make sure you download the deb files for all the necessary dependencies of build-essential as well. These are listed on packages.ubuntu.com.

Another point is that if you have (or can download) the "alternate" install CD (as opposed to the LiveCD installer), build-essential is on that CD. You can add this CD in Synaptic, and then Synaptic will know to install build-essential from the CD rather than try and use the network.

Another way to do it: on your computer, run "sudo apt-get --print-uris install build-essential", and answer yes when it asks if you want to continue. It will then print the addresses of the packages you need. If you download these and copy them to "/var/cache/apt/archives/" on your computer, then you can run "sudo apt-get build-essential" and it will install them from your hard drive.

---

### Post by ZuLuuuuuu on 2006-09-06
Thank you very much, the easiest way was to insert Desktop CD and then use Synaptic. But I will try the other ways you mentioned to install other software that are not in Desktop CD.

---

### Post by loveuchicks on 2008-08-18
i m unable to get build-essential ... i think i require that for c++ header file.. can any one give me link for that please i dont have internet on my comp

---

### Post by MONODA on 2008-08-18
i suggest that you buy the dvd collection containing the ubuntu repos since you do not always have access to the internet. You can probably get them from linuxcd.com or osdisk.com.

---

### Post by WW on 2008-08-18
> **loveuchicks said:**
> i m unable to get build-essential ... i think i require that for c++ header file.. can any one give me link for that please i dont have internet on my comp

Same advice as above: I'm pretty sure you can install build-essential from your installation CD.

---

### Post by JMannering129 on 2009-04-12
what build package should i download there is a bunch of them and i just don't know which one everyone is talking about

---

### Post by slavik on 2009-04-12
We don't ressurect dead threads around here.

---

