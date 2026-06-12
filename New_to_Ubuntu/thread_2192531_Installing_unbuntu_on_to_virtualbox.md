---
title: "Installing unbuntu on to virtualbox"
date: 2013-12-08
forum: New to Ubuntu
---

### Post by brian.farr on 2013-12-08
I have installed Virtualbox and installed unbent 13.10 on my Macbook Pro 9,1. I have opened virtual box and ran unbent and receive the following message.

[FONT=Lucida Grande]"This kernel requires an x86-64 CPU, but only detected an i686 CPU.[/FONT]
[FONT=Lucida Grande]Unable to boot - please use a kernel appropriate to your CPU."

Can anyone advise how i fix this and provide any links if I have installed the incorrect version for 9,1

Cheers


[/FONT]

---

### Post by Bucky Ball on 2013-12-08
Welcome. Incorrect version. You need the 32bit version. You are trying to run the 64bit.

To clarify: you have Virtualbox installed on the Mac OS and have Ubuntu 13.10 running as a virtual machine?

* Update: That's a modern machine with quad-core, yea?

---

### Post by brian.farr on 2013-12-08
Bucky, correct, I will install the 32bit version and see how I go, many thanks for the quick response.

---

### Post by mastablasta on 2013-12-08
i don't know about macs, but PC have a setting in bios that will enable 64 bit OS in virtualbox (hardware virtualisation- amd-v  or VT-x). read more about this here:[http://en.wikipedia.org/wiki/X86_virtualization](http://en.wikipedia.org/wiki/X86_virtualization)

---

### Post by sandyd on 2013-12-08
> **brian.farr said:**
> I have installed Virtualbox and installed unbent 13.10 on my Macbook Pro 9,1. I have opened virtual box and ran unbent and receive the following message.

[FONT=Lucida Grande]"This kernel requires an x86-64 CPU, but only detected an i686 CPU.[/FONT]
[FONT=Lucida Grande]Unable to boot - please use a kernel appropriate to your CPU."

Can anyone advise how i fix this and provide any links if I have installed the incorrect version for 9,1

Cheers


[/FONT]
When going through the new machine wizard, make sure Ubuntu (64bit) is selected

Also, make sure you have the firmware for VT-X installed [http://support.apple.com/kb/TS2744](http://support.apple.com/kb/TS2744)

---

### Post by asus-user on 2013-12-08
I had a similar problem, and as **sandyd** said:

> 
When going through the new machine wizard, make sure Ubuntu (64bit) is selected
 

This could be changed later from Machine settings under: General-> Basic -> Version.
also you might need to un-check/check the "Enable EFI" option under: System -> Motherboard.

---

### Post by jdeca57 on 2013-12-08
> **brian.farr said:**
> Bucky, correct, I will install the 32bit version and see how I go, many thanks for the quick response.

There is another reason why 32 bit makes perfect sense in a virtual environment: the memory allocated tends to be less than 4GB (I typically run Ubuntu with GUI in 1 GB) and then the 32 bit version is actually better. Smaller programs, to name an advantage.

---

### Post by brian.farr on 2013-12-08
Thanks guys, installed the 32 bit program. It seems to be working now although some of your advice went way over my head regarding VTX and EFI. Pretty new to me to be honest.
Bucky quad-core, I assume you mean processor? In answer to your question, no idea, how do I find this out?

---

### Post by amjjawad on 2013-12-08
> **brian.farr said:**
> I have installed Virtualbox and installed unbent 13.10 on my Macbook Pro 9,1. I have opened virtual box and ran unbent and receive the following message.

[FONT=Lucida Grande]"This kernel requires an x86-64 CPU, but only detected an i686 CPU.[/FONT]
[FONT=Lucida Grande]Unable to boot - please use a kernel appropriate to your CPU."

Can anyone advise how i fix this and provide any links if I have installed the incorrect version for 9,1

Cheers


[/FONT]

Hello and Welcome :)

You are lucky, I just had this very issue today and the fix, in my case, was very much easy:

Rebooted my laptop
Entered BIOS
Enabled Virtualization
Saving
Exit

Login to my system
Open VirtualBox
Choose Ubuntu 64bit 
Try again

Let us know if that solved your issue :)

P.S.
I have a Laptop, Not Mac!

---

### Post by amjjawad on 2013-12-08
> **sandyd said:**
> When going through the new machine wizard, make sure Ubuntu (64bit) is selected

If Virtualization is 'not' enabled from BIOS, you will not find 64bit listed - just happened with me today :)

---

### Post by trevino.alan90 on 2013-12-08
I've tried all these solutions. What I ended up doing in installing 13.04 x32 on and it worked just fine. But with the x64 version, it would only load the Terminal.

---

### Post by amjjawad on 2013-12-09
> **trevino.alan90 said:**
> I've tried all these solutions. What I ended up doing in installing 13.04 x32 on and it worked just fine. But with the x64 version, it would only load the Terminal.

I don't know about you but the steps I have mentioned on my previous post helped me to get the Virtual Machine up and running :)
I was trying to install Ubuntu GNOME Trusty (14.04) to start testing it (I am Ubuntu GNOME QA Lead) and it gave me some headache at the beginning but once I changed the settings in BIOS, everything is fine :) 

In my case, I need to test both i386 and amd64 so it is a must-have feature but I understand YMMV :)

Good luck and enjoy!

Should you need anything, please let us know :)

If you have no further Qs or issues, please mark this thread as solved!

---

### Post by Cerberus1971 on 2013-12-13
> **sandyd said:**
> When going through the new machine wizard, make sure Ubuntu (64bit) is selected

[/url]

Running a Win 7 PC with 8 core bulldozer. I ran into this issue. Your suggestion fixed it.
Thanks

---

