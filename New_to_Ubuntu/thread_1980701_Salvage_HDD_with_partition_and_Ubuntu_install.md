---
title: "Salvage HDD with partition and Ubuntu install?"
date: 2012-05-15
forum: New to Ubuntu
---

### Post by ross56 on 2012-05-15
Hi, I'm new to Ubuntu and the forums, so I thought I would post this question here. A few months ago, my laptop started slowing down/freezing for a few minutes at a time when I would run Steam. This happened seemingly out of nowhere, and I was forced to use a hard shut down to get out of Windows several times. After a few months talking to Steam Support, I got it working again.

Despite Steam getting fixed, my computer did the same freezing thing a few days later, making it unusable, outside of safe mode. I reinstalled Windows, and that seemed to fix the problem for a few weeks. Then, the freezing thing started again, this time right after I got into Windows, again being unusable outside of safe mode.

I was planning on installing Ubuntu on my external HDD anyway, but as of now that's all I have that I can use. I've been running 12.04 on a Seagate external HDD for a week or two now, and everything seems to be going fine. 

In the mean time, I did some diagnostics on my computer and got a 303 error on my internal HDD every time I ran the test (it turns out I had the same problem months ago, before the reinstall, but I never checked the error logs). I've read that this mean my HDD is broken beyond repair, and I should get a new one, but it doesn't appear to be broken completely. I can still access all of my files, while in Ubuntu or safe mode.

I'm wondering if I can just partition the bad part of the internal drive, and install Ubuntu on the new partition. Will that isolate the bad part of my disk, or is it likely there are other parts of the disk that are bad? Can I check that, because my disk check stops at 53% every time when it runs into the broken part of the disk. I would really like to keep my internal drive working, because the only part that doesn't seem to work is the full startup for Windows, and a new drive could cost me up to $100.

I'm about ready to make a permanent switch to Linux from Windows, so I was thinking I would install that in the safe part of the drive to increase my speed a lot, and i also wouldn't have to take this ext drive everywhere. This leads into my second question, which is: If I install Ubuntu 12.04 on the safe part of my internal drive, can I easily move everything from the external drive to the internal? I think most of my programs were installed through the software center, but there are a few that I had to do through terminal, which I'm not totally comfortable in yet. If I can't, it's not really a big deal, it would just save me the time.

Thanks for reading all of this; I know it's a pretty long post. Here are the specs of my computer:
HP Pavilion dv7-4051nr Notebook PC
AMD Phenom II P920 Quad-Core 1.6Ghz CPU
AMD (ATI) Mobility Radeon HD 5470 GPU
4 GB DDR3 RAM
500 GB Hitachi Internal HDD
--Windows 7 Ultimate 64-bit
320 GB Seagate External HDD
--Ubuntu 12.04 LTS

If you need anymore information, feel free to ask for it. Thanks again for the time and consideration.

---

### Post by Lisiano on 2012-05-15
Sorry to inform you but if you have bad sectors, then the time your disk still has is very limited. If you are under waranty then you should ask HP to replace the disk. Otherwise you can just copy everything off the internal one to the external one and use it as a cool HDD which you can disconnect, connect to another computer and boot Ubuntu with all your stuff.

To test the disk, you can use Ubuntu and it's Disk utility.

Anyway, reason is why the disks time is limited is because bad sectors are caused by an error during manufacturing, which is nothing to worry about or physical impact, which something you worry about. The former means the bad sectors will not spread and stay at a constant, the later means it will spread as there is physical damage and when the head (The thing that tries to read the data) passes over the bad sectors, it'll lose it's air cushion and either hit the disk or scratch it (RIP). Imagine something rotating at a VERY fast speed, the only way the head is not touching the disk is because there is an air cushion not letting the head touch the disk, now if the disk is not ideally flat, the cushion breaks and ... You already know.

---

### Post by audiomick on 2012-05-15
I wouldn't risk it. If the drive is looking like it is dying, just get your stuff off it and replace it. At the very most, use it for storing stuff that does not matter at all if you lose it, and expect it to fail completely at any time.

Don't just throw it out, though. There are usually some magnets in there that are great for hanging notes on the fridge... ;)

---

### Post by ross56 on 2012-05-15
Alright, I double checked the drive in the Disk Utility, and it looks like it's going to go soon. Is there any harm in me keeping it connected inside, even if it fails? I'm not really comfortable opening up my laptop and messing around, so I don't know how soon I could get it out.

---

### Post by Lisiano on 2012-05-15
> **audiomick said:**
> Don't just throw it out, though. There are usually some magnets in there that are great for hanging notes on the fridge... ;)
Don't forget about the disks themselves, cool frisbees.

> **ross56 said:**
> Is there any harm in me keeping it connected inside, even if it fails?
No harm, just don't forget to not use it for anything important. Although when it does fail, expect long boot time until it's disconnected.

---

### Post by audiomick on 2012-05-16
> **ross56 said:**
> Is there any harm in me keeping it connected inside, even if it fails? I'm not really comfortable opening up my laptop and messing around, so I don't know how soon I could get it out.

As Lisiano has already pointed out, a dying or dead drive won't cause any further harm, but is likely to cause very long boot times. The computer will be trying to address a drive that is not reacting, so things can take a while.

Don't be too afraid about swapping out a drive. In most laptops, it is just a matter of opening a cover on the bottom and taking the drive out. You generally don't have to take the laptop apart as such. Try a bit of searching in the 'net for instructions. There is a lot of info about that sort of thing out there.

---

