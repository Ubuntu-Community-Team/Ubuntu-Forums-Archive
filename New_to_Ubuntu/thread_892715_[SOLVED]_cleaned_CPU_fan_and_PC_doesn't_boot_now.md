---
title: "[SOLVED] cleaned CPU fan and PC doesn't boot now"
date: 2008-08-17
forum: New to Ubuntu
---

### Post by mridkash on 2008-08-17
Hello,
My desktop PC was freezing after boot and I decided to clean up RAM chips and CPU fan. Everything went fine until I reconnected everything and powered it up. The intel motherboard light turned on but the pc didn't start. So I checked wiring again and this time, it started but as soon as the intel screen came, the processor shut down, and every time after it did so. 
Then I tried removing the motherboard battery and reinserting it, again it started up for a few seconds and turned off. Then there was a jumper setting on the motherboard, it said;
1-2: Normal
2-3: Config
No Jumper : Recovery

The jumper was in 1-2, I removed it and started the pc again, nothing. Sometimes when I start it it makes beep sounds like beep boop beep. It might be a hardware problem, bios or wiring I don't know. 

Please Help me fix it.

CPU: Intel Prescott 3 ghz
MBoard: Intel 915 GAG
Graphics: Nvidia GeForce
RAM: DDR 256 Mb x 2
HDD: 250 GB Hitachi SATA, 80 Gb WD SATA

---

### Post by SunnyRabbiera on 2008-08-17
did you put everything back in the right way?

---

### Post by jolx on 2008-08-17
i think i had something like this, what i did is i unplugged the cpu fan the started it shut it down straight away reconnect the cpu fan and then it worked. this was with a 2.6 GHz celeron northwood on a MSI 651M-L

---

### Post by cprofitt on 2008-08-17
You will want to do the following:

A)  Remove all PC cards in the PCI slots and unhook all hard drives and cd/dvd drives
try to start the computer

B)  Remove the ram
try to start the computer (this should yield some beeps)

C)  Remove and re-seat the processor (I can only hope that you did not break it if you removed the heat sink to clean it)

If you can get the computer to boot with A -- then put one device in at a time and reboot...

---

### Post by ibuclaw on 2008-08-17
First, read your [Motherboard Manual]("http://download.intel.com/support/motherboards/desktop/sb/c6413602_en.pdf"), read it well.

Follow it's instructions to successfully connect up all wiring.
You should never dismount a motherboard yourself unless you know how it connects up.

Going blindly may result in hardware damage, smoking wires and/or fires ;)

Regards
Iain

---

### Post by lswest on 2008-08-17
also, make sure you remembered to plug in the CPU fan again, and (if there was any) that you replaced the thermal paste (or that there was still some in usable condition on the CPU or fan).  Then read the documentation for the motherboard.

---

### Post by mridkash on 2008-08-17
I started the PC again, after some minutes and the bios screen came up, and just as it started, a message flashed on the bios screen saying;
"This computer was shut down due to thermal overheating, resolve it right away by servicing it"

then again when I started it, after a few seconds, down.

---

### Post by Elfy on 2008-08-17
Sounds like the heatsink isn't mounted properly or there is no thermal paste. It would start for a while with no fan - mine did until I remembered ;)

---

### Post by Loaded.len on 2008-08-17
check to make sure you have enough thermal grease under the heatsink, seat it properly and make sure the fan is connected.

---

### Post by emshains on 2008-08-17
> **mridkash said:**
> I started the PC again, after some minutes and the bios screen came up, and just as it started, a message flashed on the bios screen saying;
"This computer was shut down due to thermal overheating, resolve it right away by servicing it"

then again when I started it, after a few seconds, down.

Obviously, you didnt replace the thermal paste (flux) or/and you didnt connect the cpu fan, or you burned you're precious Presscot Intel with HT.
Dont worry, I had heat managment problems with my 3.0ghz intel too, its like an epidemic for these to overheat, so the trick here is not to overcook youres and then you will be able to enjoy the sweet sugar-glazed muffins of hyper-threading.

---

### Post by mridkash on 2008-08-17
I dont have any thermal paste right now, but i didn't touch anything else than the fan, there was some silver grease but didn't remove it.
Did it happen just because I removed the fan for a while?
And will it not work without a fresh new thermal paste?

---

### Post by Loaded.len on 2008-08-17
Processors these days step down and eventually stop altogether when overheated.  I wouldn't worry too much about permanent damage.  That being said, why risk it?  Go to you your local computer repair shop and get a dollars worth of grease.

Note: I had an AMD Athlon 1400 that died within 5 seconds of the heatsink clip popping off when I was benchtesting it.  And yes, that damage was permanent.

---

### Post by Sinkingships7 on 2008-08-17
Er... I'm not trying to insult your intelligence, but it's always nice to check...

You didn't wash the ram with a wet cloth, did you? Also, make sure you put your fan back on the right direction. When you put your hand in front of it, you should NOT feel air coming from it, but rather from the sides of the heatsink.

---

### Post by mridkash on 2008-08-17
Thanks guys, you helped me pinpoint the problem. It was the thermal paste, I just can't believe it is that important. Processor lasts just 5-6 secs without it.
Anyway, the real problem faces me now. This computer is my parent's desktop and we live in a small town where it is difficult to find even computer dealers, forget repair centers. So, thermal paste seems impossible to get from the market.

I was wondering if I could use simple silver fabric paint powder to make a paste. And I tried it out, mixing silver color powder with linseed oil and applying the paste on heat sink. Well, its been around half an hour and the pc is working fine, the hardware monitor shows average temp. to be 60 C which is normal.:)
But I'm not willing to rely on this "solution" as yet. My dad says they use Aluminum paint in their factory and I will try that too.

Thanks for your help

Ps. My parents are using only Ubuntu for the past 1 yr

---

### Post by Sinkingships7 on 2008-08-17
You could buy some from [Newegg]("http://www.newegg.com"). They sell relatively cheap, and they're very dependable.

---

### Post by mc4man on 2008-08-18
> My dad says they use Aluminum paint in their factory and I will try that too. I would not use a paint and would be extremely careful using a homemade paste containing Aluminum particles. (may cause a short circuit if it squeezes out onto board

You really should get some real paste and clean both surfaces carefully before applying a **small** amount. The reason for using a thermal paste is to 'fill' in microscopic imperfections between the 2 metal surfaces which other wise would trap air. ( a terrible conductor of heat.

Google 'how to apply thermal paste' for tips ect.

Worst case if you could find a couple of thrown away pc's you could salvage the paste from them (preferably from same manufacturer and only temp solution

---

### Post by CEB2nd on 2008-08-18
If you decide to order thermal paste from a supplier, I recommend
a product called Arctic Silver. I used it on some nvidia video cards
that were running hot and it cured the problem. Good luck.

---

