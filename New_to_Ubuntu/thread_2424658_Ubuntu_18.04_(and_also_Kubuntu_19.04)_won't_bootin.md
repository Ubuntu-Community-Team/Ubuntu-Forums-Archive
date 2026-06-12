---
title: "Ubuntu 18.04 (and also Kubuntu 19.04) won't boot/install from USB"
date: 2019-08-12
forum: New to Ubuntu
---

### Post by tamijo on 2019-08-12
I have downloaded Ubuntu, and installed it onto a USB drive using a suggested piece of software (Universal USB Installer). When I boot up my PC I get my Motherboard's splash screen, then an Ubuntu screen with some options such as "Run Ubuntu without installing" and "Install Ubuntu". Whenever I choose either of these options (or choose none and wait for it to boot automatically) I get a grey screen with a blinking cursor, then it goes blank. It is almost as if there is no output from the video card, as I get "No Signal" on my monitor.

When I remove the USB leave the computer to boot up Windows from the HDD, it works fine. If there's any information I can add that would help, please let me know. I have tried this with Kubuntu 19.04 first, then Ubuntu 18.04.3.

If this has been covered elsewhere then please just send me a link, but there's plenty of threads I looked at and couldn't understand at all. >_<

---

### Post by Autodave on 2019-08-12
First of all, let me suggest that you stay with the 18.04 release since that is a long term service release and you will not have to update it every 6 months.

Are you trying to dual boot this with Windows?  Is the Win10?  If so, did you turn off *fast boot* in the BIOS?

---

### Post by tamijo on 2019-08-12
I'm not entirely familiar with this kind of thing, but I have Windows on my HDD, and I'm attempting to boot from the USB drive instead, so I'm not booting Windows up at all. I am currently using Windows 7, though.

Also I will be sticking to 18. I went for Kubuntu 19 on a recommendation, and when I had this problem I decided to try Ubuntu 18 until I was at least familiar with it. (By which time I will not want to switch over, I imagine.)

---

### Post by GhX6GZMB on 2019-08-12
You're too impatient. The grey/black  screen phase during install may take up to half an hour depending on your hardware. There's a lot of analysing going on with checking out your hardware. Think about doing a Win 10 System Image, which takes up to three hours.

Ubuntu is unfortunately not very verbose.

---

### Post by irv on 2019-08-12
Try this. Make sure your PC is powered completely off. Boot as if you were going to boot into Windows. As your computer starts to boot you will see, "what you called your motherboard splash screen," you should see, "something like hit F2 or Del or whatever to go into setup. Once you are at the setup screen you need to look for fast boot option. Turn it off. Next look for Secure boot. You need to turn this off also. This will keep you from booting from the USB.
After changing these settings you need to save and reboot. This time put the USB stick in and boot into ubuntu. Select try before installing. Once it comes up, make sure you can get to your network and get on the Internet. If you can then you can install it. You will have the option to wipe the HD and install or install alongside Windows. Whatever you chose at this point can not be changed so make sure you have what you want.

---

### Post by QIII on 2019-08-12
> **ml9104 said:**
> You're too impatient. The grey/black  screen phase during install may take up to half an hour depending on your hardware. There's a lot of analysing going on with checking out your hardware.
Ubuntu is unfortunately not very verbose.

No.  With a graphical installation this is patently incorrect.

---

### Post by tamijo on 2019-08-12
I disabled fast boot, and it's doing the same thing.

I was already able to get to the Ubuntu screen where I can choose to install or try without installing.

---

### Post by tamijo on 2019-08-12
I attempted to go through the help section, and ended up attempting to just a command to boot up with. I decided to try to install, and got a message saying "Could not find kernel image: install". Is it possible that this means that my USB drive somehow doesn't have everything it needs to have on it? (Or am I just misunderstanding this?)

---

### Post by GhX6GZMB on 2019-08-12
> **QIII said:**
> No.  With a graphical installation this is patently incorrect.

I beg to differ. I've installed and reinstalled Lubuntu 19.04 perhaps 20 times in the last couple of months. The grey/black screen persists 15 minutes on my machine, but the installation completes in the end. There is no HDD nor DVD activity during this time.

---

### Post by tamijo on 2019-08-12
So the suggestion is genuinely just "Leave it running and see what happens"?

I suppose I'll give it a go and check on it before bed. >_<

---

### Post by CatKiller on 2019-08-12
Information on your hardware would have been very useful in trying to help you.

> **tamijo said:**
> I get a grey screen with a blinking cursor, then it goes blank. It is almost as if there is no output from the video card, as I get "No Signal" on my monitor.

This sounds exactly like what you'd see if you were trying to use Nvidia hardware without the benefit of the proprietary driver. That's not part of the install image yet, although it is planned. If that is the case for you, pressing *e* at the "Try Ubuntu" line would let you edit the startup options: replacing *quiet splash* with *quiet splash nomodeset* often helps in that situation. You may find that it works, but at a reduced resolution, with that option. Once you've got it installed, and the proprietary driver installed, you shouldn't need that option any more.

I would also recommend 18.04 over any non-LTS release, and I *much* prefer Kubuntu to Ubuntu.

---

### Post by tamijo on 2019-08-12
Oh wow, this worked!

So now that I've been able to get it to work on "try without install", how would I go about installing with this? Pressing e in the install line and doing the same/similar command?

I assume once I get to that point, I can then just go onto Nvidia's website, download the appropriate driver for my graphics card and it should work fine?

---

### Post by CatKiller on 2019-08-12
> **tamijo said:**
> Oh wow, this worked!

Glad to hear it.

> So now that I've been able to get it to work on "try without install", how would I go about installing with this? Pressing e in the install line and doing the same/similar command?

You'll need to do it each time that you boot from removable media (since that doesn't save anything). For example, if you were trying out a bunch of different desktop environments.

You'd probably need to do it once more after you've installed, from the GRUB menu. Unless you select to download the proprietary driver as part of the install process. After that, you're likely to have the proprietary driver installed, so it shouldn't be necessary.

> I assume once I get to that point, I can then just go onto Nvidia's website, download the appropriate driver for my graphics card and it should work fine?

No, don't download things from random websites. Linux isn't Windows. The file that you'd get from the Nvidia website is pretty hostile to new users, and doesn't play nice with the rest of the system. That's there for software packagers to play with.

There will be an Additional Drivers tool that will download the proprietary driver from the software repositories.

---

### Post by tamijo on 2019-08-12
So how do I get this driver that seems to be missing? Or are you saying that the problem will only persist while I'm booting from USB?

---

### Post by CatKiller on 2019-08-12
> **tamijo said:**
> So how do I get this driver that seems to be missing? Or are you saying that the problem will only persist while I'm booting from USB?

Yes, just until the proprietary driver can be installed: the open source nouveau driver isn't as good at sniffing out the correct resolution as the proprietary nvidia driver.

There's a box you can tick as part of the install process to automatically download and install the proprietary driver. If that doesn't work for whatever reason, you can install it - once you've booted into your install, since the live session can't remember anything - by using the Additional Drivers tool from your install. Or use a package manager. However you like, really.

You'll get the hang of software and packages once you've used Ubuntu for a bit.

---

### Post by tamijo on 2019-08-12
Thank you very much. I'm going to try it when I get back tomorrow evening. My concern is that I'll install it onto my HDD and I won't have a display.

I don't want to have to mess around trying to install my copy of Windows again.

---

### Post by CatKiller on 2019-08-12
After install is a bit easier: you can call up the Grub menu at boot with a keypress (I can't remember offhand if it's Shift or Esc), which will let you edit the startup line in the same way; or, since you know that you can successfully boot the live image now, you can use that to change the startup options permanently (well, or until you choose to change them again). And installing the proprietary driver as part of the install will *probably* work, anyway. It's only generally with especially new, or especially peculiar, hardware that people have reported problems here.

Let us know how you get on.

---

### Post by tamijo on 2019-08-13
So I used the "Try before install" option as you instructed, and then installed from that. I went through various menu screens, and opted to install Ubuntu without keeping my old files/Windows.

The screen went black shortly after, and has been so for about half an hour. I'm just leaving it at the moment, but if this sounds like a problem and anybody knows of the solution then feel free to drop it here. I'm going to leave it still just in case.

---

### Post by tamijo on 2019-08-13
It has now been 90 minutes with nothing to indicate it's doing anything. How long should I wait?

---

### Post by CatKiller on 2019-08-13
Were you doing anything at the point that the screen blanked? The monitor could simply have gone into power saving mode.

---

### Post by tamijo on 2019-08-13
I ended up leaving it while I went out. When I came back it seems to have worked. Thank you for your help!

---

### Post by oldrocker99 on 2019-08-13
Have you booted in UEFI mode? I would recommend Legacy, and it might boot up better.

Although there are Linux users who have succeeded with using UEFI, which is built for Windows anyway, Every installation I have tried with UEFI has failed to install GRUB, which results in an unbootable computer.

---

### Post by QIII on 2019-08-13
> **ml9104 said:**
> I beg to differ. I've installed and reinstalled Lubuntu 19.04 perhaps 20 times in the last couple of months. The grey/black screen persists 15 minutes on my machine, but the installation completes in the end. There is no HDD nor DVD activity during this time.

You may differ as you choose.  The eventual success of the installation notwithstanding, a blank screen with a blinking cursor indicates that something untoward has taken place if one is using a graphical installer with either Ubuntu or Kubuntu.  That may be anything from a bug in the installer to some difficulty with a driver.  In any case, it is not an expected behavior and expecting that everyone else's experience should mirror yours is a generalization based on one test case.  The OP's experience indicates only that yours is not a singular condition -- or it may just be similar by happenstance.  Lubuntu uses Calamares rather than Ubiquity as its installer, so there may be no relation at all.

@tamijo -- I'm glad you are up and running.  Just be aware that this was not the normal installation experience and waiting around because Ubuntu is slow was not the "solution".

---

### Post by haplorrhine on 2019-08-13
> **tamijo said:**
> It has now been 90 minutes with nothing to indicate it's doing anything. **How long should I wait?**

I only thought this was a fair question.  OTOH, tamijo never provided hardware information like RAM etc.

---

