---
title: "HOWTO JDownloader in Kubuntu"
date: 2010-01-06
forum: Outdated Tutorials &amp; Tips
---

### Post by schnelle on 2010-01-06
First, I have to admit that I don't use this program :). But two friends of mine use it, and because I installed Kubuntu on their PCs, I had to figure out how to install JDownloader in linux. 
So i figured it out and I want to share the "knowing" with you :).

This is what you need:

1) Install java
   ```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
```
2) Go to [http://jdownloader.org/download](http://jdownloader.org/download) and choose Other (Java) and download zip file.
3) Extract downloaded zip file somewhere.
4a) Open Terminal. Go to folder where you have extracted zip file and type ```
java -jar JDownloader.jar
```
4b) If you do not want to run JDownloader from Terminal, open Dolphin, go to extracted folder, select JDownloader.jar, then right mouse click and go to properties. Then click on "edit file type". Then click on "Add" button and type in the box ```
java -jar
``` and then press "Ok".

That's all. If you want to change icon, picture is in extracted folder/jd/img/splash_sum.png

I hope this HOWTO was useful to you.

---

### Post by Canto39 on 2010-03-05
I followed all of these steps and it seemed to go fine but when I try to run JDownloader from Terminal it looks like its opening it but then it just sits there and nothing opens. Is JDownloader supposed to have a GUI? 0r is it all through the Terminal?

---

### Post by schnelle on 2010-04-03
Yes there is a GUI.

---

