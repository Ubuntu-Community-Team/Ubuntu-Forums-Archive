---
title: "Installing Google Video Uploader"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by JimmyJim on 2008-07-01
I downloaded the Google Video Desktop Uploader (ref: [https://www.google.com/video/upload/UploadInfo?hl=en](https://www.google.com/video/upload/UploadInfo?hl=en)). I checked out the installation guide (ref: [https://upload.video.google.com/video_instructions.html](https://upload.video.google.com/video_instructions.html)) and of course they give a guide for everything but Linux. 

I downloaded the .jar file. How do I install it? It appears to be a bunch of classes...  




Heheh, I'm such a newbie. :redface:

---

### Post by JimmyJim on 2008-07-01
Anyone?

---

### Post by JimmyJim on 2008-07-01
bump; I thought this would be simple..

---

### Post by JimmyJim on 2008-07-02
OK, I found out the command. Here it is if anyone needs it:

```
java -jar GoogleVideoUploader.jar
```

---

### Post by bhadotia on 2008-07-02
Install the sun-java6-bin, sun-java6-jre, sun-java6-plugins packages and sun-java6-fonts packages. Then you can run any .jar file without having to launch the command line. Just right-click on the *.jar file and select properties. Then go to 'open with' tab and select open with sun java webstart (or something like that - can't remmember). Be sure to remove the openjk 7 and icedtea plugin (remove everything related to java7) packages, if you already have them, so that these do not conflict with the above software.

---

