---
title: "Remastersys unable to find it"
date: 2014-10-12
forum: New to Ubuntu
---

### Post by joonwo on 2014-10-12
hello,
now i have configured everything and want to create my own personal ubuntu live disc/usb with my current settings and apps.
remastersys is exactly what i am looking for. but i just can't load it anymore.
can anyone help? where can i still get it ? have been looking for 5 hours just can't find it ! thanks for helping

i tried ```
wget -q http://www.remastersys.com/ubuntu/remastersys.gpg.key -O- | sudo apt-key add - 

sudo apt-get update

sudo apt-get install remastersys remastersys-gui 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package remastersys
E: Unable to locate package remastersys-gui






```

---

### Post by Vladlenin5000 on 2014-10-12
*Remastersys* has been discontinued: [http://www.remastersys.com/](http://www.remastersys.com/)

---

### Post by joonwo on 2014-10-12
> **Vladlenin5000 said:**
> *Remastersys* has been discontinued: [http://www.remastersys.com/](http://www.remastersys.com/)

i know.. unfortunately. does anyone know a repository where i still can get it ? or is there anything else out there doing a similar job like remastersys ?
thanks !

---

### Post by Vladlenin5000 on 2014-10-12
AFAIK, *Black Lab Image Creator* is the soon-to-be-released replacement.
[http://system-imaging.blogspot.com.es/](http://system-imaging.blogspot.com.es/)

Obs.: This is not a recommendation, endorsement, whatever. I never test it. The information is provided "as is", as found following links from past discussions in this forum.

---

### Post by yancek on 2014-10-12
You missed a step, see step 5 at the link below.  This is specifically for Ubuntu 12.04.  You haven't indicated which Ubuntu you are using.

[http://www.distrogeeks.com/install-remastersys-ubuntu/](http://www.distrogeeks.com/install-remastersys-ubuntu/)

---

### Post by tea for one on 2014-10-13
> **joonwo said:**
> i know.. unfortunately. does anyone know a repository where i still can get it ? or is there anything else out there doing a similar job like remastersys ?
thanks !

Have a look at Systemback

Here is some more info:-

[http://www.unixmen.com/systemback-restore-linux-system-previous-state/](http://www.unixmen.com/systemback-restore-linux-system-previous-state/)

[https://launchpad.net/systemback](https://launchpad.net/systemback)

---

