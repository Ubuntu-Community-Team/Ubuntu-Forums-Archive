---
title: "Why does &quot;hexdump&quot; reverse bytes?"
date: 2013-12-09
forum: Programming Talk
---

### Post by sha1sum on 2013-12-09
Say we use hexdump in a very simple way:

```
user@computer:~$ echo "hello" | hexdump
0000000 6568 6c6c 0a6f                         
0000006

```

if you look at the hex: 
65 = e
68 = h
6c = l
0a = newline
6f = o

So the way it basically prints is like this:

e h l l . o 
(where . is newline )

Why does it constantly reverse two bytes?

---

### Post by r-senior on 2013-12-09
It's not reversing them, everything else is:

[http://en.wikipedia.org/wiki/Endianness](http://en.wikipedia.org/wiki/Endianness)

---

### Post by steeldriver on 2013-12-09
If you want them in character order, I find it easier to use **od** with the **x1** format (hex, single byte)

```

$ hexdump <<< "hello"
0000000 6568 6c6c 0a6f
0000006
$ 
$ od -tx1 <<< "hello"
0000000 68 65 6c 6c 6f 0a
0000006

```

---

### Post by sha1sum on 2013-12-13
> **r-senior said:**
> It's not reversing them, everything else is:

[http://en.wikipedia.org/wiki/Endianness](http://en.wikipedia.org/wiki/Endianness)

Interesting. I think I get the concept of endianness. 

I still don't really understand why hexdump operates in the way it does. So it reverses two bytes,or you could argue it puts them in the logical order. But why on the two byte level? Why not on the four byte level? Why isn't the entire thing read backwards?

If I were to look at my hard drive, what does a text file with four letters look like? If I use a hex editor to look at a text file, everything is normal, or Big endian, or whatever you call it. While if I examine it with hexdump, it is reversed, or little endian on the two byte level, or someting like that.

---

### Post by The Cog on 2013-12-13
I use hd instead of hexdump. It doesn't answer the question of course, but you may choose to use hd instead, as I did once I found it.
```
$ echo Hello | hd
00000000  48 65 6c 6c 6f 0a                                 |Hello.|
```

---

### Post by sha1sum on 2013-12-13
Thanks. That's a nice option too. For my original purpose I fixed it with a pipeline into sed that reverses the two bytes back. Now I´m just curious about this endianness.

---

### Post by Bachstelze on 2013-12-15
> **sha1sum said:**
> 
I still don't really understand why hexdump operates in the way it does. So it reverses two bytes,or you could argue it puts them in the logical order. But why on the two byte level? Why not on the four byte level? Why isn't the entire thing read backwards?

One has to make a choice. ;) The choice of printing the data in two-byte quantities by default is of course arbitrary, just like the choice of one- or four- or eight-byte quantities would have been.

---

### Post by sha1sum on 2013-12-15
> **Bachstelze said:**
> One has to make a choice. ;) The choice of printing the data in two-byte quantities by default is of course arbitrary, just like the choice of one- or four- or eight-byte quantities would have been.
Okay I see. So say if I were to look at my hard drive. What would the order of ones and zeroes look like? Would it be big-endian or little-endian?

---

### Post by Bachstelze on 2013-12-15
I'm not sure it even makes sense to speak of endianness on a hard drive. A hard drive is not linear.

---

### Post by sha1sum on 2013-12-15
hmm, interesting. If it isn't linear, then what is it? Does it contain a two-dimentional matrix of bits?

---

### Post by StephenF on 2013-12-16
A traditional hard drive has typically two or four read heads each scanning a different surface. Older examples may have eight so not having consecutive bits on the same drive platter is the norm. Then there is RAID and LVM which divides up your data in various different ways among drives and partitions. At the filesystem level there is also a thing called file fragmentation that disperses parts of the file among whatever unused blocks are available which brings us onto the topic of block devices.

Drives are block devices which basically means instead of bytes you are grabbing blocks at a time effectively drives are 16384 (or some similar power of 2) bit devices when considering the data bus.

Since the surface, read hardware, and control circuitry are fully integrated the drive manufacturers are free to devise their own encoding schemes and arrangements.

Edit: Back in the 80's those machines had the drive surface details exposed to the operating system.

---

### Post by sha1sum on 2013-12-16
Okay I see. That makes sense. Thanks :D

---

### Post by The Cog on 2013-12-16
I think the byte order of things stored on disk will depend on the file type and the application that writes/reads it. 
Many programs will store their data in a specific byte order that is defined by its programmers. I'm pretty sure that sqlite database files fall into this category. These files will be hardware independent and it will be possible to transfer them files meaningfully to other machines which may use different hardware.

I'm guessing, but I think that programs that work by reading/writing memory images will tend to store their 2-byte integers in whichever order the particular processor they are compiled for uses. So that for instance, programs compiled for intel hardware will store the smaller byte first, and programs compiled for ARM hardware will store the larger byte first. This will definitely be true of machine executable program files. Such files will not be sensibly transferable between different hardware architectures.

---

