---
title: "New PC build,  Graphics card not recognized"
date: 2019-08-24
forum: New to Ubuntu
---

### Post by Badouken on 2019-08-24
Hey I just built a computer and when I log in everything is 720p and won't let me change to anything higher. I know this isn't correct because I have a dedicated graphics card. 

I check 'about' and it says my graphics are ; llvmpipe (LLVM 8.0, 128 bits) 
Though I have a Radeon 5700, its just not being utilized by Ubuntu it seems. I'm wondering what im missing here, any assistance would be appreciated. 

I have a Ryzen 5 2600X as well if that matters.

---

### Post by TheFu on 2019-08-24
Is this running inside a virtual machine?

For a physical machine install, I assume you checked the  'Additional Drivers' tab on the Software & Updates application?

---

### Post by Badouken on 2019-08-24
> **TheFu said:**
> Is this running inside a virtual machine?

For a physical machine install, I assume you checked the  'Additional Drivers' tab on the Software & Updates application? Yes this is a physical machine install and I did click "additional Drivers".

Shouldn't this GPU work out of the box on kernel 5.0? Is there anything else I can do to make the system recognize my card?

---

### Post by TheFu on 2019-08-24
If you are running 18.04, then there shouldn't be any issue with intel, AMD or nvidia GPUs that are still supported. If the card is old, then usually the F/LOSS drivers get used.

I don't know anything about newer kernels.  My systems run 4.15 and most of them are virtual.
It might help someone to help if they knew the  
a) ubuntu release 
b) specific GPU make and model - sorry - I see the Radeon 5700 now.

---

### Post by Badouken on 2019-08-24
I was on 19.04. I read perhaps I have to be on 18.04 for navi cards to work properly. So im gonna try that real quick and see if that resolves the issue.

Edit: 

So yeah I got it to work! For future reference anyone who needs help. 
I loaded up Ubuntu 18.04 and installed the drivers manually from the following; [https://www.amd.com/en/support/kb/release-notes/rn-amdgpu-unified-navi-linux](https://www.amd.com/en/support/kb/release-notes/rn-amdgpu-unified-navi-linux) then rebooted. 

Had no luck on anything above 18.04 or other distros.

Edit 2: 

And when I reboot the computer it's just a black screen... So much for that working. Is the Radeon 5700 just not supported at all? I keep reading how people have it working and they have drivers for it online specifically for Ubuntu so I'm very confused.

---

### Post by TheFu on 2019-08-25
[https://www.amd.com/en/support/kb/release-notes/rn-amdgpu-unified-navi-linux](https://www.amd.com/en/support/kb/release-notes/rn-amdgpu-unified-navi-linux) says it works with 18.04.2.  Please confirm you are running that with **lsb_release -a**

---

### Post by CatKiller on 2019-08-25
> **Badouken said:**
> Shouldn't this GPU work out of the box on kernel 5.0?

No. AMD haven't been that great at getting software support prior to the release of their hardware. Intel do get software support done in advance, and Nvidia just do their own thing.

Support for that card made it into the 5.3 kernel. AMD say they've made their installer work with 18.04 (the most recent LTS) but no one cares about backporting to non-LTS releases.

---

### Post by Badouken on 2019-08-25
> **TheFu said:**
> [https://www.amd.com/en/support/kb/release-notes/rn-amdgpu-unified-navi-linux](https://www.amd.com/en/support/kb/release-notes/rn-amdgpu-unified-navi-linux) says it works with 18.04.2.  Please confirm you are running that with **lsb_release -a** Yeah I ran lsb_release -a and can confirm im on 18.04 LTS. Still doesnt work. hmm :(

---

### Post by cruzer001 on 2019-08-25
Please verify the kernel your running, may need HWE enabled.
```
uname -r
```

---

### Post by CatKiller on 2019-08-25
> **Badouken said:**
> Is the Radeon 5700 just not supported at all? I keep reading how people have it working and they have drivers for it online specifically for Ubuntu so I'm very confused.

[When Phoronix tested it last](https://www.phoronix.com/scan.php?page=article&item=navi-august-2019) they were using a newer kernel and a newer version of Mesa than you'll have in any released version of Ubuntu. It'll probably work out of the box in either the 19.10 or 20.04 releases. AMD really needed to start on the software side earlier.

You can get newer versions of Mesa from the [Oibaf PPA](https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers), and there's a tool for getting newer versions of the kernel that I've never used called [UKUU](https://itsfoss.com/upgrade-linux-kernel-ubuntu/).

---

### Post by TheFu on 2019-08-26
> **Badouken said:**
> Yeah I ran lsb_release -a and can confirm im on 18.04 LTS. Still doesnt work. hmm :(

What is the 3rd level number?

---

### Post by Badouken on 2019-08-26
So update for people wondering and or wanting to help


I have been constantly told when asking around that I need Mesa 19.2 and kernel 5.3 to be able to have the RX5700 recognized in linux. 
So I went ahead to get these things install. Neither Mesa 19.2 nor 5.3 kernel are released yet but I grabbed the rc of both and installed them with success. 

some information for those wondering version of everything I'm on below. 

lsb_release -a returns ; 
Ubuntu 18.04.03 LTS 

uname -a ; 
5.3.0-050300rc6-generic 

glxinfo | grep "OpenGL version" ; 
3.1 Mesa 19.3.0-devel 

I ran all this on a clean install of Ubuntu 18.04 AND I even went as far as to return my open box graphics card for a brand new one just to eliminate the factor of a faulty card and with all this I'm still unable to get the graphics card to be recognized on Ubuntu. The only thing I haven't tried is install the proprietary drivers because they totally borked my system 9/10 and got the graphics card recognized and working 1/10 (until reboot).

sadly may just give up for now and load Windows :( . Until newer version of Linux release.

---

### Post by TheFu on 2019-08-26
Thanks for posting back.

Bleeding edge is hard.  I usually wait a year before getting anything "new" and do lots of research in advance before.  For example, I bought a Ryzen 2600 and avoided getting a Ryzen 2[24]00g because at the time, support for them was hit-or-miss.  Those are the ones with built-in GPUs, like Intel Core i3/i5 CPUs have.  Graphics performance isn't a consideration for me at all. I would have been happy with an 80x25 text screen, but if I'm forced to have a GPU, I want it to support my 1200p monitor. Unfortunately, none of the current gen GPUs on my list had VGA output, which I need to use my 4-port KVM switch. Ended up having to fight with a DVI-d to VGA active converter which didn't report the correct EDID from the monitor.

---

### Post by Badouken on 2019-08-26
Yeah I'm pretty new when it comes to building my own hardware so I wasn't sure. I was gonna get lower end stuff but the guy at Microcenter upsold me on the RX 5700 and said how it could run on Linux because he's also a Linux guy (the liar!) but in his defense the box does say LINUX support so I blame AMD. Im fine with waiting a bit because I got games pass free for a couple months and thats only available on windows right now. I can at least play some games to have the card essentially pay for itself :P

---

### Post by QIII on 2019-08-26
You needn't go "lower end".  If you want to you can go for last year's top model, for which the Linux community has had some time to work out the kinks -- or the OEM has had time to bother updating Linux drivers.

But the wise thing to do in any case is to spend only what you need to get the performance and features most useful to you.

---

### Post by Badouken on 2019-08-27
Yes indeed! Im quite happy with my build and the experience of troubleshooting the hardware and software side of things the past couple days. Honestly thought it was pretty fun. 
I'll surely be back in a couple weeks/months to try again once the kinks are worked out. :P

---

### Post by TheFu on 2019-08-27
AMD To Land Support For Navi 14 Into The Upcoming Mesa 19.2 Driver Stack
[https://www.phoronix.com/scan.php?page=news_item&px=AMD-Navi-14-For-Mesa-19.2](https://www.phoronix.com/scan.php?page=news_item&px=AMD-Navi-14-For-Mesa-19.2) just out today.

---

### Post by Claritux on 2019-08-30
I made a guide for installing open source drivers for RX 5700 XT/RX5700 on Ubuntu 19.04 here [https://ubuntuforums.org/showthread.php?t=2425799](https://ubuntuforums.org/showthread.php?t=2425799)

---

### Post by Autodave on 2019-08-30
Stupid question: are you sure that your monitor is connected to the RX5700 and not the on-board graphics?

---

### Post by Badouken on 2019-09-01
[**[COLOR=#000000]Claritux[/COLOR]**]("https://ubuntuforums.org/member.php?u=353762") that did it!

hank you sir! Finally! Im free! :p

---

