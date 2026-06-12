---
title: "turn external hard drive off on shutdown"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by Falc7 on 2008-05-20
When using ubuntu with my external hard drive attached, when i go to turn off the computer, my external hard drive will still be left on (the light is glowing and i can hear the disks spinning), i believe this is bad for the disk. Can i add some command somewhere so that ubuntu will turn off the external hard disk as well?

---

### Post by pedro_orange on 2008-05-20
I doubt that your PC will be able to control that external drive's power source.
Can you not just press the Off button? :P

---

### Post by Falc7 on 2008-05-20
It dosen't have an off button, i am at the moment pulling the power cord out, and i hear the disks stopping, but i don't imaging that can be very good for it can it?

I had an external hard drive before and it broke, i thought this could have caused it. Under vista the HD turns itself off with the computer, i got a new HD under warranty anyway.

---

### Post by linux phreak on 2008-05-20
You must "unmount" the disk by right clicking it in nautilus before removing the external HD.

---

### Post by pedro_orange on 2008-05-20
Hmmm...

Well it's actually better for drives to be left on. Believe it or not!
Adds to their longevity.

I'm sorry but I don't know how to turn external drives off from the command line.
You can unmount it; but that won't turn it off.
I find it strange you don't have a power button on your drive.

---

### Post by linux phreak on 2008-05-20
I think it won't turn off until you unplug the cable.That is when the power light goes off.Please correct me if i am wrong.

---

### Post by mrthundercleese4 on 2008-05-20
pull the usb cord out after you shut down and that should do it. most of the time externals hooked to usb shut down when they are no longer getting a signal from the usb. Still it sounds like more of an issure with the external hd enclosure or your usb on your mother board or card.

---

### Post by Falc7 on 2008-05-20
I see, and there is no line i can add somewhere in the shutdown file that will auto unmount at shutdown, or does ubuntu do this already?
thanks for your help

---

### Post by pedro_orange on 2008-05-20
```
umount /mnt/cdrom
```

Will unmount a CDROM drive. So take that as an example, and apply it to your hdd.

Prod dev/hda1 or summit.

---

### Post by Falc7 on 2008-05-20
> **mrthundercleese4 said:**
> pull the usb cord out after you shut down and that should do it. most of the time externals hooked to usb shut down when they are no longer getting a signal from the usb. Still it sounds like more of an issure with the external hd enclosure or your usb on your mother board or card.

I thought so, but it does shut itself off with vista at shutdown, i have a seagate freeagent if it matters

---

### Post by _sAm_ on 2008-05-20
> **Falc7 said:**
> It dosen't have an off button, i am at the moment pulling the power cord out, and i hear the disks stopping, but i don't imaging that can be very good for it can it?

I had an external hard drive before and it broke, I thought this could have caused it. Under vista the HD turns itself off with the computer, I got a new HD under warranty anyway.

I have a "Mybook" 500gig external drive witch do not have a power button, and will not shut off with the pc(this is true both with Vista and Ubuntu). Pulling the power cord bugged me right away, so I bought a "power button", and attached it(they cost very little, and its easy to do) - and it works fine(just as my other external hd witch do have a power button).

---

