---
title: "Ubuntu Server 15.10: Modules not loaded at boot time"
date: 2016-02-18
forum: New to Ubuntu
---

### Post by seb22 on 2016-02-18
I am currently using Ubuntu 15.10 server (RPi optimized edition) on my RPi2 B. I also bought a display, as suggested in another question. I got the display working by hand, namely activating SPI and I2C with raspi-config and loading the proper modules with modprobe:
```
sudo modprobe flexfb  width=320  height=480  regwidth=16 init=-1,0xb0,0x0 [...]
sudo modprobe fbtft_device debug=3 rotate=90 name=flexfb speed=16000000 gpios=reset:25 [...]

```

But this doesn't work, when the lines (without sudo modprobe of course) are written into /etc/modules and the RPi is rebooted.

I also modified the /boot/config.txt by adding the following line: 
```
dtoverlay=w1-gpio-pullup,gpiopin=4,extpullup=1
```

I also went through the /etc/modprobe.d directory and the blacklist files residing there, to see if any modules I need are blacklistet. But none needed modules are.

So, after reboot, the display remains white and `lsmod` doesn't show any modules I would need:

    ```
Module                  Size  Used by
    i2c_bcm2708             5006  0
    spi_bcm2708             7670  0
    w1_gpio                 3465  0
    wire                   25632  1 w1_gpio
    cn                      4656  1 wire
    uio_pdrv_genirq         2958  0
    uio                     8215  1 uio_pdrv_genirq
    bcm2708_rng              972  0
    snd_bcm2835            19761  0
    snd_pcm                74449  1 snd_bcm2835
    snd_timer              18197  1 snd_pcm
    snd                    51646  3 snd_bcm2835,snd_timer,snd_pcm
    i2c_dev                 6059  0
    ipv6                  335227  18
```

I see the following lsmod output, after manually calling `sudo modprobe`:

    ```
Module                  Size  Used by
    fbtft_device           27245  0
    flexfb                 12647  1
    fbtft                  27780  2 flexfb,fbtft_device
    fb_sys_fops             1141  1 fbtft
    syscopyarea             2781  1 fbtft
    sysfillrect             3305  1 fbtft
    sysimgblt               1829  1 fbtft
    w1_gpio                 3465  0
    wire                   25632  1 w1_gpio
    cn                      4656  1 wire
    uio_pdrv_genirq         2958  0
    uio                     8215  1 uio_pdrv_genirq
    bcm2708_rng              972  0
    i2c_dev                 6059  0
    i2c_bcm2708             5006  0
    spi_bcm2708             7670  0
    snd_bcm2835            19761  0
    snd_pcm                74449  1 snd_bcm2835
    snd_timer              18197  1 snd_pcm
    snd                    51646  3 snd_bcm2835,snd_timer,snd_pcm
    ipv6                  335227  18

```

So I guess, after all, it's a Ubuntu/Linux question, and not directly related to raspberry pi...
Is there anything I missed?
Or do I have to load the modules by hand every time I boot the raspberry?

Thanks!

---

