---
title: "How to create a contiuous memory block in Linux kernel for a user application?"
date: 2015-08-18
forum: Programming Talk
---

### Post by ruwan2 on 2015-08-18
Hi,

I read the following on a PCIe card for X86 PC computer:

[COLOR=#0000ff][FONT=sans-serif]Memory allocated using malloc is not contiguous. Ubuntu Linux 12.04 doesn’t have any user mode APIs to allocate contiguous physical memory [/FONT][/COLOR][COLOR=#252525][FONT=sans-serif]

I cannot understand it because my imagination on malloc is a single block. It always returns a pointer to the beginning. I can increase the pointer to go through the whole block. If the above (non-continuous) is true, how can a pointer through regular increase or decrease 1 to go through a memory block?

Thanks,

[/FONT][/COLOR]

---

### Post by ruwan2 on 2015-08-18
Hi,

A embedded image processing PCIe card can work with PC on an Ubuntu 12.04 OS. From the below description, it looks like 4 GB is a special restriction on the Ubuntu PC memory. Could you give me more detail information about it?


Thanks,



[h=3][COLOR=#0000cd]Alternative memory allocation scheme[/COLOR][/h][COLOR=#252525][FONT=sans-serif][COLOR=#0000cd]As an alternative, the CMEM module can be configured to use reserved memory at boot time in linux. Scripts are provided to configure the amount of memory to be reserved at boot time and the driver uses the reserved memory to allocate the memory requested by application instead of dma_coherent_alloc. This method only works if the amount of physical memory present in the desktop is more than 4 GB plus the required reserved memory needed. With this scheme the driver allows allocation of buffers bigger than 4 MB.[/COLOR]



[/FONT][/COLOR]

---

### Post by QIII on 2015-08-18
Strangely, the quoted references in each of your last two posts seems to come from [here]("http://processors.wiki.ti.com/index.php/Desktop-linux-sdk_01.00.00_Development_Guide").

Is this an issue with the Texas Instruments SDK?

---

### Post by kerry_s on 2015-08-18
lol, your not by chance trying to get us to do your homework ?

my son had something similar in his college course.

---

### Post by Yellow Pasque on 2015-08-18
It's just how Linux kernel handles memory. If you want to use large chunks of physically contiguous memory, you need to work outside the kernel's 4GB memory address space (or maybe use mem= boot parameter to limit its address pool).
[http://stackoverflow.com/a/116458](http://stackoverflow.com/a/116458)

---

### Post by spjackson on 2015-08-18
The **virtua**l memory allocated by malloc **is** contiguous. In your program you use pointers to virtual addresses. The OS performs mapping between virtual addresses and physical addresses and this mechanism is transparent to you. The **physical** addresses may or may not be contiguous - you do not know. Do you need to know?

---

### Post by ruwan2 on 2015-08-18
It is absolutely not a home work. It is a self work on a new position. I have the DSP card on that link used, but not buy a PCIe adapter card yet. I really want to know Linux programming at this moment. Any comments are welcome.

Author Temujin reply helps a lot. I just know kernel has a 4GB space.

---

### Post by ruwan2 on 2015-08-19
Hi, 

I have PCIe card. TI' application not said that  

[http://processors.wiki.ti.com/index.php/Desktop-linux-sdk_01.00.00_Development_Guide](http://processors.wiki.ti.com/index.php/Desktop-linux-sdk_01.00.00_Development_Guide) 

Alternative memory allocation scheme 

As an alternative, the CMEM module can be configured to use reserved memory at  
boot time in linux. Scripts are provided to configure the amount of memory to be  
reserved at boot time and the driver uses the reserved memory to allocate the  
memory requested by application instead of dma_coherent_alloc. This method only  
works if the amount of physical memory present in the desktop is more than 4 GB  
plus the required reserved memory needed. With this scheme the driver allows  
allocation of buffers bigger than 4 MB.  

The modern PC has a lot of memory > 4 GB. I would like to know how to create  
continuous memory for the PCIe card on a computer with much larger 4 GB. 

For simplicity, I do not consider PCIe card now. 

As a practice, I want to create a desktop PC linux device memory driver, which 
provide continuous physical address memory to a user. Could you have any  
opinion on my thought? 

I had basic Linux kernel device driver experience. Years ago, I followed a  
tutorial to create a memory block driver. Here, the physical continuous  
memory looks out of control to me. 



Thanks,

---

### Post by QIII on 2015-08-19
*Merged and moved to** Programming Talk**.*

You have posted several threads dealing with the TI SDK.  I have merged them into one thread.

---

