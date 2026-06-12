---
title: "Strange Problem with Wireless!"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by sim085 on 2008-05-15
Hi,

I have been using Windows on my laptop from the first time I bought it. Last week I decided to try and install Ubuntu on it (version 7.10) and everything worked fine apart from the wireless! I tried some commands from this same forum (although I cannot found the link now). Anyways the wireless still did not work so I diced to revert to Windows for the time being. However when I installed Windows back on my laptop I discovered that the wireless signal strength was very low! Actually I can only get a signal when I am next to the wireless router! This was not the case before I installed Ubuntu. Mind you; I am not saying that Ubuntu did this to my laptop; but I do not know if due to my inexperience with Linux I may have changed something without knowing and broke something!  

Any comments are more than welcome :)

Please do not hesitate to tell me should you need any more information! At the moment I have Windows XP installed on my computer, however today or tomorrow I&#8217;ll be installing the latest version of Ubuntu (currently downloading).

Thanks and Regards,
Sim085

---

### Post by pedro_orange on 2008-05-15
Perhaps you should think about dual booting.
Just so you can check the Wireless card works in both operating systems.
(Loads of guides on the net if you just google)

With regards to the Wireless card within Ubuntu; you'll have to be more specific. If you can find the brand/make of the card someone can help you; or you can google it for Ubuntu.
I'm sure someone somewhere has the same wireless card as you and got it to work.

---

### Post by sim085 on 2008-05-15
> **pedro_orange said:**
> Perhaps you should think about dual booting.
Just so you can check the Wireless card works in both operating systems.
(Loads of guides on the net if you just google)

With regards to the Wireless card within Ubuntu; you'll have to be more specific. If you can find the brand/make of the card someone can help you; or you can google it for Ubuntu.
I'm sure someone somewhere has the same wireless card as you and got it to work.

First of all thanks for the reply :)

At the moment I am only trying to see howcome my wireless card stopped work as should after I installed Ubuntu on it! ... Could it be that one of the commands I passed actually changed some hardware setting in my wireless card? Before I installed Ubuntu the Wireless card worked fine from Windows and now it is only taking a singnal when I am next to the router. Also now (with Windows installed) I installed an external wireless card which works more then fine!! So the problem seems to be on the onboard wireless card!

Basically my question is more in terms; Could I have, by passing some of the commands available on linux, actually modified some hardware setting on the card which is making it work like this?

Regards and Thanks,
Sim085

---

### Post by anewguy on 2008-05-15
Does your wireless have some sort of control panel in Windows?  Perhaps there is a toggle of some sort you need to reset.  If you continue to have problems in Windows, try reinstalling the driver.  Once you get the signal strength back where you want it, then do as mentioned and post the maker/model of your wireless card.  In Windows you can usually find this in device manager.  In Linux, start with the following in a command line window (Applications/Accessories/Terminal) and post the output back here:

lspci


Thanks.

---

### Post by Kobalt on 2008-05-15
> **sim085 said:**
> 
Basically my question is more in terms; Could I have, by passing some of the commands available on linux, actually modified some hardware setting on the card which is making it work like this?

This is quite unlikely in your case. I would rather search towards the drivers of your wireless card that you reinstalled: did you get newer ones, older? Did you reinstall your Windows system from a recovery CD or from a Windows CD. 
To me the explanation would rather be a difference between your previous and actual Windows install, possibly on the drivers side.

---

### Post by sim085 on 2008-05-15
> **Kobalt said:**
> This is quite unlikely in your case. I would rather search towards the drivers of your wireless card that you reinstalled: did you get newer ones, older? Did you reinstall your Windows system from a recovery CD or from a Windows CD.  
To me the explanation would rather be a difference between your previous and actual Windows install, possibly on the drivers side.

Basically before I installed Ubuntu I had Windows Vista and before that I had Windows XP. The wireless worked fine on both Windows XP and Vista. I then installed Ubuntu and wireless was not working. I passed some commands, gave up, and installed Windows XP. At this point I realized that the wireless signal on my laptop was week. I thought maybe the Windows XP installation went bad and therefore I re-installed it (not repaired it). However I still had the same problem. Therefore I installed the drivers that came up on CD’s with the laptop but still the same problem! I could try to install Windows Vista again to see how it works out if this may be of any help! 

Basically I thought I should try to fix the problem on Windows XP or Vista before trying to install Linux.

Thanks and Regards,
Sim085

---

### Post by Kobalt on 2008-05-15
What are the hardware specs of your laptop, and if you know, your wifi card specs?

---

### Post by sim085 on 2008-05-15
> **Kobalt said:**
> What are the hardware specs of your laptop, and if you know, your wifi card specs?

Hi thanks again for your reply. The specs are as follows:

Fujitsu-Siemens Amilo 
AMD Athlon 64 (Single Core)
Built-In Wi-Fi b/g

If you need more detailed specs I can post them later today because at the moment I am at work (sorry).

Regards,
Sim085

---

### Post by sim085 on 2008-05-19
> **Kobalt said:**
> What are the hardware specs of your laptop, and if you know, your wifi card specs?

This document has better details on my laptop:
[http://www.fujitsu-siemens.com/Resources/19/1263148151.pdf](http://www.fujitsu-siemens.com/Resources/19/1263148151.pdf)

Personally I do not think the Wi-Fi device is broken because I can get a very good signal when I am 1 meter from the wireless router but I can't get a signal when I am 5 meters or more from it. Is it possible that I passed some command which changed some internal setting in the Wi-Fi device? or this is compeltly not possible?? Also if it is possible; is there a way how I can reset such Wi-Fi device?

Regards,
Sim085

ps: I have others laptops at home which are not suffering from this same problem. They have Windows Vista and Windows XP and I never tried Linux on them.

---

