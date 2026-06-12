---
title: "Howto: Dual-boot Vista/Ubuntu (Vista Installed first)"
date: 2007-02-27
forum: Outdated Tutorials &amp; Tips
---

### Post by Uncle Spellbinder on 2007-02-27
Thought I'd share a link with you. 

**[color=#990000][SIZE="5"]I CAN MAKE NO CLAIMS THAT THIS WILL WORK FOR *EVERYONE*. PROCEED AT YOUR OWN RISK.[/SIZE][/color]**

A coworker ran across this and tried it. Said she had no problems and that it worked perfectly in her case with Vista Home Premium already installed.  She resized her partition using the included tool in Vista:

Open *Computer Management* > *Disc Management* > *Right Click Partition (Volume)* > *Click "Shrink Volume"* > *Choose your size* > *Save*.

**[color=#FF0000]DIRECT LINK[/color]**: [**How to dual-boot Vista with Ubuntu** (Vista installed first)](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)


SUMMARY:

**Scenario**: 
You want the simplest way to dual-boot Vista and Linux. You are prepared to install Linux after Vista to avoid the hassles created by Vista's bootloader overwriting GRUB.

Summary of tutorial: We'll Dual-boot Vista with Ubuntu. We'll install Vista first, using the Vista installer to create a partition on the disk for Vista which leaves plenty of unallocated space for Linux. We'll then install Ubuntu into the unallocated space, and update GRUB to recognise Vista.

To note: some distros, such as Suse recognise the Vista installation and don't require you to update the GRUB file.

[B*]Get started*[/B]

**_INSTALL VISTA_**

- Work your way through the Vista install screens until you get to "Which type of Installation do you want?"

- As this is not an upgrade install, select Custom install.

- The install location shows the drive onto which you'll install Vista.

- Click *Drive Options (advanced)* at the bottom right corner of the screen.

- Reduce the partition so that enough space is left for Linux. Go to New button at bottom right corner to create a partition.

- Select size for partition and Apply.

- The new partition is created for Vista.

- Let Vista install itself on the partition.


**_INSTALL UBUNTU_**

- Install Ubuntu to the unallocated space. Boot Ubuntu from its Live CD. Click on the Install icon on the Ubuntu Live desktop to begin the Ubuntu install process (Ubuntu creates an initial desktop in RAM before it gives you the option of installing the OS to hard drive).

- When the Select a Disk screen appears, select "Use the Largest Continuous Free Space"  button.

- Ubuntu will install itself in the large unallocated space left for it earlier.

- See the install through and then let it boot into Ubuntu. You'll notice that when the system boots, no option to boot into Vista appears anywhere. In fact, Vista is there, but waiting to be discovered by the GRUB bootloader.

- Update the GRUB file with Vista's location, but first we'll make a copy of GRUB to be safe. On the Ubuntu desktop, call up Terminal (Applications > Accessories > Terminal).

-  Type the following at the prompt:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_bak
```
and enter your root password when asked.

- Now is the fun bit. At the prompt, type:
```
sudo gedit /boot/grub/menu.lst
```
This fetches the GRUB file.

- Look for the line *## ## End Default Options ##*

- Immediately under  the line ## ## End Default Options ## (and before the first reference to Ubuntu) insert the following:

```
title Windows Vista

root (hd0,0)

makeactive

chainloader +1
```
Then press Save.

-  Before you quit the GRUB file, you may also want to increase the GRUB timeout at the start of boot to more than 3 seconds, so you have more time to press ESC to select GRUB. In the GRUB file, look for this line: timeout 3. Change it to timeout 8. Save and quit.

-  Voila! Vista is now in the GRUB menu.

-  Vista boots and the dual-booting is complete. GRUB will manage the booting of Ubuntu and Vista.

****************************************************************************************************

If instead of GRUB you want Vista's bootloader to be in charge, load up the Vista installation and install [**EasyBCD**](http://neosmart.net/dl.php?id=1). Go to &#8220;Manage Bootloader&#8221;, then &#8220;Reinstall the Vista Bootloader&#8221;, an GRUB is overwritten. You can then configure the Vista bootloader to add Linux to the boot menu.

A good rule of thumb when experimenting with dual- and multi-booting is to have a large hard drive so you don&#8217;t end up squeezing each OS through lack of space &#8211; the more you can give each system, the better they will run. And that&#8217;s about it for dual-booting with Vista. When you&#8217;re dealing with multiple operating systems you&#8217;ll always need a few tools on hand to tackle each stage, and the ones we&#8217;ve included on the cover DVD will get you through pretty much anything.

---

### Post by cewe08 on 2007-07-15
Hi, 
 I tried doing what you post, but it does not work. After i select install ubuntu, there is a message saying:
BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)

/bin/sg: can't access tty; job control turned off
(initramfs)

Then i type reboot then when the system reboot, i cant go back to visa, there is an error saying:

GRUB loading, please wait..
Error 22

then i cant do anything except to turn off my system. :( Please help.

---

### Post by bjornolai on 2007-07-18
Are you sure you didn't finish much of the installation of ubuntu. It seems like the bootloader has been installed, and I thought that happend at the very end of the installation. Anyhow, most importantly don't panic. Vista quite certainly still there, and it should be possible to get it back. Good news: the error you get is a quite common one. Bad news: it's a standard error message for almost whenever something is wrong in the bootup. Since it is a fresh install of ubuntu I would suggest simply reinstalling ubuntu. Maybe another version (edgy, dapper or feisty) or from an alternative disc (these do not have a grapichal user interface, but are really easy to use nonetheless). If you just want windows back you could try booting a live ubuntu cd. And manually configure /boot/grub/menu.lst  in the way described in the  first post (I'm guessing you haven't changed menu.lst already). That should give you the option Vista at bootup.  

Hope this can be of some use and that it hasn't broken your linux spirit :)

---

### Post by HokeyFry on 2007-09-12
i tried to install linux on my laptop (which already had vista on it), the boot loader is the way it should be, but when i select vista from the menu, it just ends up rebooting. now, i searched on the internet, and found something that said that vista needs its own bootloader to start up. whether or not this is true, is there any way to get vista to boot again?

---

### Post by dc_jt on 2007-09-22
Hi

First post here, I cant get my head round this!

I have followed what it says regarding shrinking the c drive. I have 500gb drive by the way.

This seems to work and I end up with c drive having 330gb and then 160g "not allocated", which seems right.

However when I go to install Ubuntu, the option "Manual - use the largest continuous free space" doesnt appear.

Instead it just says guided - use entire disk. Then it has two options sda and sdb both saying 250gb each. 

Why arent I geting the option to use the largest continous space??

Someone please help.

Thanks in advance

---

