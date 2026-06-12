---
title: "cannot update from ubuntu 10.10 to 11.04"
date: 2012-08-02
forum: New to Ubuntu
---

### Post by ZelAlex on 2012-08-02
I am using the update manager to update from 10.10 to 11.04 but get error in downloading packages. last 5 files only. what to do?

Preparing to upgrade and setting new software channels works fine but in getting new packages at 1281 file number i get these:

Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/libm/libmusicbrainz-2.1/libmusicbrainz4c2a_2.1.5-4ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/libm/libmusicbrainz-2.1/libmusicbrainz4c2a_2.1.5-4ubuntu2_i386.deb) 403  Forbidden
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/b/banshee/banshee-extension-ubuntuonemusicstore_2.0.0-2ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/b/banshee/banshee-extension-ubuntuonemusicstore_2.0.0-2ubuntu2_i386.deb) 403  Forbidden
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/b/branding-ubuntu/branding-ubuntu_0.7_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/b/branding-ubuntu/branding-ubuntu_0.7_all.deb) 403  Forbidden
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-branding_14.0.1+build1-0ubuntu0.11.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-branding_14.0.1+build1-0ubuntu0.11.04.1_i386.deb) 403  Forbidden
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/r/rhythmbox-ubuntuone-music-store/rhythmbox-ubuntuone-music-store_0.2.0-0ubuntu1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/r/rhythmbox-ubuntuone-music-store/rhythmbox-ubuntuone-music-store_0.2.0-0ubuntu1_all.deb) 403  Forbidden

---

### Post by marl30 on 2012-08-02
11.04 is almost dead as well, so why not just download 12.04 and install it? Upgrading is not really recommended anyway as it is usually a hit and miss deal.

---

### Post by ptn107 on 2012-08-02
Try again.  Those links to the files work fine for me.

If it does not work and you *still* want to upgrade to 11.04, download this cd image:

[_ubuntu-11.04-alternate-i386.iso_]("http://releases.ubuntu.com/11.04/ubuntu-11.04-alternate-i386.iso")

Burn it to a cd (or loop mount it [[_link_]("http://www.cyberciti.biz/tips/how-to-mount-iso-image-under-linux.html")], whichever is easier for you) and stick it in your drive.  You will be prompted to upgrade.  If it asks you to fetch the latest updates from the internet during your upgrade I would say no in your case since you had trouble.

You should consider installing 12.04 LTS.  It will be supported with updates until 2017.  If you upgrade to 11.04 (which hits end of life in two months) you will need to upgrade to 11.10 at that time.  So it really depends on how long you want to go without having to upgrade to another release:

a) Clean install or upgrade to 12.04 LTS.  So no need to upgrade for 5 years. [[_link_]("https://help.ubuntu.com/community/PreciseUpgrades/")]
b) Upgrade to 11.04, then you will need to upgrade to 11.10 in two months.  Then six months later have to upgrade 11.10 to 12.04 LTS.  Then you will still have 4 years of support without upgrades.

---

### Post by haplorrhine on 2012-08-02
> **ptn107 said:**
> Burn it to a cd (or loop mount it [[_link_]("http://www.cyberciti.biz/tips/how-to-mount-iso-image-under-linux.html")], whichever is easier for you) and stick it in your drive.  You will be prompted to upgrade.  If it asks you to fetch the latest updates from the internet during your upgrade I would say no in your case since you had trouble.
  I didn't know about that.  Can that be done with a flashdrive containing the iso files?

I was going to suggest that ZelAlex download those specific, linked packages onto someone else's computer,
transfer the .deb files to their computer with a flashdrive,
and install the packages via those copies of the files before attempting the update again.

---

### Post by ZelAlex on 2012-08-04
I want to update to the latest. I have no desire to go to 11.04 specifically. Just want latest. 

I want to clarify one thing. I had installed ubuntu from inside windows. I had an iso image of 10.10 and installed ubuntu inside windows. I also have an iso of 12.04. But when I tried to use that to install inside windows there was no such option. Can you tell me how to update to the latest or the LTS version?

---

### Post by ZelAlex on 2012-08-04
I uninstalled ubuntu 10.10 and installed 12.04 LTS but my internet stopped working. Had to uninstall it and go back to 10.10

[http://ubuntuforums.org/showthread.php?t=2037340](http://ubuntuforums.org/showthread.php?t=2037340)

---

### Post by haplorrhine on 2012-08-04
> **ZelAlex said:**
> [http://ubuntuforums.org/showthread.php?t=2037340](http://ubuntuforums.org/showthread.php?t=2037340)[QUOTE=ZelAlex;12149855]EDIT:
[http://ubuntuforums.org/showpost.php?p=10479823&postcount=3](http://ubuntuforums.org/showpost.php?p=10479823&postcount=3)
This solved it[/QUOTE]
This is solved then, aye.

---

