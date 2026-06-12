---
title: "Can't access BIOS"
date: 2013-12-30
forum: New to Ubuntu
---

### Post by courseinmiracles2 on 2013-12-30
Hi,
I am using a toshiba L-650 and running 13.10.

I have tried starting the computer then using F2 and also starting the computer ESC then F1 and I have also tried using F12

The start up sequence with Ubuntu doesn't ever give me an opportunity to enter the BIOS. The Toshiba support site says it should be either F2 OR ESC then F1.
 I have be trying restart and shutdown then start nothing seems to be working.

Any ideas

---

### Post by sammiev on 2013-12-30
> **courseinmiracles2 said:**
> Hi,
I am using a toshiba L-650 and running 13.10.

I have tried starting the computer then using F2 and also starting the computer ESC then F1 and I have also tried using F12

The start up sequence with Ubuntu doesn't ever give me an opportunity to enter the BIOS. The Toshiba support site says it should be either F2 OR ESC then F1.
 I have be trying restart and shutdown then start nothing seems to be working.

Any ideas

I have a Toshiba L-650 and F2 is to be pushed when you first see the the Toshiba screen to get into the BIOS.

---

### Post by courseinmiracles2 on 2013-12-30
Hey Sam,
Yeah...I don't get a toshiba screen. I get a flat purple screen THEN the ubuntu logo with the "loading dots" Then my desktop.

Do you have a terminal command for changeing the boot sequence?

---

### Post by courseinmiracles2 on 2013-12-30
UPDATE:
I tried using "boot-manager" and was not able to get any change.

I also installed "grub-customizer" and that just opened a window to ask which version of ubuntu I wanted to use.

Can anyone tell me if it's my toshiba or is it Ubuntu???

Pretty strange, this is usually a simple thing to do...change the boot sequence...or at least what I thought, Ha!

---

### Post by sammiev on 2013-12-30
I tried to get mine to do the same. No luck, I will try to look at it again. bbl

---

### Post by sammiev on 2013-12-30
OK I was able to get mine to do the same as yours and return it back to normal.

After you press the power button start to tap the F2 key until you see the BIOS screen. Go into Advance and Boot Speed, Press F5 to change it from Fast to Normal. Save and Exit.

---

### Post by courseinmiracles2 on 2013-12-30
Nope.
Still can't get anything even close to it.
Does anyone know how to program "grub-customizer"?

Thanks for the follow up Sam.
Not sure where to turn next...

---

### Post by lisati on 2013-12-30
> **courseinmiracles2 said:**
> I don't get a toshiba screen. 
Are you restarting your computer or are you waking it from sleep or hibernate? My day-to-day machine is a Toshiba (different model), and only shows the Toshiba splash screen if I've turned the machine off and then on again or if I've restarted it. The splash screen doesn't show when waking it from sleep or suspend.

---

### Post by jeffreyjensen1989 on 2013-12-30
Do you have a "fn" key next to the super key? I've had issues before with laptops where I had to use the function key even though it wasn't like that by default

---

### Post by courseinmiracles2 on 2013-12-30
@lisa Yes, I am doing a complete shutdown every time.

@Jeffery it does have that "FN" on the keyboard....Are you saying I should try hit that at start up OR using it as well as ...F2?

Thanks for the feed back

---

### Post by courseinmiracles2 on 2013-12-31
Ok, so this finally solved it for me, from toshiba

Issue
After "Fast Boot" has been enabled, you cannot  access the BIOS setup during power on .  The machine will bypass "Press  F2 to access Setup Utiltiy and F12 for Boot Menu" prompt.
This is a bigger issue if the hard drive crashes and access to Windows is not possible.   
 
ResolutionFast Boot can be enabled or disabled in the BIOS setup, or in HW Setup under Windows.
If  you have Fast Boot enabled and you want to get into the BIOS setup.  ** Hold down the F2 key,_THEN_ power on**.  That will get you into the BIOS  setup Utility.

You can disable the Fast Boot Option here.  You will need to **_disable Fast Boot_** if you want to use the F12 / Boot menu.   

So thanks for your feedback, I hope this helps some else.

Cheers

---

### Post by sammiev on 2013-12-31
So I guess my post up above works as that is what I told you to do but tap the F2 key until you saw the BIOS screen. :) Got 3 Toshiba L650s and it worked for all of them.

---

### Post by courseinmiracles2 on 2013-12-31
Yes Sam,
You were right. I just wasn't pressing the F2 BEFORE i hit the start button AND I didn't know about (forgot really) disabling FAST BOOTING Because it will only boot from the HD when it is enabled. So we live and learn and forget and should write **** down.;)

Thanks for your help and Happy New Year!

---

### Post by willzhigaylo on 2013-12-31
Mark thread as solved.

---

### Post by courseinmiracles2 on 2013-12-31
A quick update:
After changing the boot sequence I found it was still not booting from the cd. This is what I found on the toshiba site;

You must change from _UEFI_ to _CSM_ in the Advanced settings section.
  
    UEFI = Unified Extensible Firmware Interface (replaces the traditional BIOS)
  
    CSM = Compatibility Support Module (simulates the BIOS)

Just to cover all bases.

---

