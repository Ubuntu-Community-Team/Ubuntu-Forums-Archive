---
title: "filezilla: usb not listed in ubuntu"
date: 2019-04-23
forum: New to Ubuntu
---

### Post by billy3xs on 2019-04-23
In the Filezilla local site where I've seen drives that could be selected, there are no drives, specifically a USB pen drive I'd like to download to.
Any ideas how to see the drives would be greatly appreciated.

Also I uninstalled and reinstalled, but could not get the latest Ver.

---

### Post by Holger_Gehrke on 2019-04-23
Short answer: look in /media/YOUR_USERNAME_HERE/. There should be a directory either named with the volume-label of the stick if it has one or with its UUID if it doesn't have a label.

Long answer: historically the concept of drives is hidden from the user on Unix-like operating systems. The administrator would mount the filesystem on the drive into some directory and the user would not even know that this directory was another drive; he'd only see the directory-tree. On modern Unix-like systems, administrator and user are usually one and the same person and various automatic helper programs do some of the work for them. So instead of having to know what a drive is called and mount it manually (which is still possible), there is an automatism which will mount any storage-device that is plugged in during a session into a directory in /media .

Holger

---

### Post by billy3xs on 2019-04-23
Ha! So simple, thank you so much! 
And for a little face saving, yes I named the thumbdrive George....:p

---

