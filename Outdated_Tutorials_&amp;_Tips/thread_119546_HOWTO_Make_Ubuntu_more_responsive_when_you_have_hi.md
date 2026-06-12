---
title: "HOWTO: Make Ubuntu more responsive when you have high disk IO"
date: 2006-01-19
forum: Outdated Tutorials &amp; Tips
---

### Post by dcstar on 2006-01-19
Ubuntu defaults to the "Anticipatory" IO scheduler on boot up, when there is heavy disk IO by processes or applications running in background this can cause response issues that can be allievated by changing to "Completely Fair Queuing" IO.

I have taken these instructions (and take no credit for them!) from the thread at:
[http://ubuntuforums.org/showthread.php?t=119220](http://ubuntuforums.org/showthread.php?t=119220)

[I]To have the scheduler set to cfq on boot, pass **elevator=cfq** to the kernel.

You can edit /boot/grub/menu.lst and add it to the kernel line for your current kernel, and add it to the end of the #nonaltoptions line to have it automatically applied to future installed kernels (do not remove the # at the beginning of the line!).[/I]

For some related documentation for those who are curious about the difference between the "Completely Fair Queuing" or "Anticipatory" IO schedulers:

[http://www.redhat.com/magazine/008jun05/features/schedulers/](http://www.redhat.com/magazine/008jun05/features/schedulers/)

---

### Post by stanz on 2006-02-08
[I]Hi dcstar...
I'm not sure I'm reading this right.   It's '2' inserts?

1:**You can edit /boot/grub/menu.lst and add it to the kernel line for your current kernel,**
[i]Which is after the 'defaults' section?
and again; after : quiet splash? 
and then...
2:** and add it to the end of the #nonaltoptions line to have it automatically applied to future installed kernels (do not remove the # at the beginning of the line!).**
I'm pretty much doing this, asap~ guess i'll leave the post, anyway!  :-k
Thanks much!
[/I]

---

### Post by dcstar on 2006-02-08
> **stanz][I]Hi dcstar...
I'm not sure I'm reading this right.   It's '2' inserts?

1:**You can edit /boot/grub/menu.lst and add it to the kernel line for your current kernel,**
[i]Which is after the 'defaults' section?
and again said:**
> 
Yes, add it to your current kernel boot line to use now, and put it in the "#nonaltoptions" place if don't want to manually have to redo it after a kernel upgrade.

---

### Post by stanz on 2006-02-09
Hi dcstar,
Thanks for the info & reply. That was getting 'pretty deep', for me, not making
changes like that.
I'm trying to figure out, why my system takes sooo long to boot & load up.
It's close to a minute, with firefox taking longer to load, which don't seem right.
This is what brings me here~ trying to figure this out.

Thanks again!

---

### Post by GoldBuggie on 2006-02-10
Thank you for the howto. I did not know about these options in linux and I was actually looking for something similar since I have a tendency to have a lot of apps doing background work while I surf and such.

---

### Post by dcstar on 2006-02-10
[QUOTE=GoldBuggie]Thank you for the howto. I did not know about these options in linux and I was actually looking for something similar since I have a tendency to have a lot of apps doing background work while I surf and such.[/QUOTE]
Let us know if it makes a difference to you.

---

### Post by geofs on 2006-04-16
Ok,

To verify:

```
# cat /sys/block/hd*/queue/scheduler
noop [anticipatory] deadline cfq
noop [anticipatory] deadline cfq
noop [anticipatory] deadline cfq

```

To change it on the fly:

```
# echo cfq > /sys/block/hda/queue/scheduler
# echo cfq > /sys/block/hdb/queue/scheduler
# echo cfq > /sys/block/hdc/queue/scheduler
# cat /sys/block/hd*/queue/scheduler
noop anticipatory deadline [cfq]
noop anticipatory deadline [cfq]
noop anticipatory deadline [cfq]

```

---

### Post by dcstar on 2006-04-16
And to add to the theme, I have recently custom compiled the 2.6.16 kernel and actually set this option as the default in my system (actually didn't compile the code for the others, wasn't going to use them anyway!).

BTW, there seem to be a few options in regards to trading off desktop responsiveness versus "under the hood" performance when it comes to building your own kernel, this sort of thing could be worth looking into for those who do need different things to what is built into the standard Ubuntu kernels.

---

### Post by LordMau on 2006-07-27
Hello, while mucking around my old dist-upgrade menu.lst to import to a fresh install of dapper, I noticed that the **#nonaltoptions** line is now missing, and the "elevator=cfq" option was appended to the **#defoption** line
```
# defoptions=quiet splash elevator=cfq
```

Is this now the default? If so guess this howto needs an update or addendum? Maybe in breezy and lower it's still the same.

---

### Post by andrewski on 2006-09-10
> **LordMau said:**
> Hello, while mucking around my old dist-upgrade menu.lst to import to a fresh install of dapper, I noticed that the **#nonaltoptions** line is now missing, and the "elevator=cfq" option was appended to the **#defoption** line
```
# defoptions=quiet splash elevator=cfq
```

Is this now the default? If so guess this howto needs an update or addendum? Maybe in breezy and lower it's still the same.
So it would seem.  Could the howto be updated to reflect this?

---

### Post by jdong on 2006-09-10
Just to add as a note, Edgy Eft (6.10), the next Ubuntu release, will default to the CFQ IO scheduler for the desktop, Deadline on the server.

Note that CFQ will improve IO response times, but likely lower overall disk throughput because more seeking will take place.

Every computer is different while you might find CFQ works great for you, someone else might get better results with AS.

---

### Post by Xk2c on 2006-09-10
Hello

nice thread  :) 

I was also wandering about this elevator thing since i read about it some time ago.
I have tried elevator=cfq but that seem to reduce my system speed
e.g. throughput via usb(2) to external disk reduces ~50% with cfq here.
So then i went back to standard dapper elevator.

Now after reading here i have tried elevator=deadline which seems to be really faster.
but as a tradeoff the disk seems to make more noise -> which could reduce disk lifetime?? (i am braded with this...)

Any one a idea about that?

TIA

---

### Post by jdong on 2006-09-10
> **Xk2c said:**
> 
but as a tradeoff the disk seems to make more noise -> which could reduce disk lifetime?? (i am braded with this...)

Any one a idea about that?

TIA
The deadline IO scheduler does not make any attempts to reorder/regroup disk access to help reduce seeking (as its priority is to service the request immediately). More seeking could potentially cause more wear and tear to the drive, though I would expect other unpredictable factors to be more likely to cause the eventual demise of your drive :(

---

### Post by jdong on 2006-09-10
> **Xk2c said:**
> 
but as a tradeoff the disk seems to make more noise -> which could reduce disk lifetime?? (i am braded with this...)

Any one a idea about that?

TIA
The deadline IO scheduler does not make any attempts to reorder/regroup disk access to help reduce seeking (as its priority is to service the request immediately). More seeking could potentially cause more wear and tear to the drive, though I would expect other unpredictable factors to be more likely to cause the eventual demise of your drive :(

---

### Post by Xk2c on 2006-09-11
Thanks for the reply.  :) 

I did some short tests to compare elvator=AS and deadline here
(bootime and backup)

it seems that AS is still the best working here, when it comes to throuput in combination with system responsivness.

I have tested edgy and it is really faster then dapper.
I´ll have a look what they did there.

---

### Post by HAARP on 2006-09-11
*removes yet another item from todo list*

Thanks man, now I can copy stuff and use the system at the same time!

---

