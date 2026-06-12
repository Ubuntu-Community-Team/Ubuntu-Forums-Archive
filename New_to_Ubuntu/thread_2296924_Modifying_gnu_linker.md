---
title: "Modifying gnu linker"
date: 2015-09-29
forum: New to Ubuntu
---

### Post by auggywonger on 2015-09-29
Hi all,

As you can guess from my post being in the "New to Ubuntu" section, I am an Ubuntu newbie.  So please bear with me.  :)

Here is the background for my issue:

I am running Ubuntu 14.04.2 LTS on Nvidia's Jetson TK1 ([http://elinux.org/Jetson_TK1](http://elinux.org/Jetson_TK1)).  This Ubuntu version is specially designed for the Jetson.  The Jetson platform has 2 GB of DRAM and 16GB of eMMC space.  I am running a graph processing framework on the Jetson and unfortunately, the graph does not fit onto the DRAM.  Basically, my framework cannot currently use malloc to assign memory for the graph since there is not enough DRAM.

My thought is that I can modify the gnu linker to specify that the DRAM as well as the space in the eMMC is available for memory allocation.  That way, malloc will work.  My belief is that I can modify the linker in accordance with [ftp://ftp.gnu.org/old-gnu/Manuals/ld-2.9.1/html_node/ld_16.html#SEC16](ftp://ftp.gnu.org/old-gnu/Manuals/ld-2.9.1/html_node/ld_16.html#SEC16).

My questions are as follows:

1) Assuming I have enough space in eMMC, would this idea theoretically work?
2) Assuming the idea could work, how do I check what address ranges I need to specify for memory allocation.  I want to use both the DRAM and eMMC space.  I read the /procl/iomem and see the "storage RAM" space listed.  Presumably, that space refers to the DRAM.  But I don't know how to find the address ranges for eMMC.

Even though I am using the Jetson platform and using a specialized version of Ubuntu, I believe that my question can just as easily apply to more mainstream computers.  Essentially, I am asking how to modify the linker to use external memory for memory allocation, if that's even possible.
  
Thanks,

Augustine

---

### Post by NathanRodriguez on 2015-09-29
Looks like this topic belongs to Programming sub-forums.

---

### Post by sandyd on 2015-09-29
You don't need to do that.
What you want is to create what is called a "swap partition".

See instructions here: [https://devtalk.nvidia.com/default/topic/764828/-hint-configure-swap-on-jetson-tk1/](https://devtalk.nvidia.com/default/topic/764828/-hint-configure-swap-on-jetson-tk1/)

You can probably create a "swap file" on the eMMC as well, if you don't want to use a seperate storage device. See [https://wiki.archlinux.org/index.php/Swap#Swap_file_creation](https://wiki.archlinux.org/index.php/Swap#Swap_file_creation) for instructions.

---

