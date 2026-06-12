---
title: "trouble with booting anything"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by matthewbrave on 2008-10-26
hi

i am having some difficulty with getting my other computer to recognize the hard drive and dvd rewriter within cmos.

i have changed the ide cable from another computer with still the same result.

i have forgotten to bring my ubuntu live cd with me to see if that will make any difference but i would like to have windows installed on it.

the error i am receiving is- 

SiS900 PXE BootROM v1.09 Use BEV/BBS

CLIENT MAC ADDR: 00 0f ea c8 10 d4 GUID: 000feac8-10d4-2005-0328-062714000000
PXE-E51: No DHCP or proxyDHCP offers were received.

PXE-M0F: Existing Intel PXE ROM.
DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER

any ideas as i am really stuck with this.


thanks

---

### Post by kevstar31 on 2008-10-26
Did you remember to set the master/slave jumper on the drives?

---

### Post by CatKiller on 2008-10-26
> **matthewbrave said:**
> DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER

Is there anything on the hard drive? If not, then it won't be [bootable]("http://en.wikipedia.org/wiki/Bootable") until you install an Operating System on it.

Your installation disc will be bootable, but you'll need to tell your computer that you want to boot from that drive. There should be a setting in your BIOS for boot order. Make sure that you're booting from the DVD drive before the hard drive. And both of these before the Network.

All of this assumes that your hardware is functioning correctly. Things to check are;

Jumper settings - one Master and one Slave per IDE channel
Motherboard settings - both IDE channels should be enabled
Good cable - if you have a known-good cable, that can help enormously with isolating problems.

Of course, if you're using SATA or SCSI then you'll probably need to check different things instead, but I've not used them so I couldn't tell you what they would be.

Good luck, and post more information if you still have problems.

---

### Post by matthewbrave on 2008-10-26
hi i am new to 'cmos' and i dont know where to see if the ide channels are.

i have been able to locate a place where there is an option to detect hdd's and it has come back negative with no signs of a hdd or dvd drive.

i am using a trusted cable from my own computer which i know works.


any solutions would be greatfull.

thanks.

---

### Post by BDNiner on 2008-10-26
Look on the back of the hard drive and dvd writer. there should be some small jumpers, make sure one is set to master and the other is set to slave. 

When you have 2 devices using the same cable then one has to be the master of the other. there is also an option for cable select. that means that the position of the device on the cable determines if it is the master or the slave, if you choose this option make sure that the jumpers on both the hard disk and dvd drive are set to CS.

---

### Post by matthewbrave on 2008-10-26
ok i will go and change the jumpers to cs and try to boot and see what happens.

---

### Post by matthewbrave on 2008-10-26
ok, i have changed the dvd drive and the hdd to cs but i am still reciving the same message over and over again. i went in to cmos and it still hasnt picked up either one drives.

---

### Post by matthewbrave on 2008-10-26
i have still had no luck with this machine... can anyone help!!!

---

### Post by CatKiller on 2008-10-26
The Master should be on the end of the cable, furthest from the motherboard's IDE controller. The Slave should be in the middle. Some cables require that one particular end should be connected to the motherboard and won't work the other way round. Others will work whichever way you have them. Some are colour-coded with the motherboard end coloured blue, the Master coloured black and the Slave coloured grey.

Some BIOSes will not show anything as connected in the configuration utility itself for optical drives, although some do. They should all detect a hard drive properly though.

Some BIOSes have an option to disable one or both of the IDE channels. Not all do, though, and I can't remember exactly where the setting is in mine.

If both devices are on the same cable, it's worth trying them in the other IDE channel. It might also be worth trying them on separate IDE channels with a second cable.

It's also worth making sure that the cable is in the right way. Most of the time the connectors are keyed so that they only go in one way, but sometimes they aren't. The red trace side of the ribbon connects to Pin 0. On the drive end, this is usually closest to the power connector, but the motherboard end could be oriented in any direction.

Another thing that is worth checking is that none of the pins on any of the connections are bent.

I feel your pain. Hard drives can be a real irritant.

---

### Post by matthewbrave on 2008-10-26
i have tried all those options with nothing coming from it.

i think it is something to do with the bios.

i have also removed the battery on the mobo to reset the settings.

---

### Post by matthewbrave on 2008-10-29
i am still having no luck with this machine!!!

can anyone help me get it up and running.

i have taken out the dvd rewriter and inserted a drive that i know works!!

i am stabbing in the dark atm and i dont want to do too much as i could break it!!



thanks

---

### Post by CatKiller on 2008-10-29
When troubleshooting hardware, it's always easiest if you can get things as simple as possible.

I'm assuming that your hard drive doesn't have anything on it, so isn't bootable. So you might as well disconnect that.

You know that your replacement optical drive works, so it's probably best to concentrate on that. Use a disc that you know can be booted from - test it in another machine. It might also be worth making sure that the lens is clean and the disc is free of scratches.

If the processor is overclocked, set it back to factory settings. It might be worth going down to one stick of (known good) RAM.

Then it's just a case of checking every BIOS and jumper setting that you can. Testing each configuration, and repeating as necessary. It's tedious and frustrating, but computers are supposed to be bootable. Either something is mis-configured, or something is broken. You need to establish which it is in order to be able to correct it.

It's possible that the IDE controller is broken. Do you know how long it's been since the computer was known to be working correctly, and what sort of things have happened to it in the meantime? It's probably worth inspecting the motherboard for any damaged capacitors - any that are bulging or cracked mean that the motherboard is essentially useless.

Sorry I don't have better news for you. Good luck again.

---

### Post by matthewbrave on 2008-10-29
i have writen down exactly what comes up


Intel undi, pxe-2.0 (build 082)
copyright (c) 1997-2000 intel coprpration

sis900 pxe boot rom v1.09 use bev/bbs

client mac addr: 00 0f ea c8 10 d4 GUID: 000feac8-10d4-2005-0328-062714000000
pxe-e51:no dhcp or proxydhcp offers were recived

pxe-m0f:exiting intel pxe rom.
DISK BOOT FAILURE,INSERT SYSTEM DISK AND PRESS ENTER


WHAT ARE BIOS JUMPERS???

---

### Post by matthewbrave on 2008-10-29
wqhen i came in possetion of this comp my friend said there was a burning smell so i switched on and cpu fan wasnt working. 

i got a new one off ebay and now i can see something on the screen rather then nothing. i will atempt the one ram thing and i will also look at the mobo to see if there is anything wrong

---

### Post by CatKiller on 2008-10-29
> **matthewbrave said:**
> i have writen down exactly what comes up


Intel undi, pxe-2.0 (build 082)
copyright (c) 1997-2000 intel coprpration

sis900 pxe boot rom v1.09 use bev/bbs

client mac addr: 00 0f ea c8 10 d4 GUID: 000feac8-10d4-2005-0328-062714000000
pxe-e51:no dhcp or proxydhcp offers were recived

pxe-m0f:exiting intel pxe rom.

This looks to me like it is trying to boot from the Network. Which isn't a problem, necessarily, as long as the computer knows to also try to boot from something else as well.

> DISK BOOT FAILURE,INSERT SYSTEM DISK AND PRESS ENTER


WHAT ARE BIOS JUMPERS???

There aren't BIOS jumpers as such, but there are often jumpers on the motherboard for some low-level settings like memory/processor speed, clearing the CMOS, and so on. You might not have any jumpers on the motherboard if it is new enough, but if there are any, then one of those settings could conceivably be causing you problems. Which means you need to check them.

---

### Post by CatKiller on 2008-10-29
> **matthewbrave said:**
> wqhen i came in possetion of this comp my friend said there was a burning smell so i switched on and cpu fan wasnt working.

This seems like a significant piece of information. Depending on how long the computer was running without a fan, the processor could well have got hot enough to damage either itself or something else. It could be that you'll be looking for some new computer innards soon.

Newer processors have a thermal shutdown mechanism to prevent that sort of damage, but older processors would just get hotter and hotter until something broke. So whether you're still looking at a configuration problem, or if it's something much more serious, really depends on what happened at this point.

---

### Post by matthewbrave on 2008-10-29
well... after a close inspection of the mobo, next to the battery there are 2 small prongs and it says 'clr_cmos' under the prongs.

what shall i do now??

---

### Post by matthewbrave on 2008-10-29
the computer is an acer aspire t120e-8870

amd sempron 2800+ fsb333MHz 256kb l2

---

### Post by CatKiller on 2008-10-29
If you wanted to reset the BIOS to factory defaults, you would move that jumper to the Clear CMOS position for about half a minute, and then move it back. If you don't want to do that, then leave it be. If there aren't any other jumpers then you can tick that off your mental list of things that might cause the computer to not boot.

---

### Post by OldTimeTech on 2008-10-29
Also it has 256KB of memory, not enough to run Ubuntu...maybe Damn Small Linux or Puppy Linux.

If there was a burning smell, it could of been the processor burning, it could of been the ram....and again various other parts in the machine.

I think at this point a new mobo, processor and ram is unfortunately what you are looking at....and possibly a new hard drive if this one is not being seen either in your bios or with a cd/dvd of a linux install.

---

### Post by CatKiller on 2008-10-29
> **OldTimeTech said:**
> Also it has 256KB of memory, not enough to run Ubuntu...maybe Damn Small Linux or Puppy Linux.

That figure is for the processor's L2 cache. 256 kB is fairly common, and doesn't relate to the amount of RAM in the machine.

While the burning smell could have been a fault in the PSU that overvolted the fan, causing it to fail and potentially taking other things with it, it could well have been the fan as the primary cause, which means that the processor could be damaged and the heat *might* have taken out some of the nearby components depending on how hot it got. I'd imagine that thermal paste is quite smelly when it gets very hot, so it might not be damaged at all.

The fact that the machine successfully POSTs is a promising sign, so I've got my fingers crossed for the guy that it's still just a configuration problem and he doesn't have to shell out for new bits. The IDE controller could be faulty though, and that doesn't get tested in the POST. Once the computer is bootable, running Memtest from the Ubuntu cd and monitoring temperatures and voltages should help to isolate any potential lingering problems.

---

### Post by OldTimeTech on 2008-10-29
Sounds good

---

### Post by matthewbrave on 2009-01-02
back again still with the same problem.

i have a bit more knowledge on how these things work.

i have taken out the cpu and tried it in my friends computer and it works perfectly.

i then used his processor in the acer and it switches on but then there is nothing displayed on the screen.

i then put the acer's original processor back in and it goes back to normal with the error message.

there is a hdd in the acer with 98 on it and the jumpers are set to cs and the hdd is on the end of the ide cable.

---

### Post by matthewbrave on 2009-01-02
is there any point in flashing the bios, if so how??

---

