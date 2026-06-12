---
title: "Card reader won't work"
date: 2012-04-07
forum: New to Ubuntu
---

### Post by det0326 on 2012-04-07
Don't know if I'm in the right place or not if not someone please direct me to the correct place.
My problem is I can not get my card reader to work. I know that the reason it wont work is 
because there is no driver installed for the hardware. This is where the problem starts because
I don't know where to find the driver and even if I did I would not know how to install it. As you can see 
I am very new to ubuntu  and would need step by step instructions.
I have an HP DV4-1220us running on ubuntu 11.04 the hardware device is jmicron technologies sd+ms/pro+
mmc+xd  reader with jmb385 controller chip. If anybody knows where to get driver and how to install it
I would make me a happy camper.


PS
the driver is not in the synaptic package that I know of but heck I could be looking at it and would not know it.

---

### Post by nothingspecial on 2012-04-07
*Thread moved to **Absolute Beginner Talk**.*

---

### Post by alphacrucis2 on 2012-04-07
> **det0326 said:**
> Don't know if I'm in the right place or not if not someone please direct me to the correct place.
My problem is I can not get my card reader to work. I know that the reason it wont work is 
because there is no driver installed for the hardware. This is where the problem starts because
I don't know where to find the driver and even if I did I would not know how to install it. As you can see 
I am very new to ubuntu  and would need step by step instructions.
I have an HP DV4-1220us running on ubuntu 11.04 the hardware device is jmicron technologies sd+ms/pro+
mmc+xd  reader with jmb385 controller chip. If anybody knows where to get driver and how to install it
I would make me a happy camper.


PS
the driver is not in the synaptic package that I know of but heck I could be looking at it and would not know it.

Does the device show up when you do

```
sudo lshw
```

---

### Post by det0326 on 2012-04-07
Hi  alphacrucis2
yes it does actually in a group of 4 in a row as generic 0,1,2,3. With one of them being SD/MMC maybe why they call it a 5 in 1 card reader
maybe.  thanks for your concern and reply. have you had this problem before? 
           *-generic:0
                description: System peripheral
                product: SD/MMC Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0
                bus info: pci@0000:08:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list rom
                configuration: driver=sdhci-pci latency=0
                resources: irq:17 memory:91200300-912003ff memory:92600000-9260ffff
           *-generic:1 UNCLAIMED
                description: SD Host controller
                product: Standard SD Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0.2
                bus info: pci@0000:08:00.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: cap_list
                configuration: latency=0
                resources: memory:91200200-912002ff
           *-generic:2
                description: System peripheral
                product: MS Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0.3
                bus info: pci@0000:08:00.3
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=jmb38x_ms latency=0
                resources: irq:17 memory:91200100-912001ff
           *-generic:3 UNCLAIMED
                description: System peripheral
                product: xD Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0.4
                bus info: pci@0000:08:00.4
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=0
                resources: memory:91200000-912000ff

---

