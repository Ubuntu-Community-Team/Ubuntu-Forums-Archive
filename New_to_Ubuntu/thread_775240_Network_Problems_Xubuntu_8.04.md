---
title: "Network Problems Xubuntu 8.04"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by rhizomaticon on 2008-04-29
Hi,

First, I want to say thanks to everyone who gives their time here to Ubuntu and to helping folks like me.  The spirit of this community :guitar:s.

I have installed Xubuntu into a 20 gig partition on my 7 year old Dell Inspiron 4000 (I split the 40 gig HDD 50/50 and have XP SP2 on the other half-- I dig the partition install option).  

PIII 900 Mhz
256 mb RAM
40 gig HDD
Intel 10/100 ethernet adapter
Netgear W511 v2 PCMCIA wireless lan card

I have a couple issues: 

When installing, everything would hang for a while at a certain moment and return an error something like:

(xxxxxxxx) I/O Buffer error on fd0

and then the install seemed to finish fine
?

Secondly, I can't get ANY network connection to happen.  I know my Netgear card is not supported because it has the Marvell chipset so I might just find a new cheap one that is, but it nevertheless is recognized when I do iwconfig -- all I get is a message like "Network UNCLAIMED" and then it lists all the device characteristics.  If I remove the Netgear card, iwconfig recognizes that it's no longer present.  

iwconfig DOES recognize the Intel ethernet adapter (lists its characateristics) but returns a message of "UNCLAIMED" as well and there is nothing in the applications>system>network for the ethernet connection.

Sorry if I get my terms wrong/am inexact.  I have a feeling y'all can figure this noob out.

Thanks,
B

---

### Post by swoll1980 on 2008-04-29
[http://ubuntuguide.org/](http://ubuntuguide.org/) good networking how to

---

### Post by rhizomaticon on 2008-04-30
> **swoll1980 said:**
> [http://ubuntuguide.org/](http://ubuntuguide.org/) good networking how to

Could you be more specific?  I searched around for a while and couldn't find an answer.

Thanks again,
B

---

### Post by jimrz on 2008-04-30
You may be able to get your W511 v2 working with "ndiswrapper"... not sure ... did a quick search on these forums and did not see any quick solution.

You might see if you can find a Netgear WG511-T (the T is important) as it has the Atheros 5212 chipset and works "out of the box" in Ubuntu using the madwifi drivers. The only issue you might have is that if you need to use WPA encryption, you will have to download and install the latest firmware upgrade from the Netgear site as the card ships with older firmware (at least as recently as _+_ 6 months ago. The installation of the firmware is quick, easy and works without issues. I have one of these in my old laptop and, a few months back, recommended it to a friend and both cards work flawlessly in Ubuntu.

**EDIT:** I just searched for "WG511 v2" and found numerous threads you might want to look at, although apparently getting the right driver to work with ndiswrapper is a challenge. You may be better off with another card.

---

