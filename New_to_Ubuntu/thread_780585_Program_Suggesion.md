---
title: "Program Suggesion"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by hikujk123 on 2008-05-03
I have a video camera with miniDV tapes.  In windows, you can transfer recordings to the computer via windows movie maker using a 1394 port.  What program would you use in ubuntu???

---

### Post by SunnyRabbiera on 2008-05-03
I think kino has something similar to this, but I am unsure

---

### Post by Whiffle on 2008-05-03
Kino or dvgrab (dvgrab is what kino uses) or Cinelerra

[http://www.ibiblio.org/joey/videolinux/ieee-1394firewire-video-capture/](http://www.ibiblio.org/joey/videolinux/ieee-1394firewire-video-capture/)

---

### Post by hikujk123 on 2008-05-03
I installed kino.  How do I use it to do this?

---

### Post by herteljt on 2008-05-03
> **hikujk123 said:**
> I installed kino.  How do I use it to do this?

You'll need to make sure that you have read/write access for /dev/raw1394

Open a terminal and type

sudo chmod a+rw /dev/raw1394

This will enable you to capture video from the camera.  You'll need to go to the capture tab in Kino

---

### Post by Whiffle on 2008-05-03
Might be old, but its a start....

[http://www.kinodv.org/article/archive/13/](http://www.kinodv.org/article/archive/13/)
A tutorial video that demonstrates how to configure Firewire and how to capture from a Firewire DV device in Kino. 
[http://blip.tv/file/get/Ddennedy-KinoScreencastTutorialCapturingDV563.ogg](http://blip.tv/file/get/Ddennedy-KinoScreencastTutorialCapturingDV563.ogg)

---

### Post by hikujk123 on 2008-05-03
I get the following output.

chmod: cannot access `/dev/raw1394': No such file or directory

---

### Post by herteljt on 2008-05-03
Try this to get the dv capture working

sudo modprobe raw1394

sudo chmod a+rw /dev/raw1394

The first line loads the module, the second gives you read/write access.

Look at this article for info on how to setup the modules to load automatically

[http://www.bxlug.be/en/articles/220]("http://www.bxlug.be/en/articles/220")

Hope this helps.

---

