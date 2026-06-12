---
title: "unable to install ubuntu in windows 7"
date: 2012-02-06
forum: New to Ubuntu
---

### Post by biju1256 on 2012-02-06
Hi,
I am using Windows 7, and i downloaded ububtu into my usb stick. Later on i opened the ios file and wrote it on a cd. I removed the ios file from the drive where i had pasted earlier. And opened the exe file on the cd, installation started as normal but @ the end of installation an error message poped up saying PERMESSION DENIED. And message being displayed pls go through the log file.
Need ur help.

---

### Post by Frogs Hair on 2012-02-06
Hello and Welcome

If you are using Wubi try running it as administrator .

---

### Post by biju1256 on 2012-02-06
Yes.. I hv used wubi.. Ran as administrator... But the same message poped up saying permission denied.

---

### Post by Rafterman414 on 2012-02-06
Check this link. Someone had a similar issue and it was because the cd was bad.

[http://ubuntuforums.org/showthread.php?t=1144599](http://ubuntuforums.org/showthread.php?t=1144599)

Did you write the iso image to the disc using some program like imgburn or infrarecorder, nero etc... or did you just extract the files from the iso and then drag and drop the files onto the disc?

---

### Post by biju1256 on 2012-02-06
yes i used nero(started by default) to write the iso image...

---

### Post by Rafterman414 on 2012-02-06
If you no longer have the iso image try downloading it again and putting it in the same directory as the wubi.exe installer. After reading the posts in the last link I posted some people were able to get around the permission denied error by doing that.

[Wubi Installer]("http://www.ubuntu.com/download/ubuntu/windows-installer")
[Ubuntu ISO]("http://www.ubuntu.com/download/ubuntu/download")

Wubi should find the Ubuntu iso in that directory and use it as the installation source rather then the CD. I have never used Wubi though so I am not entirely sure how it works.

---

### Post by biju1256 on 2012-02-10
thanks a lot Rafterman414,
I hv installed ubuntu with wubi installer.... Thanks lot...
I need one more help.. Mp3 files and video files in the system doesnt play in the existing software i.e. Banshee.
Should i install a new sw?? If yes, would u pls suggest me the best.

---

### Post by holytree on 2012-02-10
The best is VLC Media player.. :D

---

### Post by fractalman on 2012-02-10
If your having trouble playing media you might need to install the codecs,  there's a package called..

ubuntu-restricted-extras

it contains codecs for playing music and vids and other stuff but ubuntu can't include it as a default package due to licensing rights.

open synaptic package manager   system >Administration> synaptic package manager

then in the searchbox enter ubuntu-restricted-extras  ,   click the box next to it and select install.

hopefully that should sort it for you.

---

### Post by biju1256 on 2012-02-10
Hi,
Since  i am new to ububtu... Thanks a lot for suggestions.

---

