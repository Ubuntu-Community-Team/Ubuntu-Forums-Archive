---
title: "how much memory does my graphics card have"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by adobrakic on 2008-06-16
i dont know how to figure this out. i got a ProSavage8 graphics card

---

### Post by shifty_powers on 2008-06-16
from what i can gather, not a lot.

is it an integrated chip by any chance? if it is a discrete card it must be pretty damn old...

---

### Post by tamoneya on 2008-06-16
what is the output of ```
sudo lshw -C display
```

---

### Post by adobrakic on 2008-06-16
*-display               
       description: VGA compatible controller
       product: VT8375 [ProSavage8 KM266/KL266]
       vendor: S3 Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-2.0 vga_controller bus_master cap_list
       configuration: driver=prosavage_smbus latency=32 maxlatency=255 mingnt=4 module=i2c_prosavage

---

### Post by tamoneya on 2008-06-16
from googling it appears to be 32 MB shared so this means that it takes it from your system memory.

---

### Post by adobrakic on 2008-06-16
So it has a total of 32mb?

---

### Post by tamoneya on 2008-06-16
im about 90% positive.  Could vary by a factor of at most 2.  Also remember that this is not 32 MB of graphics memory but shared system memory.  Much slower and it also subtracts from what is available for OS use.

---

### Post by st33med on 2008-06-16
The short answer: Yes
The long answer: Yes and no. Since the graphics card is integrated into the motherboard and has little memory (albeit, more than my Intel Integrated card's 8 MB) to store textures, polygons, images, etc. So, it has to rely on the system memory to run programs.

---

### Post by iaculallad on 2008-06-16
> **adobrakic said:**
> i dont know how to figure this out. i got a ProSavage8 graphics card

You could use your terminal to view how much video memory you have on your video card:

```
cat /var/log/Xorg.0.log | grep RAM
```

---

### Post by adobrakic on 2008-06-16
^ This is what I got when I put that
```

ado@ado-desktop:~$ cat /var/log/Xorg.0.log | grep RAM
(II) Initializing built-in extension XINERAMA
ado@ado-desktop:~$ 

```

And is there a way to increase the memory that my graphics card uses? I'm trying to get a game to play, and it needs 64mb.

---

### Post by Liakath on 2008-06-27
> **adobrakic said:**
> ^ This is what I got when I put that
```

ado@ado-desktop:~$ cat /var/log/Xorg.0.log | grep RAM
(II) Initializing built-in extension XINERAMA
ado@ado-desktop:~$ 

```

And is there a way to increase the memory that my graphics card uses? I'm trying to get a game to play, and it needs 64mb.

Dear Adobrakic,

Usually for Video Cards which uses the system memory there is an option in the BIOS for seeting up the memory allocation for Video Card. In this case I am afraid it is limited to a maximum of 32MB if the information provided in the earlier post is true.

If you need 64MB the option is to use another Video Card I am afraid.

---

### Post by inanimous on 2008-11-10
> **adobrakic said:**
> ^ This is what I got when I put that
```

ado@ado-desktop:~$ cat /var/log/Xorg.0.log | grep RAM
(II) Initializing built-in extension XINERAMA
ado@ado-desktop:~$ 

```

And is there a way to increase the memory that my graphics card uses? I'm trying to get a game to play, and it needs 64mb.

Try This: 
```
~$ cat /var/log/Xorg.0.log | grep mem -i
```

---

### Post by john6of6 on 2010-05-24
There has got to be a better way of doing this!

This is what I found.
```
lspci -v -s `lspci |grep VGA|awk {'print $1'}`
```

[INDENT]00:02.0 VGA compatible controller: Intel Corporation 82Q35 Express Integrated Graphics Controller (rev 02)
	Subsystem: Lenovo Device 3038
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at d0100000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at 1c70 [size=8]
	[COLOR="SeaGreen"]Memory at c0000000 (32-bit, prefetchable) [size=256M][/COLOR]
	Memory at d0000000 (32-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>
[/INDENT]
The line that reads prefetchable (green) gives you your video card memory size.  Surprised this isn't done cleaner somewhere as a GNOME app or something...  its got to be!

---

