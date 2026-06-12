---
title: "Set up unattended install"
date: 2021-05-14
forum: New to Ubuntu
---

### Post by bfedyk-63 on 2021-05-14
Hi, THis is my first post to the forum, so I hope I am posting in the right group. If not I can re-post elsewhere.

I have some experience of using Linux/Ubuntu as a user. I have used various Linux distros on and off over the years, as a user, and recently have got involved with Ubuntu. I currently have Xubuntu desktop installed on my laptop, so I am familiar-ish with Ubuntu as a user. I have recently got involved with Ubuntu server installs and set up. I am now starting to get involved with some server administration. Let me explain the situation. 

We have two test environment servers, one currently left to run 16.04 LTS (Xenial), the other 18.04 LTS (Bionic). These are used for installing our application for test purposes. Occasionally we need to re-install from scratch, meaning fresh OS install first, then apply the application. We sometimes have different configurations to apply, hence easier to wipe and re-install. 

The two servers are Dell rack servers, with iDRAC. So we can set up a virtual CD in iDRAC connected to a local copy of the server ISO file, and so re-install the server over the internet this way. This works fine, and I have a fast internet speed where I am based, so process is not long. However this is an attended install, requiring user input to answer questions. So I want to set up unattended install/re-install, to just set the process off, go away have some coffee and it is done. 

I have started to look at ways of doing this (this is new to me), So, I have looked at using plain dd to copy the hard drive to an image file (compressed), then there is the autoinstall option certainly for 18.04, with the autoinstall config file. I have also looked at MaaS (Metal as a Service) i.e. to set up a server that would act as the region controller and rack controller, we can store the ISO images here, physical servers would be added to the 'pool' as a resource as with cloud infrastructure. I have also looked at PXE booting. 

I am not sure the best  - most efficient and fast - option to use. We could try all the options and see which suits best. 

A further confusion is the install used in the Ubuntu servers. I have read lots of posts and some say 18.04 uses the debian-installer (d-i), others say ubiquity. It seems that the new autoinstall feature will work with ubiquity installer, not with d-i. The debian-installer uses preseed file, which U gather is not as fully automated as autinstall can be. So as I understand, 18.04 uses ubiquity and 16.04 debian-installer? 

Our 18.04 server does have a /var/opt/log/autinstall-user-data file, so this means 18.04 will work with autoinstall? 

My question is: we need to be able to wipe and install a fresh OS image quickly, and with ideally no user input. Which of the different options is best?

---

### Post by TheFu on 2021-05-14
16.04 LTS support ended last month.  No use in doing anything with that release - except wiping it and loading 20.04.  Any clients should be clearly told that 16.04 support ended. Period.

To manage server configurations, use a devops tool.  Don't make changes manually.  Ansible is pretty easy to get going.  20 minutes and you'll be ready to manage 5-5000 systems with Ansible, assuming you are already an Admin and understand advanced-beginner admin things - not advanced end-user things.

iDRAC should never be directly connected to the internet. The security failures for those are well documented. It is a great way to have a hacked server before you even get the OS loaded.

For years, Cobbler was the way to perform unattended installs, but I think it is limited to specific subnets. Don't think anyone would be doing it over the internet. Could be wrong.  With 20.04, Canonical changed the installer into a "Live Boot" situation. They may have broke stuff.

Knowing what I know about 20.04 and later, I'd learn to perform manual installs following the Debian manual, then script that for my needs, avoiding the Canonical stuff completely.  They like to change/break things too often.

Forget 16.04. It is dead, dead, dead.  You need to get your decision makers to understand that.  5 yrs - that's it. No more.  There are 2 LTS releases in 5 yrs, so a 4-yr release upgrade needs to be planned, always. No exceptions.

But I've only done reading on this unattended install stuff, so don't believe me. My choices aren't necessarily yours.  OTOH, I have scripts that were written in the early 1990s that I still use almost daily today, so I know if we avoid chasing the "new hotness" and just do the work, it can last nearly an entire career.  Only you can decide which is best.

---

### Post by grahammechanical on 2021-05-14
I think you will find that it is the Ubuntu alternative server installer version that uses the Debian installer method. The standard Ubuntu server version uses an installer called Subiquity. 

[https://askubuntu.com/questions/1035073/where-are-the-server-alternate-installer-images](https://askubuntu.com/questions/1035073/where-are-the-server-alternate-installer-images)

Regards

---

### Post by TheFu on 2021-05-14
Some "lite" reading:
[https://ubuntu.com/download/alternative-downloads](https://ubuntu.com/download/alternative-downloads) has a network installer for Ubuntu Server 20.04.
[https://discourse.ubuntu.com/t/netbooting-the-live-server-installer/14510](https://discourse.ubuntu.com/t/netbooting-the-live-server-installer/14510) uses the PXE boot method, but I don't think that works off a well-controlled LAN.

Ok, perhaps not, lite. ;)

---

### Post by bfedyk-63 on 2021-05-17
Hi, thanks. It may be using the network installer is the way to go. I will take a look. Also at the PXE boot method info. I may still have to look at MaaS, eventually.

---

