---
title: "hwmon &amp; lm_sensors"
date: 2020-07-27
forum: New to Ubuntu
---

### Post by jcdenton1995 on 2020-07-27
Hello again all,

Can anyone explain how the hwmon interface under /sys works, and how this relates to lm_sensors and a machines various integrated temperature sensors?

does lm_sensors read inputs from /sys/class/hwmon or are they two entirely seperate things?

is hwmon only for dedicated integrated temperature sensors such as those in a cpu?

is lm_sensores only for the motherboards temperature sensors?

I'm confused! any help is super appreciated!

---

### Post by CatKiller on 2020-07-27
The actual documentation is [here](https://www.kernel.org/doc/Documentation/hwmon/sysfs-interface). I don't know if that will make you less confused or more confused.

For which sensors are displayed, it depends on which sensors are able to be read. I needed to compile my own out-of-tree version of it87 to be able to read all the motherboard's sensors. Without that I only get the processor (and wireless, weirdly) since those are in-tree, but with that compiled and loaded as a module I get a bunch more.

---

### Post by jcdenton1995 on 2020-07-27
> **CatKiller said:**
> I needed to compile my own out-of-tree version of it87 to be able to read all the motherboard's sensors. Without that I only get the processor (and wireless, weirdly) since those are in-tree, but with that compiled and loaded as a module I get a bunch more.

That's interesting, when I run 'sensors' I only get CPU, GPU (Ryzen 3400G) and my WiFi too, I'm not sure what other sensors there are. I do have a hwmon device named 'asus' which I assume is my motherboard, maybe the Super I/0 sensors? but it has no inputs of any kind. It is a Nuvoton chip so I would have thought their would be no problems there.

Thanks for the documentation, I'll scan through it tomorrow but I fear it may be a bit above my comprehension at this stage...

---

### Post by Yellow Pasque on 2020-07-28
```
I do have a hwmon device named 'asus' which I assume is my motherboard, maybe the Super I/0 sensors? but it has no inputs of any kind. It is a Nuvoton chip so I would have thought their would be no problems there.
```

Maybe it needs a newer kernel to work fully. What does sensors-detct look like?:
```
sudo sensors-detect
```

---

### Post by jcdenton1995 on 2020-07-28
> **Yellow Pasque said:**
> Maybe it needs a newer kernel to work fully. What does sensors-detct look like?

Interestingly today the system seems to have loaded more kernel modules, which as @CatKiller said, has changed the hwmon device numbers and screwed up my conky a little. The new modules can be seen below...

```
Driver `k10temp' (autoloaded):
  * Chip `AMD Family 17h thermal sensors' (confidence: 9)

Driver `jc42':
  * Bus `SMBus PIIX4 adapter port 0 at 0b00'
    Busdriver `i2c_piix4', I2C address 0x18
    Chip `jc42' (confidence: 6)
  * Bus `SMBus PIIX4 adapter port 0 at 0b00'
    Busdriver `i2c_piix4', I2C address 0x1a
    Chip `jc42' (confidence: 6)

Driver `nct6775':
  * ISA bus, address 0x290
    Chip `Nuvoton NCT6798D Super IO Sensors' (confidence: 9)
```

Which has obviously added some information to my 'sensors' output...

```
amdgpu-pci-0900
Adapter: PCI adapter
vddgfx:           N/A  
vddnb:            N/A  
edge:         +32.0°C  (crit = +80.0°C, hyst =  +0.0°C)

k10temp-pci-00c3
Adapter: PCI adapter
Tdie:         +32.2°C  (high = +70.0°C)
Tctl:         +32.2°C  

jc42-i2c-0-18
Adapter: SMBus PIIX4 adapter port 0 at 0b00
temp1:        +28.5°C  (low  =  +0.0°C)                  ALARM (HIGH, CRIT)
                       (high =  +0.0°C, hyst =  +0.0°C)
                       (crit =  +0.0°C, hyst =  +0.0°C)

iwlwifi_1-virtual-0
Adapter: Virtual device
temp1:        +29.0°C  

jc42-i2c-0-1a
Adapter: SMBus PIIX4 adapter port 0 at 0b00
temp1:        +29.2°C  (low  =  +0.0°C)                  ALARM (HIGH, CRIT)
                       (high =  +0.0°C, hyst =  +0.0°C)
                       (crit =  +0.0°C, hyst =  +0.0°C)
```

I don't know why this is, yesterday when I ran sensors detect it definitely recommended the nct6775 module for my super I/O, as it did just now, but the output seems to suggest it isn't loaded? I did allow sensors-detect to add the recommended modules to /etc/modules and the ran '/etc/init.d/kmod start'.

And I have no idea what the jc42 modules are for yet.

---

### Post by Yellow Pasque on 2020-07-28
What happens when you try to modprobe manually
```
sudo modprobe -v nct6775
sensors
```

jc42 is probably the temp of the RAM modules.

---

### Post by jcdenton1995 on 2020-07-29
> **Yellow Pasque said:**
> What happens when you try to modprobe manually

The nct6775 module was already loaded so I unloaded and loaded it again and received the following output...

```
sudo modprobe -v nct6775
insmod /lib/modules/5.4.0-40-generic/kernel/drivers/hwmon/hwmon-vid.ko 
insmod /lib/modules/5.4.0-40-generic/kernel/drivers/hwmon/nct6775.ko
```

However this still dowsn't seem to have changed my 'sensors' output...

```
iwlwifi_1-virtual-0
Adapter: Virtual device
temp1:        +29.0°C  

k10temp-pci-00c3
Adapter: PCI adapter
Tdie:         +26.5°C  (high = +70.0°C)
Tctl:         +26.5°C  

jc42-i2c-0-18
Adapter: SMBus PIIX4 adapter port 0 at 0b00
temp1:        +28.2°C  (low  =  +0.0°C)                  ALARM (HIGH, CRIT)
                       (high =  +0.0°C, hyst =  +0.0°C)
                       (crit =  +0.0°C, hyst =  +0.0°C)

amdgpu-pci-0900
Adapter: PCI adapter
vddgfx:           N/A  
vddnb:            N/A  
edge:         +26.0°C  (crit = +80.0°C, hyst =  +0.0°C)

jc42-i2c-0-1a
Adapter: SMBus PIIX4 adapter port 0 at 0b00
temp1:        +29.2°C  (low  =  +0.0°C)                  ALARM (HIGH, CRIT)
                       (high =  +0.0°C, hyst =  +0.0°C)
                       (crit =  +0.0°C, hyst =  +0.0°C)
```

The order is slightly different than the output in my earlier post, but apart from that all the same readings are there. I'm not too worried as all I really need at the moment is CPU / GPU temperature, although it would be nice to know why I cant get readings from all my sensors!

---

### Post by Yellow Pasque on 2020-07-29
Maybe this bug?: [https://bugzilla.kernel.org/show_bug.cgi?id=204807](https://bugzilla.kernel.org/show_bug.cgi?id=204807)

---

### Post by jcdenton1995 on 2020-07-30
> **Yellow Pasque said:**
> Maybe this bug?: [https://bugzilla.kernel.org/show_bug.cgi?id=204807](https://bugzilla.kernel.org/show_bug.cgi?id=204807)

Yeah that looks promising, it is an Asus motherboard.

Looking at the line...

```
This conflict may cause random problems and system instability
```

I'm not willing to employ the workaround as I don't need any more temps other than CPU / GPU at the moment, which I already have. I will consider this in the future when I'm doing more things with my PC that push it to it's limits, but at the moment I don't even have a dedicated graphics card and really the most intensive thing the thing does is boot as far as I can tell, I play a few older games and indie games but I'm not running AAA games at max settings or anything. In fact I haven't seen any temps go above the low 40°c at any point.

That said I will come back to this at some point in the future when I'm doing more with it so I can potentially get a full temp reading, so thanks for turning this up!

---

### Post by Yellow Pasque on 2020-07-30
> **jcdenton1995 said:**
> Yeah that looks promising, it is an Asus motherboard.
Asus doesn't have much to do with it. More importantly, it's an NCT6798D chip. Remember that in the future if Googling.

> That said I will come back to this at some point in the future when I'm doing more with it so I can potentially get a full temp reading, so thanks for turning this up!
As the bug report states, it's not likely to be fixed.

EDIT: you can try it on a LiveUSB

---

### Post by jcdenton1995 on 2020-07-30
> **Yellow Pasque said:**
> Asus doesn't have much to do with it. More importantly, it's an NCT6798D chip. Remember that in the future if Googling.

Will do, thanks.

> As the bug report states, it's not likely to be fixed.

it's actually ironic, all of users over on r/linux_gaming were telling me that I absolutely must get a motherboard with a Nuvoton branded chip or I wouldn't be able to get any temp readings whatsoever, at all, from anything. I'm not criticizing them because it was advice given freely and in good faith, but I found it really weird at the time that alot of regulars of this forum (yourself included if I remember) immediately debunked that theory, and have proven to be correct on a number of levels where a lot of users on Reddit were misinformed.

I mean purely as a point of interest, is it just that certain misinformation gets spread around specific online communities and then just becomes 'common knowledge' that everyone parrots? weird!

> EDIT: you can try it on a LiveUSB

Good idea, will do.

---

### Post by CatKiller on 2020-07-30
> **jcdenton1995 said:**
> I mean purely as a point of interest, is it just that certain misinformation gets spread around specific online communities and then just becomes 'common knowledge' that everyone parrots? weird!

People don't come here to socialise. They come here because they have a specific problem that they want to solve, or because they want to help people solve their specific problems. 

People *do* participate in other online communities to socialise, with all of the social dynamics that implies: shibboleths, competition, rivalry, and so on.

We also don't get paid to be here, so we don't need to come up with outrageous or controversial things to attract clicks and ad revenue. 

I'm sure there's plenty of stuff that we don't collectively know here yet, and there's definitely plenty of good stuff elsewhere, but there are also other dynamics at play than pure information.

---

### Post by Yellow Pasque on 2020-07-30
You do have a better chance with Nuvoton over ITE. I think once you use the acpi flag, you will see good results.

ITE has some issues. The out-of-kernel version of it87 was better than the builtin one. But even that was held back by lack of data sheets and docs, and the person maintaining it got tired of it: [https://www.phoronix.com/scan.php?page=news_item&px=IT87-Linux-Driver-Axing](https://www.phoronix.com/scan.php?page=news_item&px=IT87-Linux-Driver-Axing)

---

### Post by jcdenton1995 on 2020-07-31
[QUOTE=CatKiller]but there are also other dynamics at play than pure information[/QUOTE]

This is pretty much what I'm interested to know, I went back and edited the post with everything I have found out here and posted a few screenshots with some pointers to help people on their way who come across it in the future. I guess that's all I can do :-s

---

### Post by jcdenton1995 on 2020-07-31
> **Yellow Pasque said:**
> You do have a better chance with Nuvoton over ITE. I think once you use the acpi flag, you will see good results.

I totally accept what your saying, I'm referring more to the majority of the posters in [this thread]("https://ww.reddit.com/r/linux_gaming/comments/hf90bp/x570_motherboards_that_will_run_linux_ideally/") who were stating that if someone buys a motherboard with an ITE chip with the intention of running Linux, they will never ever be able to get any temperature readings whatsoever of anything. Not just saying that motherboards with an ITE will not receive the same level of support.

It seems some users choose their motherboard based heavily on this :???:

---

