---
title: "Asus Eee PC 1025C UBUNTU gone wrong"
date: 2020-09-18
forum: New to Ubuntu
---

### Post by Andr_Almeida on 2020-09-18
Hi all,

A couple of years ago I tried to install Ubuntu in my old Eeepc to give a new life. It happens that half of the keyboard doesn't work and the wifi connection doesn't work either. 
Now I can't even boot to try to install Win 10 (which I wouldn't like to run on it anyway). I have pressed ESC and F2 dozens of times with no luck at all.

It would be really usefull to us now and I would appreciate some ideas about what I can do to get it doing basic browsing again.

Help a brother out, I gave it my best and I am going insane.

---

### Post by CelticWarrior on 2020-09-18
Welcome.

> [COLOR=#000000]It happens that half of the keyboard doesn't work and the wifi connection doesn't work either.[/COLOR]
So, is this a new thing? I mean, did everything worked before and now it doesn't?
If so then it's very likely an hardware problem. Reinstalling Ubuntu or installing another OS will NOT fix it.

How you access BIOS/UEFI settings doesn't change with Ubuntu or any other OS installed. What happens in a few laptops with UEFI and FastBoot setting enabled is that once it has an OS installed users may have to be way faster in pressing the key to access the settings but this isn't the case if you were able to do the same when you installed Ubuntu before. If you can't do it now, whatever the reason, it has NOTHING to do with Ubuntu.

---

### Post by Andr_Almeida on 2020-09-18
> **CelticWarrior said:**
> Welcome.


So, is this a new thing? I mean, did everything worked before and now it doesn't?
If so then it's very likely an hardware problem. Reinstalling Ubuntu or installing another OS will NOT fix it.

How you access BIOS/UEFI settings doesn't change with Ubuntu or any other OS installed. What happens in a few laptops with UEFI and FastBoot setting enabled is that once it has an OS installed users may have to be way faster in pressing the key to access the settings but this isn't the case if you were able to do the same when you installed Ubuntu before. If you can't do it now, whatever the reason, it has NOTHING to do with Ubuntu.

Thank you for your reply.

It isn't a new thing, no. Since I unninstalled Windows 7 Starter and installed Ubuntu the keyboard and wifi stopped working. Which from my basic understanding will be related to drivers.

About the BIOS, I did not know that. But all I can get from pressing F2 or ESC from the exact moment I press the power button is GNU GRUB and it does not show the USB where I have Win 10.

---

### Post by Holger_Gehrke on 2020-09-18
The key to call up the firmware can vary. On my EEE-PC  R101X it was the Delete-key. IIRC F8 was the key to get a boot device selection menu. You should really look for the manual for your device to find the right keys.

Holger

---

### Post by Andr_Almeida on 2020-09-18
> The key to call up the firmware can vary. On my EEE-PC  R101X it was the  Delete-key. IIRC F8 was the key to get a boot device selection menu.  You should really look for the manual for your device to find the right  keys.

It's definately ESC for the boot menu and F2 for the BIOS, just download the pdf manual. Thanks

---

### Post by CelticWarrior on 2020-09-18
Interesting...

So you used a computer for* a [COLOR=#000000]couple of years[/COLOR]*[COLOR=#000000] with [/COLOR]*[COLOR=#000000]half of the keyboard [/COLOR]*[COLOR=#000000]not working and no WiFi. Hopefully you were using and alternative internet connection. Yes, I'm being purposely let's say unpleasant in our interaction because you story sounds nonsensical and you came to an Ubuntu forum asking for help on how to install another OS, something also nonsensical from the get go.

Now, as additional information, the WiFi requiring additional proprietary drivers/firmware is quite plausible. Only half of the keyboard not working isn't, it has nothing to do with drivers or the OS. Have you tried an external (USB) keyboard? Results? Lastly, you may need to press F2 &#8203;**immediately** and **repeatedly** in order to access the settings. Of course, if F2 is one of the keys that don't work, there's no point in trying. Again, external keyboard...[/COLOR]

---

### Post by Andr_Almeida on 2020-09-18
> **CelticWarrior said:**
> Interesting...

So you used a computer for* a [COLOR=#000000]couple of years[/COLOR]*[COLOR=#000000] with [/COLOR]*[COLOR=#000000]half of the keyboard [/COLOR]*[COLOR=#000000]not working and no WiFi. Hopefully you were using and alternative internet connection. Yes, I'm being purposely let's say unpleasant in our interaction because you story sounds nonsensical and you came to an Ubuntu forum asking for help on how to install another OS, something also nonsensical from the get go.

Now, as additional information, the WiFi requiring additional proprietary drivers/firmware is quite plausible. Only half of the keyboard not working isn't, it has nothing to do with drivers or the OS. Have you tried an external (USB) keyboard? Results? Lastly, you may need to press F2 &#8203;**immediately** and **repeatedly** in order to access the settings. Of course, if F2 is one of the keys that don't work, there's no point in trying. Again, external keyboard...[/COLOR]

Oh no I don't think you are. Those are valid points.

I installed it, couldn't get it to work and left it in the corner. Attempted to boot it 2 or 3 times in between these years from searching online since today I decided to ask since I could not get a solution myself.
I never tried the keyboard, ESC and F2 work because I can see a kind of menu switching when Ubuntu starts if I press them.

But you already sorted one problem! I tried with the external keyboard and I got to access the boot options. 
Now I don't want to use Windows, the experience before wasn't good with 7 Starter and I don't believe it is going to be any better with Windows 10. It was just a desperate call to install something and get some life on it.

Do you have any sugestions on what Ubuntu version to install now that I can access the boot?

Many thanks for your time.

---

### Post by CelticWarrior on 2020-09-18
The latest, 20.04, perhaps not the standard Ubuntu, but one of the lighter flavors works better in old(ish) (and in your case very entry level even when it was released) hardware. Lubuntu, Xubuntu, Ubuntu-Budgie, even Kubunt are preferable to the standard Ubuntu (Gnome) because Gnome needs lots of resources and properly supported graphics.

Now that you have it working with an external keyboard it pretty much confirms an hardware problem. xUbuntu 20.04 won't solve that surely but it may now support your WiFi out of the box. If not please check the [Networking & Wireless]("https://ubuntuforums.org/forumdisplay.php?f=336") section, namely the sticky threads "Before posting..." and the one about Broadcom if applicable. It easy to find right away if you have one of those (Broadcom) that always need user installed proprietary drivers just by running 'lspci' in terminal. That being the case just follow the instructions. If not Broadcom then please follow the instructions of the "Before posting..." thread and post a new topic in that section.

---

### Post by Andr_Almeida on 2020-09-18
> **CelticWarrior said:**
> The latest, 20.04, perhaps not the standard Ubuntu, but one of the lighter flavors works better in old(ish) (and in your case very entry level even when it was released) hardware. Lubuntu, Xubuntu, Ubuntu-Budgie, even Kubunt are preferable to the standard Ubuntu (Gnome) because Gnome needs lots of resources and properly supported graphics.

Now that you have it working with an external keyboard it pretty much confirms an hardware problem. xUbuntu 20.04 won't solve that surely but it may now support your WiFi out of the box. If not please check the [Networking & Wireless]("https://ubuntuforums.org/forumdisplay.php?f=336") section, namely the sticky threads "Before posting..." and the one about Broadcom if applicable. It easy to find right away if you have one of those (Broadcom) that always need user installed proprietary drivers just by running 'lspci' in terminal. That being the case just follow the instructions. If not Broadcom then please follow the instructions of the "Before posting..." thread and post a new topic in that section.

Thank you so much for your help. You surely took me to the next level. I am now installing Lubuntu i386 because I could not find Xubuntu in 32 bits and see how it goes.

---

### Post by CelticWarrior on 2020-09-18
You don't need 32-bit. The CPU is 64-bit. That it came with 32-bit Windows doesn't matter.
The 32-bit architecture is slowly but surely dying. Even for Lubuntu the last release with 32-bit was 18.04 and because it's a flavor it has only 3 years of support. That means April 2021.

---

### Post by Andr_Almeida on 2020-09-18
> **CelticWarrior said:**
> You don't need 32-bit. The CPU is 64-bit. That it came with 32-bit Windows doesn't matter.
The 32-bit architecture is slowly but surely dying. Even for Lubuntu the last release with 32-bit was 18.04 and because it's a flavor it has only 3 years of support. That means April 2021.

I tried Xubuntu 64, it didn't allow me to instal. I guess the processor is 32 bit.

---

### Post by CelticWarrior on 2020-09-18
Maybe I googled something else or a later model with a 64-bit CPU...

Easy to find out though... In the live session, even during the installation, just open terminal and run 'lscpu'. In the first lines there should be one "CPU op-mode(s)". That one will tell you for sure ("32-bit" or "32-bit, 64-bit" are the options, the latter means a 64-bit CPU).

---

