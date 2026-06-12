---
title: "Can't boot, grub no longer showing up."
date: 2014-08-14
forum: New to Ubuntu
---

### Post by william46 on 2014-08-14
Hello!  I am a new Ubuntu user, and this system76 laptop is my first foray into linux.  

To start, I have a Kudo Professional with 14. LTS on it.  I followed instructions on the forums for dual booting windows.  (Found here [http://knowledge76.com/index.php/Windows_-_Add_MS_Windows_to_Your_System76_Machine](http://knowledge76.com/index.php/Windows_-_Add_MS_Windows_to_Your_System76_Machine)).  This set up worked for a few weeks until yesterday I had an issue booting into my windows partition.  I would select the Windows option in Grub, grub would think, then it would restart and show grub again.  I couldnt get into windows.

I googled around, and downloaded boot-repair to my Ubuntu partition.  I ran it, and it hung on "Scanning Systems" for over a half hour.  I googled THAT problem and decided to burn a boot-repair disk to boot from.  Before I did that though, I tried once more to just restart and see how grub was behaving. After I rebooted, I did not even get to grub, but a error screen reading:

"Realtek PCIe GBE Family Controller Series v2.56 (07/01/13)
 PXE-e61: Media test failure, check cable

 PXE-M0F: Exiting OXE ROM.
 
 Reboot and select proper boot device
 or insert boot media in selected boot device and press a key."

I am pretty sure I am booting from the correct device.  When I hit F7 at the boot screen and select the harddrive specifically, I get the same message.

I burned a boot-repair live cd, and booted from it.  But the same error happens, it hangs at "Scanning Systems" forever.  

I am lost.  Any advice would be very welcome.

---

### Post by sotiris2 on 2014-08-14
Just to make it sure you did reformat the whole drive to use MBR and have then installed windows and reinstalled ubuntu yourself? Then you used both system normally booting them shutting them down and booting them again with no problems. 

Then yesterday windows suddenly wouldn't boot. But Ubuntu did boot. You ran boot repair. It hanged in scanning systems so I don't think it did change everything. Was the system otherwise responsive or did it freeze? You rebooted and couldn't even get grub. Your laptop apparently tries to boot through network which should be beneath the hard drive in boot order. It does boot from a live cd though, it also gets stuck in scanning systems. 

So a few questions.
Did you boot Ubuntu more than after failing to boot windows? 

Did you reboot while on grub and failing to boot windows? or did you just pick ubuntu after trying windows a few times?

When you select your hard drive in the f7 menu, does it say just hard-drive or more like a device name for example say something like wdc-xxxx ? What about the actual bios menu? Does it list details for your hard drive? 

In the Boot repair cd, you cant run boot repair, I presume it has a file manager like ubuntu live CDs, can you mount any partitions? Can you actually open a file from them?  Does it have any disk utilities like Disks or Gparted? (do not make any changes with those yet.)

---

### Post by william46 on 2014-08-14
Hi, thanks for the response!

1) I did boot ubuntu after windows failed to boot. 
2) It says "P5: HGST HTS721010A9E630" for the SATA slot that the harddrive is in 
3) The BIOS shows a harddrive is there, at the same SATA Port 5, and it lists its capacity correctly.  Also, the boot order shown is correct - drive, cd, then network.
4) I can't mount any partitions, and when it shows the drives available to mess with, it just shows a single 1TB drive, with no volumnes to be found.  (I should have a 250g Win8 and a 750g Ubunutu.  No files can be accessed.
5) The boot repair disc comes with Gparted.  When I run it I a simialar problem, it hangs while "Scanning All Devices".  I have seen it finish with an error message like "Cannot read /dev/sda" but Im having trouble getting it to produce that message right now so i dont know the exact message.

Thanks again.  I fear the worst.

---

### Post by sotiris2 on 2014-08-14
I think you have a corrupted partition table. It may be fixable or not. I would recommend that you wait for someone more familiar with partition tables to post here. Until then stop any further attempts at fixing this since any write activity could be detrimental.

---

### Post by oldfred on 2014-08-14
Does your Boot-Repair have Disks or Disk Utility? If you installed Boot-Repair into Ubuntu live installer it will for sure.
Then click on drive and see what Smart Status is. 
If in 14.04 it now just shows overall status and you have to click on little icon in upper right corner to get details.

It is not booting hard drive so then goes down boot order to network boot ( PXE boot).

Could be major drive issue, or partition table & boot loader.

---

### Post by sotiris2 on 2014-08-14
Maybe testdisk can help him. If it's not installed
```
sudo apt-get install testdisk
```will install it on a ramdisk not on the hard drive right?

---

