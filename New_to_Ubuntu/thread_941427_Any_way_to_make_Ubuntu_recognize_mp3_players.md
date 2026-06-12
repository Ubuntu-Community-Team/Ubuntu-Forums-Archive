---
title: "Any way to make Ubuntu recognize mp3 players ?"
date: 2008-10-08
forum: New to Ubuntu
---

### Post by Bakhman on 2008-10-08
For the past year (!) I've had to use a separate computer that has XP to transfer songs to my measly 4GB Creative Zen. While I AM able to charge the player by connecting it via USB, nothing ever pops up on my desktop allowing me to transfer songs, which is probably the most inconvenient thing I'm having with Ubuntu right now.

Has anyone here gotten them to connect? Any update that fixes this? 
Thank you sooooo much :guitar: I needs music!

---

### Post by bryncoles on 2008-10-08
there are ways - ive never found out how to make ubuntu recognise craetive products as external drives (which would be ideal), but you could try installing: 

gnomad2

or

kzenexplore

from synaptic. i prefer kzenexplore, as its prettier and slightly more functional (and its works on a drag and drop principle).

plug the player into your computer via usb, then fire up the program and it *should* work...

*edit*

i once managed to get amarok to recognise the my creative player, but it had less functioanlity than kzenexplorer (and gnomad, i think) so i wouldnt personally bother going that route)

---

### Post by chaosdesigner on 2008-10-08
I'm not sure if this works for you but some programms reconize mp3 Player (For instance Amarok), so I would try that. 

Or if it doesnt work, like with my zune Player, you will have to do it with a virtual Machine, like maybe vmware.

---

### Post by billgoldberg on 2008-10-08
My creative zen acts as a mass storage device.

Go to places -> home and in the left plane look for external hdd's. One of them might be your zen.

---

### Post by 3rdalbum on 2008-10-08
There is a bug in Hardy that stops some MP3 players from automatically mounting.

Fortunately, you can manually mount them:

```
sudo fdisk -l
```
This will show you the device file names of your local disks. Find out what device file your player is at (let's assume it's */dev/sdb*):

```
pmount /dev/sdb zen
```

Your player should appear on the desktop under the name "zen", mounted under /media/zen. You can drag and drop files onto it.

You can't unmount it from the GUI. Type the following into the terminal:

```
pumount zen
```

When the terminal is ready to accept more commands, then it's safe to unplug the player.

I don't know if this MP3 player allows drag and drop and generates its own library, but you are welcome to try it.

---

### Post by Bakhman on 2008-10-08
Sweet, gnomad works! (The other one only detected jukeboxes)
This is more that I could possibly want, thanks a lot... 
^ oh and the terminal couldn't detect the player (no "sda" for it), which makes sense I suppose.

---

### Post by ubunter1 on 2009-03-19
> **3rdalbum said:**
> There is a bug in Hardy that stops some MP3 players from automatically mounting.

Fortunately, you can manually mount them:

```
sudo fdisk -l
```
This will show you the device file names of your local disks. Find out what device file your player is at (let's assume it's */dev/sdb*):

```
pmount /dev/sdb zen
```

Your player should appear on the desktop under the name "zen", mounted under /media/zen. You can drag and drop files onto it.

You can't unmount it from the GUI. Type the following into the terminal:

```
pumount zen
```

When the terminal is ready to accept more commands, then it's safe to unplug the player.

I don't know if this MP3 player allows drag and drop and generates its own library, but you are welcome to try it.


how can i make ubuntu hardy recognize my zen?, after i updated from the last version it won list it, it will charge but that is it. i typed in your instructions and this is what i got- 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc1bd6134

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19103   153444816   83  Linux
/dev/sda2           19104       19457     2843505    5  Extended
/dev/sda5           19104       19457     2843473+  82  Linux swap / Solaris
i dont see zen listed, is it a usb or hotplug issue?. any help would be appreciated. thanks.

---

