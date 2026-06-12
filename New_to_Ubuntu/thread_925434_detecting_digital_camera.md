---
title: "detecting digital camera"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by bjhome on 2008-09-20
I want to move photos off my digital camera when i plug it in its coming up on the desktop but when i open it the photos are not showing.(they are still on the camera) i would like to use digikam i have it loaded already.is this the better photo program to use?

---

### Post by SunnyRabbiera on 2008-09-20
well not all models of camera work by default, can you tell us about your digicam?

---

### Post by okey666 on 2008-09-20
digikam is I presume for KDE (the k gives it away). I would use fspot. Plug in your camera. Go Applications>>graphics>>f-spot then select your camera as the import source.

---

### Post by bjhome on 2008-09-20
its coming up with an error when transferring im trying to send you the print screen so you can see. how do i do this?

---

### Post by halitech on 2008-09-20
> **bjhome said:**
> I want to move photos off my digital camera when i plug it in its coming up on the desktop but when i open it the photos are not showing.(they are still on the camera) i would like to use digikam i have it loaded already.is this the better photo program to use?

by coming up, do you mean you get an icon on your desktop with the name of your camera?

> **okey666 said:**
> digikam is I presume for KDE (the k gives it away). I would use fspot. Plug in your camera. Go Applications>>graphics>>f-spot then select your camera as the import source.

KDE apps will run fine on Gnome and as they have expressed an opinion they would prefer to use it and already have it loaded, why not give him some steps on using digikam?

OP - we need to know your camera make and model first but then we should be able to get you up and running.

---

### Post by bjhome on 2008-09-20
my camera is a sony dsc-p32. i tried the f spot and it came up  with an error halfway through loading.

---

### Post by vikram on 2008-09-20
> **bjhome said:**
> I want to move photos off my digital camera when i plug it in its coming up on the desktop but when i open it the photos are not showing.(they are still on the camera) i would like to use digikam i have it loaded already.is this the better photo program to use?

Most digital cameras which have a USB interface can be browsed just as a USB drive. Check this before looking at digikam issues.

First check if the camera is mounted. Can you paste the output of the "mount" command before and after you plug in the camera ?

---

### Post by bjhome on 2008-09-20
now im really lost??????????? getting confused??????????

---

### Post by vikram on 2008-09-20
> **bjhome said:**
> my camera is a sony dsc-p32. i tried the f spot and it came up  with an error halfway through loading.

I confirmed that your camera model is supported in digikam - never plugged in a modern camera which wasnt supported :) actually - one of the many reasons why digikam is my favourite applications the other being  the integration with email software with batch compression, batch processing of images and plugins.

---

### Post by vikram on 2008-09-20
> **bjhome said:**
> now im really lost??????????? getting confused??????????

In short this is not a camera or digikam issue.

When the camerag is plugged in  type the following command in the terminal and paste the command

```
mount 
```

and paste the output of the same command after removing the camera and waiting for 1 minute

---

### Post by bjhome on 2008-09-20
so where do i go from here. keep it simple instructions please.

---

### Post by oldos2er on 2008-09-20
> **bjhome said:**
> my camera is a sony dsc-p32. i tried the f spot and it came up  with an error halfway through loading.

 What is the error message?

---

### Post by bjhome on 2008-09-20
Sorry but im still lost , not getting anywhere with this.I plugged camera in went to digikam and loaded the make , model of the camera. i tried to copy paste mount in the camera mount path.but i couldnt do it.

---

### Post by bjhome on 2008-09-20
How do i print screen it to you.

---

### Post by vikram on 2008-09-20
First open the terminal

Menu: Applications > Accessories > Terminal

type the following commands in the window and paste the outputs of following commands
```
 lsmod | grep usb
```
```
 mount 
```

Type the mount command before and after pluging in the camera
```

```

If you are not sure about using the terminal see this link
[https://help.ubuntu.com/community/GnomeTerminal](https://help.ubuntu.com/community/GnomeTerminal)

---

### Post by bjhome on 2008-09-20
its still not working. saying command not found.

---

### Post by bjhome on 2008-09-20
how come it doesnt automatically pick up the camera.

---

### Post by halitech on 2008-09-20
> **bjhome said:**
> its still not working. saying command not found.

which command not found?

---

### Post by bjhome on 2008-09-20
Can you please give me step by step instructions. right from when to plug the camera in and turn it on. I typed the code in and pasted the above commands but nothing happened. right now i'm all over the place i went to digikam and loaded the camera make and model. i think i need to start again from the beginning.step  by step would be good. sorry for not understanding.

---

### Post by halitech on 2008-09-20
we are *trying* to help you but without you giving us the information back that we are asking for, we can't help you so you need to help us to help yourself.

something should happen, either an error code or a message of some kind. Either that or your system is completely farked and you need to start over but again, without you posting back the information that we have requested, we are just going to go around in circles with you saying its not working and us asking you for information.

---

### Post by bjhome on 2008-09-20
its a bit hard when i dont understand what you are talking about. thats why im asking for step by step instructions. Please......so i can start again by following them. i dont know if i have been doing it correctly.everybody

---

### Post by halitech on 2008-09-21
> **vikram said:**
> In short this is not a camera or digikam issue.

When the camerag is plugged in  type the following command in the terminal and paste the command

```
mount 
```

and paste the output of the same command after removing the camera and waiting for 1 minute

> **vikram said:**
> First open the terminal

Menu: Applications > Accessories > Terminal

type the following commands in the window and paste the outputs of following commands
```
 lsmod | grep usb
```
```
 mount 
```

Type the mount command before and after pluging in the camera
```
mount
```

If you are not sure about using the terminal see this link
[https://help.ubuntu.com/community/GnomeTerminal](https://help.ubuntu.com/community/GnomeTerminal)

> **bjhome said:**
> its a bit hard when i dont understand what you are talking about. thats why im asking for step by step instructions. Please......so i can start again by following them. i dont know if i have been doing it correctly.everybody

Vikram has given you the steps to try and resolve this issue already twice so please follow them and post the output here for us so we can help you

---

