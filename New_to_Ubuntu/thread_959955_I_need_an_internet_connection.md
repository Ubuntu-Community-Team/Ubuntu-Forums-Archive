---
title: "I need an internet connection"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by collapsing wave on 2008-10-26
I need an internet connection.
Without it I cannot use the online tutorials properly. 
I cannot learn and practice to use the command line.
I can't do very much at all.


I have an ubuntu desktop now but no internet access.
I managed to get it working by disabling the LAN in the bios and now apparently need to upgrade the kernel to 2.6.24-19 as shown in this post
[http://ubuntuforums.org/showthread.p...t=Toshiba+L300](http://ubuntuforums.org/showthread.p...t=Toshiba+L300)

I only need a wired connection at the moment and have a desktop with an internet connection to work on.

I believe I can download this kernel to a usb stick and install it onto the laptop.
Can someone give me step by steps for this process. 
If no one can then I can't do it on my own and will have to scurry back to the dark side where I couldn't get onto the Microsoft web site unless I was running internet explorer. This is not what I want.

Will somebody help or point me in the right direction?

---

### Post by Pelham123 on 2008-10-27
For some reason your link only points to the Ubuntu forums main page.

Can you give some more details on your setup

ie - is this a home desktop? How are you connecting to the internet at the moment? Are you dual booting and only XP is working with internet? What modem? You say you had an internet connection, but now its not working?


etc...etc....

---

### Post by collapsing wave on 2008-10-27
The Laptop is a Toshiba Satellite Pro L300 PSLB1A-01L019
intel Celerion 550@2.00 GHz 1GB RAM 32 bit operating system

Realtek RTL8102E Family PCI-E Fast Ethernet NIC (NDIS6.0)
Realtek RTL8187B Wireless 802.11b/g 54 Mbps USB Network Adappter

have a working internet connection on the desktop running XP

strange with that link came accross this yesterday
[http://ubuntuforums.org/showthread.php?t=844163&highlight=Satellite+L300](http://ubuntuforums.org/showthread.php?t=844163&highlight=Satellite+L300)

[https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b](https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b)

was the link that i think I need but I dont want wireless (at least not yet :-) 
If the problem is the 8187B and not the 8102E then can I disable the 8187B? or is it not that simple. I know that I can upgrade to 8.10 but I wanted the long term 8.04 to learn how to drive this thing.
If I can get the wired connection working then I can mess about with the  solution to my hearts content when I want to.

---

### Post by collapsing wave on 2008-10-27
Bump

---

### Post by zvacet on 2008-10-28
Network manager>click on it>manual configuration>in network window select your modem>properties>select type of conection(dhcp or static)>DNS tab> if you use router leave address you will find there otherwise delete it and put your name servers>general tab<check your modem>go to the terminal and type

```
sudo pppoeconf
```

---

### Post by collapsing wave on 2008-10-28
I guess those step by steps were not clear enough which is slightly disheartening..
on the select type of connection I get
serial modem
PPoE
GPRS/UMTS

from this i guess that the serial modem is dail up- ignore that I have broadband.

GPRS/UMTS is asking for an access point name which I don't know about and therefore ignored...

So PPPoE was where i placed my bet added name and password but the OK box wont light up until I uncheck the enable this connection box. 
Then I  click OK so now the top bar says ppp0 Properties 

but the DNS Tab is still empty 
just prompting me to Type address if I click the add button. 



Have I made it clear that the LAN was disabled in the BIOS because otherwise Ubuntu won't load up. Will that make a difference?

Next step humbly asked for. I am going to grind this out. Never Surrender! Never retreat!

---

### Post by phidia on 2008-10-28
> **collapsing wave said:**
> I guess those step by steps were not clear enough which is slightly disheartening..
on the select type of connection I get
serial modem
PPoE
GPRS/UMTS

from this i guess that the serial modem is dail up- ignore that I have broadband.

GPRS/UMTS is asking for an access point name which I don't know about and therefore ignored...

So PPPoE was where i placed my bet added name and password but the OK box wont light up until I uncheck the enable this connection box. 
Then I  click OK so now the top bar says ppp0 Properties 

but the DNS Tab is still empty 
just prompting me to Type address if I click the add button. 



Have I made it clear that the LAN was disabled in the BIOS because otherwise Ubuntu won't load up. Will that make a difference?

Next step humbly asked for. I am going to grind this out. Never Surrender! Never retreat!

How did you disable LAN? Yes it will make a difference to have it disabled-you won't be able to use it if it's disabled.

I think you need to resolve your start up issues and then perhaps your network will just work.

---

### Post by collapsing wave on 2008-10-28
The reason I cannot resolve my start up issue is that ubuntu doesn't recognise my realtek 8187b. which is why it won't boot up.
i need to download a kernel this has been done and will work but i don't know how to do it.


but noone seems to be able to tell me how to do this to a usb stick so that i can then load it into hardy.

I'm going backwards and forwards here

so i was trying to bypass the 8187b to get my connection going as a wired connection.

This is a beginners forum. I am a beginner. 
If you have time please do a little search on my laptop (specs below)

---

### Post by oldsoundguy on 2008-10-28
Get rid of the realtec!

I have 4 desktops in operation right now .. On has a 3Com PCI network card (10/100 3C905 series .. which works in every operating system known to man!)($5.00 to $10 bucks on eBay)  And 3 wireless .. (D-Link 520G PCI which install right out of the box)($10 to $20 bucks on eBay)

---

### Post by collapsing wave on 2008-10-28
> **oldsoundguy said:**
> Get rid of the realtec!

I have 4 desktops in operation right now .. On has a 3Com PCI network card (10/100 3C905 series .. which works in every operating system known to man!)($5.00 to $10 bucks on eBay)  And 3 wireless .. (D-Link 520G PCI which install right out of the box)($10 to $20 bucks on eBay)
Thanks for the advice but I wouldn't even know where to start with that.

I know the computer can be connected. It can be done but I don't know how it can be done. The do's and Dont's ask you not to private message anyone otherwise I'd be asking them.

What I need is a working connection
Or I need to download a kernel upgrade to a usb stick and install that.
clear instructions please.

I am a beginner

---

### Post by phidia on 2008-10-28
> **collapsing wave said:**
> Thanks for the advice but I wouldn't even know where to start with that.

I know the computer can be connected. It can be done but I don't know how it can be done. The do's and Dont's ask you not to private message anyone otherwise I'd be asking them.

What I need is a working connection
Or I need to download a kernel upgrade to a usb stick and install that.
clear instructions please.

I am a beginner

I think perhaps the best idea for you is to try a different distro's live cd. 
[Zenwalk]("http://www.zenwalk.org/modules/tinycontent/index.php?id=31") has a live cd now or [mepis]("http://www.mepis.org/mirrors") might work too. 
If one of those or a different live cd boots and gets you a connection you can install that.

---

### Post by robert shearer on 2008-10-28
> **collapsing wave said:**
> Thanks for the advice but I wouldn't even know where to start with that.

I know the computer can be connected. It can be done but I don't know how it can be done. The do's and Dont's ask you not to private message anyone otherwise I'd be asking them.

What I need is a working connection
Or I need to download a kernel upgrade to a usb stick and install that.
clear instructions please.

I am a beginner

You say you have disabled the LAN in BIOS?? Presumably this is the ethernet port on the motherboard.??

What oldsoundguy says is that you should install a network card that works with linux.
Easy to do on a desktop machine, harder on a laptop.

If your laptop has a pcmcia slot and you know someone else with an ethernet pcmcia card in their laptop perhaps you could borrow the card long enough to download the "kernel' you seem to be looking for.??

What machine are you posting from ??

Where are the laptop specs??

---

### Post by collapsing wave on 2008-10-28
Mate, I don't wish to seem ungrateful, because you have taken the time out to answer me, but if that was not what I asked.

 This is the absolute beginner Talk forum, emphasis on absolute.

There is a way to get a wired connection. (part solution)
Then there is a way to solve the wireless issue(full solution)

Can someone help me. I don't understand what i need to do because I am an absolute beginner. Emphasis on absolute.

---

### Post by phidia on 2008-10-28
I don't know how you can get a connection if you have disabled the card in bios.

You could enable the card again, boot in recovery mode, and install the kernel you require.  Let the thread know what kernel you need you should be able to install it if it's in the repos. You would do all that in command line, and as you've pointed out you are a beginner-but it could be done.

You can check out the wiki on realtek cards [here]("https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCardsRealtek") plus there are links to the previous page on wired networking at the top of that page.

---

### Post by collapsing wave on 2008-10-28
RTL8187B - Windows 98 => [http://www.thecashplanet.com/ubuntu/rtl-win98-ndiswrapper.zip](http://www.thecashplanet.com/ubuntu/rtl-win98-ndiswrapper.zip) 

nice...

this is driving me up the bloody wall!

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsRealTek#PCI](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsRealTek#PCI)

Has stuff missing Ndiswrapper link is broken...grrr

---

### Post by mishivia on 2008-10-29
Hi C.wave and others,
Ok so after literally printing 200 + pages from ubuntu wiki and reading posts after posts here is my advice.
The problem you are having is a direct result from ubuntu's lack of support for winmodems. Your laptop has window software and therefore the hardware is also window hardware, hence winmodems.
Here is the light at the end of the tunnel because there is a program (scan modem) that identifies your particular modem and then tells you the driver that needs to be downloaded and configured from linmodems. Configuring may prove to be tricky but pm me and I will do all I can to help also make sure to suscribe to linmodems discussion board because the folks over there are uber patient and helpful.
Hope this helps you and your right, it may take some time (in my case lol 4+ weeks) but it CAN be done. Persevere my friend. Whats the point of using ubuntu, if at every issue you succomb to the easy way out when all issues can be resolved with a little patience.
niesha

---

