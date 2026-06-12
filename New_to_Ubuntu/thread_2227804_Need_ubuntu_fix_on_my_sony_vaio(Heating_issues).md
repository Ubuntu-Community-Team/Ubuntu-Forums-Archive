---
title: "Need ubuntu fix on my sony vaio(Heating issues)"
date: 2014-06-04
forum: New to Ubuntu
---

### Post by srinath3 on 2014-06-04
Hi everyone , i am a beginner at linux. I have got a sony vaio system which does not support ubuntu(Dual boot with windows 7) at all. Problems i have been facing are heating up issues and blue screen shutdowns. I have finally decided to buy a new laptop for me. I need an ubuntu preloaded system. What are my best choices(In India)? Which brands provide the best ubuntu loaded systems. Please suggest. I also want to know that will there be as good replacements for some of the windows applications on ubuntu? Then i will not have to dual boot the ubuntu system with windows. Looking for helpful replies , thanks in advance.

Ok this is my update - I probabiliy will not buy a new system , so i would have to stick with my sony vaio.

My systems configuration -> 
Operating System: Windows 7 Home Basic 32-bit (6.1, Build 7600) (7600.win7_rtm.090713-1255)Language: English (Regional Setting: English)
System Manufacturer: Sony Corporation
System Model: VPCEA23EN
BIOS: BIOS Date: 09/23/09 11:58:43 Ver: 08.00.10
Processor: Intel(R) Core(TM) i3 CPU       M 350  @ 2.27GHz (4 CPUs), ~2.3GHz
Memory: 3072MB RAM
Available OS Memory: 2990MB RAM

If someone has this system and have been able to work with linux/ubuntu without any heating issues , please tell me the fix.

---

### Post by Bucky Ball on 2014-06-04
Welcome. Blue screen problems? That is a Windows thing and does not occur with Ubuntu. Can you be more specific? Are you by any chance using a Wubi install rather than a dual-boot setup (Wubi = Ubuntu installed INSIDE Windows, just like any other program).

As far as replacement apps, you need to be more specific and provide a list of the things you use in Windows and will need in Ubuntu.

---

### Post by srinath3 on 2014-06-04
Yes i used wubi , i have used ubuntu even before but the system heats up so much that it shuts down by itself. I even tried light versions like lubuntu but the same problem. Is it ok for me to buy a brand new ubuntu preloaded system in this way i can avoid such issues and even the hardware will be linux compatibale , if so can you suggest me some good ones.

---

### Post by Bucky Ball on 2014-06-04
Yes, forget Wubi. It has been superseded and consider it dead. 

Try a dual-boot of 12.04 LTS or 14.04 LTS with Windows as Wubi is a thing of the past (even though it is still available for some releases, don't go there). You will get very little help with Wubi as not many people use it and there are few Wubi experts here.

If you need help with a dual-boot I suggest posting a new thread in 'Installations and Upgrade' (but do some research first). Sorry, can't help with a pre-loaded computer in India. Maybe someone else can, but I think buying a whole new laptop is a radical step before you try a dual-boot. Wubi can be, and often is, problematic. ;)

PS: You don't mention which release you are using. Please advise.

---

### Post by vasa1 on 2014-06-04
> **Bucky Ball said:**
> ...
As far as replacement apps, you need to be more specific and provide a list of the things you use in Windows and will need in Ubuntu.
This ^^^^

---

### Post by LastDino on 2014-06-04
Our country is quite lucky in that aspect, if you **must** buy new one, here is quick list from flipkart
[http://www.flipkart.com/laptops/pr?sid=6bo%2Cb5g&q=linux&otracker=from-multi&srno=po_1&allLinkPos=popular](http://www.flipkart.com/laptops/pr?sid=6bo%2Cb5g&q=linux&otracker=from-multi&srno=po_1&allLinkPos=popular)

By the way, I'm regular user of flipkart and you can trust its products.
I've my eye on this little thing which fits right into moderate budget category for experiments. 
[http://www.flipkart.com/dell-vostro-2520-laptop-3rd-gen-ci5-4gb-500gb-linux/p/itmdgszzgzxysh63?pid=COMDGSZAUFHNHGSD&otracker=from-search&srno=t_1&query=linux&ref=774c381a-bafd-4e0c-bbf8-c2192df64897](http://www.flipkart.com/dell-vostro-2520-laptop-3rd-gen-ci5-4gb-500gb-linux/p/itmdgszzgzxysh63?pid=COMDGSZAUFHNHGSD&otracker=from-search&srno=t_1&query=linux&ref=774c381a-bafd-4e0c-bbf8-c2192df64897)

Whichever you buy, please make sure you've good battery backup, a Lappy might give you less than half of what it is giving with Windows, that's about the only real drawback of using Linux instead of Windows on laptops (other one might be wireless networking but that has work around :3 ).


First, try to get the dual boot working on the one which you already own than trying to spend some money, it could teach you few things which might come in handy in future. So, +1 for requesting more details.

---

### Post by Nada__Blue_Book on 2014-06-04
if you Going to buy a new System then i can prefer to buy HP Notebook system. Hp notebook provide full Ubuntu support on their interface. you have said about your previous system problem of heating. this problem should be caused by Drivers. if your system have huge consumption of Resources and you note provide this to your system with drivers then your system should be crashed or increase Heating.

---

### Post by vasa1 on 2014-06-04
@LastDino,

Thanks for sharing. The Vostro looks very decent for the price. But no USB3? 

And what do you know about the graphics? I'm a total zero on hardware. Will it have hardware acceleration to handle things like HTML5 and other fancy stuff?

The Dell I have is an old Inspiron 1545N from 2009. No GPU. Also, it doesn't have this KVM thing which I understand can be used instead of VirtualBox ([http://ubuntuforums.org/showthread.php?t=2155354](http://ubuntuforums.org/showthread.php?t=2155354)).

And you say you like Flipkart. I've also heard a lot of good things but what about service? And what's the OS? They just say Linux. And there have been posts in the past about voiding warranties by using something else instead of the LTS (assuming it's installed with Ubuntu 12.04 LTS or Ubuntu 14.04 LTS).

Edit: I'll look at the reviews as well. Quite informative.

---

### Post by monkeybrain20122 on 2014-06-04
> **vasa1 said:**
> @LastDino,


And what do you know about the graphics? I'm a total zero on hardware. Will it have hardware acceleration to handle things like HTML5 and other fancy stuff?
.

It has HD4000, so VAAPI should work and also VDPAU with [https://github.com/i-rinat/libvdpau-va-gl](https://github.com/i-rinat/libvdpau-va-gl) (so mplayer and system flash can be hardware accelerated, which don't work on VAAPI)

On Firefox hardware acceleration would not work on html5, but with that specs you can easily do without. On Chrome/Chromium it would work, but you would need to enable it by overriding software rendering as I think hardware acceleration is disabled by default for Intel gpus.

---

### Post by LastDino on 2014-06-04
> **vasa1 said:**
> @LastDino,

Thanks for sharing. The Vostro looks very decent for the price. But no USB3? 

And what do you know about the graphics? I'm a total zero on hardware. Will it have hardware acceleration to handle things like HTML5 and other fancy stuff?

The Dell I have is an old Inspiron 1545N from 2009. No GPU. Also, it doesn't have this KVM thing which I understand can be used instead of VirtualBox ([http://ubuntuforums.org/showthread.php?t=2155354](http://ubuntuforums.org/showthread.php?t=2155354)).

And you say you like Flipkart. I've also heard a lot of good things but what about service? And what's the OS? They just say Linux. And there have been posts in the past about voiding warranties by using something else instead of the LTS (assuming it's installed with Ubuntu 12.04 LTS or Ubuntu 14.04 LTS).

Edit: I'll look at the reviews as well. Quite informative.

Most lappies in that price range don't have 3.0, especially the one for linux thing. Also, it has Ubuntu LTS, I don't think its 14.04 though, but I could be wrong as they might start shipping with latest Ubuntu for all we know very soon.

Its graphic chip is Intel HD Graphics 4000, which supports 3D. It is a good chip for Intel standards but it is hardly comparable to AMD or full-fledge graphic cards. However, you can expect good support for it. Needless to say; you shouldn't look at it as high end gaming option.

Every single electronic thing and book I've bought in last year has came from flipkart, I haven't had a problem with single product yet so I'm not entirely sure about their after sell, but usually you've product replacement system valid for defects and damages before delivery. You should always make sure your product falls under that as some don't. 
Also, it gets delivered within time (Though, that's a marketing strategy of announcing one more day than needed, it keeps everyone happy :P )
I also end-up saving few k's with flipkart shopping as their product is slightly cheaper than what you find in locale stores and there are usually some nice offers.

I don't know anything about programming, so I wont be able to assist you on its capabilities there, but I assume it should be able to work with that lappies horse power.
Also, don't get misled if you read any comment from someone who bought that to install pirated Windows copy, I'm sure most of the buyers are in that range as Amazon is selling the only DOS model at same price as what flipkart is selling Ubuntu one for and its 6 to 7k cheaper than windows model.

Edit:
Alas, looks like Monkeybrain has given better answer in fewer words :P

---

### Post by LastDino on 2014-06-04
Other options you might also consider if USB 3.0 is must 
[http://www.flipkart.com/dell-inspiron-15-3537-laptop-4th-gen-ci3-2gb-500gb-ubuntu-1gb-graph/p/itmdufyfqnzyafrd?pid=COMDUFYFQNZYAFRD&icmpid=reco_pp_same_computer_3&ppid=COMDZXZ7XGS9PZXE](http://www.flipkart.com/dell-inspiron-15-3537-laptop-4th-gen-ci3-2gb-500gb-ubuntu-1gb-graph/p/itmdufyfqnzyafrd?pid=COMDUFYFQNZYAFRD&icmpid=reco_pp_same_computer_3&ppid=COMDZXZ7XGS9PZXE)

[http://www.flipkart.com/acer-aspire-e1-572-laptop-4th-gen-ci5-4gb-500gb-linux-nx-m8esi-002/p/itmdzxz82yzffmyt?pid=COMDZXZ7XGS9PZXE&icmpid=reco_pp_historyFooter_computer_3](http://www.flipkart.com/acer-aspire-e1-572-laptop-4th-gen-ci5-4gb-500gb-linux-nx-m8esi-002/p/itmdzxz82yzffmyt?pid=COMDZXZ7XGS9PZXE&icmpid=reco_pp_historyFooter_computer_3)
Its clocked little lower so CPU performance is arguable compared to the Dell I linked in earlier post.

There is also Lenovo
[http://www.flipkart.com/lenovo-essential-g510-59-398343-laptop-4th-gen-ci5-4gb-500gb-dos/p/itmdp26exhgyducx?pid=COMDP26ETWKZUZUG&icmpid=reco_bp_historyFooter_computer_1](http://www.flipkart.com/lenovo-essential-g510-59-398343-laptop-4th-gen-ci5-4gb-500gb-dos/p/itmdp26exhgyducx?pid=COMDP26ETWKZUZUG&icmpid=reco_bp_historyFooter_computer_1)


Then there is Toshiba satellite series, which provides hip-load of options with hardware but it comes with no OS pre installed, means you need to install one yourself, be it Ubuntu or Windows. 
[www.flipkart.com/toshiba-satellite-s50-a-i2010-laptop-3rd-gen-ci3-4gb-500gb-no-os-1gb-graph/p/itmdqggthtd58guz?pid=COMDQGGSDQKBDTNF]("http://www.flipkart.com/toshiba-satellite-s50-a-i2010-laptop-3rd-gen-ci3-4gb-500gb-no-os-1gb-graph/p/itmdqggthtd58guz?pid=COMDQGGSDQKBDTNF")

[http://www.flipkart.com/toshiba-satellite-s50-a-x2010-laptop-4th-gen-ci5-4gb-500gb-no-os-1gb-graph/p/itmdqggtryvbzzxs?pid=COMDQGGS44SSPFUK](http://www.flipkart.com/toshiba-satellite-s50-a-x2010-laptop-4th-gen-ci5-4gb-500gb-no-os-1gb-graph/p/itmdqggtryvbzzxs?pid=COMDQGGS44SSPFUK)

[http://www.flipkart.com/toshiba-satellite-c50-a-i2012-laptop-3rd-gen-ci3-4gb-500gb-no-os-2gb-graph/p/itmdu5xff2xdfgb3?pid=COMDU5XFF2XDFGB3](http://www.flipkart.com/toshiba-satellite-c50-a-i2012-laptop-3rd-gen-ci3-4gb-500gb-no-os-2gb-graph/p/itmdu5xff2xdfgb3?pid=COMDU5XFF2XDFGB3)

That last one with 2 gigs of gpu looks very tempting :3

---

