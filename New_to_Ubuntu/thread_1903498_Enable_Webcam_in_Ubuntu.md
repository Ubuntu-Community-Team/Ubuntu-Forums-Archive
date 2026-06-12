---
title: "Enable Webcam in Ubuntu"
date: 2012-01-02
forum: New to Ubuntu
---

### Post by ClarkRobbins on 2012-01-02
Hello,

I'm very new to Ubuntu, and have desperately been trying to get my webcam to work.  I have a Gear Head WC735I webcam, and I am on Ubuntu 11.10.  I plugged it in, and it is working with Cheese, but will not work at [www.testmycam.com]("http://www.testmycam.com") or any similar service.  It is not recognized when I enter "lsusb".

Any help would be appreciated.  Thanks.

---

### Post by lechien73 on 2012-01-02
Hello & welcome to Ubuntu and the forums,

If the webcam works in Cheese, then it sounds like it is being detected by the computer.

If you try:

```
sudo lsusb -v
```

The camera should be listed, you can try:

```
sudo lsusb -v | grep Camera
sudo lsusb -v | grep Webcam

```
to filter the output.

With regard to testmycam.com - are you able to click the "Allow" box in the Flash applet? It sounds more like a Flash problem than an issue with the webcam.

---

### Post by Locke_99GS on 2012-01-02
It'd probably be best to be case insensitive when filtering lsusb:
```
sudo lsusb|grep -iE 'camera|webcam'
```

I'll agree, though, that is sounds like the problem is with Flash configuration.

---

### Post by ClarkRobbins on 2012-01-02
> **lechien73 said:**
> Hello & welcome to Ubuntu and the forums,

If the webcam works in Cheese, then it sounds like it is being detected by the computer.

If you try:

```
sudo lsusb -v
```The camera should be listed, you can try:

```
sudo lsusb -v | grep Camera
sudo lsusb -v | grep Webcam

```to filter the output.

With regard to testmycam.com - are you able to click the "Allow" box in the Flash applet? It sounds more like a Flash problem than an issue with the webcam.


Thanks.  Here is what I got from the filtered results:

iProduct                2 Vimicro USB Camera (Altair)
      iFunction               2 Vimicro USB Camera (Altair)
      iInterface              2 Vimicro USB Camera (Altair)
        wTerminalType      0x0201 Camera Sensor

I am not able to click "Allow" when visiting the website.  It states that there is no camera detected.

---

### Post by lechien73 on 2012-01-02
Ok, so your webcam is definitely being detected by Ubuntu. The WC735I shows up as a Vimicro USB Camera (Altair).

So, this is probably an issue with Flash. You do need an up-to-date version for webcam and microphone capture to work "properly" (I use the word "properly" with serious reservations :))

If you visit [http://www.adobe.com/software/flash/about/](http://www.adobe.com/software/flash/about/), what version of Flash does it say is installed?

---

### Post by ClarkRobbins on 2012-01-02
> **lechien73 said:**
> Ok, so your webcam is definitely being detected by Ubuntu. The WC735I shows up as a Vimicro USB Camera (Altair).

So, this is probably an issue with Flash. You do need an up-to-date version for webcam and microphone capture to work "properly" (I use the word "properly" with serious reservations :))

If you visit [http://www.adobe.com/software/flash/about/](http://www.adobe.com/software/flash/about/), what version of Flash does it say is installed?

Thanks.  It says that I have version 11,1,102,55 installed.

---

### Post by lechien73 on 2012-01-02
> **ClarkRobbins said:**
> Thanks.  It says that I have version 11,1,102,55 installed.

Well...that's pretty recent ;)

Maybe this site might help you: [http://www.swift-tools.net/Flashcam/](http://www.swift-tools.net/Flashcam/) the package they have available for download creates a virtual device for Flash to use. Since your cam is detected and working in Ubuntu, this might fix the problem.

Please let us know how it goes :)

---

