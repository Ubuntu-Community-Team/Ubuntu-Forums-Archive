---
title: "Trouble mounting DVD drive, HELP!"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by navyjosh on 2008-10-26
just bought a new asus g50 series laptop and installed ubuntu 8.10 and i can't get my dvd drive to work.  It won't even open when i press the open button.  where do i start?  thanks.

---

### Post by cariboo on 2008-10-26
Open a Applications==>Accessories-->Terminal and type:

```
sudo eject
```

Jim

---

### Post by navyjosh on 2008-10-26
tried that, nothing happened =(.  no error message, or output at all.

---

### Post by doas777 on 2008-10-26
I usually use :

```
sudo mount /dev/scd0 /media/cdrom0 
```

and 

```
sudo umount /media/cdrom0
```

good luck,
Franklin

---

### Post by navyjosh on 2008-10-26
after using:
```
sudo mount /dev/scd0 /media/cdrom0
```

i got this error message
```
mount: No medium found

```

---

### Post by navyjosh on 2008-10-27
update:

now it recognizes my dvd rom, and it will display the title of my cd underneath the icon, however i'm having trouble getting it to read the dvd or cd.

---

### Post by doas777 on 2008-10-28
I think you may be looking at a drive failure. you may wanna do an RMA, but if it came OEM built with ubuntu, put in a support call first.

---

### Post by BoricuaTEK02 on 2009-01-23
> **navyjosh said:**
> update:

now it recognizes my dvd rom, and it will display the title of my cd underneath the icon, however i'm having trouble getting it to read the dvd or cd.

Hey, Navyjosh. I have a G50 as well. Shutdown your computer, go into your Bios Setup Utility (Press F2 on the Asus Flaming logo). Go the the "Advanced" tab > SATA > and use "Compatible".

If you want to boot Vista, you will need to put the SATA setting in bios back to "Enhanced". 

That's the little work-around I have figured out on my Asus G50VM-X1. Let me know if that works!

If it still doesn't work, check to see if you've downloaded "regioncode" in the Synaptics Package Manager.

If is still doesn't work, check this last thing out...

[http://lifehacker.com/350015/enable-dvd-playback-in-ubuntu-in-two-commands]("http://lifehacker.com/350015/enable-dvd-playback-in-ubuntu-in-two-commands")

You should be fine by this point.

---

