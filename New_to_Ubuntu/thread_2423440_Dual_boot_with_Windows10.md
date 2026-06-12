---
title: "Dual boot with Windows10"
date: 2019-07-23
forum: New to Ubuntu
---

### Post by mazzone10 on 2019-07-23
Hello,

After suffering the horrors of the last Windows 10 update, I've decided to switch over to Ubuntu. I'm extremely new to this so please be gentle....

I only need Windows 10 to play FM2019 so I've decided to keep that and use Ubuntu for everything else, so a dual boot. I downloaded Ubuntu 19.04 onto a memory stick and installed it. The issue I have is that Windows 10 does not recognise the Ubuntu installation, either in the options in control panel or from a restart (It just boots straight into Windows 10 with no option to select the OS).

I'm sure this is an obvious error so hope someone can help.....


Many thanks,

Mark.

---

### Post by Impavidus on 2019-07-23
Windows only recognises Windows, that's normal. But the computer should be willing to start the Linux boot loader, which will offer a choice between Ubuntu and Windows. Unfortunately, not all computer manufactures adhere to the standards, so it may be necessary to do some tweaks.

Can you tell a bit more about the hardware? Brand, model? Did you install in UEFI or legacy mode? Also try [Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) using your live disk (the one you used for installation). Don't run the recommended repair, just create a summary. That can tell us if something was installed the wrong way.

---

### Post by richard378 on 2019-07-24
That can proberbly be fixed by changing the boot order in your bios.  It problerbly requires you to change the boot priority in Bios to the Ubuntu Grub installer.

---

### Post by Rubi1200 on 2019-07-24
Have you checked whether hibernation is enabled?

Often, the solution to some of these types of issues is to disable secure boot and/or fast startup in Windows.

Might be worth trying to see if it resolves the issue.

Boot priority, as mentioned, needs to be checked as well.

---

