---
title: "Hardy is nothing but trouble"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by Jadephyre on 2008-04-24
Okay, since all the Threads so far have done nothing for me so far, i have to open a new one to state my Problem.
I'm currently running Linux Mint 4 which is based on Ubuntu 7.10 which works great for me.
I tried one of the Ubuntu 8.04 Betas before and even they worked great... and NOW the Final of 8.04 won't even boot the Live Environment.
I tried everything i could find, downloaded both Versions (32 & 64Bit) TWICE, ran MD5 Checks on all downloads, all came out okay and still no frickin' luck.
I burned all these Discs in the latest Nero on Windows XP with Data Integrity Checks on and i highly doubt that my Internet Connection or the Burner would **** up every Image i download and trash every CD i burn as i have also burned Ubuntu 7.10 and Linux Mint 4 with the same Burner, and they all work.
So far 8.04 is nothing but trouble... if the Kernel is at fault, then by god: THROW it out and change it against one that WORKS.

At the Moment i just want to boot the LiveCD to try the Final 8.04... why in hell is it keeping me from doing so ?

My System as follows:
Acer Aspire 5050 Laptop
AMD Athlon 64 MK-36 2.0 GHz
2GB DDR2-RAM
60GB Harddisk
DVD-DualLayer Burner
14.1inch TFT-Display
ATI Radeon X1100 Graphics
Integrated Sound Card (dunno which at the moment)
Broadcom 4318 Wireless (works with NDISWRAPPER)

---

### Post by SunnyRabbiera on 2008-04-24
well if hardy is that much trouble stick with mint, besides it will get its next version soon.
Plus mint sometimes behaves better then ubuntu anyhow

---

### Post by Daverobb on 2008-04-24
Had similar series of problems with a reinstall of 7.10.  Finally did it in safe graphics mode and it went smoothly - is that an option on the hardy release cd.  using hardy now and it's fine but upgraded it over net.

---

### Post by Can+~ on 2008-04-25
I had troubles with gutsy back then, exactly the one you describe. I jumped into a shell and did:

```
sudo /etc/init.d/gdm restart
```

And it logged in as if anything, weird.

---

### Post by Jadephyre on 2008-04-25
well, i have used the last Beta once... but i had to update it through the Net to actually install it from Gutsy.
After upgrading it took one hell of long time to boot... and i have not figured out why so far... maybe because i'm a pro with Windows, but suck at configuring Linux :(
All i can hope for is that Mint 5 will come out as fast as possible, and that will be a reinstall again as there is no "dist-upgrade" included in Mint 4.
About the only downer i found compared to Gutsy...

---

### Post by spiderbatdad on 2008-04-25
ok. I goofed again. please see below.

---

### Post by spiderbatdad on 2008-04-25
opps. see below.

---

### Post by spiderbatdad on 2008-04-25
reading the output of dmesg can give you clues to solving hardware detection problems and long boot-time problems. Look for problem with apic or irq polling. Dmesg will include suggestions like: try booting with lapic, or try booting with irq poll.
Some simple parameters like those can be added to the kernel line in /boot/grub/menu.lst, or tried, once, using the 'e' to edit feature from the grub menu, and solve hardware detection problems.

As an example my kernel line is edited like this:
```
title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=604f2b74-7f64-424f-a8bf-1160a71d9ea3 ro **lapic pci=routeirq**
initrd		/boot/initrd.img-2.6.24-16-generic
quiet
savedefault
``` 

You can see at the end of the line beginning with the word 'kernel,' I have added the commands, 'lapic pci=routeirq.'

---

### Post by mattywarr on 2008-04-25
I have an Aspire 5020 and I experienced similar problems.

The following worked for me:

1. Shut down the machine, unplug and remove battery for 10 minutes
2. Run the Live CD
3. Change the boot parameters when launching the cd to include 'noapic acpi=off'

That got my LiveCD working and from there I could install happily in the GUI.

---

### Post by Jadephyre on 2008-04-25
and how long did it take to boot into the Live Environment then ?
One thing is for sure: If the Live Environment takes 5 Minutes to actually show something on the screen, then it will take the exact amount of time after Installation...

---

### Post by mivo on 2008-04-25
> **Jadephyre said:**
> If the Live Environment takes 5 Minutes to actually show something on the screen, then it will take the exact amount of time after Installation...

That's not so. The live environment is loaded entirely from the CD. It is much, much slower than loading from a hard drive. A live CD is always significantly slower than a "real" installation.

---

### Post by joshsmith on 2008-04-25
did anyone read the original post? 

this person is having trouble booting a live cd......

what happens when you try to boot. give as much detail as possible. how far along did you get.

---

### Post by Jadephyre on 2008-04-25
@Mivo
i know that a Live Environment takes a lot more time to load completely, but you should read my post again, as i said "before i get to see anything".
Okay, reading it again i reckon that i have not made myself clear.
I meant before i actually see the loading screen (the one with the Logo and the Orange Bar).
It never took that long on Ubuntu 7.04 or 7.10 which leads me to believe that there is something wrong in the Kernel that comes with Hardy, as other people here on the Forum have suggested.

@Joshsmith
without these Boot Parameters i get nowhere, the system just hangs or loops indefinetely. I have not yet tried to boot with the "quiet" Parameter removed, i will try that this weekend.
I got the Live Environment to boot a few hours back, but i won't trash my working Install of Mint 4 if Hardy takes as long to boot as it takes loading the Live Environment (which it did, after i upgraded from 7.10 to 8.04 Beta).

EDIT: The Boot Parameters being: noapic nolapic all_generic_ide=1 acpi=off

---

### Post by mivo on 2008-04-25
You could add *nosplash* to the boot parameters and remove *quiet*. This way you should be able to see at which point the system hangs (it's probably trying to do something and gives up after a while). Another parameter to try is *irqpoll*.

---

### Post by stchman on 2008-04-25
Yes, try the safe graphics mode.  That worked for my 8800GT.

---

### Post by billgoldberg on 2008-04-25
Use the alernate cd to install hardy.

---

### Post by billgoldberg on 2008-04-25
> **Jadephyre said:**
> and how long did it take to boot into the Live Environment then ?
One thing is for sure: If the Live Environment takes 5 Minutes to actually show something on the screen, then it will take the exact amount of time after Installation...

If you don't know what you are talking about it would be better not to give advice at all.

The statement you made is just plain wrong.

---

### Post by Zentradi-359 on 2008-04-25
One of my machines is a laptop, Emachines M5305. I tried to install hardy over the mandriva powerpack. All it did was go so slow I hated it... I decided to delete all the partitions off the HD and did a new install of hardy.. works great.
Dont know if this will help.

Zen :)

EDIT: Yes it also took forever for the live CD to come up. In fact it was only after the 3rd reboot into the live cd, walking away and having lunch did I notice when I came back after 20 min the live cd had loaded.

---

### Post by Jadephyre on 2008-04-26
> **billgoldberg said:**
> If you don't know what you are talking about it would be better not to give advice at all.

The statement you made is just plain wrong.

The statement i made is based on MY personal experience with Ubuntu 8.04.
Also, this Thread was started by me, so i'm not giving any kind of advice, i'm asking for advice, big difference.

@Zen
the Problem is that i can't wipe my partitions, too much Data stored on them, no way to back up at the moment.

@billgoldberg
the Alternate CD is not an option for me, Period

EDIT:
just tried the "nosplash" Boot Parameter which told me that the system can't find my Processor and hangs after trying to detect a SATA Drive that is NOT THERE as i have an IDE Harddisk in my Laptop.
Does anyone know how to disable SATA detection before the system tries to load ?

---

### Post by Jadephyre on 2008-04-26
okay, this is it, i will stick with Linux Mint 4 and will probably upgrade to Linux Mint 5 when it comes out... i see no point in wasting time and nerves to get Hardy to boot the Live Environment.
Why is it that Mint has an obviously better Hardware Detection than pure Ubuntu ?
They should not have released Hardy in this state as i would not deem that Final...

---

### Post by meindian523 on 2008-04-26
Ya know,I've got nothing but glowing tributes to even the BETA from all the *buntu users around me.You sure it's not your hardware?Avoid general and sweeping statements like "They should have not released it in this state,I don't consider it final"  etc..

---

### Post by Jadephyre on 2008-04-26
i KNOW that my Acer Laptop has a few quirks that i need to work around to successfully run any kind of Linux, but this here with Hardy is just plain ridicoulus.
Mint 4 is not giving me errors, or at least no errors that are showstoppers, i can do whatever i want in Mint, it just works.
Startup Time (from powering up the Laptop 'till i see the Login) is about two Minutes at max, with the Version of Gutsy i had running that i updated to the then latest Hardy Beta, it took me TEN Minutes just to get to see the Login Screen... i know that it was a Beta back then, but right now i would not risk installing Hardy as the Kernel obviously doesn't like my Laptop... will try again if there is a new release with a new Kernel, otherwise Hardy just isn't for me and i will have to wait 'till the Mint Guys make it usable.

---

### Post by BoardStupid on 2008-04-27
After upgrading to Hardy from Gutsy, only one thing didn't work and that was advanced desktop effects. I'm using an Acer Aspire 5050 and it takes pretty much the same time to load as it did before (I don't know if it's faster or slower since I didn't time either boot time, but the difference isn't apparent either way).
If your computer can run Gutsy, I see no reason why Hardy will be much of a bother. That being said, if you're happy using and staying with Mint, I don't see why you're so angry towards Hardy (at least you appear to be hosilte, I may be reading your posts incorrectly)

---

### Post by mlentink on 2008-04-27
> **Jadephyre said:**
> 
They should not have released Hardy in this state as i would not deem that Final...

You may think they shouldn't have, but quite a few others do. I upgraded both a HP/Compaq nx7400, a Dell desktop, a no-name-build-it-yourself-desktop-acting-as-a-server and a Dell notebook to Hardy in the last couple of days, and if anything, things are running smoother (if that's a word) now than they were before. 

So your problem may be extremely specific and would not warrant such a sweeping statement....

---

### Post by Jadephyre on 2008-04-27
now don't get me wrong here, i love Ubuntu, i have used Feisty and Gutsy and loved both of them, i just switched to Mint 4 because it came with everything i needed (codecs and stuff) but maybe i would not have switched if i would not have effed up my Gutsy Install somehow.
Now i would like to use Hardy, and the Beta worked okay, and i don't understand why the Final does not work, or takes a trunkload of time to even boot a Live Environment.

---

### Post by Wynne G Oldman on 2008-04-27
I've installed Hardy on three totally different PC's, one 32 bit server, one 64 bit laptop and one 64 bit desktop, and they all work fine. Perhaps you have a hardware compatibility problem.

---

### Post by Jadephyre on 2008-04-27
i guess so but another user has stated that he updated Gutsy to Hardy and it worked, when i did that it didn't really work... and if my Laptop would be defective, then even Mint would not run.
Anyway, i'll see if i'll get Hardy to run... if not, i will have to wait until Mint 5 sees the light of day which will be based on Hardy... hopefully that will run.

---

### Post by mivo on 2008-04-28
Since you experience the troubles relatively early in the start-up phase, you may also have them in Mint. I don't think they use a different kernel/etc (but I may be wrong). May be worth trying to get this worked out. Did you file a bug report?

---

### Post by Jadephyre on 2008-04-28
frankly i don't see the point in filing a Bug Report when there are aleady enough that cover the Kernel Thing.
It depends on the Kernel Mint 5 will use, and i highly doubt that they will use the same Kernel Hardy does after all this trouble.

---

