---
title: "Unable to install from scratch 'Ubuntu 18.04.1 LTS'"
date: 2019-01-10
forum: New to Ubuntu
---

### Post by incorporeo on 2019-01-10
Hello Forum,

After a long research on the most suitable Linux variants for me to use, I opted to Ubuntu.
However, I must say this is, so far, an intention, as it was impossible to install  'Ubuntu 18.04.1 LTS' on my 'HP XW6200 Workstation'.

I'm a newbie on Linux ):P.
Well, please don't think i'm a noob in all other subjects related to OSes.
My 'HP XW6200 Workstation' has a dual-boot with Windows Vista and Windows 7, and works very well with 2 x 3.6Ghz Xeon processors, a Nvidia Quadro and 8GB Ram.

About Ubuntu installation:

It was impossible to install Ubuntu by a burnt DVD.
At least the last version of it. I did not try any other.
The System started with a message "Attempting Boot from CD-ROM".
First, I thought it was a problem with the DVD burning process. I burnt a second one with the 'verify' option, which I use always, and the same problem occours.
The DVD burning hardware is almost new, as I bought it in 2018.

Then I tried to install Ubuntu by USB stick with no success.
I followed all the instructions I got in the Official documentation of Ubuntu, and, of course, used Rufus configured to boot in FreeDOS.
The system recognized the USB stick and booted from it. However it stopped after prompting me the language option (viewable through autoexec.bat).

I began to think about any problem which .iso file might have.
I did a few lownloads from different sources, including the official Torrent source.
The problem remains.

NOTE: All creation of media (DVD burning and USB stick configuration) were made on a external laptop, not in the workstation I want to configure.

Saying so, I have no more ideas on how to solve the situation.

So, I please request to someon in this Forum to give me some help, which I would much appreciate!

Best regards!

---

### Post by oldrocker99 on 2019-01-10
There is a sha256 checksum figure from where you download the .iso file. Follow this:[https://help.ubuntu.com/community/HowToSHA256SUM](https://help.ubuntu.com/community/HowToSHA256SUM).

It is entirely possible, if uncommon, for the download to be corrupted. That's why to always compare the sum with the printed one on the website.

---

### Post by incorporeo on 2019-01-10
> **oldrocker99 said:**
> There is a sha256 checksum figure from where you download the .iso file. Follow this:[https://help.ubuntu.com/community/HowToSHA256SUM](https://help.ubuntu.com/community/HowToSHA256SUM).

It is entirely possible, if uncommon, for the download to be corrupted. That's why to always compare the sum with the printed one on the website.

@ Oldrocker99, thank you for the valuable tip!

I made a download of 'ubuntu-18.04.1-desktop-amd64.iso' from 'http://releases.ubuntu.com/bionic/ ' and used the application 'MD5 & SHA Checksum Utility 2.1' to verify SHA-256.
SHA-256 matched.

First I tried to make an install using USB stick.
It didn't work!
(Was it because my USB stick is a 168GB Lexar, and for that, has too memory for a boot from FreeDos?)

Then, I made a bootable DVD with the .iso file.

Then, it worked!

I made a verify with my first downloads, and found that checksums did NOT match!
(Was it a corruption due to my download, or was it from the source where I downloaded? Remains the question. The fact is that I made the downloads from Ubuntu sites.)

Thank you for the help, oldrocker99!

---

### Post by oldrocker99 on 2019-01-10
Very glad to have helped. Always verify the downloads, especially since the sites make it easy. The corrupted download most likely was the download itself. I have gotten a bad download, and then a good one from the same site.

---

