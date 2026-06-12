---
title: "How to configure the RAM's location in zoom2 board"
date: 2011-05-30
forum: Programming Talk
---

### Post by difuiv250385 on 2011-05-30
Hi,
 
I know this question is not directly related to this forum.. but since I did not find the answer for this questoin posted on many other forums, I am posting it here hoping some one from us will surely clarify my doubt..(If you think I can get this answer in any perticular forum pls let me know d link..) Thnx in advance..
 
I am using zoom2 with oamp3430 chipset for android development. I have a doubt related to the address of RAM where the u-boot need to be loaded.
I am using fastboot for loading the u-boot to zoom2's nand. I just use the following command for the same,

"sudo ./fastboot flash bootloader ./u-boot.bin"
and it works absolutely fine. and on booting the phone as per the flow the u-boot is loaded to DRAM(Physical address: 0x80000000) and boots up.

But I tried loading the u-boot .bin to the RAM location directly from PC using the TRACE32/JTAG, and as the physical address of the DRAM is 0x80000000, I used the following command in TRACE32,
"data.load X:\bootloader\u-boot\u-boot.bin   0x80000000", with this I could load the image to DRAM but the system did not boot up.
Later I found from the System.map file for u-boot that 0x80E80000 corresponds to _start hence I used the command
"data.load X:\bootloader\u-boot\u-boot.bin   0x80E80000"
and this time the board booted absolutely fine.
Here my main doubt is when I do load the Image to nand using fastboot (both x-loader and u-boot), the fastboot doesnot ask any infomation about the starting address of the image(in this case 0x80E80000), then how it works that on booting the board, x-loader loads the u-boot to the address 0x80E80000 only and starts executing, from where the x-loader fetches the information that it needs to load the u-boot to 0x80E80000 location of the DRAM and start executing.
(The same thing applies to x-loader also, the _start address from system.map for x-loader is 0x40208800 and how the ROM code loads the x-loader image to 0x40208800 address of the onchip SRAM )

---

### Post by difuiv250385 on 2011-06-01
Hey why u ppl are so lazy.. jus reply atleast if this question need to be posted somewhere else.. or my understanding is wrong.. anything .. jus reply.. I am a total newbe to this forum.. hope some one understands my probs.. thnx in advance..

---

### Post by slavik on 2011-06-01
> **difuiv250385 said:**
> Hey why u ppl are so lazy.. jus reply atleast if this question need to be posted somewhere else.. or my understanding is wrong.. anything .. jus reply.. I am a total newbe to this forum.. hope some one understands my probs.. thnx in advance..
No! You do _NOT_ get to complain if you do not ask an actual question! So far, I see you describing a boot sequence/address of a devevelopment board. I do not see a single sentence ending with a question mark.

---

### Post by Petrolea on 2011-06-01
> **difuiv250385 said:**
> Hey why u ppl are so lazy.. jus reply atleast if this question need to be posted somewhere else.. or my understanding is wrong.. anything .. jus reply.. I am a total newbe to this forum.. hope some one understands my probs.. thnx in advance..

We aren't lazy. If nobody knows the answer, they usually don't reply so that's why noone has posted yet. I can't recommend a link, because I'm not into that kind of stuff. 

Also the post is badly formatted, there's so much text and no new lines. It's not really attractive to read. And what was the question again?

---

### Post by difuiv250385 on 2011-06-02
I am so sorry guys ,
I am very new to this forum so my question was not poreperly formatted, thanks a lot for your kind suggestion.
I am posting the question again with properly formatted.
 
 
I** am using zoom2 with oamp3430 chipset for android development**.
I have a doubt related to the address of RAM where the u-boot need to be loaded.
 
I am using** fastboot for loading the u-boot to zoom2's nand**. I just use the following command for the same,
 
**"sudo ./fastboot flash bootloader ./u-boot.bin"**
 
and it works absolutely fine. and on booting the phone as per the flow the u-boot is loaded to **DRAM(Physical address: 0x80000000**) and boots up.
 
But I tried loading the u-boot .bin to the RAM location directly from PC using the **TRACE32/JTAG,** and as the physical address of the DRAM is 0x80000000, I used the following command in **TRACE32,**
 
**"data.load X:\bootloader\u-boot\u-boot.bin 0x80000000",** 
 
with this I could load the image to DRAM but the system did not boot up.
Later I found from the **System.map file for u-boot that 0x80E80000** corresponds to _start hence I used the command
 
**"data.load X:\bootloader\u-boot\u-boot.bin 0x80E80000"**
 
and this time the board booted absolutely fine.
 
Here my main doubt is when I do load the Image to nand using fastboot (both x-loader and u-boot), the fastboot doesnot ask any infomation about the starting address of the image(in this case 0x80E80000), 
then how it works that on booting the board, x-loader loads the u-boot to the address 0x80E80000 only and starts executing, from where the x-loader fetches the information that it needs to load the u-boot to 0x80E80000 location of the DRAM and start executing **??????? (now this is the question :))**
 
(The same thing applies to **x-loader** also, the _start address from system.map for x-loader is **0x40208800** and how the ROM code loads the x-loader image to **0x40208800 address of the onchip SRAM** )

---

### Post by slavik on 2011-06-02
I still do not get the question ... are you asking why the start must be at 0x80E80000?

---

### Post by difuiv250385 on 2011-06-02
yes exactly, 
 
The RAM's physical address is 0x80000000 (its **256MB RAM**)then I should be able to start using the RAM location from 0x80000000 itself. But the **RAM location is mentioned as the 0x80e80000 in the system.map file** (generated during the compilation).
I could find out that this address is **configured in the config.mk file**  in the following location.
 
**"android\bootable\bootloader\u-boot\board\omap3630zoom3\config.mk" as**
**TEXT_BASE = 0X80E80000, **
 
Now I understood why I have to load the u-boot to RAM's 0x80e80000 only, 
But I want to know what are the parameters used to derive at this location.**?**
 
**In the similar way for the x-loader, the static RAM's location is configured as 0x40208800 inside the config.mk file located in x-loader folder**.

---

### Post by slavik on 2011-06-03
> **difuiv250385 said:**
> yes exactly, 
 
The RAM's physical address is 0x80000000 (its **256MB RAM**)then I should be able to start using the RAM location from 0x80000000 itself. But the **RAM location is mentioned as the 0x80e80000 in the system.map file** (generated during the compilation).
I could find out that this address is **configured in the config.mk file**  in the following location.
 
**"android\bootable\bootloader\u-boot\board\omap3630zoom3\config.mk" as**
**TEXT_BASE = 0X80E80000, **
 
Now I understood why I have to load the u-boot to RAM's 0x80e80000 only, 
But I want to know what are the parameters used to derive at this location.**?**
 
**In the similar way for the x-loader, the static RAM's location is configured as 0x40208800 inside the config.mk file located in x-loader folder**.
read CPU documentation. the first memory address it reads is dependent on CPU.

---

### Post by difuiv250385 on 2011-06-03
Hi slavik,
 
I went through the **reference manual of the OMAP3630**, all I can find is the following,
The **SDRC(SDRAM Controller**) can be connected independently to [B]two SDRAM memories.
[/B]there are **two chipselects, CS0 and CS1**,

**the start address for CS0 is always 0x8000 0000**

The start address for CS1 is defined by the SDRC.SDRC_CS_CFG[9:8] CS1STARTLOW andSDRC.SDRC_CS_CFG[3:0] CS1STARTHIGH fields.
 
Here I got only info about the start address 0x80000000 but not about the offset which leads to 0x80e80000.
 
In the source code structure I see the **TEXT_BASE=0x80e80000 entry in config.mk**(**android\bootable\bootloader\u-boot\board\omap3630zoom3\config.mk**)
and this TEXT_BASE is **used by the "mkimage"** in the following way,
 
```
 
u-boot.img: u-boot.bin
  ./tools/mkimage -A $(ARCH) -T firmware -C none \
  -a $(TEXT_BASE) -e 0 \
  -n $(shell sed -n -e 's/.*U_BOOT_VERSION//p' $(VERSION_FILE) | \
   sed -e 's/"[  ]*$$/ for $(BOARD) board"/') \
  -d $< $@


```
 
(**the above command exists in android\bootable\bootloader\u-boot\Makefile**).
 
and after the compilation I found the **"android\bootable\bootloader\u-boot\system.map" which has 0x80e80000 for _start symbol**.

I wonder how did they derive at (0x80000000 + 0x00e80000) = 0x80e80000 address and entered in config.mk file.:confused:
 
**Please go through the omap3630 reference manual if you find some time**, and help me to find the way to derive it,
**I am investigating** on it and hope it will be found.

---

### Post by slavik on 2011-06-03
The start address for CS1 is defined by the SDRC.SDRC_CS_CFG[9:8] CS1STARTLOW andSDRC.SDRC_CS_CFG[3:0] CS1STARTHIGH fields.

maybe that's the formula? (I have no idea how to read that).

---

### Post by difuiv250385 on 2011-06-07
In my case only CS0 is used and not CS1, if you look into the reference manual, it says the physical address for CS0 remains 0x80000000 always. 
I am still investigating about it.

---

### Post by difuiv250385 on 2011-06-08
I could not find any information on this doubt :( I spent about 3 days for this. 
So just dropping this topic for now.:(

---

