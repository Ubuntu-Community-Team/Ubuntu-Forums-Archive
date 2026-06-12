---
title: "how to know if i can fit a SATA drive i have a IDE drive already"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by tavati on 2008-08-21
i have a five yr old system with 40 GB IDE harddrive. how to find out that i can or cannot fit a new SATA 320GB drive?

---

### Post by tarps87 on 2008-08-21
There are two ways, find out you motherboard make and model and google it or post it here and I'll look for you, or look on the motherboard for something that looks like the picture attached

Edit: As I understand it you can use IDE drives or SATA drives not both at the same time

---

### Post by Kyle1981 on 2008-08-21
i don't think you can do it. because there is no sata socket on your motherboard.

---

### Post by jerome1232 on 2008-08-21
I'm using pata (ide) and sata drives at the same time at this very moment. If that were true than you wouldn't be able to have most dvd roms plugged in at the same time as a sata drive.

edit: How do you know there is no sata socket on his mobo? He never posted the model yet, mine is 5 years old and has two sata connectors.

---

### Post by tarps87 on 2008-08-21
Some motherboards have both, I think mine is about 3yrs old and it has SATA and IDE connectors but I'm still using IDE drives

---

### Post by tarps87 on 2008-08-21
> **jerome1232 said:**
> I'm using pata (ide) and sata drives at the same time at this very moment. If that were true than you wouldn't be able to have most dvd roms plugged in at the same time as a sata drive.

Sorry I was unclear on what I meant. I meant have your IDE cd drive(s) on one cable and hard drive on another IDE cable and as SATA hard drive connected.
Having a cd drive and hard drive on the same cable can cause problems as they have different access rates

---

### Post by Kyle1981 on 2008-08-21
> **jerome1232 said:**
> I'm using pata (ide) and sata drives at the same time at this very moment. If that were true than you wouldn't be able to have most dvd roms plugged in at the same time as a sata drive.

edit: How do you know there is no sata socket on his mobo? He never posted the model yet, mine is 5 years old and has two sata connectors.

really? oh, sorry, there were SATA disks in 2003. maybe some motherboards produced at that time have that socket

---

### Post by Kyle1981 on 2008-08-21
> **tarps87 said:**
> Sorry I was unclear on what I meant. I meant have your IDE cd drive(s) on one cable and hard drive on another IDE cable and as SATA hard drive connected.
Having a cd drive and hard drive on the same cable can cause problems as they have different access rates

yes, yes. but it's not a serious problem. of course, you'd better use a cable for each device.

---

### Post by tarps87 on 2008-08-21
> **Kyle1981 said:**
> yes, yes. but it's not a serious problem. of course, you'd better use a cable for each device.

Does that mean I can connect devices using two IDE cables and a SATA cable? I've never tried it before as I've always used IDE drive.

---

### Post by SpaceMaster on 2008-08-21
Yes.  In fact, many machines are set up that way.  Often, the boot drive will be connected via SATA, while others (CD/DVD drives, floppy drives, Zip drives, etc) will still be connected via PATA.  I've never seen this as a problem.  

If you want to boot from something other than your SATA 0 device, though, you will have to configure the correct options in the system bios (usually accessible by pressing F12 or F2 or ESC during initial boot).

Even without a SATA slot on the motherboard, it's easy to find a SATA PCI expansion card.  And for dirt cheap, too.  However, the system bios may not want to boot from a device connected in the PCI slot without proper modifications (to the bios, that is).

---

### Post by jerome1232 on 2008-08-21
> **SpaceMaster said:**
> Even without a SATA slot on the motherboard, it's easy to find a SATA PCI expansion card.  And for dirt cheap, too.
From what I understand usually better quality than the onboard stuff too.

---

### Post by Too Late on 2008-08-21
I think it's better to plug an optical drive and hdd on one cable, when having two hdds. Plugging the hdds on same cable (and optical drive on its own cable) reduces the maximum speed between hard disks.

By the way, not all old mobos having SATA connectors are SATA II compatible, even though the SATA II *should* be fully backwards compatible. Sometimes a jumper in the hdd can resolve that.

---

### Post by Kyle1981 on 2008-08-21
en, this involve many things. I don't know if his bios can support 320G disk. maybe it must be upgrated. and you can use two IDE cables and a SATA cable, it's OK. but I think there is no need to change the connection manner of IDE devices. he only need to buy a SATA cable.

---

### Post by Kyle1981 on 2008-08-21
> **Too Late said:**
> I think it's better to plug an optical drive and hdd on one cable, when having two hdds. Plugging the hdds on same cable (and optical drive on its own cable) reduces the maximum speed between hard disks.

By the way, not all old mobos having SATA connectors are SATA II compatible, even though the SATA II *should* be fully backwards compatible. Sometimes a jumper in the hdd can resolve that.

you can't insert a SATA cable into a IDE disk. so the IDE disk must be connected with CDROM, or has its own cable. 
SATA I/II is also a problem. the jumper should be set according to the motherboard.

---

### Post by Too Late on 2008-08-21
> **Kyle1981 said:**
> you can't insert a SATA cable into a IDE disk. so the IDE disk must be connected with CDROM, or has its own cable. 
SATA I/II is also a problem. the jumper should be set according to the motherboard.
Well, in the first paragraph I was talking about the situation, where there are only parallel ATA (aka IDE) devices. I was referring to this sentence:
> **tarps87 said:**
> Having a cd drive and hard drive on the same cable can cause problems as they have different access rates

---

### Post by hyper_ch on 2008-08-21
if it came with a 40gb drive it might well be that there's also a sever size limit of what your mobo can handle. maybe you'll also need a bios upgrade. Have a look at the tech docs of the mobo.

---

### Post by cwsnyder on 2008-08-21
I am sitting here using 1-200G PATA (IDE) drive as my first boot and 1-500G SATA drive.  My PATA runs the GRUB boot manager and has one installation of Windows XP Media Center and another partition of Ubuntu 8.04.  My main Ubuntu 8.04 installation is on the 500G SATA drive.

cwsnyder

---

### Post by SpaceMaster on 2008-08-21
> **Too Late said:**
> Sometimes a jumper in the hdd can resolve that.

Ode to ye, hardware jumper,
I always forget about thee,
And wonder why I can't see,
my DVD, CD, and HDD.

Picky picky systems.

---

### Post by tarps87 on 2008-08-21
I think I'll check my motherboard manual when I get home and see if supports the two IDE cables and the SATA, sillily I always assumed it wasn't possible due to the interrupts and thing. Then again the only reason I would do it is because I can, that why I'm using awn and screenlets :)

---

### Post by jerome1232 on 2008-08-21
> **SpaceMaster said:**
> Ode to ye, hardware jumper,
I always forget about thee,
And wonder why I can't see,
my DVD, CD, and HDD.

Picky picky systems.

lol, nice

---

