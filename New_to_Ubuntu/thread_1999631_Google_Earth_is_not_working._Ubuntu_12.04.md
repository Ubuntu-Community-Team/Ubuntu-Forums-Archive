---
title: "Google Earth is not working. Ubuntu 12.04"
date: 2012-06-08
forum: New to Ubuntu
---

### Post by livesourav on 2012-06-08
Hi guys, I dont knw if this is the right thread to post my problem, but i too have an issue with google earth that i am trying to solve. Any help would be much appreciated. 

The problem is when i try to open google earth by clicking on the it or through the terminal it just shows the initializing screen saying google earth and closes. 

This is the crashlog :
```
Major Version 6
Minor Version 2
Build Number 0002
Build Date Apr 14 2012
Build Time 01:09:37
OS Type 3
OS Major Version 3
OS Minor Version 2
OS Build Version 0
OS Patch Version 0
Crash Signal 11
Crash Time 1339168216
Up Time 0.892355

Stacktrace from glibc:
./libgoogleearth_free.so(+0xc645b)[0xb775445b]
./libgoogleearth_free.so(+0xc66a3)[0xb77546a3]
[0xb77ca400]
```

And this is what i got from the terminal after typing google-earth:

```
dexter@mca-linuxcore:~$ google-earth
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Google Earth has caught signal 11.



We apologize for the inconvenience, but Google Earth has crashed.
```

---

### Post by oldos2er on 2012-06-08
Post moved to its own thread.

---

### Post by Curtis6767 on 2012-06-08
Look this over. If you've already done some or all of these steps, then you might want to completely uninstall and start over.

[https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth)

Edit: Oh, and did you use Gdebi to unpack the google earth deb file? if not then if you do have to uninstall and start over, download Gdebi and then when you get back to the deb file then right click and select Gdebi. 

Hope this helps.

---

### Post by Derek Karpinski on 2012-06-08
> **Curtis6767 said:**
> Look this over. If you've already done some or all of these steps, then you might want to completely uninstall and start over.

[https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth)

Edit: Oh, and did you use Gdebi to unpack the google earth deb file? if not then if you do have to uninstall and start over, download Gdebi and then when you get back to the deb file then right click and select Gdebi. 

Hope this helps.

Google earth installed fine for me by double clicking the downloaded .deb and proceeding with the software center.

---

### Post by Corvair on 2012-06-10
Thank you Curtiss6767. 
finaly installed Google Earth on 12.04

---

### Post by reggiehg on 2012-12-02
Hi,

I'm getting the same results are Corvair:

crashlog:

```
Major Version 7
Minor Version 0
Build Number 0001
Build Date Oct 29 2012
Build Time 19:13:39
OS Type 3
OS Major Version 3
OS Minor Version 2
OS Build Version 0
OS Patch Version 0
Crash Signal 11
Crash Time 1354497532
Up Time 1.64052

Stacktrace from glibc:
./libgoogleearth_free.so(+0x1e9cfb)[0xb759bcfb]
./libgoogleearth_free.so(+0x1e9f43)[0xb759bf43]
[0xb773c400]
```& from the terminal:

```
tank@tank:~/Downloads$ google-earth
Google Earth has caught signal 11.



We apologize for the inconvenience, but Google Earth has crashed.
 This is a bug in the program, and should never happen under normal
 circumstances. A bug report and debugging data have been written
 to this text file:

    /home/tank/.googleearth/crashlogs/crashlog-50bbffce.txt

Please include this file if you submit a bug report to Google.
tank@tank:~/Downloads$ 
```I tried both with gdebi & with usc, following the uninstall instructions each time.

lsb-core was previously installed during my first Google Earth install using

[http://www.liberiangeek.net/2012/04/install-google-earth-in-ubuntu-12-04-precise-pangolin/](http://www.liberiangeek.net/2012/04/install-google-earth-in-ubuntu-12-04-precise-pangolin/)

Any other options? Thanks in advance.

Reggie

---

