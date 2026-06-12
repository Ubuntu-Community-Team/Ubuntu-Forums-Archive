---
title: "Ubuntu 18.04 only booting in recovery mode"
date: 2020-10-26
forum: New to Ubuntu
---

### Post by foxnerdaysmoo on 2020-10-26
I recently got a new Dell Precision 3431 with a Quadro P620 NVIDIA Graphics card. I am running Ubuntu 18.04, with nvidia-driver-455 (in additional drivers app).
After reading through threads of similar problems, I have made sure my graphics drivers are up to date.
I ran 
> 
sudo add-apt-repository ppa:graphics-drivers/ppa

And selected the most recent driver in Additional Drivers; it didn't work.
If I boot normally, a flashing cursor would appear. If I press keys they will appear, then get removed.
> 
sudo lswh
           *-display UNCLAIMED
                description: VGA compatible controller
                product: GP107GL [Quadro P620]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller cap_list
                configuration: latency=0
                resources: memory:a3000000-a3ffffff memory:90000000-9fffffff memory:a0000000-a1ffffff ioport:3000(size=128) memory:c0000-dffff

        *-display UNCLAIMED
             description: Display controller
             product: UHD Graphics 630 (Desktop)
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pciexpress msi pm cap_list
             configuration: latency=0
             resources: memory:a2000000-a2ffffff memory:80000000-8fffffff ioport:4000(size=64)


---

### Post by CelticWarrior on 2020-10-26
Welcome.

Quadro P620 needs 450.xx,, not the latest version.

---

### Post by foxnerdaysmoo on 2020-10-27
Thank you! After switching from 455 to 450, it works perfectly!

---

