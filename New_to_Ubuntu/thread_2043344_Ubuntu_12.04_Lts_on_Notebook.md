---
title: "Ubuntu 12.04 Lts on Notebook"
date: 2012-08-16
forum: New to Ubuntu
---

### Post by dep0 on 2012-08-16
Hi, i have a hp notebook with intel atom N2600 @1.6GHz. Is it possible for me to install ubuntu 12.04 Lts and run it properly?

---

### Post by ajgreeny on 2012-08-16
On that specification notebook you may do better with Xubuntu or even Lubuntu, both of which run a lighter, less resource hungry desktop environment.

Try Ubuntu 12.04 to see what yu think, but I suspect it may run a bit slower than you want; unity needs quite a lot of resources in my experience, however, you may find it is just as you want it.

---

### Post by NikTh on 2012-08-16
> **dep0 said:**
> Hi, i have a hp notebook with intel atom N2600 @1.6GHz. Is it possible for me to install ubuntu 12.04 Lts and run it properly?

Hi , 
you can always test it before installing. 

Grab the iso from here --> [http://cdimage.ubuntu.com/releases/12.04/release/](http://cdimage.ubuntu.com/releases/12.04/release/)

burn it to a Usb or CD and boot from. 

Click "Try Ubuntu" and test if Ubuntu runs smoothly with your hardware. 

Check , 
1)internal webcam 
from terminal(ctrl+alt+t) do 
```
gstreamer-properties
``` and click "Video" > "Test" on Default Input. 

2) Check wireless (is it work ?) 

3) Check Graphics . Is your card recognized ?

4) Install flash player and try to see a video on youtube. 
```
sudo apt-get install adobe-flashplugin
``` 

5) Close the lid and try to resume from suspend. Is it resume properly ? 

In brief : Take your own Ubuntu tour before decide to install it. If meet your needs ,then install it. 

I think this is the better way to check-test Ubuntu . If works properly on "Try" it will work properly when installed.
Thanks

---

