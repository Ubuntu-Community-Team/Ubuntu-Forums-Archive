---
title: "Cannot boot to ubuntu automatically boots to windows"
date: 2015-07-03
forum: New to Ubuntu
---

### Post by mark226 on 2015-07-03
So I'm not sure what I did but my partition that had ubuntu 14.04 doesn't work now, it auto boots to windows which it previously didn't do, instead I had the boot manager.

So using my usb with ubuntu installed it I went and tried boot manager, it said it succeeded but it still booted to windows. So I looked at the pastebin which on the last few lines said this:

If your computer reboots directly into Windows, try to change the boot order in your BIOS.
If your BIOS does not allow to change the boot order, change the default boot entry of the Windows bootloader.
For example you can boot into Windows, [COLOR=#AA22FF]**then **[/COLOR][COLOR=#AA22FF]type [/COLOR]the following [COLOR=#AA22FF]command [/COLOR]in an admin [COLOR=#AA22FF]command [/COLOR]prompt:
bcdedit /set [COLOR=#666666]{[/COLOR]bootmgr[COLOR=#666666]}[/COLOR] path [COLOR=#BB6622]**\E**[/COLOR]FI[COLOR=#BB6622]**\u**[/COLOR]buntu[COLOR=#BB6622]**\s**[/COLOR]himx64.efi

so did what it said and it didn't work, I now do not know how to change my boot since that one line of code overrides it.

Now I'm down to asking for help on the forums.

So yeah, hopefully I could get some help on this, since I need it for uni work.

Here is the ubuntu pastebin:

[http://paste.ubuntu.com/11813751/](http://paste.ubuntu.com/11813751/)

If anyone wants to know specifics about my computer please ask and i'll update this.

---

### Post by leunam12 on 2015-07-03
I am by no means an expert on this matter but I would boot into Windows then press WINDOWSKEY+R and type```
shutdown -s -f -t 00
```and press ENTER; your computer will shut down. Then start it again and go to BIOS settings and make sure that secure boot is disabled, also in some motherboards you have to have fastboot disabled.

---

### Post by jeff131 on 2015-07-03
I will do my best to help you with this. Are you using Windows 8? I will give you more information once you answer this. If so, follow these steps.

1. Go to PC settings from the search bar.

2. Go to Update and Recovery

3. Next, go to recovery.

4.  Click on advanced boot, and select your USB

I think this should work, but if you already installed it there should be a drive saying, "ubuntu"

I hope this helped, because I am pretty new to Ubuntu.

---

### Post by cariboo on 2015-07-03
You should be able to get into the boot manager by pressing a specific key combination. On my Toshiba satellite, I have to hold down the zero key while booting, then press enter when presented with a window asking me what I want to do. The Toshiba boot manager has about 8 different boot choices, including WIndows 8.1, Ubuntu, boot from USB and boot from the network.

When I installed Vivid the first time I assumed that grub would take over booting the system, but it was a no go. I have to use the boot manager every time, unless I want to boot directly into Windows 8.1. Once you figure out how to boot with UEFI, things work just like normal, I converted my desktop system to UEFI, with no windows installed, and it boot to grub normally.

It seems that dual booting with Windows always seems to make things more complicated.

---

### Post by oldfred on 2015-07-03
I see you have the 25_custom that Boot-Repair creates. Did you use Boot-Repair a year or more ago as its fix back then was to copy grub or shim into the /EFI/Microsoft folder and rename it to bootmgfw.efi which is the Windows boot file. Then default boot of Windows actually booted grub.

That was an early fix, which we do not recommend anymore, as both a Windows update overwrites the Windows efi file or a grub update may need it copied again if version is enough different.

And HP's have UEFI that use description in UEFI and only allowed "Windows" as bootable named device. But hard drive boot entry works so now the suggestion is either as Boot-Repair suggested with adding an entry to Windows BCD or copying grub or shim into /EFI/Boot and rename it to bootx64.efi which is a hard drive entry.

You also have all the HP entries in you grub menu. You probably do not need them. You can back up 25_custom and edit at will to remove most of those entries.

       # Edit 25_custom entries created by Boot-Repair:
sudo cp -a /etc/grub.d/25_custom /etc/grub.d/25_custom_backup
# turn off execute bit or it will run backup also
sudo chmod a-x /etc/grub.d/25_custom_backup
gksudo gedit /etc/grub.d/25_custom
# Then do:
sudo update-grub

---

### Post by mark226 on 2015-07-03
Hey thanks for the help guys, first off I would like to say that both fast boot and secure boot is disabled but from what leunam12 said ill still give it a go, anything is better at this point, oh and sorry I forgot to point out yeah I'm using Windows 8, Ubuntu was working fine for about two weeks now.

Next I will try Jeff131's steps and get back to you guys on what happens.

Also cariboo, I have been in the bios settings after using the command line I put in my first post and changed the boot order to usb but it still disregards those changes, and for me the boot manager (if you are talking about grub boot manager) it normally pops up and I can select what I would like to boot to windows or ubuntu. Oh and for me to get into the bios settings I need to hit the f10 key. Though I can still try and give it another go maybe it didn't save.

Sorry oldfred not sure what 25_custom is but I didn't get ubuntu working on this laptop until a few weeks ago, let alone a year ago. I will also try editing what you said but at this point I cannot get into ubuntu at all, unless there is some other way of getting into ubuntu without the boot manager that I am not aware of.

Thanks again for the replies I will try all of them and get back to you with the results.

---

### Post by mark226 on 2015-07-04
Okay so I've tried all solutions everyone gave me and from what I can tell Ubuntu now works,

Though I had to just delete the partition and re-install Ubuntu, now for all the solutions so far

the boot manager for my laptop says Usb is first in line but it ignores it regardless

I went into advance settings for booting to Ubuntu and yeah it seemed like I couldn't boot so I just went ahead and reinstall Ubuntu

Finally I couldn't do what you wanted oldfred, it seemed like I couldn't change settings at the time, due to using the usb live boot, I could probably try now and I assume it would work, I'll get back to you on that.

So in the end I got it to work but only through a very tedious way, Well basically I boot up my laptop it boots immediately to windows I go into pc settings and pick to boot to Ubuntu.

If there really is no real solution then I guess I'll have to live with that.

Edit:

So I tried oldfred's solution after I used boot repair and well it didn't seem to do much, but I can now successfully boot to manager and pick to go Ubuntu or Windows, though I have a longer list than I originally did (It was about 4 from what I remember last time now it's 10+)

---

### Post by oldfred on 2015-07-04
I am not sure if Boot-Repair still creates 25_custom or not. The edit instructions above were from inside a working Ubuntu.
If from a live installer you would have to mount the install partition first, so path is different.

Post new link to Summary report and we can suggest what to change. You may just need to houseclean old kernels. Or if Boot-Repair did add a 25_custom for all the HP efi files you may want to remove some or most of them.

---

