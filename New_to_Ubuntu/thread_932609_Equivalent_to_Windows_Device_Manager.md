---
title: "Equivalent to Windows Device Manager?"
date: 2008-09-28
forum: New to Ubuntu
---

### Post by lavadisco on 2008-09-28
I often forget what makes/models of various hardware is inside my machine, and often used to refer to the Windows Device Manager to refresh myself. Now that I've switched to Ubuntu, how can I do this? For example, right now I'm trying to figure out what webcam I have so that I can make it run in Ubuntu, but I don't know where to go to figure that out.

---

### Post by fooman on 2008-09-28
check in synaptic for gnome-device-manager, or in a terminal:

```
sudo apt-get install gnome-device-manager
```

---

### Post by lavadisco on 2008-09-28
Thank you!

However, my webcam isn't even listed in the device manager!

---

### Post by nowshining on 2008-09-28
have u tried looking on the webcam itself for a model number, etc..??

That seems more logical than having to go ummmm... thru the computer...

Do you by any chance have any sort of memory loss??

---

### Post by lavadisco on 2008-09-28
> **nowshining said:**
> have u tried looking on the webcam itself for a model number, etc..??

That seems more logical than having to go ummmm... thru the computer...

Do you by any chance have any sort of memory loss??

The webcam is embedded in the computer and only the lens is exposed, so there are no external markings on it.

Quick! Tell me EXACTLY what brand/model of (internal) bluetooth card do you have, right off the top of your head?? See, I didn't think so.

---

### Post by Lod on 2008-09-28
> **lavadisco said:**
> 
Quick! Tell me EXACTLY what brand/model of (internal) bluetooth card do you have, right off the top of your head?? See, I didn't think so.I can tell you exactly what kind of bluetooth card I have, none. It's just too easy.

Have you tried the command 'lspci' at the command line?

---

### Post by lykwydchykyn on 2008-09-28
The lsusb command will probably show you what it is.  There's probably some graphical equivalent to it, but I don't know what it would be.

---

### Post by nowshining on 2008-09-28
> **lavadisco said:**
> The webcam is embedded in the computer and only the lens is exposed, so there are no external markings on it.

Quick! Tell me EXACTLY what brand/model of (internal) bluetooth card do you have, right off the top of your head?? See, I didn't think so.

ur correct, i can't, because my  computer doesn't have one....

But, My PDa is a m125 and again without looking - the ol' now dead SD card i have was an Sandisk card with 64mb memory, my new one is a re-branded toshiba kingston card...


However what i meant really is why would u need to keep looking thru the device manager?? I mean yeah if ummm you were trying to get something to work, etc..  or for a DVD/CD/ROM, drive yes,  but not periodocally tho...  and by that i mean not like every other second...

---

