---
title: "20:04 - I bought a GPU off of Ebay, how can I tell if it is ecellerated....."
date: 2020-05-28
forum: New to Ubuntu
---

### Post by jw-middleton on 2020-05-28
I put Ubuntu on a Dell Optiplex 7010 DT. It is a small form factorn system, with a very small ps. So, I picked up a $20 low profile AMD card on Ebay. I read that I would not be able to find the drivers for a  card this old, but it seems to be working. I just can't tell if it is properly setup. Can anyone tell  from this info:

```
1:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Turks PRO [Radeon HD 7570] (prog-if 00 [VGA controller])
        Subsystem: Dell Turks PRO [Radeon HD 7570]
        Flags: bus master, fast devsel, latency 0, IRQ 32
        Memory at e0000000 (64-bit, prefetchable) [size=256M]
        Memory at f7e20000 (64-bit, non-prefetchable) [size=128K]
        I/O ports at e000 [size=256]
        Expansion ROM at 000c0000 [disabled] [size=128K]
        Capabilities: [50] Power Management version 3
        Capabilities: [58] Express Legacy Endpoint, MSI 00
        Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
        Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
        Capabilities: [150] Advanced Error Reporting
        Kernel driver in use: radeon
        Kernel modules: radeon

```

Is there a test I can do to see if the graphics are accelerated?

John

---

### Post by Tadaen_Sylvermane on 2020-05-28
Deleted my previous post as it was to dumb...

According to your post above the driver is loaded. That being said if your monitor is plugged into the card and you don't see any artifacting or other problems, and all is smooth then I'd say no worries.

---

### Post by jw-middleton on 2020-05-28
> **Tadaen_Sylvermane said:**
> Deleted my previous post as it was to dumb...

According to your post above the driver is loaded. That being said if your monitor is plugged into the card and you don't see any artifacting or other problems, and all is smooth then I'd say no worries.

Thanks Tadaen, It seems to be working fine. So, I need to find a game that would test it. Know of any?

John

---

### Post by mastablasta on 2020-05-29
Phoronix test suite comes with many tests and demos of various engines. it will give you what you need along with report on where you are at. you can also install some items manually. such as for example Unity engine test/demo etc.
how to install: 
[https://linuxconfig.org/how-to-install-the-latest-phoronix-test-suite-on-ubuntu-18-04-bionic-beaver](https://linuxconfig.org/how-to-install-the-latest-phoronix-test-suite-on-ubuntu-18-04-bionic-beaver)

usage:
[http://manpages.ubuntu.com/manpages/cosmic/man1/phoronix-test-suite.1.html](http://manpages.ubuntu.com/manpages/cosmic/man1/phoronix-test-suite.1.html)

I find it easy to use. basically you run it , then select what tests you want to do and it will do them and then give report at the end.


other options:
if you install Steam there are some good free ones that have linux versions and that you can try - Counter strike: Global offensive, Team Fortress 2, DOTA 2 to name a few

if you don't want Steam there are also a couple of nice opensource FPS games like Xonotic, Red Eclipse, World of Padman...

if you have  Quake4 or Doom3 you can run these natively as well. I also have KSP which also runs natively and i bought some native linux games of Steam (Left4 dead, Portal, Dirt, Age of wonders, Total war: Shogun, Crusader kings,...).

There are also a bunch of GOG games and other windows games that will run fluently on using Wine (or Play on linux or Proton or Lutris). I used Play on Linux for installation and so far i have Oblivion, Cod2, Cod4MW, CoDMW2, Unreal Tournament 2004, Arx Fatalis, Hitman: Blood Money, Red faction 2...

There are so many games available and working on linux these days that i don't have time to even try them all.

---

### Post by Yellow Pasque on 2020-05-29
> I read that I would not be able to find the drivers for a card this old

Then you read it wrong, or the author wrote it wrong.
The correct drivers for this GPU are already built into the OS. You won't find closed-source/proprietary drivers available for download, but that is no big loss. The open-source ATI/AMD drivers are generally better anyway.

> **jw-middleton said:**
> Is there a test I can do to see if the graphics are accelerated?

```
glxinfo -B
```
Make sure you don't see any "software rendering", "llvmpipe", etc.

---

### Post by jw-middleton on 2020-05-29
> **mastablasta said:**
> Phoronix test suite comes with many tests and demos of various engines. it will give you what you need along with report on where you are at. you can also install some items manually. such as for example Unity engine test/demo etc.
how to install: 
[https://linuxconfig.org/how-to-install-the-latest-phoronix-test-suite-on-ubuntu-18-04-bionic-beaver](https://linuxconfig.org/how-to-install-the-latest-phoronix-test-suite-on-ubuntu-18-04-bionic-beaver)

usage:
[http://manpages.ubuntu.com/manpages/cosmic/man1/phoronix-test-suite.1.html](http://manpages.ubuntu.com/manpages/cosmic/man1/phoronix-test-suite.1.html)

I find it easy to use. basically you run it , then select what tests you want to do and it will do them and then give report at the end.


Thanks Mastablasta! You spent a lot of time of that post! :o First off I'm 74 years old and have been retire since 2008. But, I worked in IT, the last 15 years as a Project Manager for physical plant stuff. Just this week I started playing with Ubuntu after buying a RPi-4B and wanting something with a bigger community. So, I'm big on benchmarks as I use to overclock all the stuff I built in the days of SETI1. I figured PTS would do the trick, but OMG what  a beast. I got it installed, but had no idea what I was doing. After getting it running, I told it to run a test, but it wanted to know what test and I didn't know. So, I picked a menu item. It asked it it should download the needed info to run the tests. Like a dummy I said yes. It started downloading TONS of data. One of the 83 packages was over 1.5 GB. I killed it and uninstalled. Then I went for a game that didn't require Steam. I ended up downloading Red Eclipse. It worked great. After dying 3 times and only getting one kill, I quit as I'd proved that it worked and am happy with my $20 graphics card. I know my 9 year old grandson will have a ball with it on his next visit.

John

---

### Post by grahammechanical on 2020-05-29
> kernel driver in use: radeon

That is your video driver and it is the open source video driver that comes as default in Ubuntu. To see if there is a proprietary video driver available open a utility called Software and Updates and open the Additional Drivers tab. If the machine is connected to the internet and you allow the utility time to work you may be offered a proprietary video driver that can be installed. 

I am still being offered a proprietary driver for my Nvidia GT216. But I use the open source Nouveau driver anyway. Different open source drivers for different makes of video card.

Regards.

---

### Post by jw-middleton on 2020-05-29
Thanks!

> **Yellow Pasque said:**
> Then you read it wrong, or the author wrote it wrong.


```
glxinfo -B
```
Make sure you don't see any "software rendering", "llvmpipe", etc.

Actually I read it multiple place as the GPU is old. Someone even post the oldest card for which AMD drivers wouuld be available. Liikely the posts were before 20.04 was released.

glxinfo told me what I was looking for:

```
Device: AMD TURKS (DRM 2.50.0 / 5.4.0-31-generic, LLVM 9.0.1) (0x675d)
    Version: 20.0.4
    Accelerated: [SIZE=3]**yes**[/SIZE]
    Video memory: 1024MB

```


Also, a few games ran great, which also answered my questions.

John

---

### Post by mastablasta on 2020-05-29
yeah Phoronix is used for serious hardware testing. they do tests, compariosn and reports of ow the new and sometime older hardware and drivers work. so one can see improvements or regressions. it's an interesting website. 

as for the tool depends what engine is used. games these days are often 6 GB or more. new ones take up 50-60 GB. it's due to high resolution textures i think.

---

### Post by jw-middleton on 2020-05-30
Thanks for all the help! You guys are great! 

SIgh...the video card must have been too much of a strain on the 250 Watt PS, as the computer died this afternoon. The card was a Dell branded card that was one of the few LP cards to fit the SFF machine. 

I am back on my RPi4-B. Oh, well...it works and I still have my main system that I working on the F@H Covid-19 project with.

Now off to the Raspbian Forum. :p

---

### Post by mastablasta on 2020-05-31
there are a few older new and relatively cheap LP out there that have good support. nvidia GT 730 is old and can run some new and older games. i use the regular sized one on a 16 year old PC. and i can play many linux and older windows games. i can also play some new ones on lower settings (reduced resolution). They also have 1030 (which is updated version of this chip), then 1050 (older entry card, 1080 and more). AMD RX 560 and 570 are also available.  there is also GTX 1650 now in LP (this one is entry gaming chip and can handle latest AAA games on medium settings). even the lower powered ones will need about 35-65 W available from the PSU. if you have hard disk, newish CPU (low powered or the kind that uses up to ma 50 W) you should be able to get them working on 250 W but it is very close. as long as PSU is gold standard it should get 220 W, which should be enough for all basic components.

for gaming GPU you do usually need slightly stronger PSU, but these 1030 series don't use as much power and seem descent as long as you don't need games to run on 4K ultra settings. 

i am annoyed by SFF boxes that need proprietary expensive PSU. luckily there are some small boxes out there that can fit in "normal" sized GPU and standard ATX PSU. quite interesting solutions out there that save plenty of space and at the same time provide enough air flow. there is also very small Intel NUC (box in the size of modem) paired with strong AMD radeon GPU that was made for gaming.

---

### Post by jw-middleton on 2020-06-04
> **mastablasta said:**
> 

...for gaming GPU you do usually need slightly stronger PSU, but these 1030 series don't use as much power and seem descent as long as you don't need games to run on 4K ultra settings. 

i am annoyed by SFF boxes that need proprietary expensive PSU. luckily there are some small boxes out there that can fit in "normal" sized GPU and standard ATX PSU. quite interesting solutions out there that save plenty of space and at the same time provide enough air flow. there is also very small Intel NUC (box in the size of modem) paired with strong AMD radeon GPU that was made for gaming.

Well the SFF system was free, so I can't complain. I really liked using it and was not happy going back to the RPi4. So,I found the mini-tower version of the same 7010 for $134 shipped. I wanted a similiar system as I figured I could use some of the parts from the SFF like the HDD, RAM, etc. It came yesterday. I moved the HDD and 2 RAM sticks to the newly acquired box and Ubuntu came up fine. I had ordered the cheapest one avail. It was the Optiplex 7010 MT with 4GB DDR3, 500GB HDD and an i5-3475S. I picked that box over the SFF one since it will take an ATX12V PS, giving me option on what GPU I could install. Although it has to be a low profile one.

When I open the box I saw a 7020 instead of the 7010 I ordered. It is 2 years newer, takes full size GPU and had an i5-4590 CPU. BUT, it uses an 8-Pin power connector for the MB, which is not ATX12V standard. I thought I was screwed until I found a 24 pin to 8 pin converter that is made just for this problem. It will be here in a few days. I checked one of the GTX 950's I have in my drawer and it fits! 

I was well aware of all the GPUs you mentioned as I have done a lot of research. I was seriously looking at the GTX 1650 LP with GDDR6 memory. It just came out last month. Now I'll be happy with the Asus Strix 950 Gaming. 

Thanks again for your help!

John

---

### Post by TheFu on 2020-06-04
ebay GPU purchases for popular version of GPUs are often lower-end cards who someone flashed the GPU BIOS to report a different card so they could sell a used $20 GPU for $50.  ebay was full of fake GT 1060 cards a few years ago.  Buyer beware.  

However, if you don't care about the high-end capabilities of the more expensive GPU and just need a GPU that works acceptably, ebay can be a place to find a deal.  Just be certain that you verify the card being sold with all the inputs and output actually matches what the source vendor says that card can have.

For example, no 1030+ GPU will have a VGA output.  Those are all deprecated so only a fake would show that in the description or card images.  Also the amount of DRAM can be wrong in the fakes.

---

### Post by jw-middleton on 2020-06-05
> **TheFu said:**
> ebay GPU purchases for popular version of GPUs are often lower-end cards who someone flashed the GPU BIOS to report a different card so they could sell a used $20 GPU for $50.  ebay was full of fake GT 1060 cards a few years ago.  Buyer beware.  

However, if you don't care about the high-end capabilities of the more expensive GPU and just need a GPU that works acceptably, ebay can be a place to find a deal.  Just be certain that you verify the card being sold with all the inputs and output actually matches what the source vendor says that card can have.

For example, no 1030+ GPU will have a VGA output.  Those are all deprecated so only a fake would show that in the description or card images.  Also the amount of DRAM can be wrong in the fakes.

Interesting post Fu. I had no idea folks did that, but I'm not surprised. I didn't think anyone would do that with the $20 card I bought, but I checked it out anyway. I found pics of one on Amazon and it matched perfectly. Now that I have a 7020, I can't use it. I did find a high profile bracket for the card, but it is $10, half the price of the card. :p.

John

---

