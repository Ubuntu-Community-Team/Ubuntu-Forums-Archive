---
title: "Getting the Guitar Hero X-plorer to work in Edgy for Frets on Fire"
date: 2007-04-07
forum: Outdated Tutorials &amp; Tips
---

### Post by robot- on 2007-04-07
Here's how you can get the RedOctane Guitar Hero II X-plorer guitar for the XBOX 360 to work in Edgy.

Follow the fantastic guide here : [http://ubuntuforums.org/showthread.php?t=318382&highlight=xbox360 ]("http://ubuntuforums.org/showthread.php?t=318382&highlight=xbox360")

but before you hit "sudo make" to build your drivers, gedit xpad.c and add in this line right to the bottom of the list of device IDs.
```

{ 0x1430, 0x4748, 0, "RedOctane Guitar Hero X-plorer", 1},
```

follow the rest of the instructions carefully and have fun! I've attached the modified [xpad.c]("http://ubuntuforums.org/attachment.php?attachmentid=29151&d=1175921877") file to this post incase you need it.

---

### Post by robot- on 2007-04-07
Here's how you can get the RedOctane Guitar Hero II X-plorer guitar for the XBOX 360 to work in Edgy.

Follow the fantastic guide here : [http://ubuntuforums.org/showthread.php?t=318382&highlight=xbox360 ]("http://ubuntuforums.org/showthread.php?t=318382&highlight=xbox360")

but before you hit "sudo make" to build your drivers, gedit xpad.c and add in this line right to the bottom of the list of device IDs.

```
{ 0x1430, 0x4748, 0, "RedOctane Guitar Hero X-plorer", 1},
```

follow the rest of the instructions carefully and have fun!

---

### Post by s5demigh on 2007-05-20
I'm sorry to ask but how do I get it to work in Ubuntu Studio 7.04?

---

