---
title: "Wireless Card Not Working"
date: 2013-01-04
forum: New to Ubuntu
---

### Post by FTBBoy2115 on 2013-01-04
I tried to install drivers for my wireless network card, but am not having much prosperity. I have gotten the drivers to install well enough to get the lights to illuminate and it detects the wireless networks nearby, but it keeps asking me for my password, even after I've given the correct one.
I have a Belkin F5D8010

A google search shows that I am having a similar issue as the poster at this site:
[http://unix.stackexchange.com/questions/59598/computer-recognizes-wireless-network-but-asks-for-password-repeatedly](http://unix.stackexchange.com/questions/59598/computer-recognizes-wireless-network-but-asks-for-password-repeatedly)

I have followed the instructions on this site: [https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D8010](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D8010)

I have tried to do this a number of times with still no complete success. I thought maybe a reboot would help, so I tried that too. But it seems I get a couple errors when shutting down and it never completes shutdown, so I have to hold down the power button to force shutdown.

Please help.

---

### Post by audiomick on 2013-01-04
> **FTBBoy2115 said:**
>  I get a couple errors when shutting down and it never completes shutdown, so I have to hold down the power button to force shutdown.

Please help.

Can't help you with the wireless, but for a safe shutdown when the computer locks up, look here

[http://en.wikipedia.org/wiki/Reisub#Uses]("http://en.wikipedia.org/wiki/Reisub#Uses")

---

### Post by FTBBoy2115 on 2013-01-04
> **audiomick said:**
> Can't help you with the wireless, but for a safe shutdown when the computer locks up, look here

[http://en.wikipedia.org/wiki/Reisub#Uses]("http://en.wikipedia.org/wiki/Reisub#Uses")

No, that didn't help with the reboot either. It didn't respond to the SysRq + REISUB. Just kept giving me the same error every 10 sec:

```

* Will now restart filesystems...    ..
[4328.064025] BUG: soft lockup - CPU#0 stuck for 22s! [kworker/u:0:5]
[4328.064384] Process kworker/u:0 (pid: 5, ti=df408000 task=df4732c0 task 48000)
[4328.064384] Stack
[4328.064384] Call Trace:
[4328.064384] Code: 00 0f ae e8 0f 31 8d 74 26 00 89 c6 89 5d f0 eb 14 8d b6 00 00 00 00 f3 90 64 8b 1d 28 70

```

---

### Post by audiomick on 2013-01-05
> **FTBBoy2115 said:**
>  It didn't respond to the SysRq + REISUB. 

alt+sysRq+reisub

---

### Post by Impavidus on 2013-01-06
> **audiomick said:**
> alt+sysRq+reisub
On a laptop you may need Fn:

[LIST]
[*]Press Alt, Fn, SysRq
[*] Release Fn
[*]Press R
[*]Release all
[*]Continue the same way with EISUB
[/LIST]
Just try it once when your system hasn't frozen yet. You should get a black screen full of reading material.


Unfortunately I don't know much about wireless drivers either.

---

### Post by Us3r Unfriendly on 2013-01-06
What driver are you using?  I did a quick search and found the windows .exe of that driver.  If that' the one your using you'll have to see if you can unzip -a that zip file and use the .sys and the .inf files in ndiswrapper.  If you have the Linux source code for that device, you'll have to compile it, blacklist any current modules being used by that device, and put that compiled module in your /etc/modules.conf ...sorry I'm away from my computer and going by memory :D

---

### Post by FTBBoy2115 on 2013-01-07
audiomick and Impavidus - Adding atl to the sequence did help. I was able to get it to reboot even though it was stuck and that cpu was not responding, according to the error msg. 

I wrote a script based off the link I gave earlier on loading the drivers. Since after the initial tries, all the commands I followed wouldn't stick, the script automated it for me. 
I have it on pastebin at pastebin.com/KiUSefnV

Us3r Unfriendly - the driver, I believe is NetAni.inf

Now that I have rebooted, same resolve... Still didn't stick. No flashing lights on the wireless card. Will work if I run my script, but it'll again keep asking for the password.

---

