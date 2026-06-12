---
title: "New to Ubuntu, installation problem Xubuntu 12.04 LTS"
date: 2013-01-04
forum: New to Ubuntu
---

### Post by SteamDonkey74 on 2013-01-04
Hello,

I am a new user here and decided to join after seeing many posts from this forum on various web searches to figure our various problems. I will get right to the problem here and then I will follow up with some of my background.

**PROBLEM** - Xubuntu 12.04 LTS installation freezes

I am installing from a disc provided by a local computer recycler Xubuntu 12.04 LTS on a Dell Dimension 2400 desktop computer. The thing was running XP, but since I already have another Dell Dimension running XP I wanted to make this a Xubuntu box.

Anyway, the installation seems to proceed just fine through various screens and it always hangs up on "creating user." I let it go all night and it had progressed even a millimeter on the progress bar.

I have 1.5 Megs of RAM and it is connected to the internet via a wireless USB thingy. One thing I don't have is the recommended min. 45 GB hard drive space as the hard drive is only 40 GB. I can fix that today if that is an issue. 

If this is something answered many times before I apologize. I have looked for an answer and I haven't found one, yet, but that's not to say it isn't out there.



**BACKGROUND** - my background with computers

I have only been using Xubuntu for a few days, so I figured my problem was a typical n00b sort of problem though I haven't found yet an answer to this particular one through my various web searches. I have a laptop with it installed I picked up at Free Geek in Portland and I am very pleased with it. I have searched for answers to a lot of questions and found a lot of answers in threads here. I have been using various Mac OS version from the mid-80s through now, and I have used DOS and nearly all Windows versions up through Windows 7. In college, I did a fair bit on the Unix machines we had sitting around. I won't call myself a heavy duty programmer or 10th level magic user of computers, but I am flexible on platform and GUI/command line usage, and feeling pushed around by planned obsolescence that I feel is built into several operating systems now I am trying to break free into the Free and Open Source Software world, including operating system.



Thanks in advance for your help!

Adam
Portland, Oregon

---

### Post by audiomick on 2013-01-04
Hi Adam. Welcome to the forums.

I can't offer you a one-hit solution. Maybe someone else can. For starters, though...

You have a disc from the shop. Let's assume that it is ok. Can you boot from that into the "try ubuntu" option?

If you can, can you open a terminal and do 
```
lshw
```

and post the bits here showing cpu and video?

I would suggest getting onto a wired connection for the install. There is a very good chance that your USB device wont work initially, whereas the wire almost certainly will. I personally just wouldn't trust wireless anything during an install.

I doubt that this is what is stopping your install, though.

Tell us again how much RAM is in there. You wrote "1.5 Megs". I doubt that you mean 1.5MB. Is it 1.5GB perhaps?

40GB is tight, but is definitely enough to install onto. The install itself will probably take up around 5GB or less. I haven't looked lately, so I am not sure. You have enough to be gettin on with, but if you are installing a lot of program or storing a lot of stuff, your 40GB might fill up quick. It is a desktop machine, right? If so, think about putting a second drive in there, perhaps before the install. You can install the OS to the smaller drive, and use the larger one for your /home.

---

### Post by SteamDonkey74 on 2013-01-04
Thank you for your response!

Oh, yes. 1.5 gb of memory. Basically, I have moved the original 512 MB stick to the second slot and put in a 1 GB stick. 

I will try wiring up the connection before I make another attempt. I have a long ethernet cable I can use temporarily. The computer isn't currently here with me but I will try those things you mentioned when I get the chance.

Thank you,
Adam

---

### Post by SteamDonkey74 on 2013-01-05
> **audiomick said:**
> 
If you can, can you open a terminal and do 
```
lshw
```and post the bits here showing cpu and video?


I was able to boot from the disc and I am actually typing this on the machine in question right now. I opened up the terminal and typed your command. A whole bunch of stuff came up. I hope I am cutting and pasting the correct stuff here.

> *-cpu
          product: Intel(R) Celeron(R) CPU 2.40GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 15.2.9
          size: 2400MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts cid xtpr
          configuration: id=0
        *-cache
             description: L1 cache
             physical id: 0
             size: 8KiB


> *-display
             description: VGA compatible controller
             product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:e8000000-efffffff memory:feb80000-febfffff



I am running on a wired connection now. I am going to attempt to install again with the connection wired up. I'll report back here with the status.

Thanks!
Adam

---

### Post by Wim Sturkenboom on 2013-01-05
I don't think that I can help with the problem that the install hangs. But I like to advise not to be connected to the internet during the install. The last time I did that, it took over 2 hours (because it's pulling in updates of all packages) while a normal install takes around 20 minutes or so.

I rather install updates afterwards.

---

### Post by SteamDonkey74 on 2013-01-05
I just marked it as solved because I am now using Xubuntu 12.04 LTS as installed on the hard drive, but I am not 100% sure what I did that worked.

I tried installing after using the CD live, or whatever it is called, wired to the internet (instead of using a wireless device). It got hung up in the same place at "creating user."

I then tried again this time installing from the CD but this time not checking any extra boxes for any extra updates or software, and this time not opting to have my user directory encrypted. I probably should have done just one of those things at a time so that I could give this community a better idea what worked, but this time it installed just fine. It took about 20-30 minutes, but it successfully installed, and I can worry about that other software and those other updates later.

Thanks, folks, for your help! I am really excited about this return to free and open source software and operating systems, and the people who gave me this old XP box for my experiment had written it off as a basket case, but it seems to be working just fine now.

Thanks,
Adam

---

### Post by audiomick on 2013-01-06
> **SteamDonkey74 said:**
> I tried installing...It got hung up in the same place at "creating user."

I then tried again...this time not opting to have my user directory encrypted.

It is really only a guess, but I strongly suspect a connection here. I can't give any basis for it other than that is "just makes sense" to me. I can't imagine how extra software or whatever could give you problems creating a user, but if you are encrypting the user directory and it hangs creating a user, then it seems logical to me that it is having trouble with the encryption. Don't ask me what the problem could be, though. I have not looked into encryption at all. Don't see any need for it on my machines.

---

