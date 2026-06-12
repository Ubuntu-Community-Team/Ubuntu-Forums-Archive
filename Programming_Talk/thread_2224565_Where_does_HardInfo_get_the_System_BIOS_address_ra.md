---
title: "Where does HardInfo get the System BIOS address range from?"
date: 2014-05-16
forum: Programming Talk
---

### Post by RJSmith92 on 2014-05-16
Hello All,

First of all sorry if this is in the wrong area, it's a random question and wasn't sure where to post it  :-?

Basically where does the HardInfo application get the memory range for the system ROM. Running the app on my system and I see -


[IMG]http://s21.postimg.org/fh70vqgdz/unbuntu.png[/IMG]

I don't think my BIOS starts at 0xF0000, I think it starts at 0xE8000 and I'm just curios as to where it might be getting this memory range from?
 
Is it retrieving it from some other source or just listing that range because that is the "traditional" system BIOS range.

Any help would be appreciated,

Thanks.

---

### Post by xb12x2 on 2014-05-17
> **RJSmith92 said:**
> where does the HardInfo application get the memory range for the system ROM. 
I don't think my BIOS starts at 0xF0000, I think it starts at 0xE8000 and I'm just curios as to where it might be getting this memory range from?
 

You might be confusing the following:

1) The physical, static size of the system (motherboard) ROM.

2) The size of the system image within the ROM. There might be other images in the ROM such as graphics adapter image, etc.

3) The actual run-time size of the BIOS.

At startup the BIOS is shadowed, i.e. copied from the physical ROM and placed into RAM, because ROM accesses are extremely slow compared to RAM accesses. During the shadowing process only modules needed during run-time are copied.  Startup modules are not needed so are not shadowed/copied.

During startup a memory-map is developed and stored in RAM at a known location for the O.S. to use during its loading and initialization. The O.S. also creates its own memory-map, which I suspect is where the hardinfo program gets its information.

Look at the files in the Linux /proc directory, such as memifo, iomem, and so on.

---

### Post by RJSmith92 on 2014-05-17
Thanks for the reply xb12x2,

I understand that the BIOS is shadowed into RAM, and using a program named RWEverything I can see that BIOS data is written between the address range of 0xE8000 - 0xFFFFF. 

Both HardInfo and Device Manager in Windows shows that between 0xD0000 - 0xE7FFF is on the PCI bus which correlates with what can be seen in RWEverything, nothing is written to the address range of 0xD0000 - 0xE7FFF, but then from 0xE8000 onwards there is BIOS data.

This is why I was wondering why HardInfo shows the BIOS start address to be 0xF0000.

I have tried this on another system that has BIOS data written between 0xE0000 - 0xFFFFF and then again in HardInfo it shows the system ROM to start at 0xF0000, which makes me wonder where the application is getting this address from? I wouldn't know what file in the /proc directory to look at for this??

Thanks again.

---

### Post by xb12x2 on 2014-05-17
> **RJSmith92 said:**
> I have tried this on another system that has BIOS data written between 0xE0000 - 0xFFFFF and then again in HardInfo it shows the system ROM to start at 0xF0000, which makes me wonder where the application is getting this address from?

Well, one great thing about open-source software is that if you need to know what HardInfo is actually doing, you could easily download its sources and take a look. Or rebuild it with debug info so you could step through it while it's running/getting that memory information.

---

