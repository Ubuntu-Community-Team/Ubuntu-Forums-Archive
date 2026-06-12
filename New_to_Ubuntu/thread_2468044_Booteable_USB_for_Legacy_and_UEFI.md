---
title: "Booteable USB for Legacy and UEFI"
date: 2021-10-16
forum: New to Ubuntu
---

### Post by santy4tas on 2021-10-16
Hello dear friends,

Following a tutorial, I created a booteable USB for Ubuntu. From an Ubuntu system I created in the USB the following partitions

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289292&stc=1[/IMG]

Then I installed Ubuntu into the LUKS Partition. So far so good. 

My concern is that, acording to the tutorial, the USB should boot in UEFI or Legacy computers but it only boot on UEFI. On Legacy it shows the typic black screen with white line flickering.

Somebody can tell me what should I do?

Thank you so much in advance

---

### Post by grahammechanical on 2021-10-16
How about giving us a link to that tutorial? 

Regards

---

### Post by santy4tas on 2021-10-16
> **grahammechanical said:**
> How about giving us a link to that tutorial?

Regards

I checked the tutorial in Reddit. If it's 0k to paste the URL in this forum I can do it. I didn't do it because I thought it was not allowed

---

### Post by grahammechanical on 2021-10-17
This is the link I often provide for burning a Ubuntu ISO image to USB memory stick.

[https://ubuntu.com/tutorials/create-a-usb-stick-on-ubuntu#1-overview](https://ubuntu.com/tutorials/create-a-usb-stick-on-ubuntu#1-overview)

In the reply to thread box click the icon of the planet and a link of a chain. And post the web site address in the panel that appears.

I asked for the link to the tutorial because I wondered why you were doing things that why. Usually a person downloads and burns the standard ISO image to USB memory stick. Then if we load the USB stick in UEFI mode Ubuntu will install in UEFI mode. And if we load the USB stick in Legacy mode Ubuntu will install in legacy mode. I do not know of any reason to partition the USB stick the way you have done.

Regards

---

### Post by yancek on 2021-10-17
In your initial post, you indicate that you "installed" Ubuntu to the LUKS partition.  I take that to mean that you have an actual install of Ubuntu on the flash drive and that this is not a USB meant to be used to install Ubuntu, is that correct?

Could you post the link you used to do this to help clarify things for us?  If you do have an actual install of Ubuntu on the flash drive and want to boot it on UEFI computers and Legacy computers, you will need a bios_grub partition (unformated) on the flash drive as well as  an i386-pc directory in the /boot/grub partition and need to  install Grub in legacy mode.  An example of this is posted below.  You will need to change the --boot-directory path shown below to suit your system as well as the device if it is not /dev/sdb 

>  grub-install --target=i386-pc --recheck --boot-directory=/mnt/seagate/boot /dev/sdb

The command above needs the i386-pc directory in the /boot/grub directory on the flash drive.  If you do not have it there, copy it from the /usr/lib/grub/ directory from any Ubuntu or Linux install.

---

### Post by santy4tas on 2021-10-18
> **yancek said:**
> In your initial post, you indicate that you "installed" Ubuntu to the LUKS partition.  I take that to mean that you have an actual install of Ubuntu on the flash drive and that this is not a USB meant to be used to install Ubuntu, is that correct?

Could you post the link you used to do this to help clarify things for us?  If you do have an actual install of Ubuntu on the flash drive and want to boot it on UEFI computers and Legacy computers, you will need a bios_grub partition (unformated) on the flash drive as well as  an i386-pc directory in the /boot/grub partition and need to  install Grub in legacy mode.  An example of this is posted below.  You will need to change the --boot-directory path shown below to suit your system as well as the device if it is not /dev/sdb 



The command above needs the i386-pc directory in the /boot/grub directory on the flash drive.  If you do not have it there, copy it from the /usr/lib/grub/ directory from any Ubuntu or Linux install.

I followed **[[COLOR=#dd4814]this tutorial[/COLOR]]("https://www.reddit.com/r/Ubuntu/comments/6o35ef/live_usb_ubuntu_encrypted/")** although it boot perfect in UEFI, it doesn't boot in Legacy as I said. 

To clarify the process I made. I installed a Live Ubuntu in USB#1 with Rufus, then I booted from this USB, I connected USB#2, created the partitions with GParted and then I installed Ubuntu into USB#2 using the normal installer that is in the Desktop

What I pretend is to have an "On-the-go Ubuntu" USB with an encrypted LUKS partition for my personal data, that I can boot both in UEFI and Legacy

---

### Post by sudodus on 2021-10-18
The following links show ways that work to create an installed Ubuntu system, that can boot both in UEFI mode and BISO mode (alias CSM alias legacy mode).

- [How to Create a Full Install of Ubuntu 20.04 to USB Device Step by Step](https://askubuntu.com/questions/1217832/how-to-create-a-full-install-of-ubuntu-20-04-to-usb-device-step-by-step)

- [url=https://help.ubuntu.com/community/Installation/UEFI-and-BIOS] Installation/UEFI-and-BIOS
[/url]

Maybe you can use instructions in the first link to create a boot system for BIOS mode. Otherwise you can backup the personal data in the home directory and make a fresh installation.

---

### Post by yancek on 2021-10-19
If you want to boot both UEFI or Legacy on different computers, you will need the bios-grub unformatted partition.  I don't see anything in the link you posted that discusses booting in Legacy mode.

---

### Post by santy4tas on 2021-10-22
> **sudodus said:**
> The following links show ways that work to create an installed Ubuntu system, that can boot both in UEFI mode and BISO mode (alias CSM alias legacy mode).

- [How to Create a Full Install of Ubuntu 20.04 to USB Device Step by Step]("https://askubuntu.com/questions/1217832/how-to-create-a-full-install-of-ubuntu-20-04-to-usb-device-step-by-step")

- [URL="https://help.ubuntu.com/community/Installation/UEFI-and-BIOS"] Installation/UEFI-and-BIOS
[/URL]

Maybe you can use instructions in the first link to create a boot system for BIOS mode. Otherwise you can backup the personal data in the home directory and make a fresh installation.

Thank you for your answer dear my friend. After visiting your suggestion of ["]("https://askubuntu.com/questions/1217832/how-to-create-a-full-install-of-ubuntu-20-04-to-usb-device-step-by-step")[How to Create a Full Install of Ubuntu 20.04 to USB Device Step by Step]("https://askubuntu.com/questions/1217832/how-to-create-a-full-install-of-ubuntu-20-04-to-usb-device-step-by-step")["]("https://askubuntu.com/questions/1217832/how-to-create-a-full-install-of-ubuntu-20-04-to-usb-device-step-by-step") I realized that at the end of the post I could found this:


[LIST]
[*]For method of creating Full Encryption BIOS/UEFI USB drive see: [How to Make BIOS/UEFI Flash Drive with Full Disk Encryption]("https://askubuntu.com/questions/1086309/how-to-make-bios-uefi-flash-drive-with-full-disk-encryption")
[/LIST]

Taking into account this is what I need (full disk encryption) I followed the process exactly as it says, with no success, I had two problems.

I could follow all the steps perfectly except for the last steps which says > [COLOR=#232629][FONT=inherit]Now mount the ESP boot partition and copy ESP/EFI/ubuntu/grub/grub.cfg and overwrite ESP/boot/grub/grub.cfg[/FONT][/COLOR]

Here appeared the first problem because the route [COLOR=#232629]*ESP/EFI/ubuntu/grub *[/COLOR]is empty for me. 

Even so, I tried to boot the USB from both, UEFI System and BIOS System. It shows the GRUB on boot:
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289323&stc=1[/IMG]



The second problem is that no matter which option I select, I am getting the following error

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289324&stc=1[/IMG]

Any ideas on what I can do? Hope you can help me.

Thank you

---

### Post by sudodus on 2021-10-22
@santy4tas,

> I could follow all the steps perfectly except for the last steps which says

[QUOTE]Now mount the ESP boot partition and copy ESP/EFI/ubuntu/grub/grub.cfg and overwrite ESP/boot/grub/grub.cfg

Here appeared the first problem because the route ESP/EFI/ubuntu/grub is empty for me.
[/QUOTE]

You must replace ESP by the actual mountpoint, where the ESP partition's file system is mounted, and if not mounted **you must mount it**.

Do you know how to mount a partition with mount?

```

sudo mount <block device> <mountpoint>
# for example
sudo mkdir /mnt/esp
sudo mount /dev/sda2 /mnt/esp

```

> Even so, I tried to boot the USB from both, UEFI System and BIOS System. It shows the GRUB on boot:

The first screenshot shows the boot menu of a persistent live system made by mkusb. But you should boot into an installed system. Maybe your computer will boot into that system if you shut down your computer, unplug the persistent live drive and boot again.

Otherwise, I don't think it works to apply 'full disk encryption' to a persistent live system.

---

### Post by sudodus on 2021-10-22
> **yancek said:**
> If you want to boot both UEFI or Legacy on different computers, you will need the bios-grub unformatted partition.  I don't see anything in the link you posted that discusses booting in Legacy mode.

Thanks for the heads up.

Please specify which link and where we should expect details about the bios_grub partition.

---

### Post by yancek on 2021-10-22
> Please specify which link and where we should expect details about the bios_grub partition.           

The link I was referring to was posted by the OP in post 6 and was what the OP used to attempt to create a bootable USB to boot UEFI and Legacy.  Reviewing that link shows nothing about installing in Legacy mode but only UEFI.  To boot also in Legacy mode, a bios_grub partition is also needed, both an EFI partition and an unformatted 1-2MB bios_grub partition, then installing Grub using the grub-install method described in post 5 modified to meet the OP's situation.

---

### Post by sudodus on 2021-10-22
Thanks @yancek :-)

---

### Post by yancek on 2021-10-23
No problem.

---

