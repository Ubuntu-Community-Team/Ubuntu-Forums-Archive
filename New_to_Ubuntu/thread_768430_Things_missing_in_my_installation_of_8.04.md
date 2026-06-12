---
title: "Things missing in my installation of 8.04"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by Petronius on 2008-04-26
I have just installed Ubuntu 8.04 using the alternated CD download, as I'm using an old IBM 600 Thinkpad to test out Linux for the very first time. It is my first experience of Linux so I really am a complete novice. 

I was really quite impressed with the installation, it was a bit long as you might expect on such an old laptop, but it went smoothly and I now have a working dual boot Windows/Linux machine.

Not too keen on the color scheme but I fixed that easily enough. Nice set of installed applications as well. Now I'm ready to start on the Internet but Ubuntu did not automatically install my wireless card so I have do it manually. 

Two problems: 

1. Help told me to look at Sytem-Preferences-Hardware information, but the entry "Hardware information" does not exist. I found I could add a Control Center and then Hardware Testing found the wireless card, but, please, how do I add this "Hardware information" entry?

2. To use my Windows card driver Help also told me to use ndisgtk from System-Administration-Synaptic Package Manager, but ndisgtk is not listed. Could you tell me how to add it? I did find and install two packages by downloading to another computer. These were ndiswrapper-common-xxx and ndiswrapper-utils-xxx but they don't help. 

I'd really like to fix my Internet access problem so I can get down to the real job of testing out Linux as I really like the look of it.

Thanks

---

### Post by frup on 2008-04-26
this is the ndiswrapper website [http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/)

find a .deb of ndisgtk which corresponds to the version you downloaded of ndiswrapper.

can't help with the rest. I'm wondering if the missing "Hardware information" exists at all. I don't have it (upgrade from beta though, not alternate install) I have two hardware options under system>administration though, Hardware drivers and Hardware testing.

---

### Post by jepong on 2008-04-26
for hardware information... try installing hardinfo from the repository.

---

### Post by Petronius on 2008-04-26
Thanks, but there is nothing called ndisgtk.deb on the Source forge web site, and all the files there are sources which, as a beginner to linux, I really don't want to tackle yet.

I haven't found a ndisgtk.deb by surfing either. Maybe Help is wrong? 

As for the "Hardware information" entry goes, why is the Help wrong on this? Have I made a mistake trying Ubuntu Linux? Maybe it is not stable or something?  

It would be much nicer if Linux would automatically detect and install new hardware, like Windows does.

---

### Post by ghost_ryder35 on 2008-04-26
what type of wireless card are you using?  Make Model # etc....

---

### Post by Petronius on 2008-04-26
its a SWEEX LW056.

---

### Post by neko18 on 2008-04-26
Do you know what the name of your wireless card is?

Edit: Someone already asked. Sorry.

---

### Post by ptn107 on 2008-04-26
'Hardware Info' is not installed by default in Ubuntu 8.04.

---

### Post by Petronius on 2008-04-26
Oh. Its a pity that Help implied it was installed. Very confusing. Still I've made a little progress on the wireless card front. I found a package at 
[http://ubuntu.mirrors.tds.net/ubuntu/pool/universe/n/ndisgtk/ndisgtk_0.6-0ubuntu3]("http://ubuntu.mirrors.tds.net/ubuntu/pool/universe/n/ndisgtk/ndisgtk_0.6-0ubuntu3")
and that gave me ndisgtk which let me install the driver for my wireless card (now that is a package which really should be installed by default).
The card and my network are recognised, but that's where my progress has halted because I can't get it to connect Firefox to the Internet yet.

Would you have any advice on what to fill in all those network connection boxes? Or does Firefox need some settings?

To a Windows user trying linux for the first time its all very familiar from where Windows was in the days of Windows 3.1!

---

### Post by Petronius on 2008-04-26
OK, I got it working thanks to a forum post I found. Just make sure "Enable roaming mode" is checked. Now I'm connected and surfing. 

Thanks all

---

### Post by Power_G on 2008-10-11
Hello! I'm trying to find the linux driver for Sweex wireless card  LW056, but i can't. Would you like to help me?

---

