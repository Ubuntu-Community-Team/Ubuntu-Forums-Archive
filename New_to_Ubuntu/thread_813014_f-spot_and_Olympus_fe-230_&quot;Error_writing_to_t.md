---
title: "f-spot and Olympus fe-230 &quot;Error writing to the port&quot;"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by chchandler on 2008-05-30
I posted this yesterday to the Multimedia section but got no replies, so perhaps that's the wrong place for it.  I've had good luck here in ABT, so let's see...

I connect the camera via the USB cable and f-spot detects it and offers to import my photos. Then it waits and after a bit I get the error message "Error writing to the port."  Now whenever I connect the camera it just waits a bit and give me that error.

A quick search of the forums don't show this - I've looked at my logs and nothing screams at me.

Suggestions?

---

### Post by wolfen69 on 2008-05-30
try gthumb to import photos. works great with my camera. when you first plug in the camera, cancel anything that offers to import for you. then open gthumb.  then go to file>import photos.

```
sudo apt-get install gthumb
```

---

### Post by chchandler on 2008-05-30
Well, I've found with some experimenting that I can delete the checkmark in Removable Drives and Media so nothing launches automatically when I attach a camera.  The media card mounts as a drive, then I use f-spot's Import to get what I want.  Seems to work almost as well.

I'm not going to mark this one solved, but I can work around it.

---

### Post by Sonja on 2008-06-29
Where is this checkmark? In what program and where? I want to try your partial solution.

---

### Post by chchandler on 2008-06-29
System|Preferences|Removable Drives and Media

Uncheck the box to automatically download when a camera is connected.  

HTH...

---

