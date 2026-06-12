---
title: "Intel ich10"
date: 2008-09-27
forum: New to Ubuntu
---

### Post by kbozz71 on 2008-09-27
Hi guys, got a Biostar TForce TP43D2A7 mobo with an e7200 proc, when I try to install Ubuntu 8.04 it can't detect any hdd partition. Win XP sees it just fine. Is it an Intel sata driver incompatability? or could my install cd be corrupt? Thanks

---

### Post by Presto123 on 2008-09-28
Could you post what kind of error it states? Did you build the thing yourself or was it bought at a store? There could be a few issues that these questions can help solve.

---

### Post by khedoros on 2008-09-28
I've got a board with the same southbridge and sata controller as kbozz's. It's an Intel ICH10. I've looked in the kernel source (driver/ata/ahci.c, I think), and there are a list of device IDs, ending with some things with comments labeling them as ICH9. So....my guess is that it's supportable, but its deviceID hasn't been added into the appropriate driver. In short, I guess I need a newer kernel...

---

### Post by Roasted on 2008-10-14
I ran into this problem just a few days ago. I built a new computer and ran into this issue.

My problem was:

- XP would only recognize IDE mode, not SATA, because there was no pre-loaded SATA driver.
- Ubuntu would only recognize AHCI mode (SATA mode) because there was no support for IDE Legacy mode... which I understand is just the southbridge not being completely compatible.

How did I fix it?

Well, I had to do this... 

I downloaded nLite... which is a program where you can "slipstream" items (drivers, service packs, etc) into your copy of XP, then re-burn it to a new disc. The problem is, your copy of XP cannot detect AHCI mode because it does not have the SATA driver. So, you need the SATA driver. But how can you install the driver if you can't even install the OS? nLite will do that.

The steps required:

- Boot into XP (IDE mode, if necessary).
- Download nLite.
- Start nLite.
- Put your XP CD in your computer.
- Create a folder on your desktop. Name it something like... XP Source.
- Explore your Windows XP CD in your computer. (don't just double click. Right click and hit explore).
- Select all, and hit copy. Go to your XP Source folder you created on your desktop and paste everything over.
- in nLite, select the XP Source folder as your target.
- You'll get to a screen asking you to integrate drivers. Here's where YOU need to go out to your motherboard manufacturer's web site and look for the SATA drivers. They may be named anything. My drivers in particular were named storage manager. So keep a thorough eye out.
- Select your drivers to be integrated and go to the next screen.
- I suggest you "create image" instead of burn. I couldn't ever get burn image to work. But I create image and then select "make iso."
- Using Nero, I burn the image to a CD (or DVD, if your's is too big for a CD).

Presto. Now, when you boot up to your newly working XP cd, you should be able to boot with your BIOS set to AHCI mode since you integrated your SATA drivers on this CD. Make SURE you set it to AHCI mode first. I forgot that, booted to IDE mode, got all excited, and then later realized I was never in AHCI mode to begin with. 

Also - Be patient with it. It took me 3 tries till I found the proper drivers. As I said, mine were labeled storage manager, which isn't what I expected, so I overlooked them a couple times till I got it right.

If you need any additional help, post back here. I'll do my best to help you with this.

---

### Post by ByteJuggler on 2008-10-14
Re installing XP on unsupported SATA chipsets:
Normally motherboard driver CD's have a utility to create a driver floppy for use during XP installation, to allow you to supply the needed SATA drivers.  Does these motherboard CD's not include such, and/or do you not have a floppy drive?

---

### Post by ByteJuggler on 2008-10-14
> **kbozz71 said:**
> Hi guys, got a Biostar TForce TP43D2A7 mobo with an e7200 proc, when I try to install Ubuntu 8.04 it can't detect any hdd partition. Win XP sees it just fine. Is it an Intel sata driver incompatability? or could my install cd be corrupt? Thanks

What mode is your controller set to?  Is AHCI enabled?  As others have intimated, you should use AHCI as Ubuntu supports that standard out of the box, and then fix your XP installation.  This thread [here]("http://orenshamir.wordpress.com/2008/10/13/installing-ubuntu-linux-and-xp-on-ich10/") is also about this problem.

---

### Post by Roasted on 2008-10-15
Oh my gosh, I completely forgot that the floppy drive can do the same thing I spoke about above.

If you have a floppy drive, load the SATA (AHCI) driver on a floppy disk. Boot to your XP cd and hit F6 when it starts the setup. It'll say press F6 to setup raid devices or something. Hit F6 then. Then, load the driver.

The downside: You have to do that every single time when you reinstall XP. Make sure you remember that.

nLite upsides and downsides:

Upside - It's a once and done thing.
Downside - Until you do it once or twice, it can be a little confusing. I remember it was hard for me to pick it up, simply cause I didn't have a guide. But now? Pssh. It's a breeze. There's also a 6 minute YouTube video about doing it, and it helped me a lot.

---

