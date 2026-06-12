---
title: "Need help with Camorama error message &quot;/dev/video0&quot;"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by OKnotOK on 2008-06-16
I have not been successful in trying to get help with getting my microphone to work with Cheese, so I'm hoping someone might be more interested in helping out with Camorama and hopefully just chuck Cheese altogether. 

I'm running Ubuntu 8.1 on a 64-bit system. The camera is Logitech Quickcam Deluxe (its a lap-top camera, but it clips onto my flat-screen monitor the best)

When I try to start Camorama, it says "Could not connect to video device /dev/video0. However, since the camera (though not audio) works with Cheese, I know the camera is connected & is not defective.

I've already tried searching for a thread about this, but if I found the right info, I was not able to tell. 

Thank you in advance for any help anyone is able to offer.

---

### Post by sdennie on 2008-06-16
My webcam doesn't work with camorama either.  I haven't looked into the issue much because I don't use the webcam but, I believe it's because some webcam drivers don't support V4L but only V4L2 (which I don't think camorama supports).  The reason I think this is the case is because I can start gstreamer-properties and, in the Video tab, the "Test" button works fine for the webcam when I set it V4L2 and doesn't work when it's set to V4L.

---

### Post by OKnotOK on 2008-06-16
> **vor said:**
> My webcam doesn't work with camorama either.  I haven't looked into the issue much because I don't use the webcam but, I believe it's because some webcam drivers don't support V4L but only V4L2 (which I don't think camorama supports).  The reason I think this is the case is because I can start gstreamer-properties and, in the Video tab, the "Test" button works fine for the webcam when I set it V4L2 and doesn't work when it's set to V4L.

Can you use your webcam with ANY program? I don't really care what program I end up using, so long as it works.

---

### Post by sdennie on 2008-06-16
Yes, I can see it with Ekiga and Cheese and I would imagine any other app that allows me to explicitly set V4L2 instead of V4L (which I don't think camorama will let me).

---

### Post by OKnotOK on 2008-06-16
> **vor said:**
> Yes, I can see it with Ekiga and Cheese and I would imagine any other app that allows me to explicitly set V4L2 instead of V4L (which I don't think camorama will let me).

Cheese won't do audio... I've been trying to get help with getting my mic to work, but no one seems to be able to. 

Isn't Ekiga like a phone program? I'm looking to record & playback videos... not chat or make calls.

---

### Post by OKnotOK on 2008-06-17
*Bump*

Help?

Anyone?

PLEASE?

---

### Post by mybunche on 2008-06-29
I'm still running 6.10 and I have the same error message. ie could not connect to video device /dev/video0. I know my webcam works because it's fine with Ekiga, even though I haven't setup Ekiga. Camorama gives that error message because my webcam is /dev/video1. My TV tuner card is /dev/video0. 

You make it work my typing in terminal
$ camorama -d=/dev/video1

This will start Camorama and you should see video. When you close ther terminal window it also closes Camorama. You need to enter this command every time you want to use Camorama. I don't know how to make it permanent.

---

### Post by mybunche on 2008-06-29
Following on to my above reply to Camorama error 'could not connect to video device /dev/video0'
If your webcam works when typing:
$ camorama -d/dev/video1
in the terminal, to make the change permanent, you can alter the command used to start the application.

1. Right click on Ubuntu logo at top left and select Edit Menus.

2. Navigate to the Camorama application under Applications – Graphics.

3.Right click, select Properties.

4.In the command field type: camorama -d=/dev/video1
Click close. When Camorama is now choosen, it will run this command.

---

