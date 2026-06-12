---
title: "Having some issues with Ubuntu 24.04...I think?"
date: 2024-05-21
forum: New to Ubuntu
---

### Post by ubundtcake on 2024-05-21
Hello!
I'm brand new to Ubuntu and replaced Windows with an Ubuntu install.
When I originally installed it -- a popup asked me if I'd like to connect to the internet for additional software and I selected "No" and I'm wondering if that's why I'm now having these issues.

I've been watching a lot of tutorials online and I noticed a lot of the guides aren't working for me -- for example someone recommended the GNOME tweaker so I followed the steps to download from the App Center. I had to manually change the filter from "Snap" to "deb" for it to even show up in the search results. When I installed it -- it just never showed up anywhere in my system ...no install package or anything. It also doesn't even show up in my list of Apps in the App Center. To find it in the App Center I have to research for the App and it gives me the option to "Uninstall"

Another issue is my download speeds are half of what they are on my other PC so I don't know how to speed it up or if I'm missing a WiFi card driver?

Sorry guys I'm a new born Linux baby and I'm a little lost --- help!!

Thank you!

---

### Post by currentshaft on 2024-05-21
a"

---

### Post by TheFu on 2024-05-21
Best to ask 1 question per thread.  the expertise for networking is different than the expertise for Gnome stuff.  I haven't use Gnome in about 15 yrs, for example, so I know very little about Gnome.

When you search for online articles, be 100% certain 
a) they are from a reputable site
b) they are for your exact release - not any different version.  Things change, especially with GUI stuff.

> **ubundtcake said:**
> 
When I originally installed it -- a popup asked me if I'd like to connect to the internet for additional software and I selected "No" and I'm wondering if that's why I'm now having these issues.

Doubtful.  That question is just if you want to run patching during the install process.  I find it is best to get the install up and running, then after the first reboot, do my normal weekly patching on the system.  That will get the same results, just the install won't be screwed if networking has any issues.  

Further, this isn't intuitive, but the installer and that installation environment is created by a different team than the OS.  Normally, it doesn't matter too much, but the one place I've seen it matter is with network drivers, especially wifi. Hard to believe this, but often the installer has better wifi drivers than the installed OS.  I don't know why. Seems like that would be harder than keeping the drivers from the OS team.  I still don't understand why there are differences, but I've seen them myself.

> **ubundtcake said:**
> 
I've been watching a lot of tutorials online and I noticed a lot of the guides aren't working for me -- for example someone recommended the GNOME tweaker so I followed the steps to download from the App Center. 

There probably aren't many guides or tutorials for 24.04 online yet.  See my first list.  Be careful following help from random sites.  There are a bunch of noobs in the Linux world who probably mean well and think they found a solution, but they don't have deep enough knowledge to realize it was just coincidence.   My rule of thumb for finding websites with reputable answers are to only use those with "ubuntu" in the DNS part of the URL.  help.ubuntu.com  wiki.ubuntu.com  askubuntu.com  are all fine.  JoesBlog.net ... not so great.

---

### Post by ubundtcake on 2024-05-22
**Thank you** for such a thorough reply! 
I will definitely take your advice and keep it to a one question per post type deal -- probably much easier to get relevant answers.

I think I'm going to spend more time on the Ubuntu forums/website to educate myself a little more so I can formulate better questions. The PC I'm using has no data or anything of importance on it so I guess a few mistakes would be okay.
I'm on day 3 since installing so I'm just super new

---

### Post by ubundtcake on 2024-05-22
To answer your question: 
I used a speed test online to check the speed (Ookla) and the upload speed was normal but the download speed was actually waaay more than half what I get on my Windows computer connected to the same network. (Windows: 290mbps / Ubuntu: 20 mbps)

---

### Post by Rubi1200 on 2024-05-22
Welcome to the forums :-)

Wired or wireless connection?

Do you happen to know what network cards are installed?

---

### Post by ajgreeny on 2024-05-22
As a start open a terminal (Ctrl+Alt+t) and run command ```
inxi -Fzx
```
Please copy and paste all the output you see back here using code-tags.
See my signature below for a how-to of code tags.

---

### Post by TheFu on 2024-05-22
> **Rubi1200 said:**
>  Wired or wireless connection?

Do you happen to know what network cards are installed?


^^^^^^^^^^^^^^^^^^^^^^^
THIS!  The requested **inxi -Fxz**  command output will tell us much about the system, hardware, how it is connected.
Speed test results can fluctuate during the day, so it isn't the best way to test networking, but it is good you shared

a) the same computer with Windows is 200 Mbps.  Ubuntu is 20 Mbps.

b) drivers for Linux are sometimes not as good as MS-Windows.  That's because the vendors ensure their Windows drivers are as good as possible.  For Linux, if they even bother, they make certain that the driver works at a minimal level.  If you make good hardware choices, then the drivers for Linux have more features and are tuned to work well.

c) 24.04 is new.  As part of your trouble shooting, _after posting the requested command + output_, you can try booting from the installation flash drive, going into Try Ubuntu mode and testing again.  If the results are the same or 200 Mbps, that data would be helpful.  Either way, it is worth looking at the network drivers used by both the Try Ubuntu mode and the installed drivers.  If they are the same, then the same results are likely. If they are different, different results are likely and perhaps a better driver was automatically picked which can be used instead.

d) For many common issues related to performance or hardware, there are data gathering tools which should be run for the gurus to have data to make suggestions.  After all, there are 100s of different network cards in the world, so nobody can help without knowing YOUR exact network card. See how that makes sense?  With Linux, we often need to know the chip inside the device to make it work, not so much the brand and model.  Some vendors, cough, realtek, cough, are known for keeping the same model name, but completely changing the chips inside.  This makes it hard for anyone, especially the computer to guess which driver will work best.

Some good commands to gather data:
[LIST]
[*]inxi -fxz
[*]lshw
[*]lspci
[*]lsusb -t
[*]
[/LIST]
And there are a few specialty scripts created by long-time people from these forums to aid in gathering all the useful information for more complex problems like wifi or sound or installation issues.  These are named something like "wifi trouble shooting script"   "audio data script" and the "boot-info".  For the last one, there are a few good tools - that can gather information, but still need a guru to manually review.  Boot-Repair (just run the tool, click the gather info button, never attempt a repair unless someone you trust specifically tells you to do that) and the system-info script.  [https://github.com/UbuntuForums/system-info](https://github.com/UbuntuForums/system-info) 

Many times, it is best to have these tools pre-installed on the system, before they are needed. Most are small.

Anyway, looking forward to seeing the requested command.  Or **lshw -C network** should provide less output, only related to the network question, but the inxi command will provide a clearer overview.

---

### Post by ubundtcake on 2024-05-22
Hi thank you so much for such an extensive response!
I forgot to mention I am connecting using WiFi

a) I ran the inxi -fxz command and then went back and rebooted from the installation software. There was no difference between the results except for the numbers next to the CPU cores -- and that difference was very small.

b) Lucky me... looks like I have a Realtek network card 

Would you like me to post the command response using the inxi -Fzx command? 
[ Is there anything in there that I should be cautious posting publicly?]

Thank you!

---

### Post by ubundtcake on 2024-05-22
[COLOR=#000000]```
[/COLOR]
**[COLOR=#0000cd]CPU:[/COLOR]**
  **[COLOR=#0000cd]Info[/COLOR]**: quad core **[COLOR=#0000cd]model[/COLOR]**: AMD A10-7870K Radeon R7 12 Compute Cores 4C+8G
    **[COLOR=#0000cd]bits[/COLOR]**: 64 **[COLOR=#0000cd]type[/COLOR]**: MT MCP **[COLOR=#0000cd]arch[/COLOR]**: Steamroller **[COLOR=#0000cd]rev[/COLOR]**: 1 **c[COLOR=#0000cd]ache: L1: [/COLOR]**256 KiB [COLOR=#0000cd]**L2**: [/COLOR]4 MiB
  **[COLOR=#0000cd]Speed (MHz): avg[/COLOR]**: 1764 **[COLOR=#0000cd]high[/COLOR]**: 1966 **[COLOR=#0000cd]min/max: [/COLOR]**1700/3900 **[COLOR=#0000cd]boost[/COLOR]**: enabled [COLOR=#0000cd]**cores**[/COLOR]:
    [COLOR=#0000cd]**1**[/COLOR]: 1697 [COLOR=#0000cd]**2**[/COLOR]: 1700 [COLOR=#0000cd]**3**[/COLOR]: 1966 **[COLOR=#0000cd]4[/COLOR]**: 1696 **[COLOR=#0000cd]bogomips[/COLOR]**: 31143
  **[COLOR=#0000cd]Flags[/COLOR]**: 3dnowprefetch abm aes aperfmperf apic arat avx bmi1 bpext clflush
    cmov cmp_legacy constant_tsc cpb cpuid cr8_legacy cx16 cx8 de
    decodeassists extapic extd_apicid f16c flushbyasid fma fma4 fpu fsgsbase
    fxsr fxsr_opt ht hw_pstate ibs lahf_lm lbrv lm lwp mca mce misalignsse
    mmx mmxext monitor msr mtrr nodeid_msr nonstop_tsc nopl npt nrip_save nx
    osvw overflow_recov pae pat pausefilter pclmulqdq pdpe1gb perfctr_core
    perfctr_nb pfthreshold pge pni popcnt pse pse36 ptsc rdtscp rep_good sep
    skinit ssbd sse sse2 sse4_1 sse4_2 sse4a ssse3 svm svm_lock syscall tbm
    tce topoext tsc tsc_scale vmcb_clean vme vmmcall wdt xop xsave xsaveopt


[COLOR=#000000]
```


[/COLOR]

---

### Post by ubundtcake on 2024-05-22
Thank you ! :) Happy to be here!

I'm connecting wirelessly

[B][U]Network Cards:
[/U]
[/B]_Ethernet:_ Realtek RTL8111/8168/8211/8411 PCI Express Gigabit Ethernet

_Wireless_: Realtek RTL-8185 IEEE 802.11a/b/g Wireless LAN

---

### Post by TheFu on 2024-05-22
That isn't what was requested.  The specific commands provide information that you may not understand, but are very important.

I don't touch wifi stuff. Someone else will need to take over.  I consider wifi an abomination and too full of security failures for any considered use without a full VPN too, even at home.

---

### Post by ubundtcake on 2024-05-22
That response was directed to another user who asked me for those specifications, so no, definitely not what you requested. I believe you may have overlooked the response I intended for you, but I'll copy it into this response:
> [COLOR=#000000]Hi thank you so much for such an extensive response![/COLOR]
[COLOR=#000000]I forgot to mention I am connecting using WiFi[/COLOR]

[COLOR=#000000]a) I ran the inxi -Fxz command and then went back and rebooted from the installation software. There was no difference between the results except for the numbers next to the CPU cores -- and that difference was very small.[/COLOR]

[COLOR=#000000]b) Lucky me... looks like I have a Realtek network card[/COLOR]

[COLOR=#000000]Would you like me to post the command response using the inxi -Fxz command?[/COLOR]
[COLOR=#000000][ Is there anything in there that I should be cautious posting publicly?][/COLOR]

[COLOR=#000000]Thank you![/COLOR]

I understand you were looking for me to give you the results from that specific command, but that is a lot of information. Like you said, I don't really understand it and agree that it's very important -- which is why I was a tad hesitant to post it. I just wanted to clarify that there was nothing I needed to edit out before posting publicly.

And I fully agree that wifi is a security nightmare lol I have my other PCs connected through Ethernet. I was given a PC so I decided to experiment a bit with Ubuntu  before I went out buying new cables and what not (I'm on day 4 of the install). But yes, I have full VPN set up on it.

---

