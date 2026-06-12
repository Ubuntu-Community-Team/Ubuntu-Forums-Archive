---
title: "Secure Boot hardware and Ubuntu"
date: 2012-05-17
forum: Recurring Discussions
---

### Post by GrouchyGaijin on 2012-05-17
Hi Guys,

I just read an article about something called Secure Boot and that on new PCs it *could* mean that we won't be able to install Ubuntu (or any other Linux OS).

My question is how much of a worry is this?  Does anyone really know yet?
I'm guessing this wouldn't affect the ability of people or businesses like System76 to build machines with Linux installed, correct?

What do you all think?

---

### Post by xedi on 2012-05-17
AFAIK the current status is the following:

Microsoft will in the future force manufacturers to have UEFI secure boot enabled if they want to be Windows 8 certified. However, they differentiate between traditional and ARM hardware:

On traditional PCs: You will be able to disable secure boot
On ARM: You are screwed when you want to run Linux

The worst case scenario will be if manufacturers will not let you disable it voluntarily but on traditional PCs at least Microsoft is not forcing them to do so and I think that scenario is unlikely.

On ARM my speculation is that there will be so many hardware manufacturers which will not follow the certification guidelines, that you won't have to worry that you will not find hardware to run Ubuntu on.

---

### Post by drs305 on 2012-05-17
Moved out of Absolute Beginners (Support) to Recurring Discussions.

---

### Post by GrouchyGaijin on 2012-05-17
> **xedi said:**
> AFAIK the current status is the following:

On ARM my speculation is that there will be so many hardware manufacturers which will not follow the certification guidelines, that you won't have to worry that you will not find hardware to run Ubuntu on.

What exactly does ARM include?  Is that just things like smart phones or does that also include Netbooks like the EeePC I have running Ubuntu?

---

### Post by xedi on 2012-05-17
Smartphones and Tablets use mostly ARM processors, correct. Some speculate that also more Netbooks/Ultrabooks/Notebooks will use ARM processors for energy efficiency in the future. My guess is that your EeePC has a "normal" Atom CPU.

At this point I would not worry too much, event though I find Microsoft's strategy worrisome in principle.

---

### Post by 3rdalbum on 2012-05-19
> **xedi said:**
> My guess is that your EeePC has a "normal" Atom CPU.

If he's running Ubuntu on it, then it is. Nobody would not know what ARM is and yet be running a downloaded copy of Ubuntu on their ARM system :-)

Note that some el-cheapo netbooks have ARM CPUs, but these all run either Windows CE, an old version of Android, or a horrible custom-built Linux that's been themed to look like Windows 95. Ugh.

I think we'll see fewer and fewer ARM devices. Intel now has its Atom CPUs to a decent standard and has started putting them in mobile phones. Once Intel can release quad-core Atoms, they'll wipe ARM CPUs out of the Smartphone/Tablet market. Manufacturers want to work with x86 CPUs and Intel GPUs, not ARM and one of a dozen badly-supported mobile GPUs.

---

### Post by roelforg on 2012-05-19
> **3rdalbum said:**
> If he's running Ubuntu on it, then it is. Nobody would not know what ARM is and yet be running a downloaded copy of Ubuntu on their ARM system :-)

Note that some el-cheapo netbooks have ARM CPUs, but these all run either Windows CE, an old version of Android, or a horrible custom-built Linux that's been themed to look like Windows 95. Ugh.

I think we'll see fewer and fewer ARM devices. Intel now has its Atom CPUs to a decent standard and has started putting them in mobile phones. Once Intel can release quad-core Atoms, they'll wipe ARM CPUs out of the Smartphone/Tablet market. Manufacturers want to work with x86 CPUs and Intel GPUs, not ARM and one of a dozen badly-supported mobile GPUs.

[https://wiki.ubuntu.com/ARM](https://wiki.ubuntu.com/ARM)
Canonical is working on it, so it seems.

---

