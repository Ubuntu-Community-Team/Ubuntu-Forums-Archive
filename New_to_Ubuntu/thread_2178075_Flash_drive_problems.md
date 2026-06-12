---
title: "Flash drive problems"
date: 2013-10-01
forum: New to Ubuntu
---

### Post by populus2 on 2013-10-01
I am having several problems with removable media this week. A 64GB card will not mount after I accidentally pulled the card reader's lead out of the USB port. So I started copying the files instead onto an old 32GB (FAT32) flash drive which became read-only as I'd almost finished. Not only that, but 'Properties' shows the current contents of the stick as 29GB but the files themselves show as 41GB. 

I tried dmesg and check/repair filesystem on the flash drive but the check seemed to be hanging for several hours. I've no idea about the 64GB card - I tried it on a Windows PC and it doesn't even show up. I'm new to this and am really getting frustrated.

---

### Post by DuckHook on 2013-10-01
Hi populus2 and welcome!

With respect to the 64GB card, there is a slight chance that you may have caused it irreparable harm by disconnecting it in the middle of a write operation. If a block is being written and the power fails, this would toast the whole block. If the block holds partition content, you would scramble its partition. And if static was involved, the card could be toast. Although the card won't mount, is it even recognized? Connect it to a USB port with your reader and open Disk Utility. Can it see the card at all? If so, you may be able to salvage the card at least by repartitioning it.

With respect to the 32GB flash drive, you mention that it is old. What have you done with this drive in the past? Flash drives have a limited number of write cycles, but it is unlikely that you would have exhausted those unless you wrote to the drive incessantly. Did you defrag the drive constantly or install a full OS on it? Most check/repair utilities will also perform many write operations (that's how it checks) and were designed for HDDs and not flash drives. There's so much variation in USB flash drives that it's hard to advise you on this one. USB flash is dependent on the quality of its components and construction, efficiency of its controller, how much free space is left for load balancing, and can be quickly degraded through heat, shock or water, especially water.

Frankly, if you cannot get the 64GB card working again, I would advise you to purchase another USB stick rather than try wrestling with the old one. They are absurdly cheap these days (Best Buy on sale for $9.99) and you will waste far more than ten bucks worth of your time trying to chase down what is wrong. Of course, if you are treating your time as an investment in the learning process, then that's an entirely different matter, but most people just want to solve the matter and get on with life.

---

### Post by Pako Pako on 2013-10-01
> **populus2 said:**
> A 64GB card will not mount after I accidentally pulled the card reader's lead out of the USB port.
DuckHook said everything that could be said -- interrupting data transfer can be highly unpredictable and can toast the entire drive. If the data is incredibly important, you can take it to data-retrieval specialists who will physically dissect the drive to try and get a read.

> **populus2 said:**
> So I started copying the files instead onto an old 32GB (FAT32) flash drive which became read-only as I'd almost finished. Not only that, but 'Properties' shows the current contents of the stick as 29GB but the files themselves show as 41GB.
I had an issue recently with one of my SanDisk pen-drives. Emailing a representative they told me that attempting to fill the drive beyond its limits triggers a safety inside that turns the drive into read-only mode. I could back up the data, but in order to write to the drive again I had to fill out an RMA for a new drive.

---

### Post by populus2 on 2013-10-02
Thanks both for your replies - I'll post some more info as soon as I get time to investigate further.

---

### Post by sudodus on 2013-10-02
Maybe you can find some useful information at this link

[https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)

---

### Post by DuckHook on 2013-10-02
> **Pako Pako said:**
> ...attempting to fill the drive beyond its limits triggers a safety inside that turns the drive into read-only mode.The problem is that many USB sticks are made to work (and look like HDDs) through some tricks that can sometimes come back to bite you.

The principle behind all drives, whether HDDs or Flash, is that deleting a block of data doesn't actually *delete* it; it just clears the pointer to that data from the filesystem database, thus "freeing" that block to be overwritten. As an aside, this is why recovery software has a decent chance of "undeleting" a file. The underlying info is actually still there until it is overwritten by new data.

In the case of an HDD, this clearing of the pointer is all that is needed. The nature of magnetic disk media is such that any new data simply overwrites the old data--end of story. However this is most definitely not what happens in flash drives.

In a flash drive, it is not enough to just erase the pointer to the data. The whole of the physical data block must be actively erased before any new data can be written to it (and with flash memory, this means overwriting the block with '1's, not '0's). Moreover, data must be erased in full blocks because the architecture of NAND memory does not permit erasures at the byte level. Therefore, "erasing" a piece of flash memory consists of a very time-consuming bulk process and not an efficiently fine-tuned one.

A further problem with USB flash drives is that they have become so cheap that manufacturers cannot afford to include trimming technology (which is what forces SSDs to immediately erase blocks as soon as they are deleted). Instead, controller chips on USB flash drives are designed with built-in algorithms that erase blocks only as needed. This is one of the reasons why flash drives start out slower than SSDs and get even slower with accumulated use. There are fewer and fewer erased blocks that they can write data to, and more of the controller's time and resources are being used to hunt down open blocks or erasing previously used blocks.

The final kicker is that in the interest of wear-levelling, a block cannot simply be erased and reused because almost all modern memory uses MLC transistors in the interest of saving costs. MLC only has from 1000 to 5000 write cycles (depending on quality of the component), so the USB controller must perform some fancy juggling whereby less-used blocks are rotated into use and well-used blocks are rotated out of use. But as the flash drive gets closer and closer to being filled, this process approaches a critical threshold beyond which the controller cannot process any further blocks. And especially if the drive is an old well-used one filled with many previously used blocks, you may not be able to fill the drive more than part-way before the controller becomes so bogged down trying to free up old blocks that it just gives up the ghost. There's even a technical term for it called "gridlock" (appropriately enough). Once this happens, it is no longer possible to write to that USB drive. It becomes read-only.

I suspect that *populas2* gridlocked his/her old flash drive. The 64GB card died from a different cause.

I am told that there is no way to recover a gridlocked drive to make it writable again. This is probably what the SanDisk rep actually meant by "triggering a safety". His description was not very accurate, but far shorter than my long-winded explanation.

I wonder if an old drive can be revitalized by writing '1's to every block? It could probably be done with something like *dd*. I've never tried it, and of course, it would have to be done on a drive that was not yet gridlocked. If anyone out there has tried, I'd be all curiosity as to how it turned out.

---

### Post by sudodus on 2013-10-02
Thank you for an interesting post ***DuckHook*** :KS

Would it be OK to link to it from [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)?

---

### Post by DuckHook on 2013-10-02
> **sudodus said:**
> Would it be OK to link to it from [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)?:lolflag: I'm not sure how *accurate* it is! I'm no expert, so frankly, it's just a summary based on what I've gleaned from reading [Wikipedia]("http://en.wikipedia.org/wiki/Flash_memory") and various postings from other forums, but by all means, feel free to link to it if you feel it will be helpful. You might wish to have a real expert vet it first though...:biggrin:

---

### Post by sudodus on 2013-10-02
Ok :-)

---

### Post by Pako Pako on 2013-10-03
> **DuckHook said:**
> The problem is that many USB sticks are made to work (and look like HDDs) through some tricks that can sometimes come back to bite you.

...(Blocks vs pointers)...

In a flash drive, it is not enough to just erase the pointer to the data. The whole of the physical data block must be actively erased... in full blocks because the architecture of NAND memory does not permit erasures at the byte level... a block cannot simply be erased and reused because almost all modern memory uses MLC transistors... (which have) from 1000 to 5000 write cycles, so the USB controller must perform some fancy juggling whereby less-used blocks are rotated into use and well-used blocks are rotated out of use. But as the flash drive gets closer and closer to being filled, this process approaches a critical threshold beyond which the controller cannot process any further blocks. And especially if the drive is an old well-used one filled with many previously used blocks, you may not be able to fill the drive more than part-way before the controller becomes so bogged down trying to free up old blocks that it just gives up the ghost. There's even a technical term for it called "gridlock" (appropriately enough). Once this happens, it is no longer possible to write to that USB drive. It becomes read-only.

I suspect that *populas2* gridlocked his/her old flash drive.

I am told that there is no way to recover a gridlocked drive to make it writable again. This is probably what the SanDisk rep actually meant by "triggering a safety". His description was not very accurate, but far shorter than my long-winded explanation.
Yes, I agree. Except that when I mentioned my flash drive "hitting gridlock," it was a new one I bought this year that I had only used for about a month. I surmise that something other than age must have hit the drive and hence my paranoia for "over-writing" to newer flash drives. (In that instance, it coincided with accidentally dragging a 10 GB ISO file into it's remaining 4 GB storage.)

> **DuckHook said:**
> I wonder if an old drive can be revitalized by writing '1's to every block? It could probably be done with something like *dd*. I've never tried it, and of course, it would have to be done on a drive that was not yet gridlocked. If anyone out there has tried, I'd be all curiosity as to how it turned out.
It has mixed results. I have an old flash drive (it has 64 <I>MB</i> of storage) that required regular low-level formats in order to keep it useable. I have a vague idea of what might be wrong (worn controller vs worn blocks).

As for grid-locked drives, no way of changing anything via software. (It's possible to physically remove the chips from the stick and flash them on another device.)

---

