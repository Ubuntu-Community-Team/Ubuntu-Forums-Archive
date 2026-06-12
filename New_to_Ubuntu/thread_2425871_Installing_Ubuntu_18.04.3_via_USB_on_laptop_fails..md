---
title: "Installing Ubuntu 18.04.3 via USB on laptop fails."
date: 2019-09-01
forum: New to Ubuntu
---

### Post by ceegen on 2019-09-01
Tl;dr: Have a Dell Inspiron 15 7000 (model 7567, from 2017) Gaming laptop, and it currently can't run Ubuntu.

Simplified CPU specs
CPU: Intel Core i5-7300HQ
GPU: NVIDIA GeForce GTX 1050 Ti (4GB GDDR5)
RAM: 8GB DDR4, 2400MHz
HDD: 256GB SSD

Attempted the USB install method. Couldn't boot from the USB.

```
Console output #1:
Failed to open \EFI\BOOT\mmx64.efi - Not Found
Failed to load image \EFI\Boot\mmx64.efi: Not Found
Failed to start MokManager: Not Found
Something has gone seriously wrong: import_mok_state() failed
: Not Found
```


[https://askubuntu.com/questions/1085550/cant-install-ubuntu-18-10-on-xps-15-efi-boot-mmx64-efi-not-found](https://askubuntu.com/questions/1085550/cant-install-ubuntu-18-10-on-xps-15-efi-boot-mmx64-efi-not-found) <-- Tried this.

Got Ubuntu to load. Was able to connect to the internet to download updates while installing, even. (Had to allow networking in the bios first, but it worked). Had errors upon first loading, though.

```
Console output #2:
40110a
[ 0.149517] mce: [Hardware Error]: TSC 0 ADDR fef1ffc0 MISC 7880010086
[ 0.149520] mce: [Hardware Error]: PROCESSOR 0:906e9 TIME 1567293075 SOCKET 0
 APIC 0 microcode b4
[ 0.149524] mce: [Hardware Error]: CPU 0: Machine Check: 0 Bank 7: ee20000000
40110a
[ 0.149525] mce: [Hardware Error]: TSC 0 ADDR fef1ce40 MISC 47880010086
[ 0.149528] mce: [Hardware Error]: PROCESSOR 0:906e9 TIME 1567293075 SOCKET 0
 APIC 0 microcode b4
[ 7.985471] tpm_crb MSFT0101:00: [Firmware Bug]: ACPI region does not cover t
[ 7.985531] tpm_crb MSFT0101:00: [Firmware Bug]: ACPI region does not cover t
[ 8.033448] Couldn't get size: 0x800000000000000e
[ 8.655302] [drm:lspcon_init [1915]] *ERROR* Failed to probe lspcon
[ 8.655333] [drm:intel_ddi_init [1915]] *ERROR* LSPCON init failed on port B
```

 Was done installing, when it asked me to restart. Pressing the restart button in the window dialogue nearly-instantly froze the screen/mouse for about 20 minutes, after which it went to the console. It was still displaying the above console output from the initial console window when starting up the system with the USB stick. Let the laptop run for about 40 more minutes before the console spit out this:
(The first line is me unplugging the mouse)

```
Console output #3:
[ 1318.375359] usb 1-1: USB disconnect, device number 2
[ 2239.500196] printk: systemd-shutdow: 39 output lines suppressed due to ratelimiting
[ 2239.503267] print_req_error: I/O error, dev sdb, sector 461180 flags 80700
[ 2239.503302] print_req_error: I/O error, dev sdb, sector 461180 flags 0
[ 2239.503338] print_req_error: I/O error, dev sdb, sector 461180 flags 0
[ 2239.503367] print_req_error: I/O error, dev loop0, sector 460328 flags 0
[ 2239.503419] print_req_error: I/O error, dev sdb, sector 461180 flags 0
[ 2239.503434] SQUASHFS error: squashfs_read_data failed to read block 0xe0c49d0
[ 2239.503447] print_req_error: I/O error, dev loop0, sector 460330 flags 0
[ 2239.503465] SQUASHFS error: Unable to read data cache entry [e0c49d0]
[ 2239.503493] print_req_error: I/O error, dev sdb, sector 461180 flags 0
[ 2239.503508] SQUASHFS error: Unable to read page, block e0c49d0, size b3bd
[ 2239.503534] print_req_error: I/O error, dev loop0, sector 460332 flags 0
[ 2239.503564] SQUASHFS error: Unable to read data cache entry [e0c49d0]
[ 2239.503580] print_req_error: I/O error, dev sdb, sector 461188 flags 0
[ 2239.503588] SQUASHFS error: Unable to read page, block e0c49d0, size b3bd
[ 2239.503614] print_req_error: I/O error, dev loop0, sector 460334 flags 0
[ 2239.503633] SQUASHFS error: Unable to read data cache entry [e0c49d0]
[ 2239.503668] SQUASHFS error: Unable to read page, block e0c49d0, size b3bd
[ 2239.504347] SQUASHFS error: squashfs_read_data failed to read block 0xdc3c936
[ 2239.504372] SQUASHFS error: Unable to read data cache entry [dc3c936]
[ 2239.504391] SQUASHFS error: Unable to read page, block dc3c936, size c8e8
[ 2239.504418] SQUASHFS error: Unable to read data cache entry [dc3c936]
[ 2239.504438] SQUASHFS error: Unable to read page, block dc3c936, size c8e8
[ 2239.504462] SQUASHFS error: Unable to read data cache entry [dc3c936]
[ 2239.504481] SQUASHFS error: Unable to read page, block dc3c936, size c8e8
[ 2239.504768] SQUASHFS error: squashfs_read_data failed to read block 0xd921922
[ 2239.504790] SQUASHFS error: Unable to read data cache entry [d921922]
[ 2239.504809] SQUASHFS error: Unable to read page, block d921922, size f6a5
[ 2239.504838] SQUASHFS error: Unable to read data cache entry [d921922]
[ 2239.504857] SQUASHFS error: Unable to read page, block d921922, size f6a5
[ 2239.504881] SQUASHFS error: Unable to read data cache entry [d921922]
[ 2239.504900] SQUASHFS error: Unable to read page, block d921922, size f6a5
[ 2239.506643] systemd-shutdown[1]: Syncing filesystmes and block devices.
[ 2239.507770] systemd-shutdown[1]: Sending SIGTERM to remaining processes...
[ 2239.510863] systemd-journald[1041]: Received SIGTERM from PID 1 (systemd-shutdow).
[ 2329.511119] systemd-shutdown[1]: Sending SIGKILL to remaining processes...
[ 2329.516707] systemd-shutdown[1]: sending SIGKILL to PID 1492 (Xorg).
[ 2329.517586] systemd-shutdown[1]: Sending SIGKILL to PID 2202 (busybox).
[ 2329.518639] systemd-shutdown[1]: Sending SIGKILL to PID 11684 (WebKitNetworkPr).

```
At which point I had to turn it off because it was the end of my shift, so I held down the power button. Upon powering back up, the laptop made it to the desktop just after entering a password, the mouse pointer and default background loaded, then locked right up. Had to power off. Tried again starting it back up, same thing.

Tried to reinstall and got the console output #1 again. Same fix got it to boot up from the USB again. Attempted to reinstall without the "Raid" [edit: in the bios] option checked. Same problem though.

Are there any tests I can run from the live USB to test or fix something? Can't promise anything, the thing might freeze up on me. Did once when I was attempting to do something, at which point I came here to post this.

---

### Post by guiverc on 2019-09-01
Did you verify your download? and the write to install media?
There is a "Check disc for defects" option when you boot the Ubuntu install media; and I suggest you use it.

Squashfs errors are due failures to read data on the install media (or hardware failure), but I'm betting it was a bad download, or bad write-to-install media, and the 'check disc for defects' will confirm this.
[I]
ps: note the "check disc for defects" is the install media, be it on cd/dvd/thumb-drive or another media, and does not mean your hdd/ssd.
[/I][https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)
&#8203;[https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0](https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0)

---

### Post by ceegen on 2019-09-01
Yes, I am 100% sure. Even bought new USB sticks just to make sure it wasn't a failing USB stick.
Re-downloaded and tried, same problem.

---

### Post by wildmanne39 on 2019-09-01
Hello and welcome to the forum.

*Thread moved to **New to Ubuntu a more appropriate sub-forum**.*

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by guiverc on 2019-09-01
Did you run the `check disc for defects`?

Squashfs errors means the USB-thumb-drive failed, your USB device is faulty, or the data on the thumb-drive was faulty (ie. your software that wrote the ISO did a bad job, or wrote a bad ISO because your download was faulty & unvalidated).

The faulty device is `sdb`, you can see IO errors everywhere, so it's hardware or bad data written (bad data written to the media is the easier option to fix & confirm).  The secors also tell you which parts of device are bad.

---

### Post by ceegen on 2019-09-01
I wrote the ISO to the USB, from two different downloads, to two different USB sticks, one was brand new.
Used 'sudo dd if=~/ubuntu18.04.iso of=/dev/sdb status=progress' on another linux system to make the boot sticks.
None of the drives have errors: the primary machine, nor the target machine, and none of the USB drives.

---

### Post by guiverc on 2019-09-01
What you just gave doesn't confirm either a valid ISO download (refer to how-to-verify link I already provided), or the write-to-media was valid (refer to installation/CDintegritycheck link I already provided).  The second validation-check will catch most bad downloads also, however it may appear differently on your screen to how it appears in the wiki page I provided.  On UEFI systems there is no graphic at all (it can resemble a grub screen), on some boxes you get a keyboard-in-rectangle & person-in-circle where you need to press a key for menu to appear (logo will be different to my provided link), and is my suggestion. It checks for Squashfs errors as presented in your first post on device sdb (which I've assumed was your installation device).

---

### Post by ceegen on 2019-09-01
It installed with the errors from console output #2, which are probably causing read/write errors.

[edit] also, it installed just fine on another laptop.... So.

---

### Post by oldfred on 2019-09-01
Dell typically needs UEFI update & SSD firmware update if SSD. Even if newer system.
You do have to have drives in AHCI mode, not RAID nor Intel RST. But have to install AHCI drivers into Windows first if dual booting.
If dual booting you need to have Windows fast start up/always on hibernation off.
With nVidia, you normally need nomodeset boot parameter for both installer & first boot. Then install nVidia driver using ppa. Very newest Ubuntu will install nVidia driver if update selected during install.

Details & links to more info in link in my signature.

Other Dell 7000, but issues common across almost all models of Dell. Bigger issues if model based on AMD or Intel.
       DELL Inspiron 15 7577 18.04 needed boot parameters
[https://ubuntuforums.org/showthread.php?t=2386049](https://ubuntuforums.org/showthread.php?t=2386049)
Post installation issues Ubuntu 18.04-Dell inspiron 7559
[https://askubuntu.com/questions/1072382/post-installation-issues-ubuntu-18-04-dell-inspiron-7559](https://askubuntu.com/questions/1072382/post-installation-issues-ubuntu-18-04-dell-inspiron-7559)
Dell 7559 Install 16.04 or 18.04, best to skip all 16.04 info
[https://connorkuehl.github.io/dell-inspiron-7559-linux-guide/index.html](https://connorkuehl.github.io/dell-inspiron-7559-linux-guide/index.html)
Dell Inspiron 7566
[https://ubuntuforums.org/showthread.php?t=2342359](https://ubuntuforums.org/showthread.php?t=2342359)

---

### Post by ceegen on 2019-09-02
I don't think it is a BIOS issue. I updated to the latest BIOS firmware via USB flash using the .exe provided on the web page. There's an option to select it from the BIOS, and it seemed to have worked without any errors. BIOS still loads fine.

Could it have errors because of an M2 drive? Incorrect drivers? Proprietary hardware? It seems the model numbers matter, a lot. The hardware is not consistent across model numbers, and so any of the solutions for other models that are listed, (many of which I have tried) do not work.

It is now freezing on the login screen, when attempting to boot from the M2 SSD that came with it. Being nearly 2 years old I am wondering if it isn't some kind of problem with the drive itself starting to fail? SSDs are known to have this problem, though I am wary of buying another HD just to check... Especially since it freezes when run 'live' from the USB.

Just not compatible I think?

---

### Post by oldfred on 2019-09-02
Did you update firmware on SSD?

---

### Post by ceegen on 2019-09-02
I reinstalled Windows 10 just to test, and it works fine as Windows 10. Looking at the Dell web page it seems that the 15-7567 model only has Win10 support, which could indicate proprietary secret stuff that hasn't been implemented to work with Ubuntu.

---

### Post by oldfred on 2019-09-02
Most Intel based systems just work. And Dell usually is one of the better ones.
Many systems need UEFI update & SSD firmware update, just for cpu chip virus issues.
But Dell requires some UEFI settings & nVidia needs nomodeset.

---

### Post by ceegen on 2019-09-02
> **oldfred said:**
> Many systems need UEFI update & SSD firmware update, just for cpu chip virus issues.

We'll see what happens when I try to update things with Windows installed, and then try to get Ubuntu back on there after updating the firmware. I do believe that Windows directly updates the firmware via the OS, since they have licenses with hardware manufacturers, just for UEFI stuff.

> But Dell requires some UEFI settings & nVidia needs nomodeset.

Links? Got readily available info on that? This is new information to me.

Thank you.

---

### Post by oldfred on 2019-09-02
Some Dell will now update UEFI from Linux.
       Dell update UEFI/BIOS from Linux
[https://www.dell.com/support/article/us/en/19/sln171755/updating-the-dell-bios-in-linux-and-ubuntu-environments?lang=en](https://www.dell.com/support/article/us/en/19/sln171755/updating-the-dell-bios-in-linux-and-ubuntu-environments?lang=en) 
    
While possibly different models, Dell usually has similar UEFI & UEFI settings.
       Dell UEFI Dual boot instructions using Something Else
[https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN](https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN)
[https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en](https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en)
Dell with NVMe needs AHCI & boot option nvme_load=YES
[https://www.dell.com/support/article/us/en/19/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en](https://www.dell.com/support/article/us/en/19/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en)
[https://www.dell.com/community/Laptops-General-Read-Only/Dell-M-2-FAQ-regarding-AHCI-vs-RAID-ON-Storage-Drivers-M-2-Lanes/td-p/5072571](https://www.dell.com/community/Laptops-General-Read-Only/Dell-M-2-FAQ-regarding-AHCI-vs-RAID-ON-Storage-Drivers-M-2-Lanes/td-p/5072571)
[https://www.dell.com/support/article/us/en/19/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en](https://www.dell.com/support/article/us/en/19/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en)
Dell XPS 13 9560 install without issues
[https://ubuntuforums.org/showthread.php?t=2357321](https://ubuntuforums.org/showthread.php?t=2357321) 
    
Dell needs AHCI mode, not RAID nor Intel RST for drives. But you have to first install the Windows AHCI driver if dual booting.
Most nVidia need nomodeset to boot install media & first boot. Then from inside Ubuntu usually low quality graphics install the nVidia driver. If newer nVidia card use ppa to get latest versions.
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.

      
 If wrong nVidia driver or upgrade, you must purge & install correct driver
[https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946](https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946)
[https://ubuntuforums.org/showthread.php?t=2380061](https://ubuntuforums.org/showthread.php?t=2380061)
[https://ubuntuforums.org/showthread.php?t=2362351](https://ubuntuforums.org/showthread.php?t=2362351) 
    
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) & 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

If you use your browser & search for Dell in link below in my signature, you find most of above info. Just not your specific model.

---

### Post by ceegen on 2019-09-03
Nope, looks like I'm going to have to try Ubuntu 19.04 or 19.10, see if they work on this thing.
Tried installing it alongside Windows 10 as per all instructions and considerations taken, different configurations several times, still did same thing.
Just hoping an updated kernel can fix that problem. If not, I might be reading up on building a custom kernel in the near future.
This might be fun, else we'll see how aerodynamic laptops are.

> [COLOR=#000000]Just not your specific model.[/COLOR]

This seems to be a specific problem. ;)

---

