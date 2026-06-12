---
title: "How can I know what is my swap ?"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by DrakeGis on 2008-11-13
Hi I'm using Intrepid and suddenly I have 71% of my swap (partition) occupied. Is there any application that will show me what I'm storing in the SWAP, so I could recognize what application is using the swap in such a way ???
Thanks

---

### Post by billgoldberg on 2008-11-13
> **DrakeGis said:**
> Hi I'm using Intrepid and suddenly I have 71% of my swap (partition) occupied. Is there any application that will show me what I'm storing in the SWAP, so I could recognize what application is using the swap in such a way ???
Thanks

Open a terminal and type in

```
top
```

That will tell you what application is using that much memory.

---

### Post by pennacook on 2008-11-13
when you have top running, make sure you sort by memory usage by using capital m to sort that way.

---

### Post by DrakeGis on 2008-11-13
I guess I wasn't clear. I want to know what applications are using my SWAP, no my RAM. Is there any way to do this ?

I also followed your advise and 'top' told me that 14% of my MEM was occupied by miro, after killing miro my SWAP occupancy went down from 72% to 66%. Still extremely high (according to System Monitor).

---

### Post by rbprogrammer on 2008-11-13
In addition to billgoldberg, having 70% of your swap space occupied might be normal.  It depends on how much RAM you have; the more RAM you have the less swap space is needed, and vice versa for the less RAM that you have the more swap space is needed.

As far as a program that will tell you how much swap space is used, I might be able to suggest Conky.  I have no experience with it, but it is basically a program that will display system information (eg, swap space).

---

### Post by MasterSander on 2008-11-13
In top you can also view the amount of swap used by applications

---

### Post by DrakeGis on 2008-11-13
Thanks for the information. It doesn't really matter how much RAM I have. As you mentioned the occupancy of the SWAP is related with the RAM and is particular of each system. I can tell you that in my system 70% is extremely high (I never go over 10%).
Conky seems to give me the information of swap space, but not the content (so I can identify the application that is using it)
Thanks.

I don't know what option should I use to see SWAP use in top.

---

### Post by rbprogrammer on 2008-11-13
Maybe I didn't understand you before, but I am not too sure that you can determine how much swap space is used by each application.  The managing of the swap space is done solely by the operating system, thus allowing the application to seem like it always has access to RAM.

---

### Post by DrakeGis on 2008-11-13
rbprogrammer: oh... I see. Thanks anyway.

MasterSander: For individual applications ? How ?

Funny Fact: I restart miro and My SWAP usage is still 66%.

---

### Post by rbprogrammer on 2008-11-13
Well, I am kind of learning about this topic now in my Operating Systems class at the University, but basically the operating system will determine which segments of memory that are used least often and swap them into "swap space".  Then if a program tries to access a segment that is registered in swap space, the operating system will have to make room in RAM to move that segment in so that the program can continue executing.

Try googling, or even on wikipedia, looking up Virtual Memory Management.  That should give you a basic understanding of how the operating system manages virtual memory to physical memory.

---

### Post by philinux on 2008-11-13
[http://www.linux.com/feature/121916](http://www.linux.com/feature/121916)

---

### Post by rbprogrammer on 2008-11-13
DrakeGis, also remember that the usage of swap space depends on how much RAM you have _**AND**_ how many applications are loaded.

Sorry if I didn't state that before if you didn't know. :lolflag:

---

### Post by psusi on 2008-11-13
You can't tell WHAT is in swap.  Once you kill a few things that are hogging memory, that will free up plenty of ram, but swap usage will not go down right away because there is no sense swapping stuff back in until it is needed.

If, for some odd reason, you really want to pull everything back into ram, then temporarily disable then re-enable swap:

```

sudo swapoff -a
sudo swapon -a

```

---

### Post by DrakeGis on 2008-11-13
rbprogrammer: I have a background in Computer Sciences, I know how it works, I know what information could be possible to recover (depending on the implementations), what I don't know is whether ubuntu/linux has that functionality implemented.

philinux: PLEASE, I don't want to be Rude. Could you explain me how an article on determining the size of the SWAP will help me to see what applications are actually using that space ?

Again, thanks for your time.

---

### Post by rbprogrammer on 2008-11-13
> **psusi said:**
> You can't tell WHAT is in swap.  Once you kill a few things that are hogging memory, that will free up plenty of ram, but swap usage will not go down right away because there is no sense swapping stuff back in until it is needed.

If, for some odd reason, you really want to pull everything back into ram, then temporarily disable then re-enable swap:

```

sudo swapoff -a
sudo swapon -a

```

Well that's a fun fact!  I never knew you could turn on and off the swap space on a whim like that :guitar:

---

### Post by philinux on 2008-11-13
I added the link for background info. which includes the commands in post 13.

Funnily enough when I read this thread I'd been playing around with ies4linux and firefox for windows in wine.

I decided to check my memory with "free". Nearly all my mem was used up and 3.9gig of swap and 1 processor was at 100%. The system was behaving normally. 
I had to reboot to get back to normal though. I've since added system monitor to my panel.

---

