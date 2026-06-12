---
title: "Unable to mount Nikon D40x under Hardy Heron"
date: 2008-10-07
forum: New to Ubuntu
---

### Post by nicolas.boullosa on 2008-10-07
Before today, I never had a problem connecting the camera and downloading the photos.

Last time I used the camera with the computer, I think I disconnected the camera without unmounting the volume first.

I did a change in the computer: I downloaded Picasa 3.

I tried to connect the camera to a Mac and I also was unable to do it.

Whatever it is, it seems it happens right now, but before in worked properly under 8.04.

Strange. 

- I don't know how to manually mount the camera.
- Also, doing "lsusb" the device does not appear in the list.
- I'm using a Vaio SZ laptop (I've never had a problem with the camera before).

As a sollution right now, I only see buying a Card Reader or similar.

Does anybody know how to address this sort of issues?

Thanks in advance,

---

### Post by clive littlewood on 2008-10-07
Hi

Try installing Digicam from the repos. and using the detect function.

Digicam has detected every camera i have connected to it including Nikon.

Hope this helps

cl

---

### Post by nicolas.boullosa on 2008-10-07
Hello,

Thank you for your quick answer:

- It seems Digicam auto-detect does not work in this case.
- If I Add the camera manually (Nikon D40x is in the list of the App), and then try to connect trhough PTP, changing the USB option in the menu of the camera from card to PTP mode, it doesn't work either.

Weird. It seems it must be related either:

- The last time I disconnected the camera without unmounting it first.
- The Picasa 3 install.

Thank you, though,

---

### Post by nicolas.boullosa on 2008-11-25
Question solved after I upgraded to 8.10: now the camera mounts and I'm able to use any software (Picasa 3, etc.) in order to get the photos from the camera.

Thank you,

---

