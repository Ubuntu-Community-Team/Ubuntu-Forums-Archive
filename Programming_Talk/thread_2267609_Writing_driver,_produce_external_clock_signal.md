---
title: "Writing driver, produce external clock signal?"
date: 2015-03-02
forum: Programming Talk
---

### Post by pgib8 on 2015-03-02
Hi, I'm trying to write a camera driver. I need to provide a clock to the camera and I'm not sure how to do this.
I tried something like this:
```
my_xclk = clk_get(NULL, "cam_xclk"); 
clk_enable(my_xclk);
```
(Error checking is in the original code)


I'm missing a link between this code and an actual pin, or is the clk struct already tied to a pin?
Btw. I'm using Gumstix Overo EarthSTORM and the pin I want to use is c25 (CAM_XCLKA).


Maybe someone knows a little about this and can point me into the right direction?

---

### Post by ofnuts on 2015-03-03
Your question is missing a lot of context. Would that be for a Raspberry Pi? If so you'll have a better luck in a forum dedicated to it...

---

### Post by pgib8 on 2015-03-06
> **ofnuts said:**
> Your question is missing a lot of context. Would that be for a Raspberry Pi? If so you'll have a better luck in a forum dedicated to it...
I posted in a bunch of forums and you're the only one that even replied, so thanks for that. It's not a Raspberry Pi, it's a Gumstix Overo. It's similar but newer processor. The Raspberry Pi (at least from my recent knowledge) has an ARM11 processor (ARMv6 core architecture) and the Overo has a Cortex-A8 processor (ARMv7 core architecture).

In any case, I figured out the solution and will post the code after a thorough cleanup.

---

### Post by pgib8 on 2015-03-06
So it literally took me 30 hours to get a simple clock output from the ISP.
I was originally trying to work with what Linux had to offer but it turned into a nightmare. I cut through the red tape by controlling the registers directly. This is my starting point for writing a camera driver for the OV2640, and again, this is for the Gumstix Overo EarthSTORM with AM3703 processor.
```

[FONT=arial]// Processor AM3703 (AM/DM37x Multimedia Device)[/FONT]
[FONT=arial]// Enable clock output for camera (XCLK) on pin C25 (cam_xclka)[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]static void __iomem* my_io;[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]int init_module(void) {[/FONT]
[FONT=arial]  unsigned int i;[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]  //Step 1: Configure pin-mux to use cam_xclka function (as opposed to gpio_96).[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]  my_io = ioremap(0x48002110, SZ_1);[/FONT]
[FONT=arial]  i = ioread32(my_io);[/FONT]
[FONT=arial]  i &= ~(0xffff0000); //CONTROL_PADCONF_CAM_XCLKA[15:0][/FONT]
[FONT=arial]  iowrite32(i, my_io);[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]  //Step 2: Enable clocks and power of the ISP (Image Signal Processor).[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]  my_io = ioremap(0x48004F10, SZ_1);[/FONT]
[FONT=arial]  iowrite32(0x01, my_io); //enable L3/L4 interconnect clocks for camera interface.[/FONT]
[FONT=arial]  my_io = ioremap(0x48004F48, SZ_1);[/FONT]
[FONT=arial]  iowrite32(0x02, my_io); //wake-up transition for camera clock domain.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]  my_io = ioremap(0x48306FE0, SZ_1);[/FONT]
[FONT=arial]  iowrite32(0x30107, my_io);  //turn on power to camera core domain[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]  //Step 3: Configure CAM_MCLK which comes from DPLL4 M5.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]  my_io = ioremap(0x48004F40, SZ_1);[/FONT]
[FONT=arial]  iowrite32(0x1E, my_io); //CAM_MCLK is DPLL4 clock divided by 30[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]  my_io = ioremap(0x48004D00, SZ_1);[/FONT]
[FONT=arial]  i = ioread32(my_io);[/FONT]
[FONT=arial]  i &= ~(1 << 30);        //power-up DPLL4_M5_CLK[/FONT]
[FONT=arial]  iowrite32(i, my_io);[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]  my_io = ioremap(0x48004F00, SZ_1);[/FONT]
[FONT=arial]  iowrite32(0x01, my_io); //enable CAM_MCLK[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]  //Step 4: Turn on cam_xclka[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]  my_io = ioremap(0x480BC050, SZ_1);[/FONT]
[FONT=arial]  i = ioread32(my_io);[/FONT]
[FONT=arial]  i &= ~0x0000001F;  //clear DIVA[4:0] (xclka divisor)[/FONT]
[FONT=arial]  i |= 0x1E;         //set DIVA, cam_xclka = CAM_MCLK divided by 30[/FONT]
[FONT=arial]  iowrite32(i, my_io);[/FONT]
[FONT=arial]  //Note: DIVB[9:5] can be used to turn on cam_xclkb.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]  //Note: On my system the clock came out at 7.2MHz[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]  return 0;[/FONT]
[FONT=arial]}[/FONT]

```

---

