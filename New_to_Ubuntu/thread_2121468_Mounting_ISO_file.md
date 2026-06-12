---
title: "Mounting ISO file"
date: 2013-03-02
forum: New to Ubuntu
---

### Post by echo775 on 2013-03-02
I recently switched to ubuntu to try it out and so far so good. i have run into a wall though. Im trying to mount an iso image to a virtual drive in order to play the windows game on ubuntu.(rome total war) i have wine and g mount iso and have done similar things on windows. So when i try to mount an image with g mount the program says the file is read only. on a forum somewhere (here or somewhere else) i read that iso files are accually read only files and the warning is pointless. so when i mount the iso for CD1 i can get the install to start and work fine until disk 2 is required. when i try to unmount the image gmount iso says the image isnt mounted (nothing available to unmount in the third info entry box). I checked my home folded and found that the image was mounted and i was able to navigate its contents, thats how i get the install started. When i try to unmount the computer tells me the device is busy and it wont unmount. when i try to mount disc 2 to the same folder i created for the game it says the file is not empty. I tried to learn a few of the commands to mount and unmount the iso that way but everywhere i go all the info is vague. PLEASE HELP ME

---

### Post by carl4926 on 2013-03-02
Install

AcetoneISO

then it's easy

---

### Post by echo775 on 2013-03-02
ty tryin now, hopefully works, all the frustration

---

### Post by echo775 on 2013-03-02
ok now acetoneiso is telling me my iso file is not an iso file therefore it cannot be mounted

---

### Post by echo775 on 2013-03-02
AcetoneISO doesnt recognize an iso file as an iso file, tells me to use image converter to extract files n such, did that, no luck Plz helps again. Im so lost

---

### Post by ayiiba on 2013-03-02
I have videos image files i want play this on ubuntu
what software in ubuntu can i use to play

---

### Post by carl4926 on 2013-03-02
> **echo775 said:**
> ok now acetoneiso is telling me my iso file is not an iso file therefore it cannot be mounted

So is it or isn't it
How was it made?

---

### Post by matt_symes on 2013-03-02
Hi

> **echo775 said:**
> ok now acetoneiso is telling me my iso file is not an iso file therefore it cannot be mounted

To paraphrase carl, so is it a valid ISO ?

Open a terminal and type

```
file <path_to_iso>
```

to see what Ubuntu thinks of it.

Here's and example for you.

```
matthew-S206:/home/matthew/storage/my_isos % file precise-desktop-amd64.iso 
precise-desktop-amd64.iso: # ISO 9660 CD-ROM filesystem data 'Ubuntu 12.04 LTS amd64          ' (bootable)
matthew-S206:/home/matthew/storage/my_isos % 

```

A bootable CD-ROM ISO.

Kind regards

---

### Post by matt_symes on 2013-03-02
**Threads merged.**

Please do not create multiple threads about the same subject.

It dilutes community effort to help you and to help others.

---

