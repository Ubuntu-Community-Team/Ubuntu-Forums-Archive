---
title: "How to get ASUS Eee PC 1015 Netbook to boot to bootable USB stick?"
date: 2011-10-19
forum: New to Ubuntu
---

### Post by swarup on 2011-10-19
Just bought a ASUS Eee PC 1015 Netbook. Here are the specs:

ASUS Eee PC 1015PEB-BK603 Refurbished Netbook - Intel Atom N450 1.66GHz, 1GB DDR2, 160GB HDD, 6-Cell, 10.1" SVGA, Windows 7 Starter, Black.

I've downloaded Ubuntu 11.10 and made a bootable USB pendrive using unetbootin. 

I've gone into the bios and reset the boot sequence so that the netbook looks first for a removable device, and only after that boots to its own HDD. But despite that, it continues to boot straight into ASUS Cloud, and then into Win 7 Starter, without seeing the USB stick.

I called ASUS tech support and asked how to get to a boot screen, and they said the only way they know is to reset the boot sequence in the bios. They did not know how to get to an actual boot screen which asks you directly what you want to boot to.

Anyhow, the resetting of the boot sequence should have worked. Help?

---

### Post by Harry.k on 2011-10-19
huh, worked in my 1000h with no problem. Maybe the img was corrupted. Try it on another computer.

---

### Post by Paqman on 2011-10-19
You need to press a key during boot to get the Eee PCs to show their boot menu. IIRC it's Esc. Stumped me for a bit the first time I tried to get Linux onto one of mine.

---

### Post by fooman on 2011-10-19
hello,  have you tried pressing the escape key as the computer boots? ....that may bring up a screen with options for which drive/device to boot from (works on my daughters eee,  but that is an older model).

---

### Post by mcduck on 2011-10-19
Somebody here had exactly the same problem with Eee PC 1015 just a few days ago, and the solution suggested to him was to boot to Windows, where there should be an icon that allows you to disable the Asus Express Gate. After that reboot the computer and press the Esc key to access the boot device selection.

Edit: Oh. It's actually you who posted that thread. You really shouldn't dual-post here, it's even against the forum rules (and pretty much counts as abusing the resources of the people who contribute their free time to help others on these forums)

Anyway: [http://askubuntu.com/questions/18763/install-10-10-netbook-edition-on-eee-pc-1015-using-a-usb-hdd]("http://askubuntu.com/questions/18763/install-10-10-netbook-edition-on-eee-pc-1015-using-a-usb-hdd")

---

### Post by Harry.k on 2011-10-19
try f2 when POST is shown

---

### Post by Harry.k on 2011-10-19
try f2 when POST is shown. This'll show the bios for most eeepc netbooks

---

### Post by swarup on 2011-10-19
> **mcduck said:**
> Edit: Oh. It's actually you who posted that thread. You really shouldn't dual-post here, it's even against the forum rules (and pretty much counts as abusing the resources of the people who contribute their free time to help others on these forums)

Anyway: [http://askubuntu.com/questions/18763/install-10-10-netbook-edition-on-eee-pc-1015-using-a-usb-hdd]("http://askubuntu.com/questions/18763/install-10-10-netbook-edition-on-eee-pc-1015-using-a-usb-hdd")

That thread was a different subject-- I always try to make a thread very specific. There I was just trying to get to the boot menu. Since then I have found out how to enter the bios and re-order the boot sequence so that "removable drive" boots first-- which should make it unnecessary to get to the boot menu. But it STILL isn't working, which doesn't make sense.

I have read through the link you referenced, and that may give some clue:
 
> # restart your netbook and hit ESC immediately. This will launch the BIOS settings manager.
# Here go to boot settings. Now you do not need to change the boot order to have "removable devices booted first". Rather, from the menu entry under boot sequence, enter the submenu "Hard drives" (or something like that) and here change the priority of the drives such that your USB stick is booted first, and not your HDD. It might be confusing that your stick is not handled as a removable device, so watch up at this point.

Funny thing is, when I go into the bios and enter the boot sequence option, I don't find a "submenu" for "hard drives" the way it says above. All I find is the option to set as desired, boot device priority  for the following three: HDD, CD-ROM, Removable Device. As mentioned, I placed "removable device" first, with no result.

---

### Post by swarup on 2011-10-19
Somehow, hitting the "ESC" key is now working, and it is sees the USB stick as a bootable device. We're in business! Ubuntu is installing ...

---

### Post by mcduck on 2011-10-19
> **swarup said:**
> Just after I hit F10 to exit and save changes to bios, I hit "ESC"-- and it went to the boot menu! And all that is listed there is the HDD. So the computer is not even seeing the USB stick as a bootable device. 

Does that mean something is wrong with the bootable USB I made? I'll try using it on a desktop I have-- that should work right?

The askubuntu instruction specifically mentions that the USB drive might not be recognized as a removable device but as a hard drive.

However if you only see one hard drive in the boot device selection, then the bootable USB drive probably wasn't created successfully. Since you have another computer around, you definitely should try if the USB stick boots on that one.

edit: too slow. But great that you got it working, and good luck with your Ubuntu install. :)

---

### Post by swarup on 2011-10-19
Hey, mcduck, I'm so sorry about any misunderstanding there may have been re this new thread...it was only done with the best intentions. And thank you so much, and also to everyone else, for the help! :p

---

### Post by mcduck on 2011-10-19
> **swarup said:**
> Hey, mcduck, I'm so sorry about any misunderstanding there may have been re this new thread...it was only done with the best intentions. And thank you so much, and also to everyone else, for the help! :p

No worries. :) Both threads started in quite similar way and probably could have been dealt in a single thread, but I understand that it was done with best intentions so it's fine by me.

---

