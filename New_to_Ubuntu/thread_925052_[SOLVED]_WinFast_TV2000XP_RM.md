---
title: "[SOLVED] WinFast TV2000XP RM"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by vasiauvi on 2008-09-20
Hello all,
I know that with this topic are a lot of threats.I have read a lot about this.
First of all I had to say that the tvruner worked well on Ubuntu 7.10 and after I upgradet to 8.04 also worked well.
After the system updated the kernel the tvtuner stoped working.
I can put all this listing: lspci -v,dmesg, lsmod .

Can anybody help me specific for my PC and tvtuner?
I think I am loosing my mind, I was so happy that I have reached to watch tv on 7.10 and no on 8.04 I can't anymore!!! :(:(:(:confused:

Please help me!!!!
```
lspci
```
```
00:0a.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
00:0a.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)

```

```
dmesg
```

```
 bttv: driver version 0.9.17 loaded
[   42.663895] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   42.663977] bttv: Bt8xx card found (0).
[   42.664006] ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 18 (level, low) -> IRQ 19
[   42.664020] bttv0: Bt878 (rev 17) at 0000:00:0a.0, irq: 19, latency: 32, mmio: 0xfa000000
[   42.664203] bttv0: detected: Leadtek TV 2000 XP [card=34], PCI subsystem ID is 107d:6609
[   42.664208] bttv0: using: Leadtek WinFast 2000/ WinFast 2000 XP [card=34,insmod option]
[   42.664248] bttv0: gpio: en=00000000, out=00000000 in=003ff502 [init]
[   42.664290] bt878 #0 [sw]: Test OK
[   42.664589] bttv0: tuner type=56
[   42.664594] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[   42.665087] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   42.665557] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   42.698199] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   42.953058] tuner: disagrees about version of symbol tea5767_attach
[   42.953067] tuner: Unknown symbol tea5767_attach
[   42.953232] tuner: Unknown symbol tda8290_probe
[   42.953298] tuner: Unknown symbol tda8290_attach
[   42.953607] tuner: disagrees about version of symbol simple_tuner_attach
[   42.953611] tuner: Unknown symbol simple_tuner_attach
[   42.953660] tuner: disagrees about version of symbol microtune_attach
[   42.953664] tuner: Unknown symbol microtune_attach
[   42.953858] tuner: disagrees about version of symbol tea5761_attach
[   42.953862] tuner: Unknown symbol tea5761_attach
[   42.955396] bttv0: registered device video0
[   42.955428] bttv0: registered device vbi0
[   42.955458] bttv0: registered device radio0
[   42.955480] bttv0: PLL: 28636363 => 35468950 .. ok
[   42.987163] input: bttv IR (card=34) as /devices/pci0000:00/0000:00:0a.0/input/input6
[   43.266496] bt878: AUDIO driver version 0.0.0 loaded
[   43.266557] bt878: Bt878 AUDIO function found (0).
[   43.266579] ACPI: PCI Interrupt 0000:00:0a.1[A] -> GSI 18 (level, low) -> IRQ 19
[   43.266589] bt878_probe: card id=[0x6609107d], Unknown card.
[   43.266592] Exiting..
[   43.266597] ACPI: PCI interrupt for device 0000:00:0a.1 disabled
[   43.266607] bt878: probe of 0000:00:0a.1 failed with error -22

``` 
and
```
lirc_dev: IR Remote Control driver registered, major 61 
[   73.003111] ivtv:  Start initialization, version 1.1.0
[   73.003529] ivtv:  End initialization
[   73.005054] lirc_pvr150: no version for "lirc_unregister_plugin" found: kernel tainted.
[   73.174585] lirc_pvr150: bt878 #0 [sw]: no devices found
[   93.332599] bttv0: PLL can sleep, using XTAL (28636363).
[   93.654151] bttv0: SCERR @ 1f2f7014,bits: HSYNC FDSR SCERR*
[   93.904516] bttv0: PLL: 28636363 => 35468950 .. ok
[  191.682814] bttv0: timeout: drop=320 irq=7187/7187, risc=1f2f703c, bits: HSYNC OFLOW
[  191.682937] bttv0: reset, reinitialize
[  191.682967] bttv0: PLL: 28636363 => 35468950 . ok
[  912.633956] bttv0: PLL can sleep, using XTAL (28636363).
[  912.909969] bttv0: PLL: 28636363 => 35468950 .. ok
[  955.113219] bttv0: PLL can sleep, using XTAL (28636363).
[  955.308474] bttv0: PLL: 28636363 => 35468950 .. ok
[ 2030.274760] bttv0: timeout: drop=977 irq=14837/14837, risc=15af905c, bits: HSYNC FDSR
[ 2030.275031] bttv0: reset, reinitialize
[ 2030.275066] bttv0: PLL: 28636363 => 35468950 . ok
[ 2143.498041] bttv0: timeout: drop=1509 irq=16410/16410, risc=1f2f703c, bits: VSYNC HSYNC FBUS FDSR
[ 2143.498342] bttv0: reset, reinitialize
[ 2143.498378] bttv0: PLL: 28636363 => 35468950 . ok
[ 2158.035635] bttv0: timeout: drop=1591 irq=16608/16608, risc=1eeee03c, bits: VSYNC HSYNC FBUS FDSR
[ 2158.035933] bttv0: reset, reinitialize
[ 2158.035967] bttv0: PLL: 28636363 => 35468950 . ok
[ 1406.566767] bttv0: PLL can sleep, using XTAL (28636363).
[ 1406.759894] bttv0: PLL: 28636363 => 35468950 .. ok
[ 1663.731493] bttv0: PLL can sleep, using XTAL (28636363).
[ 1663.932239] bttv0: PLL: 28636363 => 35468950 .. ok

```

:confused:

---

### Post by vasiauvi on 2008-09-20
No one can help me?:(

---

### Post by bumanie on 2008-09-20
If I were you, I'd boot with the previous kernel that worked. I have no sound on kernel 2.6.24-21-generic, but it works fine on kernel 2.6.24-18-generic, so I boot with that. Try the last working kernel and put a bug report into launchpad.

---

### Post by vasiauvi on 2008-09-20
I have booted on the other kernel that I have: 2.6.22-14 geberic (i don't have kernel 2.6.24-18-generic) and a message appeared: something with video card. The resolution was on 800X600, and the windows didn't have Close,Minimise,Maximize buttons, I couldn't move the windows and the problem is that now, when I have booted again on 2.6.24-21 generic the resolution is good but the windows are the same.I can't do nothing :((. What is wrong??

---

### Post by vasiauvi on 2008-09-20
Seems it was a problem with compiz.Now I have resolved this problem.
I have opened Kdetv and now I have sound, but not video.
This is the error:
"Unable ti grab video.
Video display is not possible with the current plugin configuration.Try playing with the configuration options of the V4L2 plugin"

How can I resolve this????

---

### Post by vasiauvi on 2008-09-22
Nobody knows haw can I resolve this?
This are the logs for :
dmesg: [http://paste.ubuntu.com/48863/](http://paste.ubuntu.com/48863/)
and kern.log
[http://paste.ubuntu.com/48862/](http://paste.ubuntu.com/48862/)

---

### Post by vasiauvi on 2008-09-26
Ok.
I give up!:(

---

### Post by adrian.todireanu on 2008-12-29
Go [HERE]("http://ubuntuforums.org/showthread.php?t=647129")!!!
if you're still interested.

---

