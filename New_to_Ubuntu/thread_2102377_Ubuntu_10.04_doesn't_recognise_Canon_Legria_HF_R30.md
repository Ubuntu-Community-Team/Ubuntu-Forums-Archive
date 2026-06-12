---
title: "Ubuntu 10.04 doesn't recognise Canon Legria HF R306"
date: 2013-01-07
forum: New to Ubuntu
---

### Post by Gimly_axe on 2013-01-07
Dear all,

I'm relatively new to Ubuntu and have very little experience with the command line.

I have Ubuntu 10.04 (Lucid) and am trying to connect my camera Canon Legria HF R306 to the laptop to download the videos.

The problem is that the camera is connected to the laptop by a usb cable but the computer doesn't see it.

What can I do?

---

### Post by sudodus on 2013-01-07
Did you try with a photo organizer like Shotwell, F-spot or Digikam?

Such programs are good at finding cameras.

By the way, it's a video camera, so I would suggest Shotwell or Digikam.

If you don't have them, install them with ***Synaptic*** or with the terminal window commands

```
sudo apt-get install shotwell
```
```
sudo apt-get install digikam
```

---

### Post by Gimly_axe on 2013-01-07
Dear sudodus,

Thank you for your kind answer. I'm going to try the programs you  suggest now.

However, I've solved the issue with a little lateral thinking: I've put the SD card in the card reader. No need to detect the camera now.

I'm going to tag this thread as [SOLVED] now.

Thank you once more.

---

### Post by 3rdalbum on 2013-01-07
That camera was first released in 2012 as far as I can tell, and your distro was released in 2010; that may well be your problem.

Try using a live CD of Ubuntu 12.04 or better yet, 12.10 and see if it works as expected. If it does, then you need to use a newer version of Ubuntu.

EDIT: Your lateral thinking was a good solution too. I'm glad you can access the files now with little fuss.

---

### Post by sudodus on 2013-01-07
> **3rdalbum said:**
> That camera was first released in 2012 as far as I can tell, and your distro was released in 2010; that may well be your problem.

Try using a live CD of Ubuntu 12.04 or better yet, 12.10 and see if it works as expected. If it does, then you need to use a newer version of Ubuntu.

EDIT: Your lateral thinking was a good solution too. I'm glad you can access the files now with little fuss.
+1

I can only agree :-)

---

