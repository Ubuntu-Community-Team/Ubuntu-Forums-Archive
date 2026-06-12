---
title: "[Linux Mint] Can't boot up!"
date: 2009-01-30
forum: Other OS Talk
---

### Post by CJ Master on 2009-01-30
Hello. :)

I can't seem to get Linux Mint 6 to boot up. (Installed via windows, LiveCD doesn't want to work either.)

It gets stuck at several places for several minutes, most notably at "Hardware Abstraction Layers" and then just plane freezes when loading BlueTooth.

Yes, I know this is an Ubuntu forum, but Linux Mint 6 is completely based on Ubuntu Linux 8.10, and it's said that almost all advice that works on Ubuntu should work for Linux Mint as well.

Thanks very much for all your help! :D

---

### Post by Montblanc_Kupo on 2009-01-30
Does the system boot ANY distro?

---

### Post by CJ Master on 2009-01-30
Well I found an old CD of "Ubuntu Mepis 6" (whatever that is) and it booted fine.

---

### Post by alienexplorers on 2009-01-30
When you downloaded the Linux Mint 6 .iso, did you burn it a a slow speed and did you check the md5 checksum.  Almost sounds like a bad boot CD.

---

### Post by CJ Master on 2009-01-30
No... set it to auto speed. And when you use Mint4Win (AKA Wubi) it automatcally checks MD5 checksums.

---

### Post by Montblanc_Kupo on 2009-01-30
I've had issues with that. I would burn the cd at as low a speed as possible for best compatibility. Case in point...

Current machine booted fine off a cd I made from downloaded Ubuntu .iso... put it into an older machine to install it... wouldn't even boot. Burned again at 8x (lowest option it would give Me) and put it in... booted fine.

If other versions of Ubuntu work... then it's probably just bad media... My understanding is there isn't that much difference between Ubuntu and LinuxMint in the backend stuff.

---

### Post by CJ Master on 2009-01-31
Too be 100% sure I redownloaded and mounted the iso instead of burning. But nope.. still problems :(

---

### Post by CJ Master on 2009-01-31
Alright... Mandriva doesn't work, openSUSE doesn't work, the only linux distro that seems to work is Mepis. (Not that it's a bad system at all... on the contrary I like it. However, I like linux mint more :( )

Oh - Windows XP works also.

---

### Post by CJ Master on 2009-01-31
bumping :)

---

### Post by CJ Master on 2009-02-01
Oh yea! Forgot to mention.. but Ubuntu doesn't want to load either.. Using XP atm.

---

### Post by CJ Master on 2009-02-01
Bump again :(

---

### Post by bapoumba on 2009-02-02
Moved to Other OS Talk, you may find more Mint users here :)

---

### Post by CJ Master on 2009-02-02
Hmm... yea, although Mint still does have same underlying code as Ubuntu...

But thanks. :)

---

### Post by orethrius on 2009-02-02
Just a thought, but does the install / live disc have some method to "check disc for errors"?  I've been having a similar issue with my self-burned 8.10 discs, and it turns out that the ISO didn't burn all the packages to disc.  From what you describe of the ISO, it almost sounds like it may be faulty itself, but those are two distinct issues.

---

### Post by CJ Master on 2009-02-02
Hey orethrius,

Mint probably does have a check disk for errors option, but if the disk didn't have all the packages, wouldn't the Md5 checksum be diffrent? Well before installing Mint4Win checks the checksums.

---

### Post by orethrius on 2009-02-02
> **CJ Master said:**
> Hey orethrius,

Mint probably does have a check disk for errors option, but if the disk didn't have all the packages, wouldn't the Md5 checksum be diffrent? Well before installing Mint4Win checks the checksums.

I'm not sure how it checks the MD5 of a raw device, I'm just saying that this sounds like one of two things.

1.  The ISO didn't burn completely, but somehow whatever packages are checked for MD5 equivalence did.  I had this happen with 8.10.
2.  The ISO itself is faulty, and the MD5 will always be "correct".

There is, of course, a third possibility, but I figure you'd notice this one:
What system are you running (vendor and full model if possible), and which ISO file are you using?

---

### Post by jrusso2 on 2009-02-02
When a setup hangs at the HAL stage usually that is hardware the install is having a hard time with.

---

### Post by orethrius on 2009-02-02
> **jrusso2 said:**
> When a setup hangs at the HAL stage usually that is hardware the install is having a hard time with.

Well, and that's why I'm wondering about the vendor/model information, we can get more detailed information regarding potential workarounds with that data.

---

### Post by CJ Master on 2009-02-03
I'll go check the CD.

..Oh and btw, the computer is a T6524 from Emachines. I'd upgraded it a bit... added a Radeon 3870, some more ram, and a Patriot Solid State Drive.

---

### Post by Zero Prime on 2009-02-04
I recommend setting up a true dual boot instead of using the Windows installer.  It might work a lot better for you.

---

### Post by CJ Master on 2009-02-05
Oh yeah, tried that too. Didn't really seem to make any diffrence. Thanks though.

---

### Post by Nero147 on 2009-02-06
I've had similar problems on a couple of old systems. I usually ended up fixing them with custom boot parameters. So a couple of things you could try would be 

noapic

or if that doesn't work try

no acpi

or the combination of the two. also there was a time when I had to disable dmraid when installing fedora. Although from what you're describing I wouldn't guess that. but the apic and acpi might help.

when you boot into the disk there should be an option for more options or custom boot. or something to that effect.

---

### Post by CJ Master on 2009-02-07
Unfortunantly. Those didn't help :( thanks very much for trying to help though.

In other news: I got Debian to run perfectly. But please don't make me stay here!! Debian is just... too... sterile.........

---

