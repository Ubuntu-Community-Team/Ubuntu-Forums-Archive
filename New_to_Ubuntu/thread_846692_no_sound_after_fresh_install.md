---
title: "no sound after fresh install"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by LRT on 2008-07-01
i just installed hardy heron and on my first boot everything was working beautifully, including sound. but 5 minutes later i rebooted the machine and now i have no sound. how can this be? i haven't changed any sound settings at all during the 5 minutes i had the computer turned on.

i know absolutely nothing about configuring sound. ANY suggestions or ideas would help me. thanks!

---

### Post by wrtpeeps on 2008-07-01
> **LRT said:**
> i just installed hardy heron and on my first boot everything was working beautifully, including sound. but 5 minutes later i rebooted the machine and now i have no sound. how can this be? i haven't changed any sound settings at all during the 5 minutes i had the computer turned on.

i know absolutely nothing about configuring sound. ANY suggestions or ideas would help me. thanks!

Does your motherboard have onboard sound, and are you using a seperate soundcard?

My issue with sound was that ubuntu was trying to use my onboard device rather than the seperate soundcard in my system.

If you do have a seperate sound card, try disabling onboard sound in the bios.

---

### Post by |{urse on 2008-07-01
click the menu > system > preferences > sound
click the tab labeled "sound" 

what that look like? 

might also be helpful if you open a terminal and type

> dmesg | tail

and paste it's output here

---

### Post by LRT on 2008-07-01
this is a laptop. i have onboard sound.

dmesg | tail 

[   59.231444] [drm] Initialized drm 1.1.0 20060810
[   59.245791] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[   59.245809] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   59.246653] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   59.246880] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   59.247182] [drm] Initialized i915 1.6.0 20060119 on minor 1
[   59.318634] NET: Registered protocol family 17
[   89.905427] NET: Registered protocol family 10
[   89.906698] lo: Disabled Privacy Extensions
[   93.283510] eth0: no IPv6 routers present

i'm not sure if this tells me anything...

---

### Post by LRT on 2008-07-02
ok i got sound working after i unmuted everything in the alsamixer gui. but now when i rebooted i have no sound again and everything from the alsamixer is still unmuted.

---

### Post by LRT on 2008-07-03
no ideas??? is this problem really that hard???

---

### Post by fiddledeedee on 2008-07-10
I'm having similar problems, the sound wasn't an issue in ubuntu 6.x. Ever since the fresh install of 8.04 I get no sound no matter what media file I play.

---

