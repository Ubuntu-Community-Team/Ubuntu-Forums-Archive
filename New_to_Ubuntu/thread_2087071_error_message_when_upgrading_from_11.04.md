---
title: "error message when upgrading from 11.04"
date: 2012-11-22
forum: New to Ubuntu
---

### Post by sheppydog on 2012-11-22
i get messages telling me 11.04 is no longer supported

when i try to upgrade i get the following error message:
  	 	 	 	 	 	  

 'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'


i am an absolute beginner when it comes to doing anything on ubuntu so please speak simply and take me through what i should do step by step, please


thankyou

---

### Post by arpanaut on 2012-11-22
Take a look here:
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

### Post by ajgreeny on 2012-11-22
In all honesty, with 11.04 being out of support, and the best version for you now probably being the last long term support (LTS) 12.04, I think you should simply do a new, clean install.

To update further than you are at the moment, you would have to go from 11.04 to 11.10, and then from 11.10 to 12.04, and I don't think it is worth attempting that.

Just backup everything in your home, including all the hidden files and folders, reinstall 12.04, and then restore your home again. You might like to consider having a separate /home partition this time, if you don't already have one; it makes reinstallation a lot easier.

See [Separate home at install.]("http://www.psychocats.net/ubuntu/installseparatehome")

---

