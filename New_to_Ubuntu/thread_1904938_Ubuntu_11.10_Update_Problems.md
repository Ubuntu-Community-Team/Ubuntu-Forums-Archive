---
title: "Ubuntu 11.10 Update Problems"
date: 2012-01-05
forum: New to Ubuntu
---

### Post by hockeykid1022 on 2012-01-05
So I upgraded to Ubuntu 11.10 when it was first released, but encountered I few problems when it was installed. I run Ubuntu off of VirtuaBox or a virtual machine, but I don;'t think that is the problem because Ubuntu 11.04 worked perfectly on it.

Anyways, I've been trying to figure out these problems since the new version came out.

Problem #1: I click the Software Center to open it up. The icon blinks on the dock, but no window pops up.

Problem #2: I get a message saying Ubuntu couldn't receive some updates. Here's a picture of the error message when I click the red icon with a minus symbol in it.

[IMG]http://i1209.photobucket.com/albums/cc381/hockeykid1022/Ubuntu11.png[/IMG]

Please help me and tell me what I need to do to fix this!

Thanks in advance!

- hockeykid1022

---

### Post by spacecheck on 2012-01-05
So go into /etc/apt/sources.list.d/ and look to see what is written on line one of the file akirad.lis(I cannot see the rest of the filename).

Good luck!

---

### Post by hockeykid1022 on 2012-01-05
> **spacecheck said:**
> So go into /etc/apt/sources.list.d/ and look to see what is written on line one of the file akirad.lis(I cannot see the rest of the filename).

Good luck!
How do I do that?

---

### Post by 2F4U on 2012-01-06
sudo gedit /etc/apt/sources.list

---

### Post by spacecheck on 2012-01-06
> **2F4U said:**
> sudo gedit /etc/apt/sources.list

Actually, this error message doesn't point to /etc/apt/sources.list
Instead it points to a subfolder or file beginning with the name "akirad.lis " in /etc/apt/sources.list.d/

---

### Post by hockeykid1022 on 2012-01-07
> **spacecheck said:**
> Actually, this error message doesn't point to /etc/apt/sources.list
Instead it points to a subfolder or file beginning with the name "akirad.lis " in /etc/apt/sources.list.d/
So how do I get to it?

---

### Post by spacecheck on 2012-01-09
> **hockeykid1022 said:**
> So how do I get to it?

Why not use Nautilus, the file manager, to open up the folders etc, apt, and sources.list.d, to see if there is a file (or additional folder, since the entire path was cut off in your screenshot) called "akirad.lis*". You may have to check "Show hidden files" to be able to see them, though.

You would also probably profit from reviewing this thread:

[http://ubuntuforums.org/showthread.php?t=1703618](http://ubuntuforums.org/showthread.php?t=1703618)

Have fun!

---

