---
title: "Three questions from an old-newbie"
date: 2020-11-15
forum: New to Ubuntu
---

### Post by kagesan on 2020-11-15
Been away for years, and I'm fairly sure this multi-question thread violates a few hundred guidelines that I haven't yet read, but I'm still getting my forum sea-legs back while attempting to solve a few issues at the same time.

I've been off-Ubuntu since U10-U12, and am back now using U18.  I'm looking for clear, unambiguous instructions for the following 3 issues (I assume that I need to be re-directed to a separate thread for each of them):

**1. VPN app**  - choosing a freebie and installation instructions)

- Attempted install of my Witopia VPN with very good guidance from excellent techies, but U18 just wouldn't take it 
- Tried an alt - IKEv2-SF - also doesn't work (still in system)


**2. DNS change** (including which alt-DNS is generally considered best and specific, clear install instructions)

- This is exploratory:  I don't know if this would work better / be more secure than my native DNS or not.


**3. Canon Pixus TS3330 Printer drivers installation**

- IJ Printer Driver Ver. 5.90 for Linux
- ScanGear MP Ver. 3.90 for Linux

Per Canon instructions I already downloaded BUT HAVE NOT INSTALLED these 2 Canon-recommended driver files:

- cnijfilter2-source-5.90-1.tar.gz (for printing)
- scangearmp2-source-3.90-1.tar.gz (for scanning)

Reasons I HAVE NOT installed drivers via the tar.gz files:

**a. The only U18 instructions I was able to find for installing the correct drivers does NOT include my specific printer model (Pixus TS 3330)**

See:

Canon IJ Printer, ScanGear MP Drivers for Ubuntu 18.04, 18.10
[http://ubuntuhandbook.org/index.php/2018/10/canon-ij-printer-scangear-mp-drivers-ubuntu-18-04-18-10/](http://ubuntuhandbook.org/index.php/2018/10/canon-ij-printer-scangear-mp-drivers-ubuntu-18-04-18-10/)

Related question:

**b. Is there any reason to *avoid* simply decompressing and installing the drivers from the tar.gz files I downloaded?  I mention this because I have seen several instruction and info web pages which claim doing that could be either ineffective or just plain screw up the works.**  


Note - my system inventory:

I can dump a concise, short or long version (or both) of my physical system inventory if need be.  The short version is 12 line items long, while the longer version is 30-ish line items long.


Thanks for any steerage offered.

Kagesan

---

### Post by TheFu on 2020-11-15
> **kagesan said:**
> Been away for years, and I'm fairly sure this multi-question thread violates a few hundred guidelines that I haven't yet read

Welcome back.  Putting multiple, unrelated questions into 1 thread won't get you good answers for all of them. Different people have different skills.  Also, the thread title really needs to be about the 1 issue in the thread to actually attract eyes from people who might know something about that specific thing.  I fear you won't get the help you seek because you didn't split 3 questions into 3 specific thread with 3 specific titles.

> **kagesan said:**
> I've been off-Ubuntu since U10-U12, and am back now using U18.  I'm looking for clear, unambiguous instructions for the following 3 issues (I assume that I need to be re-directed to a separate thread for each of them):
20.04 is the LTS that should be loaded today, unless there is a very good reason to use 18.04 still. If there isn't - stop. wipe and start with 20.04. You'll find that people are more current with their knowledge for 20.04 than they are for 18.xx or any other release.  Again ... more eyes leads to more possible answers, some might actually be helpful.

**Recommendation: Load 20.04.**

> **kagesan said:**
> **1. VPN app**  - choosing a freebie and installation instructions)
VPN stuff is built into Network Manager.  Both openvpn and wireguard should be supported.
Avoid any free VPNs, since those are clearly making money by violating your privacy. Also, just because a VPN is paid, doesn't mean it is safe or not evil. There are a number of extremely popular VPNs that have ties to repressive govts, for example. Those govt have access to all the traffic that you hoped to protect by using the VPN. [https://help.ubuntu.com/stable/ubuntu-help/net-vpn-connect.html.en](https://help.ubuntu.com/stable/ubuntu-help/net-vpn-connect.html.en)  I don't use network-manager, so I cannot provide any specific guidance beyond what the Ubuntu Desktop Guide provides.  Just be certain to reference the Desktop Guide for the version of Ubuntu Gnome3 you are using. If you aren't using the Gnome3 DE, you should always mention that you are using another DE - or people will provide incorrect help. It doesn't hurt to say you are using Gnome3 either.  

Today, wireguard is production ready and many commercial VPNs are supporting it.
**Recommendation: Use commercial, trusted, paid, VPN that supports wireguard. Use the built-in Network-Manager network VPN tool.**

> **kagesan said:**
> **2. DNS change** (including which alt-DNS is generally considered best and specific, clear install instructions)
DNS has changed in the last 5 yrs from a service provided by your ISP, but not really monitored into yet another way to track our use of the internet.  Ubuntu has cocked up the DNS management, IMHO, by installing a caching DNS server on all our desktops whether we want one or not. I don't have any beginner friendly steps to correct this. Sorry.  Since Canonical decided to do this, DNS has been failing more and more often. When DNS fails, less technical people will come and claim "the internet is down", when it is really just their DNS that broke.  Whenever the caching service fails on my machines, I remove it and manually configure the /etc/resolv.conf file like we did in 1993. That has always solved my DNS issues since resolvconf and systemd-resolved have been added.  Pfffft.

To prevent your ISP and others from seeing your DNS queries, DNS over HTTPS has been created.  This way, the DNS provider is really the only people who see all your DNS. Sadly, I haven't found any DNS providers who I'd trust. I certainly don't trust Cisco's or Oracle's or google's or cloudflare's or Joe's DNS of Akron. In my tinfoil hat wearing world, the least evil choice above is probably  Cloudflars's 1.1.1.1 and 1.0.0.1 service over HTTPS. They are fast, at least.  I use a local DNS server on my LAN, which provides caching across all the LAN devices as well as DNS filtering for ad networks and trackers. Currently, it doesn't use DoH, but I've read that it is supported. This is not a trivial, beginner-friendly, solution.

**Recommendation: None.**  I'd use **sudoedit** to modify the /etc/resolv.conf and look for more research for a DNS-over-HTTPS solution.

> **kagesan said:**
> **3. Canon Pixus TS3330 Printer drivers installation**

Years ago, my mother had a Canon printer. It didn't work with Linux, but there were $60 commercial printer drivers made by a company in Europe somewhere.  But the printer was $50 and used $20 of ink every year.  At the time, I was fearful of paying for commercial software under linux because I'd been burned by software that didn't support kernel updates a few times. This abandoned my hardware and it never worked again.  Since then I've always bought hardware that had drivers built-into the Linux kernel so it would be supported 15+ yrs.  I convinced Mom to give away that printer, bought her a $50 laserjet with solid Linux drivers - plug-n-play - and a 10K page toner cartridge to put into it when the 1000 page toner shipped with the printer ran out.  She joked that the 10K page would last longer than she would be alive. She was correct.

**Recommendation: None.**

> **kagesan said:**
> **b. Is there any reason to *avoid* simply decompressing and installing the drivers from the tar.gz files I downloaded?  I mention this because I have seen several instruction and info web pages which claim doing that could be either ineffective or just plain screw up the works.**  

Assuming I didn't convince you to sell/give away the printer, we should always be afraid of downloading software from random places on the internet and using that software.  If you didn't get those tgz files from Canon, then you have to ask how much risk you are willing to accept. Drivers run with elevated privileges, so they can easily provide an attacker remote access into your system.  A linux system is a great C&C for world-wide botnets.

**Recommendation: Always consider the source of any software you allow to run on your devices.**

> **kagesan said:**
> 
Thanks for any steerage offered.

I'm not sure you'd really thank me for what I wrote above.

As for short system information here's one of mine:
```
$ inxi -bz
System:    Host: hadar Kernel: 4.15.0-123-generic x86_64 (64 bit)
           Desktop: **FVWM 2.6.5** Distro: **Ubuntu 16.04 **xenial
Machine:   Mobo: ASUSTeK model: ROG STRIX B450-F GAMING v: Rev 1.xx
           Bios: American Megatrends v: 3103 date: 06/17/2020
CPU:       Hexa core **AMD Ryzen 5 2600** Six-Core (-HT-MCP-)
           speed/max: 1347/3500 MHz
Graphics:  Card: NVIDIA GP108 [**GeForce GT 1030**]
           Display Server: **X.Org 1.19.6** driver: **nvidia**
           Resolution: 1920x1200@59.95hz
           GLX Renderer: GeForce GT 1030/PCIe/SSE2
           GLX Version: 4.6.0 NVIDIA 430.64
Network:   Card: **Intel I211** Gigabit Network Connection driver: **igb**
Drives:    HDD Total Size: 1012.2GB (58.6% used)
Info:      Processes: 488 Uptime: 12:59 Memory: **13241.2/32160.8MB**
           Client: Shell (bash) inxi: 2.2.35 

```
See how I show the command and wrap everything in "code tags"? The code tags makes it more readable. I've bold'ed the important parts for generic information. I don't use any DE, the fvwm part is where the DE would normally be shown. The inxi command can show lots more details based on different options.  My uptime is short - I patch on Saturdays. Normally, my uptime would be a few weeks.

---

### Post by mastablasta on 2020-11-16
you can try the PPA. if it doesn't work you can always uninstall it.

edit it should work: [https://launchpad.net/~thierry-f/+archive/ubuntu/fork-michael-gruz](https://launchpad.net/~thierry-f/+archive/ubuntu/fork-michael-gruz)

> [COLOR=#333333][FONT=monospace]Scangearmp2 driver add the 10/2019[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]=======[/FONT][/COLOR][COLOR=#333333][FONT=monospace]=======[/FONT][/COLOR][COLOR=#333333][FONT=monospace]=======[/FONT][/COLOR][COLOR=#333333][FONT=monospace]=======[/FONT][/COLOR][COLOR=#333333][FONT=monospace]=[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]   G6000 series, G6080 series, TS5300 series, TS5380 series, TS6300 series, TS6380 series,[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]   TS7330 series, TS8300 series, TS8380 series, TS8330 series, XK60 series, TS6330 series,[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]  [/FONT][/COLOR][COLOR=#ff0000][FONT=monospace]** TS3300 series**[/FONT][/COLOR][COLOR=#333333][FONT=monospace], E3300 series[/FONT][/COLOR]

---

### Post by kagesan on 2020-11-16
> **TheFu said:**
>  **SNIP** 

Humble thanks for the full coverage.  I'll be back atcha in kind ASAP.  In the meantime - FYI - I appreciate the straight-talk comeback.

> **mastablasta said:**
> you can try the PPA. if it doesn't work you can always uninstall it.

edit it should work: [https://launchpad.net/~thierry-f/+archive/ubuntu/fork-michael-gruz](https://launchpad.net/~thierry-f/+archive/ubuntu/fork-michael-gruz)

Thanks very much for the fast reply.  

Unless I'm misreading the michael-gruz PPA listing, the TS3300 is now included in the code (when launching the PPA in terminal).  So I ran the PPA and will see if it works when I try the printer in roughly 24 hours.

If you think I'm misreading the PPA terminal text, feel free to say so:  I'm all ears.

> **TheFu said:**
>  **Split 3 questions into 3 specific threads with 3 specific titles.**   

Rgr - burned in memory.

 
  > **TheFu said:**
>  **20.04 is the LTS that should be loaded today (snip) Stop. Wipe. Start with 20.04.**   

Rgr - I don't like it, but then I don't have to like it: I just gotta do it. (grrrr....)

> **TheFu said:**
> ** VPN stuff is built into Network Manager. **    

Right - it's built into U18 too, but my Witopia VPN just plain don't work with U18. Having said that, I'm going to switch to U20 per your advice, so the subject is academic: I'll install U20, get back with the Witopia techies, and see if that (U20) solves the problem.

> **TheFu said:**
>  **DNS... (snip)  This is not a trivial, beginner-friendly, solution. Recommendation: None. **    

That kinda makes my decision for me: I will take no action to change my current DNS unless and until a genuinely good and trustworthy alt-DNS comes along. Like I originally mentioned, that question was exploratory, and your reply painted a fairly clear picture of the subject's topography - right now it's kinda like chasing down a herd of squirrels on crack.

                        > **TheFu said:**
>                            
[B]Years ago, my mother had a Canon printer... [snip]
Recommendation: None.
If you didn't get those tgz files from Canon [snip]
Recommendation: Always consider the source of any software you allow to run on your devices.[/B]
   


Loud and Clear.

I tried it mastablasta's way: sudo add-apt-repository ppa:thierry-f/fork-michael-gruz

That ppa's terminal-listed models now includes mine (TS3300), so I ran it. I won't know if it works until I test the printer in roughly 24 hours. But I hope that at least meets the right standards for *where* to get the files (PPA / repository).


As for the tar.gz files I mentioned: they came straight from a Canon-referred link... which is academic now since I deleted them and went with mastablasta's PPA suggestion.

In case you think I'm side-stepping your suggestion about the printer - I'm not. I just don't have the funds to choose otherwise for the time being (same with using an 8 year old laptop which I got for USD $400). I'm trying to make it work at least for long enough to print a couple dozen pages of docs for some important work in the short run. As for the Canon, it's a new one, though I got it for free (I know - that's usually a bad sign all by itself), and if it fails using my old (soon-to-be-U20) laptop, I can probably have a friend get it working via a silly but effective little iPad app.

      
                         > **TheFu said:**
>  **I'm not sure you'd really thank me for what I wrote above. **


On that count, you're dead wrong: Your reply is a welcome breath of fresh air in a world whose atmosphere is currently densely polluted with blinding flashes of either vitriolic or bucolic bull****, and happy-skippy hyper-sensitive PC-Woke-ness. So thank you, and don't change your style - for whatever my vote is worth.
  
Short version:  Humble thanks for the time and effort that went into your reply.
 
KageSan

-Message Ends-

---

### Post by CelticWarrior on 2020-11-16
> [COLOR=#000000]Right - it's built into U18 too, but my Witopia VPN just plain don't work with U18. Having said that, I'm going to switch to U20 per your advice, so the subject is academic: I'll install U20, get back with the Witopia techies, and see if that (U20) solves the problem.[/COLOR]

It should work in any version: [https://www.personalvpn.com/support/linux/ipsec](https://www.personalvpn.com/support/linux/ipsec)

---

### Post by kagesan on 2020-11-17
> **CelticWarrior said:**
> It should work in any version: [https://www.personalvpn.com/support/linux/ipsec](https://www.personalvpn.com/support/linux/ipsec)

That's exactly what both I and the Witopia techno-Einsteins figured, but it didn't happen.  That was despite the fact that they were seeing exactly what I was seeing on my screen in every, single step of the process - start to finish.  The Witopia techs even observed (paraphrased) "You've done everything correctly - it should be working, and we don't have any explanation for why it *isn't* working."

FWIW, this is a first for me: 
Until now (U18 on my "new" 8 year old laptop) I've never had any issue with Witopia installing and working well in more than a decade - and that covers a dozen machines ranging from a 10 year old netbook to several full boat Win7 and Win10 desktop systems. Short version:  Witopia never failed me until now - using U18 on my refurbished Panasonic CF-B11 notebook. Go figure. 

          -- > Sidebar:   I've attached a screenshot of my Panasonic's inxi-bz system inventory in case it shows any glaring related issues of which I'm just plain ignorant.

That said, this particular issue is academic because (a) it *isn't* working on U18, and (b) I'm switching to U20 per steerage from TheFu.  

Humble thanks for taking the time to weigh in.  I'll post results after a U20 install, and _*I will use your Witopia link to install the VPN*_.

KageSan

- Message Ends -
.
.

---

### Post by TheFu on 2020-11-17
Article about DNS-over-HTTPS, privacy and security: [https://www.cloudflare.com/learning/dns/dns-over-tls/](https://www.cloudflare.com/learning/dns/dns-over-tls/)  

I didn't say this previously, but the Cloudflare CEO (I think he's the CEO, but I could be wrong) is a believer in freedom of speech beyond what most people could afford to believe AND stand behind. For a long time he was demonized for this, since the company refused to block, what some people saw as unpopular, content.  A tremendous amount of pressure happened for years before he reconsidered.  I don't remember the steps taken, but 100% freedom of speech lost. The world has drastically changed in the last 20 years and I think we've learned that 100% anything-goes freedom-of-speech in any forum, everywhere, can lead to unexpected things.

BTW, please don't post images for text data.  Too hard for others to copy/paste to point out stuff and 10x wasteful of bandwidth for people who pay for internet by the byte. We are used to text, terminal, output, in specific formats. To retain the output format, use "code tags" [https://ubuntuforums.org/misc.php?do=bbcode#code](https://ubuntuforums.org/misc.php?do=bbcode#code)

---

### Post by DuckHook on 2020-11-17
I'm sure that intentions are honourable all around. Normally, standard staff response to some of the above posts would involve a series of private messages and discrete edits, but I'm going to treat this occasion as a teaching moment. Therefore, please do not take what follows personally. There is no rebuke involved. It's more a matter of illustrating why forum policy exists and why we apply it as rigorously as we do.

It is important to understand that this community is not an arm of government. Hence, appeals to "free speech" and (if American) "first amendment rights" are misplaced, misguided and nonsensical. There are scads of political forums all over the Internet which make it their purpose to wallow in partisan vitriol. We refuse to be one of them. So, for those hooked on their daily fix of political poison, they are advised to disgorge their bile elsewhere. It is not permitted here. This goes for religion too.

I value these forums in large part because they serve as a respite from the culture wars. I wager that the vast majority of forum members feel likewise. Therefore, every staff member is pledged to keep things that way. In discharging our duties we render no judgment on the politics of the day, whether wokeness, anti-wokeness, PC or anti-PC. Any views on these and similar topics are irrelevant on these forums. Consequently, we will nix any attempt to co&#8209;opt this venue for use as a personal soapbox.

Please do carry on with this interesting thread, but all members should now understand the importance of refraining from the added colour commentary.

---

### Post by QIII on 2020-11-17
To that I will add that it might be of interest to all to research the Xhosa/Zulu concept of "ubuntu", after which this OS is named.  

We value ubuntu here, it guides our philosopy and practice of forum moderation.

Please review the Forum Rules and posting guidelines links in my signature.

---

### Post by MartyBuntu on 2020-11-17
> **kagesan said:**
> 

**1. VPN app**  - choosing a freebie



Skip the "free" VPN services. In my opinion, even less secure than no VPN at all. Your data sold off to whoever is willing to pay.

> **kagesan said:**
> 


**2. DNS change** (including which alt-DNS is generally considered best and specific, clear install instructions)




If you don't care for your ISP's DNS, try Google's. Typically, there's not a world of difference. Only specific use cases would a DNS change provide substantial improvements.

---

### Post by kagesan on 2020-11-18
> **TheFu said:**
>  (snip) The world has drastically changed in the last 20 years and I think we've learned that 100% anything-goes freedom-of-speech in any forum, everywhere, can lead to unexpected things.

Ah yes:  The Butterfly Effect... Unanticipated Consequences... or as it's called in one former profession:  BlowBack.

I started college over _**50**_ years ago - during DARPA days and Xylogic's TME (terminal mode emulation), when: 
(a) It was real trendy for alleged "students" and the SDS (they did bombings and kidnappings) to protest-shutdown entire universities, colleges and classes - for which I paid dearly in tuition, fees, books, and hard honest work, and 
(b) I got my PL1, Basic, Cobol, Algol and Fortran coding work done by generating 40-pound trays of "punched-cards", which - when four wheel carts were in short supply - had to be physically carried 100 yards in the rain and snow to a data processing center equipped with a "state of the art" IBM 370-158 with a footprint the size of a city block.  And in the intervening years, I've worked for two POTUS, after which I couldn't rid myself of the residual Beltway toxicity even with a bleach-bath and Level 5 Decon measures... along with a few other gigs in 30+ countries on five continents.  So - short version - I have a fair idea of what's happened in the past _**20**_.

> **TheFu said:**
> BTW, please don't post images for text data.  Too hard for others to copy/paste to point out stuff and 10x wasteful of bandwidth for people who pay for internet by the byte. We are used to text, terminal, output, in specific formats. To retain the output format, use "code tags" [https://ubuntuforums.org/misc.php?do=bbcode#code](https://ubuntuforums.org/misc.php?do=bbcode#code)

Rgr - burned in memory.  Humble thanks once again.

KageSan

- Message Ends -

---

### Post by kagesan on 2020-11-18
> **DuckHook said:**
>  (snip) I'm going to treat this occasion as a teaching moment. 

Probably a wise choice. Post logged and noted.  Further affiant sayeth naught.

KageSan

- Message Ends -

---

### Post by kagesan on 2020-11-18
> **MartyBuntu said:**
> Skip the "free" VPN services. In my opinion, even less secure than no VPN at all. Your data sold off to whoever is willing to pay.

If you don't care for your ISP's DNS, try Google's. Typically, there's not a world of difference. Only specific use cases would a DNS change provide substantial improvements.

Rgr all - action taken accordingly:  I use a pay VPN now and will continue to do so;  No action on DNS - keeping my native provider.

Thanks for weighing in - you never know what even the smallest advice variance can do to help.

KageSan

- Message Ends -

---

