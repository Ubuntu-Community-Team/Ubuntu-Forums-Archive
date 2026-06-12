---
title: "My webcam doesn't work - could it possibly be because /dev/video0 has nothing in it?"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by gottabeandrew on 2008-05-08
I have a logitech quickcam sphere mp. Although it works with aMSN and skype, it doesn't work with Easycam2, Camorama or stickam (and other flash applications).

Is this to do with the fact that /dev/video0 (which it keeps referring to) is empty?

---

### Post by sdennie on 2008-05-08
This happens with my webcam as well.  I believe the problem is related to the fact that the webcam only uses Video for Linux 2 whereas applications like camorama are expecting to use Video for Linux.  I'm not sure if there is a workaround for specific apps but, if the app allows you to choose between "v4l2" or "v4l", choose "v4l2".

---

### Post by ebozzz on 2008-05-11
In my situation Camorama will not even launch. Once you click OK after getting the error */dev/video0 is empty*, the app closes. Is there a way edit without launching the app? 

I can get Cheese and Ekiga to work. My hope was to also get a look at Camorama to make a determination as to which was best for my needs. Thanks....

---

