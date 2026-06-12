---
title: "n00b ?- What slows down ubuntu"
date: 2008-09-22
forum: New to Ubuntu
---

### Post by miesnerd on 2008-09-22
I've heard in the past that having more programs installed on your computer slows it down (both in Windows and Linux). I've also heard having a more full disk slows down your computer.
For the first one, i can understand how this is true if each of the installed programs are loaded at startup or have a small applet running in the background, but other than that, I dont understand.

Im looking for understanding. Please, if either of these first two sentences are true, I'd like to understand the how and why.

Thanks.
Miesnerd

---

### Post by ethoxyethaan on 2008-09-22
your computer speed is determined by the temperature of the core and the amount of energy you apply to your processor so your speed is always the same. however your "usefull performance" is affected by the amount of processes running at the same time.

>> example: if you run both a Video decoder and a Game, the performance of both will degrade  
>> compared to the performance of Them running individually. 

however the speed on how a program "loads" data into your memory is determent by the read/write speed of your hard disk. on windows FAT32 your data is often spread over your disk and this might effect the peformance. on linux data is stored differently there is less fragmentation on the disk because of the EXT3 indexing. (but this might be complicated to explain). 

so on both systems if data is fragmented it will bring your performance down. the more programs you install (and that run constandly!) will also effect your performance.

disks with more data stored on them often have a larger fragmentation of data and therefore could effect your read/write speed.

i hope this helps

---

### Post by miesnerd on 2008-09-22
> **ethoxyethaan said:**
> your computer speed is determined by the temperature of the core and the amount of energy you apply to your processor so your speed is always the same. however your "usefull performance" is affected by the amount of processes running at the same time.

>> example: if you run both a Video decoder and a Game, the performance of both will degrade  
>> compared to the performance of Them running individually. 

however the speed on how a program "loads" data into your memory is determent by the read/write speed of your hard disk. on windows FAT32 your data is often spread over your disk and this might effect the peformance. on linux data is stored differently there is less fragmentation on the disk because of the EXT3 indexing. (but this might be complicated to explain). 

so on both systems if data is fragmented it will bring your performance down. the more programs you install (and that run constandly!) will also effect your performance.

disks with more data stored on them often have a larger fragmentation of data and therefore could effect your read/write speed.

i hope this helps

that does help quite a bit. I have some follow up questions, as I am a curious fellow:

The only part I dont understand is the power part you talked about first. Are you saying where, in my BIOS, i run more (i think its volts) thru my ram, etc, changes the performance of the processor or the ram?

Ive read up on filesystems so the EXT3 part doesnt suprise me a bit. Does it have that much of an effect, though?

---

### Post by billgoldberg on 2008-09-22
> **miesnerd said:**
> I've heard in the past that having more programs installed on your computer slows it down (both in Windows and Linux). I've also heard having a more full disk slows down your computer.
For the first one, i can understand how this is true if each of the installed programs are loaded at startup or have a small applet running in the background, but other than that, I dont understand.

Im looking for understanding. Please, if either of these first two sentences are true, I'd like to understand the how and why.

Thanks.
Miesnerd

If your hard drive is almost full things might slow down. That is true.

The number of programs installed don't matter, it's the number of processes running that matter.

--

You can use the command top ( or better install htop and then use the command "htop") to see what is giving your cpu('s) troubles.

-- 

I see etoxyethaan told the same as me, but in more detail.

Oh well.

---

### Post by miesnerd on 2008-09-22
> **billgoldberg said:**
> If your hard drive is almost full things might slow down. That is true.

The number of programs installed don't matter, it's the number of processes running that matter.

--

You can use the command top ( or better install htop and then use the command "htop") to see what is giving your cpu('s) troubles.

thanks guys.
Im not having any trouble, its just that its time for me to finally answer a number of questions I've had for a while (others include understanding how swap works, etc) since im now advising all my linux converts on how to keep their computers in order. This was the one question I had where I couldnt find a good answer on the internet.

---

### Post by ethoxyethaan on 2008-09-22
not the ram but rather the Processor speed. its called over clocking but its not recommended because it might damage your hardware if not cooled properly. 

freezing a processor down to 0 kelvin would be a nice idea to boost the performance but a costly one. 

i'm not even sure if that is a good idea because transistors don't work a sertain temperatures

oh wait i have to stop here before i dig up my electronics (the class i failed ------)

---

### Post by Gorgamel on 2008-09-22
> **ethoxyethaan said:**
> freezing a processor down to 0 kelvin would be a nice idea to boost the performance but a costly one.

Not to be a wice ***, but freezing the cpu down to 0 (zero) kelvin would not be that very smart. By the definition of kelvin is ```
the theoretical absence of all thermal energy
/Wikipedia
```
Thus, if the cpu would be at 0 kelvin, there would be no movement what so ever of the atoms. And having no movement would banish any electricity coming through. Just an input ;)

---

### Post by billgoldberg on 2008-09-22
> **miesnerd said:**
> thanks guys.
Im not having any trouble, its just that its time for me to finally answer a number of questions I've had for a while (others include understanding how swap works, etc) since im now advising all my linux converts on how to keep their computers in order. This was the one question I had where I couldnt find a good answer on the internet.

Swap:

I'm not an expert on these things but from what I know swap is used when you are short on ram memory. 

I guess the wikipedia article on swap will tell you more.

---

### Post by miesnerd on 2008-09-22
> **billgoldberg said:**
> Swap:

I'm not an expert on these things but from what I know swap is used when you are short on ram memory. 

I guess the wikipedia article on swap will tell you more.

nah, no biggie. I was able to learn sufficient info about swap earlier. I got it. Really, what I wanted to do is set how fast each computer used swap (ie moving it away from 60 ). I have a desktop that has 5 GB of ram. It has NEVER used swap to my knowledge, so i changed that to 0. Laptop, however, has 512 of ram, so I set it to 100. I see where some people said that might be inadvisable, but I changed my partitions so I have a lot of swap space. Regardless of what is said, I noticed a positive difference in performance.

---

### Post by 73ckn797 on 2008-09-22
Swap IS used when RAM is insufficient or loaded up from many processes being used. The system must "swap" off the temp unused info to a section of the hard drive (swap file). One way that I have ran a swap file, at least in windows, was to designate a portion of a second drive for swap. That keeps the main drive from going all over the disk trying to run program files and at the same time trying to swap memory load. I have not looked into how to do that with Ubuntu but I will be soon. It is probably a very easy thing to do.

---

### Post by miesnerd on 2008-09-22
bill:
wanted to say I checked out your blog also, and I liked it.

---

### Post by billgoldberg on 2008-09-22
> **miesnerd said:**
> bill:
wanted to say I checked out your blog also, and I liked it.


Thanks.

---

