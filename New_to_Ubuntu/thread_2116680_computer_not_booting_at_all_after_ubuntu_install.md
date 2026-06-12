---
title: "computer not booting at all after ubuntu install"
date: 2013-02-16
forum: New to Ubuntu
---

### Post by ChicagoTed on 2013-02-16
I'd like to start by saying that I know I'm a gigantic idiot.

So I have two HDDs, C: and F:. My Windows 7 is on a partition on C: and on F: is all of my Steam data and games. I installed ubuntu 12.04 using the installer on the ubuntu site and choose a 20GB sized partition on F: for ubuntu. That all went fine. Next, I choose the "Reboot Now" selection from the installer menu. This is where I messed up, I think.

The reboot was taking a very long time (30-45 minutes). I had no idea what to do. I didn't even get to the main boot menu where you select whether to boot with ubuntu or Windows 7. So I pulled out the battery.

On the second try, everything worked fine. I got to the big purple screen where it just says ubuntu and the five dots for loading (sorry if there's a technical term for this). The leading indicator filled up, and proceeded to take a very long time, again. This, also, may be where I messed up. I thought if I tried again, it might be able to boot properly. So I pulled out the battery. 

Now I've been at this stage for awhile: I hit the power button. Four buttons on the keyboard light up, but not the keyboard itself (this is the norm; the whole thing doesn't light up till I log in on windows). The screen has no indication of even being on. It's not a black screen, it's just off. The fans run. No sound occurs. If I want to try again, I have to remove the battery.

Is the only way to fix this to remove my F: drive?

edit: So I just heard the Windows 7 startup sound. I have no diea what to do now.

---

### Post by Mark Phelps on 2013-02-16
IF you actually installed to "F", you installed INSIDE Windows using Wubi, which uses the Windows boot loader to get initial access to the OS selection screen.  So, as long as you can't get that far, you won't be able to boot into Ubuntu, either.

Since you probably didn't make the Win7 Repair CD, you also don't have a disk to use to repair Win7.

If you're willing to pay a little money, you can purchase the ISO to create that repair CD from the link below:

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

Once you have that ISO, you will need to use a working PC to burn that to CD.  Then, boot from that CD and run Startup Repair three times -- that's right, three times -- as it often takes all three passes to completely repair Win7 boot problems.

---

### Post by ChicagoTed on 2013-02-16
> **Mark Phelps said:**
> IF you actually installed to "F", you installed INSIDE Windows using Wubi, which uses the Windows boot loader to get initial access to the OS selection screen.  So, as long as you can't get that far, you won't be able to boot into Ubuntu, either.

Since you probably didn't make the Win7 Repair CD, you also don't have a disk to use to repair Win7.

If you're willing to pay a little money, you can purchase the ISO to create that repair CD from the link below:

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

Once you have that ISO, you will need to use a working PC to burn that to CD.  Then, boot from that CD and run Startup Repair three times -- that's right, three times -- as it often takes all three passes to completely repair Win7 boot problems.

That's the thing, though--how do I get the system to boot from that CD if I can't even see the boot menu? Or anything? It's not as if the screen goes black, it just never turns on at any point during the boot.

---

### Post by Impavidus on 2013-02-17
You don't need the menu where you can choose between Ubuntu and windows (yet), this is about the BIOS. When you switch on the computer, press escape/delete/F12/F10/something else (it depends on your hardware) to get into a menu where you can select from which medium to boot. This is before your computer tries to load an OS, so trying to install Ubuntu cannot have damaged it (only flashing the BIOS can, but even that's unlikely).

I presume this means you didn't try to install Ubuntu from a live disk (for which you'd have to boot from a dvd/usb), so this is indeed a wubi install.

I'm curious, most computers show a vendor's splash screen as the first thing after powering on, even before trying to find a boot medium. You say it isn't there. Was there such a screen in the past? If so, there's something wrong with your graphics on a very low level. Maybe try a cold-finger reset: [http://ubuntuforums.org/archive/index.php/t-2093824.html](http://ubuntuforums.org/archive/index.php/t-2093824.html), fourth post. Things may have gone wrong because of your hard resets. Clearly your computer does boot, as you heard the windows sound.

---

### Post by Sef on 2013-02-17
> I'd like to start by saying that I know I'm a gigantic idiot.

You are not an idiot. If you never make mistakes, you will never learn.

---

### Post by Mopar1973Man on 2013-02-17
> **Sef said:**
> You are not an idiot. If you never make mistakes, you will never learn.

+1

So very true!

---

### Post by Mark Phelps on 2013-02-17
> **ChicagoTed said:**
> That's the thing, though--how do I get the system to boot from that CD if I can't even see the boot menu? Or anything? It's not as if the screen goes black, it just never turns on at any point during the boot.

That's typically because there is often a BIOS setting that hides the POST (Power On Self Test) messages; thus, instead of getting a bunch of scrolling text messages, you get a LOGO screen, or in your case, nothing.

You would need to get into the BIOS, find that setting, and turn it off. I don't know the make or model of your PC, so my guess is you would press the Del key, or one of the Function keys, to get into the BIOS.

---

