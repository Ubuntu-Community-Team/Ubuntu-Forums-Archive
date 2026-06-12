---
title: "Driver instal program on Desktop won't execute"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by mizwell on 2008-05-11
Help the geezer please

Failing to get NDISWRAPPER to create the WPA driver from XP, I downloaded the Linux driver files {linux-wlan-ng-0.1.14-prel} for my Linksys WPC11 v3.0 pcmcia wireless card.

Absolutely nothing works. Right clicks to execute the shell script files gets nothing. I have no idea what to do beyond this.

My old laptop is headed for the trash heap if wireless can't be made to work.

ANY help would be greatly appreciated.  Coming from the Mac OS x world, I am totally frustrated after 2 weeks of Xubuntu. I realy want this all to work.

HP Pavilion N3330
540 MHZ
256 MB ram
5 GB HD
xubuntu 8.04

Linksys WPC11 v3.0 PCMCIA card
for WPA2 Personal Airport Extreme

---

### Post by warbread on 2008-05-11
Always keep a cool head.  You don't learn if your frustrated.  I know, yesterday I almost had an aneurism just trying to view some medical files on Ubuntu and hardly got anywhere.  That said, I can totally understand where you're coming from.

It would help to know what it is you've done thus far.   What instructions have you followed and what have you tried to get it working?  According to [these community docs]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys"), your card works out of the box, or did at least.  I normally assume that it didn't, since you're here and asking questions, but since we're in the beginner's forum I'll have to ask just to make sure we're covering all the bases.  So, try going into the terminal and typing 

```
:-$ lspci
``` 

with the card in the slot and post the output here.

---

### Post by mizwell on 2008-05-11
Thanks for the response. Will be keying in (slowly) from another computer.
Problems seem associated with trying to join WPA2 network. All options were for WEP working from the menu bar icon.
Got WPA driver for Windows from Linksys site. Card worked with WPA Windows driver on my WinXP laptop. Linlsys site has Linux driver but no info if WPA2. I tried to load the Linux driver using Synaptic but I couldn't it to recognize the "package". Then tried to "execute" the Configure shell via right click. No luck.

Next moved to NDISWRAPPER using the Linksys WPA driver for Windows. NDISWRAPPER would not accept any of the .inf files from the Window WPA driver.

Also got into the permissions thing as I tried to move drivers to the target machine and extract them. Very frustrating for me. Did get both driver files to the Pavilion N3330. 

 

$lspci
00:00.0 HOST BRIDGE: VIA TECH VT8501 [APOLLO MVP4] REV 04
00:01.O PCI BRIDGE: VIA TECH VT8501 [APOLLO MVP4 AGP]
00:07.0 ISA BRIDGE: VIA TECH VT82C686 [APOLLO SUPER SOUTH] (REV22)
00:07.1 IDE INTERFACE: VIA TECH VT82C586A/B/VT82C686/A/B/VT823X/A/C PIPC BUS MASTER IDE (REV10)
00:07 USB CONTROLLER: VIA TECH VT82XXXXX UHCI USB 1.1 CONTROLLER (REV 10)
00:07.4 BRIDGE: VIA TECH VT82C686 [APOLLO SUPER ACPI] (REV 30)
00:0a.0 CARDBUS BRIDGE: 02 MICRO INC 0Z6812 CARDBUS CONTROLLER (REV 05)AUDIO CONTROLLER ESS TECH ES1983S MAESTRO-3i PCIAUDIO ACCELERATOR
00:0d.0 MULTIMEDIANAUDIO CONTROLLER: ESS TECH ES1983S MAESTRO-3i PCI MODEM ACCELERATOR
00:0d.1 COMMUNICATION CONTROLLER: ESS TECH ES1983S MAESTRO-3i PCI MODEM ACCELERATOR
01:00.0 VGA COMPATIBLE CONTROLLER: TRIDENT MICROSYS CYBERBLADE/i7d (REV 5d)
$

---

### Post by warbread on 2008-05-11
Well, I've got some good news and I've got some bad news.  The good news is that I know what's wrong.  The bad is that you can't get this card on a WPA2 protected network.  It just can't do it.  The best that card can do is WPA.  See the [Wi-Fi Alliance's product certification list]("http://certifications.wi-fi.org/wbcs_certified_products.php?search=1&lang=en&filter_category_id=3&listmode=1"), more specifically the certifications of a [Linksys WPC11 v3.0.]("javascript:popUp('wbcs_ViewCertificate.php?product_id=298',576,445,'lef');")

However, this isn't a Linux issue, so if you want to spend just another $40 or so (I think) you can get a wireless card that will work on your network and salvage the laptop.  Regardless, it would be a shame to just toss it.  If you really don't want to keep it, why not put it up on Craigslist.com in your area for cheap/free?  There always some poor college kid who's looking for a laptop that's good enough for typing up research papers and such.  

The only other option is, of course, to lower the security on your router.  That's up to you, but I don't much see the point in it myself.

---

### Post by mizwell on 2008-05-13
Thanks for getting back with news.  Albeit not quite what I'd hoped for. 

I'm confused because the card works on our existing WPA2 Airport Extreme network using a Toshiba laptop with WinXP Home. Linksys had a WPA update (firmware included, I think)on their web site which is working on the WinXP laptop.  Are you saying that even though it works in WinXP it can't be made to work in xubuntu linux?

What I tried to do was NDISWRAPPER that driver, but failed. Linksys also has a Linux driver with the same release date as the WinXP WPA capable driver update. I had a hunch it might include WPA capabilities but after a couple of tries, I find I am clueless on how to get the driver package to "execute".

Before laying out more cash I would like to try the linux driver. Could you advise me as to how to execute the downloaded driver package?

Thanks again for your time and expertise.

---

### Post by Xiong Chiamiov on 2008-05-13
Ugh, ndiswrapper.  Sorry, I'm not the man to help you out with that (though there are definitely those here who can), I just wanted to drop in and say that if you do buy a new card, those from [Edimax]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2052810031+50001924&name=EDIMAX") work out-of-the-box in Linux, and they're cheap to boot.  I've got the EW-7128G, and besides being $25, it gets amazing reception.  And yes, trash bad, Craigslist good.  I just picked up an ancient 8meg-ram type of laptop for $20 last week, and, if I can iron out some details, 'll be putting Linux on it.  Your lappy will still be useful to someone.

---

