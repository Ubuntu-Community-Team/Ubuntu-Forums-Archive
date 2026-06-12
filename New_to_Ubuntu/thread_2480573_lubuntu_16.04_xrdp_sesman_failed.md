---
title: "lubuntu 16.04 xrdp sesman failed"
date: 2022-11-02
forum: New to Ubuntu
---

### Post by pierofp on 2022-11-02
I'm new in the forum and lubuntu. I've connection and login with success but session ended as in the pic attached. Could you help me to resolve it ?
From Microsoft W10 client via remote desktop connection to lubuntu 16.04 xrdp server with LXDE :

*connecting to sesman ip 127.0.0.1 port 3350*
*sesman connect ok*
*sending login info to session manager, please wait...*
*xrdp_mm_process_login_response: login successful for display*
*started connecting*
*connecting...*
[I]connected ok

[/I]Thanks

---

### Post by guiverc on 2022-11-02
Why did you install Lubuntu 16.04 LTS?

It reached *end of life* in 2019-April; [three years after it was released]("https://lubuntu.me/xenial-released/")

Even Ubuntu 16.04 LTS is *end of standard support* thus only gets security upgrades if ESM is applied - [https://fridge.ubuntu.com/2021/03/13/extended-security-maintenance-for-ubuntu-16-04-xenial-xerus-begins-april-30-2021/](https://fridge.ubuntu.com/2021/03/13/extended-security-maintenance-for-ubuntu-16-04-xenial-xerus-begins-april-30-2021/)

Your machine should be kept offline given you're using a release that hasn't had security fixes since 2019-April for LXDE & desktop components, or 2021-April for your base components.

The only supported releases of [Lubuntu now are 20.04 & 22.04]("https://lubuntu.me/lubuntu-21-10-end-of-life-and-current-support-statuses/")

---

### Post by pierofp on 2022-11-03
Because I've a Pentium M 2200 MHz with two RAM modules 512 MB 333 MHz + 256 MB 266 MHz while waiting a new two modules of 1 GB 333 MHz compliant with 266 MHz and a new SSD of 512 GB. Do you think this hardware is able to support Lubuntu 20.04 & 22.04 ? Thanks

---

### Post by ActionParsnip on 2022-11-03
Ubuntu 16.04 is end of life and supported by nobody (without payment to Canonical). Debian are still supporting x86 architecture. You may want to use that instead.

---

### Post by guiverc on 2022-11-03
I used many pentium M laptops (*mostly old IBM thinkpads, but also others*), plus other pentium 4 & pentium D desktops inQA (*Quality Assurance*) testing of *i386* releases of Lubuntu, meaning up to and including Lubuntu 19.04 which was release where *i386* ISOs were *finally *turned off.

I still have Lubuntu 18.04 installed on one at least (*possibly more, though most were used in QA for later Debian releases which I also test, and I've left Debian on most that I use on occasion*), eg. the following still has a Lubuntu 18.04 LTS install on it (*I now refer to it as Ubuntu 18.04 LTS with LXDE*)

```
ibm thinkpad t43 (pentium m, 1.5gb ram, radeon x300)
```

The last release I QA-tested with pentium M was [18.04.5]("https://fridge.ubuntu.com/2020/08/14/ubuntu-18-04-5-lts-released/") (*it used the kernel stack from 20.04 thus occurred late 2020*), and two IBM Thinkpads didn't like the 5.4 kernel used in that stack (*they were unreliable, other pentium M thinkpads were good though; solution was to use the GA kernel stack in my opinion though* *as those devices ran 18.04 with the GA stack perfectly!*), so if it was me & I wanted Ubuntu, I'd opt for 18.04 (*using the GA kernel stack if your device didn't like the HWE kernel stac**k; using 18.04.5 media live for ~10 minutes should show if its a problem with your video hardware; it was only the oldest IBM thinkpads that seemed impacted*).   [*if you need more detail on the problem; it'll be found on Lubuntu's discourse**; as it was other users that brought it to my attention!*]

**No pentium M** will run 20.04 or later releases, and my own QA testing for anything 18.04 or later involved only 1GB of RAM or higher. I still use a r50p, t42p (*both run Debian*), a dell....  and whilst I did some QA with less RAM before then, it's now too long ago I'd be unreliable.

I'd not use 16.04 and pay for ESM support (*if used online* or sharing a network etc). Given 18.04 reaches EOSS (*end of standard support*) in April 2023, I'll replace the last 18.04 that I'm aware of running 18.04 with Debian myself then (*if not before*), but as I see no need just yet with how I use the machine I'm in no hurry to do that.

FYI:  I had one HP device that performed much better with Lubuntu than Debian; it was the most under-powered device I have, but for the rest of the ~25 devices I used in QA (>10 being *i386*); the difference between Debian & Ubuntu (using LXDE, LXQt, Xfce or *lighter desktops*) was so minimal as to be *moot*.

---

### Post by pierofp on 2022-11-03
You convinced me, I'll try update 18.4 . This is the message I receive at logon :

*Welcome to Ubuntu 16.04.7 LTS (GNU/Linux 4.15.0-142-generic i686)*

* * Documentation:  [https://help.ubuntu.com](https://help.ubuntu.com)*
* * Management:     [https://landscape.canonical.com](https://landscape.canonical.com)*
* * Support:        [https://ubuntu.com/advantage](https://ubuntu.com/advantage)*

*0 updates can be applied immediately.*

*New release '18.04.6 LTS' available.*
*Run 'do-release-upgrade' to upgrade to it.*

---

### Post by guiverc on 2022-11-03
You're using 16.04(.7) and the 4.15 kernel, ie. the HWE kernel stack.  The GA kernel stack for 16.04.7 was 4.4.

I'd (*if in your shoes*), either install the GA kernel stack as well (*both GA & HWE kernel stacks can co-exist, unless you're using closed-source kernel modules; aka video drivers*, *eg. the t43 I mentioned that I have that still runs 18.04, has both the 4.15 (GA) & 5.4 (HWE) kernel stack installed)  ***OR** write a Lubuntu 18.04.5 ISO to thumb-drive and test that in a *live* session as I tried to mention last message.

As your system is currently using the HWE kernel stack, you'll upgrade from 16.04 to 18.04 with that stack, meaning you'll switch from the 4.15 kernel to 5.4, that had problems with two old thinkpads I own (*plus five other users reported having trouble with on Lubuntu's discourse, askubuntu, possibly here too*).  If you add the GA kernel stack; you'll be added the 4.4 kernel to your existing system now, which will upgrade to the 4.15 you're already using now as you'll note you reported in your last comment.

If your machine is good on HWE (5.4 kernel) it won't matter, but if it isn't... you'll discover problems when you reboot on 18.04.

FYI:  If you're too late when you see this; you'll still be able to boot into the 4.15 kernel installed when on 16.04 unless you tell it to be removed (*ie. tell your system to reclaim disk space & clean old stuff*).  It'll just be easier (*in my opinion*) to test for it now given I found out you can just a *live* session for streaming youtube vids or something pointless & have an answer in about 10 mins... it'll still be streaming *(if all is good*) or ~dead if you'll have problems..

Another reason for the GA or older kernel stack, is just that I found some older hardware actually had less *tearing* with older kernels too without needing any *configuration or additional changes*  (*for some reason the dell latitudes with pentium M cpus outperformed IBM here as they had intel and not amd/nvidia with my boxes anyway*).

If you're not familiar with kernel stack choices (LTS releases have choice); refer [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

With Lubuntu; the initial install media sets the default; Lubuntu had the same behavior as Ubuntu Desktop 18.04 in the wiki doc I referenced (ie. 18.04 & 18.04.1 defaults to GA; 18.04.2 (or 16.04.2, 14.04.2 & later media) default to HWE)

---

### Post by pierofp on 2022-11-03
boot hangs at. Starting terminate plymouth boot screen and I don't get to the login screen systems seems to boot fine, can switch to tty and I'm logged in, what I can to do ?

---

