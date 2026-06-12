---
title: "Only half my ram recognised"
date: 2011-09-16
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Quackers on 2011-09-16
Occasionally after a reboot I'm finding that the system is only recognising 1GB of available ram, whereas 2GB is installed.
When this happens a reboot usually cures it.
Is this likely to be a ram problem, an oneiric problem or just a glitch?
Anybody else seeing anything similar?
Thanks.

---

### Post by ventrical on 2011-09-16
I can't even get system monitor to open in this new install :)

---

### Post by Rocksinboxes on 2011-09-16
Did you attempt to boot into recovery mode? You can get there by holding shift before the  Ubuntu splash screen.  You also might want to do a 'dpkg-reconfigure -a' from the  terminal. Please let me know if this helps.

---

### Post by garvinrick4 on 2011-09-16
Hi Quackers I have 2 installs up to date and ram is recognized. Have a nice evening Quackers.

---

### Post by DogMatix on 2011-09-16
No problem with RAM being recognised here either.

**probably insulting question:** Is your RAM seated properly?


Similar problems have vexed me until I checked!

---

### Post by ventrical on 2011-09-16
No probs here on my tower.

---

### Post by ratcheer on 2011-09-16
No problem here, either. 8 GB RAM, all recognized.

Tim

---

### Post by Quackers on 2011-09-17
Thanks people, I'll just keep an eye on it :-)

---

### Post by ZarathustraDK on 2011-09-17
Are your ram-blocks identical?

How many ram-seats does your motherboard have?

Thinking it could be some issue about trying to run unidentical ram-blocks in dual-channel mode, or something along those lines. Try switching around the blocks if you got 4 sockets, just make sure you always got one in slot 1. Either slot 1,2 or 1,3 (last is dualchannel on most motherboards). Usually the 4 seats have one of two colors, putting to blocks in the same color-seats means running it in dualchannel-mode, which is preferable if your ram-blocks are identical and your mobo supports it.

Just my $0.02

---

### Post by Quackers on 2011-09-17
The laptop is 3 and a half years old and the ram sticks have been in it from the start. It has 2 ram slots and the ram sticks are definitely matched.
Thanks for the suggestion though :-)

---

### Post by ventrical on 2011-09-17
Sometimes I keep extra ram sticks on hand -or- in many cases i can interchange it if it is simple DDR, that way I can tell if a stick has gone bad.

  I just tested my Acer Aspire 3620 with fresh install of Oneiric and it read 1.5 GBs which is the actual amount of RAM.

  I'll keep an eye also.

 Sometimes - in my several years of experience- I have experimented with RAM of all sorts and especially on DELLs, the RAM sort of gets a hardware <BLOCK>. So , what I do is physically uninstall and re-install the ram sticks and in several instances it has unlocked that which was blocking it - dynamic or static ram both.

---

### Post by JRV on 2011-09-20
Run memtest and see what it says.

---

