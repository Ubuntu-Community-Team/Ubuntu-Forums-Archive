---
title: "Installing jUploadr with Menu Installation! (in Hardy)"
date: 2008-08-22
forum: Outdated Tutorials &amp; Tips
---

### Post by Dragoncracker on 2008-08-22
[SIZE="2"]**_Introduction:_**[/SIZE]

Seeing as how I noticed there was no guide to installing jUploadr I figured someone should write one.  (That and its about time I gave something back to a great community that has helped me out so many times)

[SIZE="2"]**_jUploadr:_**[/SIZE]

(From the [jUploader website]("http://juploadr.org/"))
> jUploadr is a cross platform, cross-site Photo uploader. Currently it runs on Windows Linux and OS X and supports both Flickr and Zooomr. It allows you to set all properties of a photo before you upload it. It also supports batch editing, so you can make short work of uploading a bunch of files. 

[SIZE="2"]**_To install jUploadr:_**[/SIZE]

1. download [jUploader]("http://juploadr.org/download_linux.php") to your desktop
2. rename the file to jUploadr.tar.gz
3. open a shell (Applications > System Tools > Konsole) and enter the following commands
```
sudo mkdir /usr/local/share/java
```
```
cd Desktop
```
```
sudo mv jUploadr.tar.gz /usr/local/share/java
```
```
cd /usr/local/share/java
```
```
sudo tar zxvf jUploadr.tar.gz
```
```
sudo rm jUploadr.tar.gz
```
```
exit
```

There its installed, lets...
[U][SIZE="2"][B]
Add it to the applications menu![/B][/SIZE][/U]

1. right-click applications 
2. go to Edit Menus
3. Change the directory on the left to "Internet"
4. Click "New Item"
5. Enter the following in the dialog box
```
_Type:_Application
_Name:_ jUploadr
_Command:_ /usr/local/share/java/jUploadr-1.1.2-linuxGTK-i386/jUploadr
_Comment:_Upload pictures to Flickr and Zooomr
change the icon to /usr/local/share/java/jUploadr-1.1.2-linuxGTK-i386/juploadr.ico
```
6. Click "Ok" in the dialog box and "Close" in the menu editor

**_[SIZE="2"]Your done, I hope you Enjoy![/SIZE]_**

_Notes:_ the paths may need to be changed to reflect the version of jUploadr that you downloaded. This tutorial does not cover installing java, you will also need this installed if it isn't already, there have been plenty of good tutorials on this so I won't cover it.

---

### Post by abenrob on 2008-12-16
Thanks for the useful post! Seems to work great so far.

---

### Post by matt.cohenprice on 2009-01-21
this is great! thanks Dragoncracker.

Dragoncracker's original tutorial is designed for Hardy/Kubuntu installation, I believe, but I am happy to let you all know it works perfectly with my Intrepid/Ubuntu installation as well. 

Thanks!

---

### Post by kimme on 2009-02-14
It worked here as well on my Ubuntu/Intrepid system.

---

### Post by Pharmacore on 2009-07-12
Works a treat in jaunty also. Thank you.

---

