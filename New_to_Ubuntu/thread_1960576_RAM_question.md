---
title: "RAM question"
date: 2012-04-17
forum: New to Ubuntu
---

### Post by seal308 on 2012-04-17
Hello
So i had 1gb of ram. 
I used this command 
sudo dmidecode --type 17
found the type and counted the number of pins
I went to my local electronics store and bought the ram.
It fit in perfectly.
I went into terminal and put in the same code
sudo dmidecode --type 17
i noticed it read 2gb ram but the speed still said 533 mHz (the same as before with the 1gb)
is there something wrong.
shouldn't it be faster?

---

### Post by anewguy on 2012-04-17
The speed you are referring to is the clock/bus speed of the memory.  That won't change when you add memory.  The speed shown for your processor won't change when you add memory.  Since you effectively double your memory, you should notice some (doesn't mean big) difference in how apps perform.

Dave ;)

---

### Post by Cheesemill on 2012-04-17
To get a speed increase your motherboard must support dual-channel RAM.

You also have to make sure you installed the RAM in the correct slot, the pair of sticks will need to be in specific positions (check your motherbiard manual for more details).

---

### Post by seal308 on 2012-04-17
well there is only one slot in the machine for the ram.
I do notice a tiny bit of difference. 
But is their some quantitative/numerical results that can prove that the ram is working.

---

### Post by daslinkard on 2012-04-17
What are the specifications of your machine?  Manufacturer, Model, etc.?

---

### Post by TheMTtakeover on 2012-04-17
> **seal308 said:**
> Hello
i noticed it read 2gb ram but the speed still said 533 mHz (the same as before with the 1gb)
is there something wrong.
shouldn't it be faster?

I believe that is how fast your computer interacts with the RAM. So as long as it's showing 2GB and thats how much you put in, it should be good.

---

### Post by Cheesemill on 2012-04-17
> **seal308 said:**
> well there is only one slot in the machine for the ram.
I do notice a tiny bit of difference. 
But is their some quantitative/numerical results that can prove that the ram is working.

If there is only 1 RAM slot in your machine then no, the memory wont run any faster by swapping out a 1GB stick for a 2GB stick. 533MHz is probably the fastest RAM speed supported by your motherboard.

---

### Post by seal308 on 2012-04-17
Really.
My computer says it does support 2gb of ram though. 
So just b/c it supports it, it doesn't mean it will make any differece?
The machine i'm using is an eeebox model number EB1006

---

### Post by daslinkard on 2012-04-17
It looks as if you can actually step up to a faster bus speed on the RAM from 533 mhz to 667.

Here is from [Crucial.com]("http://www.crucial.com/store/mpartspecs.aspx?mtbpoid=700DDC81A5CA7304")

---

### Post by seal308 on 2012-04-17
if that is true than why does the speed still read 533 even though the new 2gb ram is in?

---

### Post by daslinkard on 2012-04-17
Because chances are when you went to the brick-n-mortar store, they had the lower speed of 533 mhz.  The Link I gave you has 667 mhz at I believe $30 USD.

---

### Post by Cheesemill on 2012-04-17
Because you have bought RAM that runs at 533MHz

---

### Post by seal308 on 2012-04-17
ok thx i'll look into this

---

### Post by seal308 on 2012-04-17
so i check and it says PC2-5300 on the box of the ram.
So is that the speed?
do i need pc2-6400?

---

### Post by seal308 on 2012-04-17
i think this is it
[http://ncix.com/products/?mode=productreviewread&product_id=28109](http://ncix.com/products/?mode=productreviewread&product_id=28109)

---

### Post by daslinkard on 2012-04-17
Yes if you want to upgrade the bus speed you will want to go from the 533 mhz to the 667 mhz.  I posted the link to the faster RAM in an earlier response to you pertaining to crucial.com.  Depending upon what stores you have, you might not be able to purchase the faster RAM in your area.  If not you have the trusty World Wide Web at your fingertips.

---

### Post by seal308 on 2012-04-17
the specs on the ram you linked is this
DDR2 PC2-5300 • CL=5 • Unbuffered • NON-ECC • DDR2-667 • 1.8V • 256Meg x 64 • 
what indicates that it is faster?

---

### Post by anewguy on 2012-04-17
ddr2-667 -> it will run at a 667mhz clock rate instead of the 533mgz with your current memory.  I didn't look at any of the specs for your motherboard, but I'm assuming the others did and that it support 667mhz without you needing to overclock.

Again, this is just memory speed.  You will only notice a small difference.  You are not going to get some big jump in performance.  Going to 2gb from 1gb is where the most of your performance increase is going to come from, and as I explained way back at the beginning of your thread, it won't be that obvious, no big jump in the apparent speed of your computer.  Plus, as I also mentioned, you're not going to see that 533 change, nor your CPU speed change.  Changing your memory to ddr2-667 will provide a little improvement and the number you are watching will change to 667 - but remember, it's not changing the speed of the CPU or the rest of your computer.  There may be the appearance of a neglibable speed increase in your apps.

Dave

---

### Post by seal308 on 2012-04-17
i see. so instead of upgrading ram, is there anything i could do?
someone told me to upgrade to an ssd, but that's a bit pricy 
or is it that my motherboard is really limiting me to speeding it up at all?

---

### Post by 3rdalbum on 2012-04-17
The EeeBox computers are fairly low performance so there isn't much you can do.

You can't upgrade the CPU or GPU. You now have extra RAM in case you need it (probably don't really, Ubuntu is pretty efficient).

The SSD will make a marked difference in the amount of time spent waiting for things to load. Even a low capacity one like 64 gigs should be good, as long as it is decent quality (NOT Kingston)

---

### Post by seal308 on 2012-04-17
k thx. 
I'll try saving up for 1 then.
But 64 gb is a little low on space.
Is there a way to compensate.
I don't want cloud storage.
However i do have a few external harddrives that i've used for time machine and cloning on my mac.
Could i use those on the desktop running ubuntu if it only had 64 gb and just sort of shared hard drives?

---

### Post by anewguy on 2012-04-18
> **3rdalbum said:**
> The EeeBox computers are fairly low performance so there isn't much you can do.

You can't upgrade the CPU or GPU. You now have extra RAM in case you need it (probably don't really, Ubuntu is pretty efficient).

The SSD will make a marked difference in the amount of time spent waiting for things to load. Even a low capacity one like 64 gigs should be good, as long as it is decent quality (NOT Kingston)

+1.  That type of extremely small PC really doesn't have any upgrade paths except what you've done for memory and the possibility of an SSD.  Just remember, after things have loaded, it will still be the same - same cpu speed, same memory speed, etc..  Only disk I/O's will be faster.  I have a 64gb SSD I run Ubuntu from.  If you need more that 64gb, there area 128 SSD's and I've even seen a 256gb SSD floating around.  Things have greatly improved with SSD's, but keep in mind they still won't last as long as a hard disk.

---

### Post by 3rdalbum on 2012-04-22
> **seal308 said:**
> k thx. 
I'll try saving up for 1 then.
But 64 gb is a little low on space.
Is there a way to compensate.
I don't want cloud storage.
However i do have a few external harddrives that i've used for time machine and cloning on my mac.
Could i use those on the desktop running ubuntu if it only had 64 gb and just sort of shared hard drives?

Yeah, you can happily use the SSD as / and an external HDD as /home. Or put / and /home on the SSD and use the external HDD for music and movies and such. You'd be surprised how far 64 gigs can go when you're not putting movies in that space.

---

