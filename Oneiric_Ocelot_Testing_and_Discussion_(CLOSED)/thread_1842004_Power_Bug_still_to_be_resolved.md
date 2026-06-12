---
title: "Power Bug still to be resolved"
date: 2011-09-10
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by xgt001 on 2011-09-10
Oneiric fully Updated
reporting from powertop here and the power consumptions are as follows
upto - 37 W - Kernel 3.0.0.10 (default)
22 W max kernel 2.6.36.4 (Ubuntu generic from site)

ATI Mobility Radeon 6370 with fglrx,
Core i3 370 M, 3 gb DDR3


i still find it a major concern as Unity is most useful for us Laptop users....i know this is an Upstream issue but still aint no good when Ubuntu is munching away power :(

Bug #760131 reports that its yet to be fixed....

---

### Post by fjgaude on 2011-09-10
> **xgt001 said:**
> Oneiric fully Updated
reporting from powertop here and the power consumptions are as follows
upto - 37 W - Kernel 3.0.0.10 (default)
22 W max kernel 2.6.36.4 (Ubuntu generic from site)

ATI Mobility Radeon 6370 with fglrx,
Core i3 370 M, 3 gb DDR3


i still find it a major concern as Unity is most useful for us Laptop users....i know this is an Upstream issue but still aint no good when Ubuntu is munching away power :(

Bug #760131 reports that its yet to be fixed....

Fully updated doesn't mean much when we have almost five weeks before release. Lots of work still left to accomplish.

---

### Post by _d_ on 2011-09-10
> **fjgaude said:**
> Fully updated doesn't mean much when we have almost five weeks before release. Lots of work still left to accomplish.

I'm pretty sure OP meant that Oneiric is fully updated to today or whenever the last set of related updates were available. :)

---

### Post by fallenshadow on 2011-09-10
I am very worried about 11.10 sucking even more power than 11.04. Im afraid to upgrade on my netbook as battery life is bad enough as it is already.

I also find it runs very hot and the fan is nearly constantly going to keep the heat down. :(

---

### Post by gunksta on 2011-09-10
To me, one major goal of Ubuntu is to make Linux available and useful for non-geek consumers. I know the problem is upstream, and Canonical does not focus many resources on kernel development (clearly, Canonical focuses on other things) but this rampant power consumption makes it difficult for all users who choose to use mobile devices. Battery life on my Thinkpad X220 is just not acceptable right now. I'd be willing to jump ship to a another distro, but I know the problem will just follow me.

Michael Larabel over at Phoronix has done a lot to document the issue and has even shown when the problems were introduced. I don't see why this isn't seen as a major problem by Canonical/Red Hat/etc. I may have to downgrade my laptop in order to get decent batter life out of the system and that's ridiculous.

---

### Post by QCompson on 2011-09-10
> **gunksta said:**
>  I don't see why this isn't seen as a major problem by Canonical/Red Hat/etc. I may have to downgrade my laptop in order to get decent batter life out of the system and that's ridiculous.
Completely agree. I don't know if there is any easy way to address the priority structure (given how decentralized it is and the number of companies/individuals involved), but it would be nice if more developer focus was used on improving things like power management in the kernel versus things like... oh say, creating another desktop shell.

---

### Post by effenberg0x0 on 2011-09-10
There's an interesting article + chart here:
[http://www.phoronix.com/scan.php?page=article&item=linux_mobile_uffda&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_mobile_uffda&num=1)

I installed Ubuntu Jaunty on a Thinkpad in 2009 and remember to have worked a little on improving its power consumption and succeeded. Looking at my bookmarks, I see I have followed instructions from the ThinkWiki, posted at: 

[http://www.thinkwiki.org/wiki/How_to_reduce_power_consumption](http://www.thinkwiki.org/wiki/How_to_reduce_power_consumption)

So, I can tell that tweaking things a little you can get a very decent power-consumption, because I did back then.
I guess most of the advice there is probably still valid. Aside from compiling a new kernel or patching it, which is not something I would advice anyway, the rest of the settings are pretty quick and easy to implement. 

Maybe you could give a try to some of the tweaks mentioned there and post back the sort of improvement you have achieved? 

Regards,
Effenberg

---

### Post by cariboo on 2011-09-10
> **xgt001 said:**
> Oneiric fully Updated
reporting from powertop here and the power consumptions are as follows
upto - 37 W - Kernel 3.0.0.10 (default)
22 W max kernel 2.6.36.4 (Ubuntu generic from site)

ATI Mobility Radeon 6370 with fglrx,
Core i3 370 M, 3 gb DDR3


i still find it a major concern as Unity is most useful for us Laptop users....i know this is an Upstream issue but still aint no good when Ubuntu is munching away power :(

Bug #760131 reports that its yet to be fixed....

Have you run:

```
sudo powertop --calibrate
```

To see if there is a difference?

---

### Post by xgt001 on 2011-09-11
> **cariboo907 said:**
> Have you run:

```
sudo powertop --calibrate
```

To see if there is a difference?

hey thanks a lot!!! it makes my power consumption go down as much as upto 12W!!! 
(though its on 2.6.36.4 kernel from Ubuntu Kernel tree and backlight gets too dim though:D)


as far as switching distros... it will be totally useless i guess... as all the distros are coming up with 3.0.x kernel and most AFAIK dont even have a proper bug report about the issue...

(i am just 19 so i dont have much knowledge forgive me if i am ignorant :p)for a workaround you could 

1) custom compile a kernel based on 2.6.37 or earlier (but you would miss out one or the other key module and you will have to recompile again ...which is not so beautiful experience :p and so far i have failed to generate custom headers which are necessary if you want to reinstall those custom kernels in a fresh Ubuntu install)

2) use older kernels from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) which will work pretty well for Intel/(Nvidia?) laptops...
3) sadly there are very few kernels which boot up on ATI laptops ...this kernel "Just works"..[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36.4-natty/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36.4-natty/)

but you will have to take care of Broadcom wifi by using Proprietary drivers...also i recommend using fglrx with these older kernels... (radeon driver support has been fantastic in 3.0.x and up)

---

### Post by alexvy13 on 2011-09-11
I edited the ma confit file for Bluetooth so it wouldn't start at boot up and I've been having better power efficiency, will try the powertop validate thing later but will it work with the latest kernels?

---

### Post by gunksta on 2011-09-11
My biggest complaint with powertop is that while it does let me improve my battery life, the changes are not persistent. Before enabling the tunables via powertop, my laptop reportedly uses 19-20 watts. After enabling all of the tunables, my laptop reportedly uses 12-13. That's a real improvement, but the improvement is ephemeral. When I reset my computer, everything goes back to the way it was. Not ideal. I don't want to run powertop every time I unplug my laptop. More to the point, I want to use my laptop for work, not waste my time fiddling with powertop/etc.

I looked at the mailing list for powertop, and it seems that the devs aren't interested in creating a system to automate the changes. The facts are simple - mobile devices are selling faster than desktops. Users want energy efficient operating systems. Clearly, powertop knows how to decrease power usage.

I just don't see why this has to be so complicated. It should be as simple as selecting a power profile.

---

### Post by gunksta on 2011-09-11
While this needs to be automated / tied to a GUI or something, I think something like this is a big step in the right direction:

[http://docs.redhat.com/docs/en-US/Red_Hat_Enterprise_Linux/6/html/Power_Management_Guide/tuned-adm.html](http://docs.redhat.com/docs/en-US/Red_Hat_Enterprise_Linux/6/html/Power_Management_Guide/tuned-adm.html)

It would be easy to take this and add a GUI wrapper around this that would let a user change the computer's profile. In fact, if I had an easy to use control, it might be even better than doing this automatically, in case I needed the computer to operate at full speed briefly while unplugged.

---

