---
title: "Is Linux ready for Vista-influenced hardware?"
date: 2006-08-09
forum: Other OS Talk
---

### Post by mozetti on 2006-08-09
Referencing [this Extremetech.com article](http://www.extremetech.com/article2/0%2C1697%2C2000438%2C00.asp) discussing the influence MS & Vista have had on computer hardware. Will the current linux kernel/modules be capable of using some of the new hardware that will come out to work with Vista, like crypto-ROMs (HD-DVD, Blu-Ray, Cable-card), Mobos with embedded flash, and hybrid hard drives?

Will the hardware be usable, even if it doesn't support the new technologies immediately? For example, if I bought a new mobo with embedded flash memory & a crypto-ROM, would I be able to use it as a "standard" mobo if Linux didn't support the new features yet? Would Linux gain the same efficiencies from technologies like embedded mobo flash memory that Vista does? Would Linux want to use technologies like using USB-flash drives as an extension of the kernels available non-volatile memory? Are there efforts already underway to incorporate this kind of support into the kernel/modules? 

As a relatively new Linux user, I was just wondering what impact hardware changes resulting from MS's OS dominance might have on Linux. Your thoughts?

---

### Post by maniacmusician on 2006-08-09
Well, I'd have to say that unless the basic architecture of mobos changes radically, we should be fine. I think at the worst we'd have unrecognizable inputs that the system would have to ignore. I mean, the protocols for the way the current hardware is handled certainly won't change...there will still be PCI slots, IDE interfaces, and they will still be wired the same way as before. So i don't foresee any big problems...except for the dissapointment of not being able to immediately use the technology of course. not that I'd be able to afford it or anything.

I'm not a big expert on OS architecture, but this is the gut feeling I get from the situation; but only in the near future. The kind of stuff that they talk about at Extremetech won't catch on for a while yet. You'll probably see those on only the most high end systems. but when that *does* happen, we will definitely have to adapt to it. For one thing, we'll have to work on developing better support for 64-bit systems, as they will clearly come into dominance in the next couple of years.

We can already handle stuff like dual-core processors, and with a little big of haggling, even advanced 3D graphics and good video processing, but we're probably not in good enough shape to take on DirectX 10 capable video cards. It's safe to say that in at least 3 years, trying to use something like Dapper for a high-end system would probably be futile; but I don't think we have to worry. we have great programmers and some really smart people working on Ubuntu. I have no doubt that by the time the technology comes out, we'll be ready for it, *if* the team makes that their focus. In the past, there has been a lot of emphasis on getting low-end systems to run smoothly. Now, there's more of a focus on current and emerging technologies (or at least there should be).

---

### Post by rattlerviper on 2006-08-09
One would think that if it changed so much windows would have a backwards compatability issue.  Being unable to run pre vista software. I had problems when I made the switch to xp from 98.  Most things ran, but a few didn't run right even using the compatability thing.  If exspensive software fails to work people are gonna get upset.  If I just paid 679 bucks for a copy of Photoshop CS2 and the switch to vista made it stop working I would be more than upset, I would be searching for alternatives.  

So another question is can Microsoft handle the changes?

---

### Post by mozetti on 2006-08-09
> **rattlerviper said:**
> So another question is can Microsoft handle the changes?

Another question for another thread, maybe. Backwards compatibility for MS is one thing, but I'm more interested in these newer technologies and Linux's ability to capitalize on them. Some of them are pretty interesting, like the onboard flash memory and hybrid drives, and should benefit any OS. But, the OS needs to support/incorporate these hardware advances. If the new technologies are univeral improvements (crypto-ROMs are different story, but may be necessary if all HD content requires it), Linux should probably incorporate them -- might there be problems doing this with MS having a heavy influence on hardware?

---

### Post by skirkpatrick on 2006-08-09
Some of it is probably a moot point.  Hybrid drives will probably be indistinguishable from normal drives (your drive already includes a RAM cache on it but the drive handles it for you).  As far as flash memory on the mobo, why wouldn't they just make it look like a drive or USB device?  Most embedded PC's utilize an embedded flash drive as well as the ability to connect a standard drive.

---

### Post by mozetti on 2006-08-09
> **skirkpatrick said:**
> As far as flash memory on the mobo, why wouldn't they just make it look like a drive or USB device?  Most embedded PC's utilize an embedded flash drive as well as the ability to connect a standard drive.

My understanding is that the embedded flash memory on the mobo would be for system use, and not a storage area for user access. For example,  write-caching and not storage.

Of course, with Linux it may be possible to use it as another storage device. But, with GB Procs and GB HDDs, what real benefit would a mobo-embedded flash storage add?

---

### Post by skirkpatrick on 2006-08-09
From what I read, it would be good for laptops and such so that suspend/hibernate would go to the flash memory instead of the harddrive and you'd essentially never turn off your laptop.  Considering how many write cycles flash has, I wouldn't be too thrilled about it.

---

