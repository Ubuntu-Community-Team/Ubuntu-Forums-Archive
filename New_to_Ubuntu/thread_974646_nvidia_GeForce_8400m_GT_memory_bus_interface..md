---
title: "nvidia GeForce 8400m GT memory bus interface."
date: 2008-11-07
forum: New to Ubuntu
---

### Post by Kosimo on 2008-11-07
Hello guys. 
I am running Intrepid, with the latest nvidia 177.80 drivers (from official repos).
There is any way to discover the video memory bus interface?
I know that the official nvidia webpage says that the 8400m GT should have a 128bit interface, but on windows all programs, like gpuz (and even nvidia official drivers) says that I have a 64bit...
So, I'm wondering if anybody knows some way to check this if is possible on linux.

Thank you in advance.

---

### Post by ibuclaw on 2008-11-07
```
sudo lshw -C display
```
Should give you the information you need.

Here's my output:
> 
  *-display               
       description: VGA compatible controller
       product: GeForce 8400M GS
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=nvidia latency=0 module=nvidia

Is this what you were asking for?

Regards
Iain

---

### Post by Kosimo on 2008-11-07
> **tinivole said:**
> ```
sudo lshw -C display
```
Should give you the information you need.

Here's my output:

Is this what you were asking for?

Regards
Iain

Exactly. I was looking for this ;)

```
  *-display               
       description: VGA compatible controller
       product: G86M [GeForce 8400M GT]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=nvidia latency=0 module=nvidia

```

So, I am totally disappointed with nvidia as they lied.

[http://www.nvidia.com/object/geforce_8400M.html](http://www.nvidia.com/object/geforce_8400M.html)
Here says that the 8400m GT HAVE a 128bits interface, but I only have 64bits.

---

### Post by ibuclaw on 2008-11-07
Hmm... that is interesting.

[SNIP]
On second thought, it could be the drivers you are using...

Nvidia, for one reason or another may be lagging behind on the 8400GT implementation, so the kernel instruction to utilise the full 128bit width of your bus isn't present at this current time.

I cannot think of any other reason why it could be like that.

Regards
Iain

---

### Post by Kosimo on 2008-11-08
> **tinivole said:**
> Hmm... that is interesting.

[SNIP]
On second thought, it could be the drivers you are using...

Nvidia, for one reason or another may be lagging behind on the 8400GT implementation, so the kernel instruction to utilise the full 128bit width of your bus isn't present at this current time.

I cannot think of any other reason why it could be like that.

Regards
Iain

I wouldn't think that..  It also happens in Windows with latest official drivers.
The only reasonable explanation for this is that my videocard has a simple (and cheaper) 64bit bus.  As I said: nVidia=Liers

---

