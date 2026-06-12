---
title: "Which Ubuntu OS goes better if installed within Windows 8"
date: 2013-08-28
forum: New to Ubuntu
---

### Post by shuvadeepghosh on 2013-08-28
I am using Windows 8 in a HP laptop. Which of the various Ubuntu operating systems can be installed along with the Windows 8 in the laptop?

---

### Post by rock2 on 2013-08-28
Have you tried some live CD / USB to decide which version you like? Since its windows 8,  i am guessing its a new hardware and you will be practically able to run almost everything.

---

### Post by newb85 on 2013-08-28
As rock2 pointed out, the flavor of Ubuntu shouldn't make a difference.  Your hardware will likely support the more full-featured ones, like Ubuntu, Kubuntu, and Ubuntu Gnome Remix.

As a side note, your title reads "within Windows 8".  I strongly recommend that you *not* install *buntu using Wubi (a.k.a., the Windows Ubuntu Installer), but rather that you use a Live DVD/USB to install Ubuntu in a true Dual-Boot setup.  Wubi installs can be more problematic and more difficult to troubleshoot.

---

### Post by deadflowr on 2013-08-28
> **newb85 said:**
> As rock2 pointed out, the flavor of Ubuntu shouldn't make a difference.  Your hardware will likely support the more full-featured ones, like Ubuntu, Kubuntu, and Ubuntu Gnome Remix.

As a side note, your title reads "within Windows 8".  I strongly recommend that you *not* install *buntu using Wubi (a.k.a., the Windows Ubuntu Installer), but rather that you use a Live DVD/USB to install Ubuntu in a true Dual-Boot setup.  Wubi installs can be more problematic and more difficult to troubleshoot.

Yes, and at this point, WUBI is not even supported for Windows 8.
Though some people have tried.(What I've seen, the success rate is 50/50)
The recommendation is to install Ubuntu 64-bit version.(preferably a newer version, like 13.04)
[http://www.ubuntu.com/download/desktop/windows-installer](http://www.ubuntu.com/download/desktop/windows-installer)

---

### Post by rock2 on 2013-08-29
It just occured to me when [COLOR=#000000]newb85 quoted it. Are you trying to VBox or dual boot? If you are trying to install "within" Win 8 (as opposed to "along with"), i guess your choices are limited to VBox / KVM. [/COLOR]

---

### Post by Jonathan Precise on 2013-08-29
> **shuvadeepghosh said:**
> I am using Windows 8 in a HP laptop. Which of the various Ubuntu operating systems can be installed along with the Windows 8 in the laptop?

I recommend using Ubuntu 13.04 or Kubuntu 13.04. I have read in the release notes that "Install alongside" doesn't work on Ubuntu GNOME Remix 13.04:(, so I recommend you to NOT use Ubuntu GNOME (Ubuntu is fine:)), unless you use manual partitioning (for advanced users).

Also, as secure-boot support is still experimental, according to [COLOR=#008080]_UEFI Help_[/COLOR] in the links below.

---

### Post by squakie on 2013-08-30
Before you attempt an install (hopefully dual-boot -> where you'll get a menu where you can select ubuntu, windows, etc., as the operating system to boot), *PLEASE* search for posts by oldfred about installing with efi/uefi.  This is *VERY* important - so please do this before you install.

---

### Post by Jonathan Precise on 2013-08-30
In my signature, you can see "UEFI HELP 2". That's some advice from oldfred about Windows-8/UEFI cases.

---

### Post by squakie on 2013-08-30
Sorry - I missed that Jonathon!  ;)

---

