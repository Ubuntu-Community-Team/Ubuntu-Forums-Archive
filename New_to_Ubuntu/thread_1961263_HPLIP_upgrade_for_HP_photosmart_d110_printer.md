---
title: "HPLIP upgrade for HP photosmart d110 printer"
date: 2012-04-18
forum: New to Ubuntu
---

### Post by tyanka on 2012-04-18
1st day on ubuntu 10.04. Can someone help me to upgrade to HPLIP version that is more recent than the 3.10.2 version that I just installed. I'm trying to get my d510 Photosmart printer to connect. I looked around and saw that an upgraded prepackaged version was an easier install- how do I get it and install it. Thanks!!

---

### Post by 3rdalbum on 2012-04-18
Ubuntu 10.04 is about two years old now. Generally I recommend that people use the latest version of Ubuntu (11.10, or in a week it will be 12.04) unless there's a specific reason to use an older version.

The newer version of Ubuntu will have a newer HPLIP package too.

If you are using 10.04 for a specific reason, i.e. later Ubuntus won't work with your hardware, then read on.

You may be able to go to [http://packages.ubuntu.com](http://packages.ubuntu.com) and look up the packages for HPLIP for a newer version of Ubuntu. I can't guarantee that they'll install without demanding you update most of your system's other packages, but you can give it a try. If you look at the hplip package, it will also list some other packages it needs ("dependencies"); you'll need to install the dependencies first, and then the main hplip package.

However, if at all possible, you'll have a better time using a later Ubuntu such as 12.04, which is about to be released and currently is in beta. You can download and install Beta 2 today and it will update itself to the final release when available.

---

### Post by jawilljr on 2012-04-19
Try the commands below:

```
sudo add-apt-repository ppa:hplip-isv/ppa
sudo apt-get update
sudo apt-get install hplip hplip-gui
```

Or alternatively you can use [these instructions](http://hplipopensource.com/hplip-web/install/install/index.html)

Jerry

---

