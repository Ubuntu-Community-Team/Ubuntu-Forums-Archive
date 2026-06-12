---
title: "Virus"
date: 2013-10-30
forum: New to Ubuntu
---

### Post by schmitta on 2013-10-30
When restarting my system I get a flash of a modal box on my screen which usually means a virus may be executing. Are there any known viruses for ubuntu and how should one get rid of them? Thank you. ALvin....

---

### Post by ajgreeny on 2013-10-30
I don't understand. What exactly is the modal box and why do you think it may be a virus.

There are no viruses in the wild for Linux, so I think you can probably rest easy about that, but tell us more about what you actually see when you restart.

---

### Post by The Cog on 2013-10-30
I get a flash of what might be a dialog box as I restart my laptop quite often - it shows for a fraction of a second as it is shutting down. I suspect that in my case it is something that normally lives in the system tray with its window hidden, possibly gigolo. Or maybe it is a brief flash of the lightdm login dialog, I'm really not sure. If this is what you are seeing, I think you can assume it's not a virus. I don't understand why you say it is modal though.

ajgreeny: A modal dialog is one that stands in front of the main application window, preventing you from using the main application window until the modal dialog window is closed again. Quite often it is an "Are you sure" type question or some kind of warning.

---

### Post by schmitta on 2013-10-30
My understanding of a modal box is any box that appears at the front of a screen usually displaying a message and must be cleared before you can proceed. The box in this case clears itself as its operation has executed. In windows these are cmd line dialog boxes that the virus uses to start itself. Its not a flash of the screen and it is definitely a modal box at the start of the session not at the end. Is there any virus eradicating softwsre for linux? clam?

---

### Post by cbennett926 on 2013-10-30
Ubuntu, or rather Plymouth, is not recognizing that it needs to NOT display what is going on behind the scenes. It is just displaying what exactly it is doing, this is beneficial to see if any errors are going on. Such as on my system whenever I start/shutdown it tells me that KVM is disabled in the Bios among other settings I have made that it wasn't expecting. Don't worry nothing insecure is going on with your system from what you have told us. Linux runs a pretty awesome system of virus protection, the need to type your password to run just about ANYTHING on your system. So, as long as you haven't set yourself in a root-only login (not easy to do) you're fine. 

TL;DR

No virus, just telling you what's going on; albeit really quickly.

---

### Post by cbennett926 on 2013-10-30
> **schmitta said:**
> My understanding of a modal box is any box that appears at the front of a screen usually displaying a message and must be cleared before you can proceed. The box in this case clears itself as its operation has executed. In windows these are cmd line dialog boxes that the virus uses to start itself. Its not a flash of the screen and it is definitely a modal box at the start of the session not at the end. Is there any virus eradicating softwsre for linux? clam?

Whoops sorry didn't see this. Here's a list taken from Ubuntu (other than Clam I should add):


[LIST]
[*=left][FONT=inherit][Avast! Linux Home Edition]("http://www.avast.com/linux-home-edition#tab4"). More information about Avast! at [wikipedia]("http://en.wikipedia.org/wiki/Avast!") and an install guide at [UbuntuGeek]("http://www.ubuntugeek.com/avast-antivirus-for-ubuntu-desktop.html"). Avast's product key didn't work so we contacted the company & are awaiting their response. [/FONT]
[*=left][FONT=inherit][AVG Antivirus]("http://free.avg.com/download.prd-alf"). AVG is popular in Windows. Like most antivirus programs it detects infected files but doesn't remove the infections. Unusually though, it also doesn't move infected files to a quarantine folder. There is a more detailed page about [Avg in Ubuntu]("https://help.ubuntu.com/community/Antivirus/Avg"). [/FONT]
[*=left][FONT=inherit][Avira Antivirus]("http://www.avira.com/en/support-download-free-antivirus"). Requires Java to use the GUI.[/FONT]
[*=left][FONT=inherit][BitDefender Antivirus]("http://www.bitdefender.com/PRODUCT-80-en--BitDefender-Antivirus-Scanner-for-Unices.html"). Limited time trial version available apparently but only after filling in a form. [BitDefender]("https://help.ubuntu.com/community/BitDefender") checks for Windows viruses. There is a community documentation page about it [here]("https://help.ubuntu.com/community/BitDefender"). [/FONT]
[*=left][FONT=inherit][Panda Antivirus]("https://help.ubuntu.com/community/PandaAntivirus"). I didn't check this one but it appears to be old and no longer maintained. It used to have some unique & awesome features[/FONT]
[*=left][FONT=inherit][F-PROT Antivirus for Workstations (home users)]("http://www.f-prot.com/products/home_use/linux/"). Free for personal use. GUI front-ends are available, but may require some manual work. e.g. [XFProt]("https://help.ubuntu.com/community/XFProt"). I have not tried the GUI front-ends.[/FONT]
[*=left][FONT=inherit][Wiki list]("http://en.wikipedia.org/wiki/Linux_malware#Anti-virus_applications")[/FONT]
[/LIST]

---

### Post by newb85 on 2013-10-30
If you had a hypothetical virus, it hypothetically wouldn't need to launch a visible terminal to work in the background. The real question is how you could have ended up with a malicious executable in your system. Have you added unscrupulous software sources? Do you carelessly set files you download as executable? Did you make Ubuntu listen on ports unnecessarily and not set up a firewall?

---

### Post by ajgreeny on 2013-10-30
> **The Cog said:**
> ajgreeny: A modal dialog is one that stands in front of the main application window, preventing you from using the main application window until the modal dialog window is closed again. Quite often it is an "Are you sure" type question or some kind of warning.

Yes, thanks.  A quick search soon told me the answer to my own question.  However, I still believe that the OP is worrying unnecessarily about having a virus that is affecting the ubuntu OS.

---

### Post by DuckHook on 2013-10-30
At the risk of burying you in information overload, here are my two-pennies:

1. People coming to Linux from Windows are usually absurdly over-sensitive about viruses and yet completely desensitized to real security concerns. Windows has conditioned them into thinking of Windows' deficiencies as normal.
2. It is extremely difficult to catch a virus in Linux. You almost have to consciously install one. There are no viruses in the wild and AV software is a waste of time, money, computing resources, and most importantly, a diversion of proper focus. You should be doing a lot of other things to protect yourself, but the AV con-game is not one of them.
3. Although viruses are insignificant, things like Trojans and rootkits (which require you to actively do something stupid to get them installed) are a real danger. If you have lousy password habits, install programs promiscuously, neglect to harden your browser, don't stay updated, or generally think of security as a software fix rather than good habits and judicious conduct, then you are at risk. Since you are posting about your security concerns in the first place, it doesn't seem like you fall into this category.
4. A lot of screen flashing, etc does happen in the bootup/shutdown process. A piece of malware is unlikely to be written so shoddily as to make its presence known in this way. They are creatures of stealth and don't advertise their presence. The really nasty ones will even cover their tracks in your logs.
5. If you are truly interested in Linux security, then you will make sure of the following before wasting your time hunting for viruses:

A. Practice good authentication habits. This means logging in with passwords instead of the truly idiotic Windows convention that bypasses the challenge/response process and encourages people to be lazy pathetic bums. And even then, use high-entropy passphrases instead of easy-to-crack passwords.
B. Encrypt your private data directories or even your whole /home directory using LUKS or ecryptfs. This is completely predicated on (A) above and is obviously pointless without login authentication.
C. Do not activate the root account. Use sudo only when absolutely necessary and only if you know precisely why you are doing so.
D. Read and understand your logs regularly and as a matter of habit.
E. Activate your firewall with UFW or its graphical equivalent GUFW. Open only the minimal necessary ports for productive functionality, both incoming and outgoing. Preferably, open nothing incoming.
F. Create apparmor profiles for all apps facing the internet, that have access to system resources, or that are known attack vectors (like CUPS, SSH, VNC, etc).
G. Turn off all unnecessary services/modules/drivers and run only the minimal number needed for functionality. (e.g. I turn off bluetooth on my devices and use safer workarounds.)
H. Don't add PPAs as if you were swallowing candy (the way some people do) and use only software from the repositories. More advanced users will compile outside software and even their own kernels, but they presumably know what they are doing and have done all of their background checks. However, even among Linux veterans, this is a known attack vector for worms and trojans.
I. Harden your browser with adblock, noscript, better privacy, WOT and a cooking manager.
J. Remove Java and Flash if you don't need them.
K. Better still, use a primitive browser incapable of cookies or scripting (like links2) for your everyday browsing.
L. Always stay updated, and never run obsolete out-of-support OSes.
M. Don't be stupid.

The above practices will not render you immune, but they will go a long way to making you too difficult for most crackers to bother with. And you will note that AV apps don't make a single appearance in any of the above. Of all these measures, it is (M) that is most important. Nothing will protect you from the consequences of your own stupidity. If you download an app from i-own-you.com and then install it with sudo just because you like that cute kitten that shows up on your system tray, then you are the author of your own tragedy and no combination of software or safeguards will protect you.

The subject of security is vast and has its own subforum on this site. There are further measures that advanced users can take from port scanning to rootkit checking. However, this would be putting the cart before the horse with most users. There's no point in learning how to use snort if you can't even be bothered to authenticate at login.

If you want to learn about security the right way, read the stickies in the security subforum and read everything in the following links:

Basic Security:

[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)
[https://sites.google.com/site/easylinuxtipsproject/security](https://sites.google.com/site/easylinuxtipsproject/security)

Advanced Security:

[https://help.ubuntu.com/community/Security](https://help.ubuntu.com/community/Security)
all stickies in:
[http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338)
in particular:
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)
and anything by bodhi.zazen, Dangertux, Ms Daisy

---

### Post by whitesmith on 2013-10-30
**DuckHook** has written a brilliant summary of security in Linux. Every newbie I've helped asks, "Where's the anti-virus?" Explaining why an AV is not needed always provokes shifty-eyed looks. Windows has so mercilessly corrupted computing that it is the Basic of OSes. Just as Basic almost forces a user to use gotos and other bad programming practices, so Windows forces newbies into the Microsoft paradigm-du-jour: first there was COM, then came OLE, followed by ActiveX. Each did essentially the same as its predecessor, but cost more because who would have shelled out $200 or thereabouts for an operating system that could't claim **new!** and **improved!** -- few indeed I'm sure. That's the Windows problem: it must be the Jolly Green Giant of OSes, or buyers will think twice about pouring more money into the pockets of its rich owners. This alone should make a potential buyer of Windows to look for an alternative. Ubuntu certainly isn't perfect, but it's close.

---

### Post by DuckHook on 2013-10-30
I did not cover another area of huge risk and exposure, which is WIFI.

It surpasses belief how Windows users will go to extreme lengths to spend, install, maintain, and put up with AV, Defender-this, Guard-that, yada-yada-yada, only to plonk themselves down in the middle of an Internet hotspot and proceed to retrieve their e-mail, surf everywhere and do highly sensitive tasks up to and including their Internet banking (I've seen instances of this and more).

It is child's play, nay, infant's play, to set my laptop WIFI NIC into promiscuous mode, and with only a few tools, be able to read every packet that is whizzing between each one of those devices and the router. The fact that some cafes will only allow connection by password is a laughable measure that can't even be dignified by the word "security". Since I have the same password, the contents may as well be transmitted in the clear.

The only way to properly protect yourself in such an environment is to tunnel all of your traffic, either through SSH or a VPN, but either way, it has to be done properly. A proper VPN is the best approach and can actually yield a significant measure of safety and security, but it has to be a proper one, set up with strong encryption, a good protocol (yet again, not MS's awful malodorous PPTP) and a high-entropy key.

I'm getting close to diverting this thread, but the point is that focusing on viruses in Linux is like being so obsessed with having parachutes on a boat that you forget to look out for the icebergs.

---

### Post by The Cog on 2013-10-31
I think there is a terminology problem here though. You differentiate between viruses, worms, trojans and root-kits. Windows users do not - to them all of these is a "virus". Windows AV software generally tries to find all forms of malware. 

Bearing this difference in terminology in mind, it could be a little misleading to tell a windows user there are no viruses for linux. A windows user might understand you to mean there is no known malware for linux, and there certainly is. Equally, to a windows user asking for AV software is expecting to be told about anit-rootkit tools as well.

Just noting what I see as a potential cause for misunderstanding.

---

### Post by DuckHook on 2013-10-31
> **The Cog said:**
> I think there is a terminology problem here though. You differentiate between viruses, worms, trojans and root-kits. Windows users do not - to them all of these is a "virus". Windows AV software generally tries to find all forms of malware.

Bearing this difference in terminology in mind, it could be a little misleading to tell a windows user there are no viruses for linux. A windows user might understand you to mean there is no known malware for linux, and there certainly is.Good point. I thought that I had made the differences clear by contrasting point 1 with point 3. Point 3 also made it very clear that these other forms of malware are definitely something to be worried about, but it doesn't hurt to further clarify as you have just done.

Even if we take "virus" to mean malware in general, I think the observations and suggestions contained in my post are still valid. As only one example, the subset of "viruses" more properly called rootkits are notoriously hard to identify or eradicate, and AV software like Norton, Symantec, Kaspersky, etc has a miserable success rate against them. So, even Windows users are fooling themselves when they assume that such AV products will protect them against rootkits. Modern rootkits are so cunning that they operate at the kernel level, or may even virtualize the kernel so as to hide one further level "below". Running AV on such a compromised system will tell the user that everything is hunky-dory, and lull him into a sense of security that is not only false, but dangerous. I know that an Absolute Beginners forum is not the place to get technical, but the point is that for the really nasty stuff, Windows AV software is pretty much useless even for Windows, never mind Linux. This means that, as far as Linux is concerned, good computing habits and defense in depth are the real safeguards; not some AV app.

> Equally, to a windows user asking for AV software is expecting to be told about anit-rootkit tools as well.I don't quite agree with you about this one. I realize that I am generalizing here, but in my experience, the vast majority of Windows users are not really interested in security. When they ask about AV, they expect to install something like Norton, Symantec, Kaspersky, etc. and then forget about it. And this is, in fact, the way most AV software is marketed. They are designed to be (and almost advertise themselves as) install-and-forget, and thereby perpetuate the thinking that so long as users *pay* some company to guard-them-against/clean-up-after their foolishness, they can continue acting the fool. 

Therefore, when educating Windows users about Linux security, there are actually two problems that must be addressed:

1. The fallacy that commercial AV apps are even applicable to Linux, and
2. The Windows mindset

Of the two, it's actually the Windows mindset that is the harder one to overcome. In fact, most new users cling to AV apps because the alternative--truly learning and committing to security--either bores or intimidates them. This can be seen in the number of users on this very forum who ask about installing AV and then about how to turn off password challenge at login, often in the same breath. There's no real commitment to security here; just a desire to get an unpleasant chore over and done with. I suppose there isn't much anyone can do about this mindset. But at the least, we shouldn't take part in feeding the delusion that AV apps are some kind of magic bullet.

Alright. Enough of that. I'm getting off my high horse and taking off the tin-foil hat. Best of the Hallowed Eve to you Cog. Hope you got lots of candy tonight. :)

---

### Post by Mopar1973Man on 2013-10-31
Thank you Duckhook your right on the money. I was once a fool that own Windows OS'es and now finally switched over to Ubuntu Linux. I tend to study up on the security stuff for Linux on configurations more so that add-on software. I would rather keep more horse power of the CPU for my Apps than wasting it on add-ons...

---

### Post by The Cog on 2013-11-01
DuckHook:

Please don't think I was levelling any criticism of anyone in the debate. I was just noting that I think the terms virus and anti-virus seem to have different meanings to the two groups, and it can make for misunderstandings.

---

### Post by DuckHook on 2013-11-01
> **The Cog said:**
> ...Please don't think I was levelling any criticism of anyone in the debate...Didn't take it the wrong way for a second. Knew you were just contributing and trying to clarify, which is a good thing, and it's a good point  that you make. I too was just riffing off of all the thoughts flying  around (and, truth be told, shamelessly indulging in some old fashioned soapbox oratory).

---

### Post by 3rdalbum on 2013-11-02
I think Duckhook has covered things well, but some graphics cards retain their framebuffer memory even after a restart. When you reboot and the graphics driver is loaded by the operating system, it briefly displays the last image in the framebuffer which is basically the last thing you saw before restart.

It happens and is NOT caused by viruses, it's just a normal behaviour.

---

### Post by schmitta on 2014-02-07
Not being sophisticated yet I only rarely use chmod and do not listen to ports (I don't have a firewall installed unles UBUNTU has one).

---

