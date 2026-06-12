---
title: "All Memory Not Showing UP"
date: 2012-11-04
forum: New to Ubuntu
---

### Post by hbrock on 2012-11-04
I am only showing 5.8GB out of 9GB:

```
harrison@harrison-Aurora:~/Desktop$ lshw -C memory
WARNING: you should run this program as super-user.
 *-memory                
   description: System memory
   physical id: 0
   size: 5961MiB
```

But when I run lshw -C memory it show all 9GB:

```
[sudo] password for harrison: 
*-firmware              
   description: BIOS
   vendor: Alienware
   physical id: 0
   version: A10
   date: 07/30/2010
   size: 64KiB
   capacity: 4032KiB
   // other stuff here
   *-memory
   description: System Memory
   physical id: a
   slot: System board or motherboard
   size: 9GiB
*-bank:0
      description: DIMM 1333 MHz (0.8 ns)
      product: KP223C-ELD
      vendor: Kingston
      physical id: 0
      serial: 43791B85
      slot: DIMM0
      size: 2GiB
      width: 64 bits
      clock: 1333MHz (0.8ns)
 *-bank:1
      description: DIMM 1333 MHz (0.8 ns)
      product: KTW149-ELD
      vendor: Kingston
      physical id: 1
      serial: B0953279
      slot: DIMM1
      size: 1GiB
      width: 64 bits
      clock: 1333MHz (0.8ns)
 *-bank:2
      description: DIMM 1333 MHz (0.8 ns)
      product: KP223C-ELD
      vendor: Kingston
      physical id: 2
      serial: 7A381B2B
      slot: DIMM2
      size: 2GiB
      width: 64 bits
      clock: 1333MHz (0.8ns)
 *-bank:3
      description: DIMM 1333 MHz (0.8 ns)
      product: KTW149-ELD
      vendor: Kingston
      physical id: 3
      serial: B0E63277
      slot: DIMM3
      size: 1GiB
      width: 64 bits
      clock: 1333MHz (0.8ns)
 *-bank:4
      description: DIMM 1333 MHz (0.8 ns)
      product: KP223C-ELD
      vendor: Kingston
      physical id: 4
      serial: 7A3B1B2B
      slot: DIMM4
      size: 2GiB
      width: 64 bits
      clock: 1333MHz (0.8ns)
 *-bank:5
      description: DIMM 1333 MHz (0.8 ns)
      product: KTW149-ELD
      vendor: Kingston
      physical id: 5
      serial: B0BF3277
      slot: DIMM5
      size: 1GiB
      width: 64 bits
      clock: 1333MHz (0.8ns)
```

How can I get all the memory to be used?

---

### Post by squakie on 2012-11-04
Please post the maker and model of your PC - there may be something with the way memory is mixed.  There are a couple of ways to come up with 6gig, but it may be saying something when the 1st slot in each group of 2 contains 2 gig, while the other slots contain 1 gig.  I don't really know.  There was a time when motherboards/cpus required memory installed in matched pairs, but unless you are running an older system I wouldn't think that could be the issue now.  Knowing the make and model of your PC we can try to look at the manufactures site and see what it says about memory in the slots on your board.

---

### Post by hbrock on 2012-11-04
> **squakie said:**
> Please post the maker and model of your PC - there may be something with the way memory is mixed.  There are a couple of ways to come up with 6gig, but it may be saying something when the 1st slot in each group of 2 contains 2 gig, while the other slots contain 1 gig.  I don't really know.  There was a time when motherboards/cpus required memory installed in matched pairs, but unless you are running an older system I wouldn't think that could be the issue now.  Knowing the make and model of your PC we can try to look at the manufactures site and see what it says about memory in the slots on your board.

I have an Alienware Aurora with:
CPU: Intel Core i7
System chipset: Intel x58 Express

---

### Post by hbrock on 2012-11-04
I got all 9GB to show up. Here is what I did:

Place 2GB modules into banks 0, 1, 2
Place 1GB modules in banks 3, 4, 5

---

### Post by squakie on 2012-11-04
Thought it might be something like that - some motherboards have a list of the combinations allowed in the sockets.

Glad you got it working!

---

### Post by mike acker on 2012-11-04
> **hbrock said:**
> I got all 9GB to show up. Here is what I did:

Place 2GB modules into banks 0, 1, 2
Place 1GB modules in banks 3, 4, 5

interesting..... what does your performance monitor show you are using ? mine runs very steady at someplace close to 1 GB

which leads me to wonder why I put in 16GB memory .   i might take out all but 4GB and see if it starts using the swap space . i don't have a 2GB chip to test with

---

### Post by jerome1232 on 2012-11-04
even free ram does get used as a file cache, so it's not useless

---

### Post by hbrock on 2012-11-05
> **mike acker said:**
> interesting..... what does your performance monitor show you are using ? mine runs very steady at someplace close to 1 GB

which leads me to wonder why I put in 16GB memory .   i might take out all but 4GB and see if it starts using the swap space . i don't have a 2GB chip to test with

Am using between 700MB - 1.4GB most of the time. But I do alot of development work with Java and C++.

My SWAP is always 0%

---

