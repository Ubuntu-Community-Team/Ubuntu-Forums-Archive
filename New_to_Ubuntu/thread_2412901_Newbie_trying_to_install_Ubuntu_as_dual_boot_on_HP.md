---
title: "Newbie trying to install Ubuntu as dual boot on HP Elitebook 745 G2 with Windows10 us"
date: 2019-02-18
forum: New to Ubuntu
---

### Post by handyboy on 2019-02-18
I have an HP Elitebook 745 G2 with Windows10 Home using UEFI that was working OK before I loaded Ubuntu to it.
What I have done:
1. Downloaded Ubuntu 18.4.2 LTS to my other HP PC (x360).
2. Used Rufus to create a USB Stick (8GB Toshiba).
3. on the Elitebook, plugged in USB stick and pressed Power Button to boot.
4. Installed Ubuntu (or thought I had done so). I used the option to update as installing but had no Internet connection as I normally use Wi-FI. I got a message advising that the WiFi Adaptor could not be found.  I looked for help on ubuntuforums and realised that I needed to update my kernel. I did this update (ran *sudo apt-get install bcmwl-kernel-source*, but this did not help. I tried many different things from the ubuntu forum but to no avail.  Eventually I clossed the PC down to reflect on my problems.
5. When I tried to REBOOT the PC would not boot and looped flashing a message too fast to read.
6. Pressed and held Power Button to kill the machine.  Read forum to find I needed to use F12 key to get to boot stuff.
7. Tried to reboot after 2 minutes using the USB stick again.
8. Rebooted with USB stick, pressed F12 (many times) and got to a Boot Error message. Tried all the options and eventually have been able to get Windows10 to work again but only with the following process: Remove USB stick. Press Power Button and then F12 to get to Boot Error. Press enter, then F9 and then choose *.acpi---- *from two options to get to EFI File Navigator where I choose *Boot* from EFI file. then choose *EFI* at the \ list. Choose Microsoft from the \EFI list and then *BOOT *from the \EFI\Microsoft list and then choose *bootmgfw.efi* from the long list at \EFI\Microsoft\Boot list.:D

Now I need to find out how to fix this unhappy mess - my objective is to have a dual boot pc with both Windows10 and Ubuntu that does not require the long-winded approach detailed above.
Please advise bearing in mind that I am an Ubuntu newbie and not that good with Windows at the OS level.

Thanks in advance

---

### Post by oldfred on 2019-02-18
Have you updated UEFI from HP? Should be done even if not installing Ubuntu.
If SSD also update firmware.

Did you use Windows to shrink the NTFS partition to make space for Ubuntu? And reboot Windows so it can run chkdsk?
Is drive in AHCI mode in UEFI.
Do you have UEFI Secure Boot on?
Do you have really good backups of Windows? Do not proceed unless you do.

System is UEFI, did you boot Ubuntu installer in UEFI boot mode, so it would install in UEFI boot mode? If you boot in BIOS mode, it installs in BIOS mode.

While many systems use f12, HP uses different keys.
I think it is Escape & f9 and escape f10? check your manual. 

If WiFi not working best to use hardwired connection to install and get correct driver for your wireless.

This will need Internet:
       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) 
    
More details on UEFI install in link in my signature.

Issues often common by brand. Bigger difference by brand if AMD or Intel based.
So these may be similar:
       HP Envy 17 - 18.04.1 works See post #3
[https://ubuntuforums.org/showthread.php?t=2392797](https://ubuntuforums.org/showthread.php?t=2392797)
HP Pavillion X360 13-a220nw
[https://ubuntuforums.org/showthread.php?t=2359510](https://ubuntuforums.org/showthread.php?t=2359510) & 
[https://ubuntuforums.org/showthread.php?t=2407615](https://ubuntuforums.org/showthread.php?t=2407615)
[https://ubuntuforums.org/showthread.php?t=2406993](https://ubuntuforums.org/showthread.php?t=2406993)
HP OMEN 15-ce0xx
[https://ubuntuforums.org/showthread.php?t=2407145](https://ubuntuforums.org/showthread.php?t=2407145)
HP UEFI boot order change with efibootmgr does not stick, but change in HP's UEFI does work
[https://ubuntuforums.org/showthread.php?t=2390309](https://ubuntuforums.org/showthread.php?t=2390309)

---

### Post by richard378 on 2019-02-23
One question. Do you have a optane hard drive?  If you do then you can't duel boot.

---

### Post by oldfred on 2019-02-23
You can still change to AHCI.

       Intel Optane - See Intel response that no performance difference between RAID & AHCI.
[https://communities.intel.com/thread/121155](https://communities.intel.com/thread/121155)

---

### Post by handyboy on 2019-02-23
Hello OldFred and Richard378 - No I do NOT have an optane hard drive.

OldFred,  [COLOR=#00ff00] THANK YOU[/COLOR] for your detailed reply.
I think I have eventually completed all the suggestions you made in your original detailed reply. I can now get Windows10 to boot up normally, I can get Ubuntu by pressing [esc] at bootup and selecting F9 to Select Boot Options.  I then select ubuntu as the Boot Option and then ubuntu at the GNU GRUB screen.
I sorted the lack of WiFi by using a wired connection and then selecting my WiFi and setting it to automatically be used.

[COLOR=#ff0000]NOTE TO OTHER NEWBIES:[/COLOR]
If only I had read the whole reply through AND checked the links AND THEN learned how to do the tasks I had not done before ( I'm not a Windows or PC guru ), I think I would have saved myself quite a lot of time.

---

### Post by oldfred on 2019-02-23
If it is working, please change to [Solved], so others can find thread.

---

### Post by handyboy on 2019-02-24
Thanks again oldfred !):P

---

