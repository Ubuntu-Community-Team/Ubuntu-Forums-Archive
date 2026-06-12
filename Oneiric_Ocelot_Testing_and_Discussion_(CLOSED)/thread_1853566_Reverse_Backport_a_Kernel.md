---
title: "Reverse Backport a Kernel?"
date: 2011-10-02
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Martin Marshalek on 2011-10-02
So, as has been discussed ad nauseum in the Linux world, power consumption has dramatically risen in recent kernels. As a laptop user, this prevents me from realistically using anything much newer than Lucid or Maverick. I have tried Oneiric and I really think that it is going great, minus the power usage. 

So this got me thinking, would it be possible to use say, Maverick's kernel version (2.6.35 I believe) which works perfectly on my hardware in Oneiric? Would this break xorg and stuff like that or is it simply a matter of compiling an older kernel/grabbing the debs from the maverick archives?

---

### Post by xgt001 on 2011-10-02
finally!!! someone posted about this :D

ok regarding to maverick kernel... well i tried using 2.6.35-30 which i guess is the "latest" maverick kernel on oneiric install and trust me works pretty fine!!! no issues were experienced (minus the driver issues ofcourse which is very hardware dependent). personally i would suggest simply compiling your own kernel based off 2.6.37.6 source BUT myself  found it useless as i couldnt figure a way to build the custom header files... which are not required but essential if you wish to use that kernel on other machines or after reinstalling your own os...

i find 2.6.36.4 and 2.6.37.6 pretty "cool" :p

---

### Post by Martin Marshalek on 2011-10-02
That's great :) I was thinking of trying to do an install and then just enabling either the maverick or lucid repos to grab the kernel and headers from there. What kind of hardware issues were there? All my hardware works with the lucid kernel so all I would need is to make sure that Oneiric's fglrx works with an older kernel.

---

### Post by el_koraco on 2011-10-02
> **Martin Marshalek said:**
> That's great :) I was thinking of trying to do an install and then just enabling either the maverick or lucid repos to grab the kernel and headers from there. What kind of hardware issues were there? All my hardware works with the lucid kernel so all I would need is to make sure that Oneiric's fglrx works with an older kernel.

Just get it [here ]("http://www.google.com/url?sa=t&source=web&cd=1&ved=0CBwQFjAA&url=http%3A%2F%2Fkernel.ubuntu.com%2F%7Ekernel-ppa%2Fmainline%2F&rct=j&q=kernel%20ppa&ei=3f-ITriCJuea1AWLsNzjDw&usg=AFQjCNHH0Rk4RLsC0SWaJb-pEepOMDaS3w&cad=rja")
I've run the latest fglrx on .35 with no problems. If you can't boot into the Maverick kernel for some reason, try to purge fglrx and see if it helps, but I don't think you should have trouble. But the power consumption thing is blown out of proportion, it may not affect you at all, since it's only affecting a subset of users.

---

### Post by Martin Marshalek on 2011-10-02
Cool, thanks for the info on fglrx, I think I may try something like this with a Natty install later to see what happens. The issue does affect me though. Running powertop on lucid with fglrx I only consume about 7-15 watts whereas on natty with the stock kernel and fglrx I get 25-30 watts. I tried the pcie_aspm thing but nothing changed so an older kernel is really my only solution until this is fixed upstream.

---

### Post by cariboo on 2011-10-02
There other ways to get around the power consumption issue, other than reverting to an older kernel.

Give:

```
powertop --calibrate
```

a try, I've had good results from using it on my Compaq Mini 1100. 

Secondly give [Jupiter]("http://www.webupd8.org/2010/07/jupiter-ubuntu-ppa-hardware-and-power.html") a try, I haven't achieved as good result as with powertop, but my netbook doesn't have pci-e.

One warning though, Jupiter was written using mono, so if you are anti-mono, you may not want to use it.

---

### Post by Martin Marshalek on 2011-10-02
Hmm, I'll have to give Jupiter a look then. I read about it somewhere but wasn't really sure what kind of tweaks it applied. It looks promising. I'll have to check it out then before I go the old kernel route. As soon as I have a night to tinker I'll definitely give it a go. 

For the time being, Lucid with a few ppa's is doing quite nicely for productivity's sake, but I really want to get to using the new Unity since it has become quite polished since Natty and looks really great.

---

### Post by lucazade on 2011-10-03
kernels from mainline ppa are good.. only downside is they don't come with ubuntu patches like ureadahead and apparmor.
I'd use a kernel from natty or would search thru ppa, sometime some good soul recompile the kernel with the ubuntu patches in it (usually guidoic ppa)

---

