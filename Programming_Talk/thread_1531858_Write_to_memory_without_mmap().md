---
title: "Write to memory without mmap()?"
date: 2010-07-15
forum: Programming Talk
---

### Post by MindSz on 2010-07-15
Hi,

I'm trying to do some inline assembly for an ARM processor in a C program for an embedded Linux system. The problem I'm facing is that even though I can successfully write to peripheral devices (GPIO), I find myself forced to use the mmap() to get a valid address.

I know the addresses I'm trying to write to because I have the Chip's datasheet, but if I try to do write to the address the system freezes. This leads me to believe there's a flag I'm missing or something like that.

Does anybody know a way to bypass this? Can you actually write directly to memory without MMAPing it? Do you know which flags must be activated?

Any help, any idea, and any links will be greatly appreciated.

---

### Post by rnerwein on 2010-07-15
> **MindSz said:**
> Hi,

I'm trying to do some inline assembly for an ARM processor in a C program for an embedded Linux system. The problem I'm facing is that even though I can successfully write to peripheral devices (GPIO), I find myself forced to use the mmap() to get a valid address.

I know the addresses I'm trying to write to because I have the Chip's datasheet, but if I try to do write to the address the system freezes. This leads me to believe there's a flag I'm missing or something like that.

Does anybody know a way to bypass this? Can you actually write directly to memory without MMAPing it? Do you know which flags must be activated?

Any help, any idea, and any links will be greatly appreciated.
hi folk
this is no sultion - but i can tell you with embedded sysytems i got horrible expirecnce. 
it's no standard and next is - how you call the "mmap" ??. 
embedded systems and ASM-call is a ticked to hell. 
next question - which assembler are you calling on which processor  ?? -
i think you will get a SIGSEGV - or you are running your proc as super user. if not   then it's a big  --> bug
ciiao

---

### Post by MindSz on 2010-07-15
This is what I have working right now. It compiles with gcc (for ARM) and it works fine, but I'm trying to get rid of the mmap() and call directly to the hardware address. (This is supposed to alternate between a red and green LED)

```
#include <stdio.h>
#include <sys/mman.h>
#include <fcntl.h>
#include <unistd.h>

int main(void){

  int dev_mem;
  int address;
  int g=0xfd, r=0xfe;
  int output1;

  unsigned long delay1 = 10000;
  unsigned long delay2 = 10000;

  dev_mem = open("/dev/mem", O_RDWR|O_SYNC);
  address = (unsigned long) mmap(0, getpagesize(), 
				 PROT_READ|PROT_WRITE,
				 MAP_SHARED, dev_mem,
				 0x80840000);
  
  printf("Addr: %X\n", (unsigned int) address);

  asm volatile (
	"loop1:\n"			\
	"ldr %[output1], [%[ADDR]];\n"\
	"mov r0, %[C1];\n"	    \
	"loop2:\n"		    \
	"subs r0, r0, #1;\n"	    \
	"bne loop2;\n"		    \
	"str %[RED], [%[ADDR]];\n"  \
	"b   loop1;\n"		    \
	: [out1] "=r" (output1)
	: [ADDR] "r"(address + 0x20), [RED] "r"(r), [GREEN] "r"(g), [C1] "r"(delay1), [C2] "r"(delay2)
	: "memory", "r0", "cc"
  );

  return 0;
}

```

---

### Post by jpkotta on 2010-07-16
If this is a protected memory system, then (AFAIK) the only way to do it is either the method you're using now, or to do it in the kernel.  "Protected memory" means it has an MMU and virtual addressing, which Linux needs to run (exception: uCLinux).

BTW, there is a framework in the kernel to write drivers that toggle LEDs (or really any GPIO).  You can control them from userspace through a file in /sys.

---

### Post by xb12x on 2010-07-16
> **jpkotta said:**
> BTW, there is a framework in the kernel to write drivers that toggle LEDs (or really any GPIO).  You can control them from userspace through a file in /sys.

jpkotta, can you point me to information about this framework. And do you remember the name of the file in /sys? 

thanks

---

### Post by jpkotta on 2010-07-16
> **xb12x said:**
> jpkotta, can you point me to information about this framework. And do you remember the name of the file in /sys? 

thanks

Well I did some digging and I think I found it.  Here is a patch from the kernel I was working on.

```

diff -r 470e3f497aae -r 78efb70c90ce arch/arm/mach-omap1/board-osk.c
--- a/arch/arm/mach-omap1/board-osk.c	Mon Feb 04 18:30:39 2008 -0600
+++ b/arch/arm/mach-omap1/board-osk.c	Tue Feb 05 18:33:52 2008 -0600
@@ -49,6 +49,8 @@
 #include <asm/arch/common.h>
 #include <asm/arch/mcbsp.h>
 #include <asm/arch/omap-alsa.h>
+#include <linux/leds.h>
+#include <asm/arch/led.h>
 
 static struct mtd_partition osk_partitions[] = {
 	/* bootloader (U-Boot, etc) in first sector */
@@ -173,11 +175,34 @@
 	},
 };
 
+static struct omap_led_config osk5912_led_config[] = {
+    {
+	.cdev = {
+	    .name = "osk:led0",
+	},
+	.gpio = 9,
+    },
+};
+
+static struct omap_led_platform_data osk5912_led_data = {
+    .nr_leds = ARRAY_SIZE(osk5912_led_config),
+    .leds = osk5912_led_config,
+};
+
+static struct platform_device osk5912_led_device = {
+    .name = "omap-led",
+    .id = -1,
+    .dev = {
+	.platform_data = &osk5912_led_data,
+    },
+};
+
 static struct platform_device *osk5912_devices[] __initdata = {
 	&osk5912_flash_device,
 	&osk5912_smc91x_device,
 	&osk5912_cf_device,
 	&osk5912_mcbsp1_device,
+	&osk5912_led_device,
 };
 
 static void __init osk_init_smc91x(void)
@@ -447,6 +472,10 @@
 
 	osk_flash_resource.end = osk_flash_resource.start = omap_cs3_phys();
 	osk_flash_resource.end += SZ_32M - 1;
+	if (omap_cfg_reg(W8_1610_GPIO9)) {
+	    printk(KERN_ALERT "Could not MUX ball W8 to GPIO9\n");
+	    osk5912_led_data.nr_leds = 0;
+	}
 	platform_add_devices(osk5912_devices, ARRAY_SIZE(osk5912_devices));
 	omap_board_config = osk_config;
 	omap_board_config_size = ARRAY_SIZE(osk_config);

```

As you can see, it's for the OMAP5912OSK dev board from Spectrum Digital.  The kernel was 2.6.22.

The problem is that I did this a few years ago and the details are fuzzy, so it's pretty likely that there is more to it than this.  Also, the correct way to do it very well might have changed since then anyway.  The way I figured it out was a combination of reading files in Linux's Documentation directory, Linux Device Drivers 3rd Ed., and looking at various examples in the source.

I can't remember the name of the file.  The way /sys works is when you instantiate a device or driver in the kernel, it creates several files in /sys associated with it; you can think of them as being hardlinked together.  Something in /sys would have been named "osk:led0", and something else would have been named "omap-led".  They probably would have been somewhere under /sys/bus/platform, because it was a "platform" device (Platform devices are basically uncategorized devices that are specific to a particular board or SoC).

---

### Post by xb12x on 2010-07-16
Thanks, jpkotta! I'm on the steep side of the learning curve when it comes to Linux internals.

---

