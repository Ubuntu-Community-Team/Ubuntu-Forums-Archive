---
title: "Ubuntu 22 vs Windows 11 Battery life on laptop"
date: 2022-10-26
forum: New to Ubuntu
---

### Post by hajado on 2022-10-26
[COLOR=#333333][FONT=&quot]Hi everyone![/FONT][/COLOR]

[COLOR=#333333][FONT=&quot]I have a pre-install Linux Ubuntu question - one of the main reasons I would like to upgrade to ubuntu is that I hope my laptop gets slightly better battery life (I don't expect miracles).[/FONT][/COLOR]

[COLOR=#333333][FONT=&quot]I have read, however, that not having optimized drivers as happens on Windows, the battery could last even less, but I found more articles of a couple of years ago, I do not know if the situation has changed or not, so I ask it here .[/FONT][/COLOR]

[COLOR=#333333][FONT=&quot]My question therefore is this: by installing Linux Ubuntu and WITHOUT installing add-ons such as TLP that I read around on various sites, will I get comparable or better battery life? Or worse?[/FONT][/COLOR]

[COLOR=#333333][FONT=&quot]Also if I eventually install this TLP "module", once installed will it work immediately without the need for special configurations?[/FONT][/COLOR]



[COLOR=#333333][FONT=&quot]A thousand thanks![/FONT][/COLOR]

[COLOR=#333333][FONT=&quot]P.s. My laptop configuration is as follows (it's an HP laptop):[/FONT][/COLOR]

[COLOR=#333333][FONT=&quot]- I7 11850HE[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]- 16Gb ram[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]- integrated intel Iris XE video card + secondary card Geforce MX 450[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]- ssd 256 + 1Tb traditional hdd,[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]- monitor 17 inches fullHD)[/FONT][/COLOR]

---

### Post by MAFoElffen on 2022-10-27
Which HP laptop is it? Have you checked what people are saying the battery life is with Windows 11? You already know how it runs with Ubuntu...

I know with my Lenovo laptop, that I have setup as a dual Boot. It lasts longer running Ubuntu 22.04, than it does running Windows 10. IDK about with Win 11.

---

### Post by ActionParsnip on 2022-10-28
You can always boot to live Ubuntu USB and test

---

### Post by Autodave on 2022-10-28
I have 4 laptops and they all get much better life on Linux rather than Win10.

---

### Post by hajado on 2022-10-28
Thanks a lot for the replies!

I have this laptop:

[https://support.hp.com/it-it/document/c06970630](https://support.hp.com/it-it/document/c06970630)


If I install Ubuntu (or mint) I need to install the TRP utility too?

And if I try the OS from the usb stick, will it have the same battery life as it would once installed on the hard drive?
[COLOR=#202124][FONT=arial]will it have the same battery life as it would once installed on the hard drive?[/FONT][/COLOR][COLOR=#202124][FONT=arial]will it have the same battery life as it would once installed on the hard drive?[/FONT][/COLOR]

---

### Post by grahammechanical on 2022-10-28
> And if I try the OS from the usb stick, will it have the same battery life as it would once installed on the hard drive?

Why would you think otherwise? The Ubuntu live session runs in memory just like any operating system installed on a hard drive. Programs are loaded into memory when opened and flushed from memory when closed. 

> If I install Ubuntu (or mint) I need to install the TRP utility too?

Could you explain what this utility is and does? Or, provide links that show that this utility must be installed in Linux. May internet searches reveal trp to be a media file format. 

Regards

---

### Post by hajado on 2022-10-28
> **grahammechanical said:**
> 

Could you explain what this utility is and does? Or, provide links that show that this utility must be installed in Linux. May internet searches reveal trp to be a media file format. 

Regards


I'm sorry, I misspelled. I meant the TLP utility, present at this address:


[https://linrunner.de/tlp/index.html](https://linrunner.de/tlp/index.html)

---

### Post by mIk3_08 on 2022-10-30
> **hajado said:**
> [COLOR=#333333][FONT=&amp]My question therefore is this: by installing Linux Ubuntu and WITHOUT installing add-ons such as TLP that I read around on various sites, will I get comparable or better battery life? Or worse?[/FONT][/COLOR][COLOR=#333333][FONT=&amp][/FONT][/COLOR]
I have HP Elite refurbished Laptop with MS Windows installed on it when it came to me and I decided to change it to Linux Ubuntu immediately. Its been running with Linux Ubuntu for almost a decade now. So far so good. My battery is still running well until now. Regards and cheers.

---

### Post by grahammechanical on 2022-10-30
On Ubuntu 22.04 we go to System Settings>Power and we can make adjustments. There are options to set the Power Mode to Performance; Balanced or Power Saver mode. There are other settings that we can adjust. I do not think that on Ubuntu we need this TLP utility. It might be needed on other desktop environments.

Regards

---

### Post by DuckHook on 2022-10-30
> **hajado said:**
> I'm sorry, I misspelled. I meant the TLP utility, present at this address:


[https://linrunner.de/tlp/index.html](https://linrunner.de/tlp/index.html)
Just a word to the wise…

TLP is available in the standard Ubuntu repos and it is not necessary to download it from an outside (and therefore questionable) source. In fact, one should never install anything from outside sources unless one is absolutely, positively certain about the author and the integrity of his/her site. Even then, take pains to sandbox the app within either a VM or container, which is obviously difficult or impossible when dealing with a utility.

I gather that you are new to Ubuntu/Linux. You may find it fruitful to read the contents in my link: Linux is Not Windows

---

