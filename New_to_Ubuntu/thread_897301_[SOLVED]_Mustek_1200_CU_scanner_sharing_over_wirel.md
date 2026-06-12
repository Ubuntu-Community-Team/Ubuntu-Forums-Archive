---
title: "[SOLVED] Mustek 1200 CU scanner sharing over wireless network"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by theozzlives on 2008-08-22
keep trying to find a solution on the net that works. I have a Compaq DeskPro computer, Mustek 1200 CU USB scanner, and Ubuntu 8.04 running on a Samba Shares Network, I'm trying to access my scanner from my wireless laptop (Dell Inspiron 1525)/ Any help would be appreciated.

---

### Post by Redache on 2008-08-22
I don't think there's a way to really do this as Scanners are input devices and tend to need the person to be physically by the equipment. Unless yours has the ability to do this.

---

### Post by prshah on 2008-08-22
> **theozzlives said:**
> keep trying to find a solution on the net that works. I have a Compaq DeskPro computer, Mustek 1200 CU USB scanner, and Ubuntu 8.04 running on a Samba Shares Network, I'm trying to access my scanner from my wireless laptop (Dell Inspiron 1525)/ Any help would be appreciated.

As long as your scanner is seen by SANE (Scanner Access Now Easy) on the computer where it is connected to, you can easily scan via a remote machine as well!

See the topic on "remote scanning" on [this link]("http://www.gentoo-wiki.com/HOWTO_Installing_USB_Scanner").

Post back here if you run into any difficulties.

---

### Post by theozzlives on 2008-08-22
> **prshah said:**
> As long as your scanner is seen by SANE (Scanner Access Now Easy) on the computer where it is connected to, you can easily scan via a remote machine as well!

See the topic on "remote scanning" on [this link]("http://www.gentoo-wiki.com/HOWTO_Installing_USB_Scanner").

Post back here if you run into any difficulties.

I can't scan from my laptop, or my Windows Machine so I'm assuming it's how the backend is setup.

---

### Post by prshah on 2008-08-22
> **theozzlives said:**
> I can't scan from my laptop, or my Windows Machine so I'm assuming it's how the backend is setup.

Oops.. Windows uses TWAIN, not the SANE api; so you cannot scan remotely through Windows unless you do it through java access of SANE.

Yes, the backend for SANE has to be set up on the computer that the scanner is connected to, You have to perform the following tasks:

a) Setup SANE on the scanner "server" computer
b) check if the SANE client on the same computer can scan successfully
c) Now "extend" the SANE backend configuration to include remote scanning, and open up required network ports
d) set up SANE on your (linux) client computers to connect to the SANE backend on your "server" computer to use the scanner. This includes SANE setup as well as firewall settings.
e) check if your clients can successfully scan remotely.
f) Further "extend" the SANE backend to allow use through Java; you will have to setup a recent jdk and open ports in the firewall
g) Check if Windows can successfully initiate a scan through a browser and receive the file as a download.
h) Subsequently, linux clients can also use the Java route, but using the SANE frontend is much "cleaner"

All these tasks are outlined in the link given in the previous post. 

Post back if you have any difficulties.

---

### Post by theozzlives on 2008-08-22
[QUOTE=prshah;5642498]Oops.. Windows uses TWAIN, not the SANE api; so you cannot scan remotely through Windows unless you do it through java access of SANE./QUOTE]

I'm using xsane win32 and that link was just a waste of paper & ink.

---

### Post by theozzlives on 2008-08-23
I got it to work, I just had to go back to 7.10 (Gutsy Gibson). Thanks for your help,

---

