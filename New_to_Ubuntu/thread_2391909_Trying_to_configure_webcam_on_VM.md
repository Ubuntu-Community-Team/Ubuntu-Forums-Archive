---
title: "Trying to configure webcam on VM"
date: 2018-05-14
forum: New to Ubuntu
---

### Post by tesch on 2018-05-14
Hello everyone,

I'm trying to make my webcam work on linux via VM.
I've check some tutorials on how to make VM to detect your integrated camera, but cheese doesn't detect any..
When i do```
 lsusb
``` i get :
```
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub 
Bus 001 Device 002: ID 80ee:0021 VirtualBox USB Tablet 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

I think that my camera should be the second result but how can I tell linux that this is my camera ?

Thanks for your help !

---

### Post by TheFu on 2018-05-15
Inside the hypervisor, you have to pass the USB device through to the VM for exclusive use.  The hostOS cannot have access to it.
Doing it via virt-manager is pretty easy.  I suspect other VM GUI tools have a way to do this as well.

---

### Post by tesch on 2018-05-16
This is actually what I've done (I think) :
But linux still doesn't detect it, maybe I've some manipulation to do that I don't know..[IMG]https://imageshack.com/a/img921/2431/RgvYZ8.png[/IMG]

---

### Post by TheFu on 2018-05-16
I didn't think USB v1.1 was fast enough for webcams?

---

### Post by tesch on 2018-05-17
I've tryed them all actually and none of them is working, the camera is detected by VM but it still doesn't working..

[IMG]https://imageshack.com/i/pnBwxZhAp[/IMG]

It worked strangly yesterday, the webcam wasn't detected as a webcam but as a USB device. And when I started the VM the webcam was detected by cheese but it was all black.. And then the VM just crashed. I did it several time but it was the same everytime. I tryed today to do it again, but it wasn't the case and it just back to the previous problem

---

### Post by TheFu on 2018-05-17
Guest additions current?
Is v4l2 loaded?
Do any other USB devices passthrough?

Black from any video usually means the driver settings are off.

Don't forget that any changes to the VM settings requires a VM restart, at minimum.

Have you tried other management programs besides cheese?  

BTW, I've never used vbox on a Linux host and stopped using it completely around 2012-ish due to stability problems.

---

### Post by tesch on 2018-05-17
I tryed with another user and it doesn't worked (if this is what you meant)
Yes I just download it, but it doesn't chage anything..
So I can actually select my webcam :

[IMG]https://imageshack.com/i/pmPyP9fCp[/IMG]
So I tryed to select it and I get this error :
[IMG]https://imageshack.com/i/plHKRBMup[/IMG]
I've seen on Internet that I should delete something on my registers but I don't have the one they talk about..


Then I tryed with an USB key and this time I get this error :
[IMG]https://imageshack.com/i/pl79xdK8p[/IMG]

Yes I've also tried fswebcam, which light the led of my camera but then I've the error : 
Timed ou waiting for frame !
No frames captured.

Yeah i see that now.. I'm kind of regretting to use VM..

I've also one strange thing is that my camera seems to be detectded but there is some kind of a free space that I can select :
[IMG]https://imageshack.com/i/po1iiYBfp[/IMG]

---

