---
title: "opengl / nvidia issues ?"
date: 2011-09-18
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by oly on 2011-09-18
is anyone aware of issues with opengl with the latest updates i have nvidia drivers installed but launching guild wars causes unable to initalise opengl and all webgl apps have stopped working in firefox i still have unity which suggest 3d is working.
I have tried re-installing the nvidia drivers and checked that mesa gl is installed so any ideas ?
is this a known issue or one i should reporting, guessing being opengl some one else may have encountered it.

---

### Post by Gnurfos on 2011-09-18
I don't know Guild Wars, but if you're running it with Wine, I had problems too. To solve them, I have to run wine with:
```
LD_LIBRARY_PATH=/usr/lib32/nvidia-current
```I don't know if you're supposed to do this by hand, or if it's a "bug". (and no idea about webgl).

---

### Post by Wise Ferret on 2011-09-18
This seems to affect all 64 bit nvidia users who run 32-bit 3d apps. Reported in bug [#852873]("https://bugs.launchpad.net/nvidia-drivers-ubuntu/+bug/852873").

Thank you very much for the workaround!

---

### Post by vhaarr on 2011-09-18
Thanks a lot for the workaround!

---

### Post by flipper T on 2011-09-18
how do i "run wine" with the code ?

just enter the code into a terminal then run wine ?

that seems to have no effect for me, still same errors encountered.

---

### Post by genefy on 2011-09-18
Post #3 has the answer in the link in coincidentally enough. Post #3.. To make it easy. it's LD_LIBRARY_PATH=/usr/lib32/nvidia-current your_program_name_and_path..

So for Starcraft for instance it would be.

LD_LIBRARY_PATH=/usr/lib32/nvidia-current '/home/username/.wine/drive_c/Program Files/StarCraft II/StarCraft II.exe'

Hey, anyone know how I can put this in a shell script? I've been trying but can't seem to get it right.

---

### Post by flipper T on 2011-09-18
followed your instructions and got:

```
fixme:win:EnumDisplayDevicesW ((null),0,0x32f8bc,0x00000000), stub!
```

---

### Post by genefy on 2011-09-18
I don't exactlly know the answer to that one. There are alot of posts on it.

---

### Post by sparker256 on 2011-09-18
> **genefy said:**
> Post #3 has the answer in the link in coincidentally enough. Post #3.. To make it easy. it's LD_LIBRARY_PATH=/usr/lib32/nvidia-current your_program_name_and_path..

So for Starcraft for instance it would be.

LD_LIBRARY_PATH=/usr/lib32/nvidia-current '/home/username/.wine/drive_c/Program Files/StarCraft II/StarCraft II.exe'

Hey, anyone know how I can put this in a shell script? I've been trying but can't seem to get it right.

I have a working shell but it is in the same folder as the application that I am trying to run.

LD_LIBRARY_PATH=/usr/lib32/nvidia-current ./X-Plane-i686

Bill

---

### Post by genefy on 2011-09-19
Thank you, you helped indirectly, I was putting \'s before spaces, and I put a slash after current, when I shouldn't have for the shell script itself. Thanks alot, and I hope our 64 bit problems get fixed.

---

