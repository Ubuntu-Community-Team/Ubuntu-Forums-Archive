---
title: "Help with figuring out my RAM specs."
date: 2008-09-16
forum: New to Ubuntu
---

### Post by the badger on 2008-09-16
Hi.

I want to try and find some more RAM for my franken-computer. I am posting in hopes that someone can help me interpret what I need...
I'm not sure I'm using the right terminal codes, maybe there is a command which will give me straight up the info i need to start hunting on craigslist? 

so far...
 **$ sudo lshw** gives me the following output about memory:
```
*-memory
          description: System Memory
          physical id: 26
          slot: System board or motherboard
          size: 512MiB
          capacity: 1536MiB
        *-bank:0
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: DDR1
             size: 512MiB
             width: 64 bits
        *-bank:1 
             description: DIMM DRAM Synchronous [empty]
             physical id: 1
             slot: DDR2
             width: 64 bits
        *-bank:2
             description: DIMM DRAM Synchronous [empty]
             physical id: 2
             slot: DDR3
             width: 64 bits
     *-pci
          description: Host bridge
          product: nForce2 IGP2
          vendor: nVidia Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: c1
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-nvidia module=nvidia_agp
        *-memory:0 UNCLAIMED
             description: RAM memory
             product: nForce2 Memory Controller 0
             vendor: nVidia Corporation
             physical id: 0.1
             bus info: pci@0000:00:00.1
             version: c1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0

```
etc...

and **$ sudo dmidecode --type 17** gives me this:
```
Memory Device
	Array Handle: 0x0026
	Error Information Handle: Not Provided
	Total Width: 72 bits
	Data Width: 64 bits
	Size: 512 MB
	Form Factor: DIMM
	Set: None
	Locator: DDR1
	Bank Locator: Bank0/1
	Type: DRAM
	Type Detail: Synchronous
```
it shows this 3 times, only the other two say 'no module installed' for size.

So I need DIMMs, but do they need to be 512mb or can they be anything-up-to? Is this DDR2 or DRAM - or both?!? Does 'synchronous' mean 66MHz or did I not find that bit of info? And do I need to find out the number of pins on the memory module?

Lots of questions, I know. Apologies! Knowledge and/or insight much appreciated.

---

### Post by oilchangeguy on 2008-09-16
just open the case. the ram is easy to get at in either a desktop or a laptop. you can then take a stick with you and make sure you get the right ram for your computer.

---

### Post by Jazzy_Jeff on 2008-09-16
Just goto [http://www.crucial.com](http://www.crucial.com) and use their tool to see which ram you can use. It will ask for your computer model or motherboard model. Hope this helps.

---

### Post by Sky Pixie on 2008-09-16
I don't know which speed SDRAM you need or whether it's DDR SDRAM.  There is information printed on a sticker attached to each memory module.

Not sure about the following (double checking):
You have 512 MiB installed in one slot.  Two more slots are available.  The total capacity supported by the motherboard is 1536 MiB.

Purchase two more memory sticks of 512 MiB each.

Edit #2
Please post the following part of sudo lshw:
```
*-core
       description: Motherboard
       product: P35-DS3L
       vendor: Gigabyte Technology Co., Ltd.

```

---

### Post by the badger on 2008-09-16
wow. well, I checked out crucial.com and opened up my case. these gave me two totally different results, but I think I'll stick with what my system is telling me (it's a home-built job, but not my home).

if anyone else can point me to a good, concise site which can refresh my memory (ha ha) about how to make sure I'm picking up the right RAM it would be much appreciated.

thanks :)

---

