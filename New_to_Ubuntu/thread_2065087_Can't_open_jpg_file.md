---
title: "Can't open jpg file"
date: 2012-10-01
forum: New to Ubuntu
---

### Post by kaushalsharma on 2012-10-01
Hello,

I have a similar problem.
When I type the command on the terminal

>**file Photo0024.jpg**    ;It gives the following output
  Photo0024.jpg: data

And when I open it using Image Viewer in ubuntu, It displays the following message:

**Error interpreting JPEG image file (Not a JPEG file: starts with 0x50 0x83)**

Similarly for another image, Image viewer displays the following message:

**Error interpreting JPEG image file (Not a JPEG file: starts with 0x0e 0xc1)**

How can I see these images?

---

### Post by sffvba[e0rt on 2012-10-01
*Post moved to **own** thread.*


404

---

### Post by Wim Sturkenboom on 2012-10-01
Your files seem to be corrupted. Can you view them on another system (which I doubt)?

---

### Post by audiomick on 2012-10-01
Try opening them with GIMP. You might have to install it first, I think. It should be available through the software centre.

I don't know for sure that this will work, but I have a vague memory of exactly that problem, and I think the solution was to open the images with something other (more sophisticated? ) than the image viewer.

---

### Post by androssofer on 2012-10-01
> **kaushalsharma said:**
> Hello,

I have a similar problem.
When I type the command on the terminal

How can I see these images?

can you copy the file, then rename the copies to Photo0024.png? or Photo0024.gif?

see if it opens those formats?

---

### Post by zombifier25 on 2012-10-01
> **androssofer said:**
> can you copy the file, then rename the copies to Photo0024.png? or Photo0024.gif?

see if it opens those formats?

I doubt it will work though. The command file intepreted it as "data", whcih means either the jpeg is corrupted, or it's not a jpeg at all.


OP, it would be nice if you tell us where you got it.

---

### Post by vasa1 on 2012-10-01
> **zombifier25 said:**
> ...
OP, it would be nice if you tell us where you got it.
^^^
In as much detail as possible :)

The thread from which this thread was spawned mentioned someone saving .html files as .jpg and then trying to open them in image viewers.

... though even that wouldn't give the error OP is seeing. "file" would still report it as an html file.

---

