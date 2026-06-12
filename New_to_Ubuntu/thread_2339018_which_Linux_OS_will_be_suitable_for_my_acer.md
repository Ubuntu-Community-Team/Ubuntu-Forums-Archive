---
title: "which Linux OS will be suitable for my acer"
date: 2016-10-04
forum: New to Ubuntu
---

### Post by bluesfloyd on 2016-10-04
hi, guys
            i want to install Linux, but which OS will be suitable for  my acer, extensa 5235 laptop,  i use my laptop for emailing, browsing  and playing cd's/dvd's

                           thank for your time guys,
                                                                bluesfloyd

 SYSTEM SPEC,
 Processor Intel(R) Celeron(R) CPU          900  @ 2.20GHz, 2195 Mhz, 1 Core(s), 1 Logical Processor(s)
 BIOS Version/Date    Phoenix V1.3311, 21/12/2009   
SMBIOS Version    2.5   
Embedded Controller Version    255.255   
BIOS Mode    Legacy   
BaseBoard Manufacturer    Acer
 Installed Physical Memory (RAM)    4.00 GB   
Total Physical Memory    3.90 GB   
Available Physical Memory    2.97 GB   
Total Virtual Memory    4.59 GB   
Available Virtual Memory    3.77 GB

 [Disks]
Description    Disk drive   
Manufacturer    (Standard disk drives)   
Model    Samsung SSD 850 EVO 250GB
 [Display]
Mobile Intel(R) 4 Series Express Chipset Family (Microsoft Corporation - WDDM 1.1)
Adapter Description    Mobile Intel(R) 4 Series Express Chipset Family (Microsoft Corporation - WDDM 1.1)

---

### Post by Bucky Ball on 2016-10-04
Welcome. What do you want to do with your Acer? Why not download a bunch of ISOs, burn them to USB and 'Try *buntu'? You can try them all 'before you buy' directly from the install media without changing anything on your drive. 

You can go for the AMD64bit version of whichever flavour of Ubuntu you go for (that is for both Intel and AMD processors). Incidentally, FYI, here are the [specs for that processor]("http://ark.intel.com/products/41498/Intel-Celeron-Processor-900-1M-Cache-2_20-GHz-800-MHz-FSB"). 

(PS: Please use default text and forget the bold. Thanks.)

---

### Post by kurt18947 on 2016-10-04
Your machine doesn't have the newest shiniest hardware which is  plus. Windows 7 so it probably doesn't have UEFI and no Secure Boot. Often the biggest hardware bugaboo is wireless networking. Do you know which wifi chip you have? Cnet has this to say, I don't know how accurate it is:

[https://www.cnet.com/products/acer-extensa-5235-15-6-celeron-900-3-gb-ram-250-gb-hdd/specs/](https://www.cnet.com/products/acer-extensa-5235-15-6-celeron-900-3-gb-ram-250-gb-hdd/specs/)

wifi:  Acer InviLink Nplify

A quick search using that name in the networking and wireless forum shows nothing newer than 2012 so that's good news. I'll bet you can boot a live DVD/USB and it'll work.

---

### Post by poorguy on 2016-10-04
I have an  Acer Aspire 5630 BL50 laptop that I installed Ubuntu Mate 16.04 on and I had no problems with anything right out of the box all installed and runs well.

---

### Post by T2uiYKb7 on 2016-10-04
It's high enough spec to try all distributions. By Linux standards that's quite a capable PC. 

I've used way way worse at times. High bit rate, high resolution video will probably be your only issue.

[B]Edit: If you want to make this process as short as possible (not downloading and testing multiple Live ISOs) Google Xubuntu, Ubuntu Mate, Ubuntu Gnome, Lubuntu, Kubuntu, Ubuntu and look at screen shots and decide what you like the look of. Keep in mind all versions except normal Ubuntu can be changed significantly in terms of appearance by the user. 

You can also switch desktop environments at login (after you install them.) So you can install Kubuntu and "login as" Xubuntu, or Lubuntu. So in a way it doesn't really matter what you install.

[COLOR=#008000]Second edit: Actually if your new to Linux and a long time Windows user don't get the normal Ubuntu or Ubuntu Gnome these will be very confusing. The other versions will feel much more natural.[/COLOR][/B]

---

### Post by harleybronco on 2016-10-04
All great advice, above, here. The one thing I would say or add to any of this is that it really depends on what you want to do with Ubuntu, or Linux. Often it just comes down to how you want your computer to LOOK, but even that is all customizable in Ubuntu.

I agree with playing around with live CDs of all the distros. Some use different Ubuntu engines, and you may find one more preferable than the other, but they are all Linux at the core.

---

### Post by RobGoss on 2016-10-04
What makes Ubuntu so great is the fact you have so many different distributions to try out and if one does not work the way you want it to move on to the next one. I have a number of distrubtions already loaded up on USB's and DVD's, I can try out anyone of my choice. Ask your self this, what do you really want out of Linux?

---

### Post by wildmanne39 on 2016-10-04
With your processor I recommend Lubuntu it will be the lightest on resources but you can try out as many versions as you wish as stated using the live version of each.

---

### Post by bluesfloyd on 2016-10-05
hi,guys
          big thanks for your warm welcome and detailed helpful posts above,
 i do intend to use some windows programs on the choice of Ubuntu distros, what Ubuntu distros runs best with windows programs,

                                              thanks again guys,
                                                                          bluesfloyd,

---

### Post by mastablasta on 2016-10-05
ubuntu doesn't run Windows programs. if you plan to run Windows stuff, then it is better to use Windows. you can run some programs to a various degree using Wine - check here: [SIZE=2]https://appdb.winehq.org/
[/SIZE]
everything less than gold is not going to run well.

another option is to run them in virtualbox or similar emulation. if you run just some programme here and there this would be a solution. but do not expect to run any 3D hardware accelerated stuff in virtualisation well.

HINT: Xubuntu, Lubuntu and Mate need less system resources as they use a more simplistic (not hardwasre accelerated) desktops without special effects etc. Ubuntu and Kubuntu also have "fallback modes" with simpler graphics available. you Will need resoruces to run emulations/virtualisations.

---

### Post by Bucky Ball on 2016-10-05
As above. Sounds like you need to do a bit of research about Ubuntu/Linux. It is in no way a drop in replacement for Windows. Windows programs are NOT going to work natively and some may or may not work with WINE. 

Rather than the WINE kludge, you are much better advised to find Linux/Ubuntu alternatives for your Windows apps. If your main aim is to run Windows programs in Linux, better to stay with Windows and what you know rather than leap on the learning curve expecting to run Windows programs. Windows programs are for Windows and getting them to run in Linux will only ever be a messy workaround. ;)

(The alternative is to install Ubuntu, install Virtualbox in Ubuntu then Windows as a virtual machine. The end result of this is you are still running Windows, just as a virtual machine, so wouldn't bother.)

Bottom line: if you're thinking Ubuntu is a free drop-in replacement for Windows it isn't. They are not related in almost any way (apart from they are both operating systems). Switching to Ubuntu is going to require you to put your learning hat on and look for alternative applications to do what you were doing in Windows.

---

### Post by kurt18947 on 2016-10-05
^^^^^^^^^^^^^
What Bucky said. I've had pretty good luck opening and saving Microsoft formatted documents in LibreOFfice as long as they're not highly formatted or containing macros. GIMP is more capable than I am when doing graphics and photo manipulation. If you need professional grade Microsoft/Adobe functionality, you'd probably be better served to use Windows. I've had pretty good luck with VirtualBox but I don't know that your machine would be up to that.

---

### Post by T2uiYKb7 on 2016-10-05
> **bluesfloyd said:**
> hi,guys
          big thanks for your warm welcome and detailed helpful posts above,
 i do intend to use some windows programs on the choice of Ubuntu distros, what Ubuntu distros runs best with windows programs,

                                              thanks again guys,
                                                                          bluesfloyd,

What Windows programs? You can't use the same setup files but Ubuntu does run many well known Windows programs using versions made specifically for Linux.

Programs like: Skype, Firefox, Thunderbird, TeamViewer, Google Chrome, Firefox, VLC and many more.

---

### Post by Bucky Ball on 2016-10-05
> **andrew.nz said:**
> Programs like: Skype, Firefox, Thunderbird, TeamViewer, Google Chrome, Firefox, VLC and many more.

All cross-platform (run on more than on OS) and you would be using the Linux versions, not Windows versions. Therefore, not Windows programs. These are available for more than one OS but they are NOT the same 'under the hood'. They wouldn't work across platforms if they were. They are 'ported' to the different OSs. ([Skype also works on Android]("https://www.skype.com/en/download-skype/skype-for-android/"), for instance, but not the Linux version of Skype or the Windows version of Skype, the Android version of Skype).

So, same applies. Windows programs (or Windows versions of programs) will not work on Linux. Linux *versions* of *cross-platform* programs that may have a version for Windows also, will. :)

Download the Windows versions of Skype, Firefox, Thunderbird, TeamViewer, Google Chrome, Firefox, VLC and none of them will work in Linux (unless you are using Wine, which they may or may not work in, or Win as a virtual machine). You need to use the Linux versions, in other words, Linux apps.

---

### Post by T2uiYKb7 on 2016-10-05
**@Bucky Ball**

I think your making it a little confusing. He just needs to know *those same programs are available* on Linux just from a different source.

---

### Post by Bucky Ball on 2016-10-05
What is confusing is calling a Linux program a Windows program when it's not, it's cross-platform and ported to up to four different operating systems, but either way, I think it is clear now. Let's get back to the issue at hand. Thanks.

---

### Post by T2uiYKb7 on 2016-10-05
I didn't say that.

> **andrew.nz said:**
> You can't use the same setup files but Ubuntu does run many well known Windows programs using versions made specifically for Linux.

**Edit: OK I get it, your worried about Windows being credited for those programs** **being made. I don't think he's worried about that.**

---

### Post by QIII on 2016-10-05
I am going to say this again for the benefit of the OP, who is new:  *You cannot run Windows programs on Linux*, with the exception that some few will run to some extent or another when using the kludge that is WINE.

Just to be clear.  

The Skype, Firefox, Thunderbird, TeamViewer, Google Chrome, Firefox, VLC you run on Linux are ***Linux*** applications.

It's not about "credit" for who or where those programs were made.  In fact, Firefox and Thunderbird were developed by the open source community.  Google (even at their employees' desks) runs on Linux (Ubuntu, primarily).  You are NOT talking about programs Windows has any credit for.

---

### Post by T2uiYKb7 on 2016-10-05
^ As I explained in six words several posts ago.

> **andrew.nz said:**
>  using versions made specifically for Linux.

---

### Post by QIII on 2016-10-05
The explanation was incorrect.  You conveniently edited out "Windows programs".

If you would care to go ahead and continue to argue with yet another member of the Staff after Bucky Ball attempted to ensure that another member of the forums community is not led astray by inaccuracies, do so at your own peril.

Bucky Ball asked to have the thread get back on point.  Please make sure that happens.

---

