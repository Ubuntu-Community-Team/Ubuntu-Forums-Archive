---
title: "Trying to repair boot (incl. Boot-Repair log)"
date: 2021-01-13
forum: New to Ubuntu
---

### Post by uciricu on 2021-01-13
Hi folks,

I have not posted here before, but I am looking for help with my Ubuntu boot.

I have been using it successfully on my Windows machine (with a dual boot) since I got this thing in September. However, last week or the week before, I believe there was an update to Ubuntu, and since then, after I select Ubuntu from the boot menu, it brings me to (first, the Ubuntu splash screen, then) a black screen with the blinking underscore in the top left of the screen. Sometimes it also shows some lines, with timestamps before them, saying Bluetooth has failed, or something.

In looking up how to fix this, I found Boot-Repair. I installed the .iso to an external USB drive. I successfully booted to that USB and ran the recommended repair. It gave me some error message about how I need an ESP partition that I don't have; I looking into that, and I eventually saw that my first partition (used by Windows I believe) *is *an ESP partition, or at least it is flagged as such. So I'm not sure what the problem is.

Here is my paste. Can anyone help me figure out how to solve my boot issue?
[https://pastebin.com/1my7J7mX](https://pastebin.com/1my7J7mX)

Thanks a million!
-B 

P.S. While I was booted into the Boot-Repair USB, I used gparted (which is in there too) to adjust one of my Ubuntu partitions (I have three: the one with the OS on it (I think), the swap, and the one where I store my files, desktop etc.), that is, the first one with the OS, and took the space out of my 30GB swap, which seemed excessive. Hopefully I didn't bugger anything up when I did that, but it didn't seem o require moving any data, as swap was to the right of the OS partition and was empty; the OS partition was expanded to the right and the left side (with the files) wasn't moved.

---

### Post by oldfred on 2021-01-13
Did a Windows update turn fast start up back on. That locks up Windows partitions and often the ESP then cannot be seen.
I could also be some corruption in the FAT32 partition that Windows chkdsk or Linux dosfsck may fix.

sudo /sbin/fsck.vfat -V <the fat32 device>
man dosfsck
sudo fsck.vfat -t -a /dev/nvme0n1p1

---

### Post by grahammechanical on 2021-01-13
I do not mean to be awkward but you have run Boot Repair and obtained a report which you have provide a link to but you also allowed Boot Repair to do a repair. So, what is the situation now? After boot repair did its stuff? You described the situation that was happening before Boot Repair repaired the boot process or at least it claimed to.

Or, am I misreading your post? If so, please describe the boot menu that you select Ubuntu from. Is it the Ubuntu boot loader called Grub? If so, do you see Advance Options for Ubuntu? Select that and from the list select an earlier Linux kernel. If the kernel at the top of the list is 5.8 generic, then choose 5.4 generic and trying booting from that kernel. What happens after doing that.

Regards

---

### Post by uciricu on 2021-01-13
> **oldfred said:**
> Did a Windows update turn fast start up back on. That locks up Windows partitions and often the ESP then cannot be seen.
I could also be some corruption in the FAT32 partition that Windows chkdsk or Linux dosfsck may fix.

sudo /sbin/fsck.vfat -V <the fat32 device>
man dosfsck
sudo fsck.vfat -t -a /dev/nvme0n1p1

Thanks for your post. I went into the BIOS and Quick Startup was on. I changed it to Diagnostic, then booted to the live USB again. Boot-Repair gave me the same error:

[IMG]https://puu.sh/H6KbI/78fe4c9eed.png[/IMG]

As for running those commands, are those things I can do on Windows cmd? It looks like an Bash script to my (very novice) eyes, but my Ubuntu is out of commission right now, which I am trying to repair.

---

### Post by uciricu on 2021-01-13
> **grahammechanical said:**
> I do not mean to be awkward but you have run Boot Repair and obtained a report which you have provide a link to but you also allowed Boot Repair to do a repair. So, what is the situation now? After boot repair did its stuff? You described the situation that was happening before Boot Repair repaired the boot process or at least it claimed to.

Or, am I misreading your post? If so, please describe the boot menu that you select Ubuntu from. Is it the Ubuntu boot loader called Grub? If so, do you see Advance Options for Ubuntu? Select that and from the list select an earlier Linux kernel. If the kernel at the top of the list is 5.8 generic, then choose 5.4 generic and trying booting from that kernel. What happens after doing that.

Regards

Thanks for your post. I tried to run Boot-Repair, but when I clicked on the button to run the recommended repair, it gave me an error (the one seen in the above post; I took a picture). Ubuntu is still not booting up; nothing has been fixed or changed.

I select from the Grub menu, as I have ever since I got this computer and installed the dual boot. It appears to be GNU Grub version 2.04. Here's the settings for Ubuntu (if I press e on the Ubuntu option):
[IMG]https://puu.sh/H6Kew/456d7853f5.png[/IMG]

I also tried booting from the 5.4 generic kernel from the advanced setting. It gave me the same black screen with some bluetooth errors.
[IMG]https://puu.sh/H6Kfs/ea269f976e.png[/IMG]

It stays stuck on this ad infinitum. So, the problem has still not changed at all.

Is there anything further I can try?

With appreciation,
-B

---

### Post by oldfred on 2021-01-14
Please do not post screen shots of terminal output.
Just copy & paste the terminal output. If longer also use code tags.

Have you tried recovery mode, second line in grub menu?

---

### Post by yancek on 2021-01-14
The image you posted in post #4 indicates that you need to set the boot flag on the EFI partition which would be:  nvme0n1p1
Boot the Ubuntu usb you have with Ubuntu on it and set the boot flag by using GParted which is on the usb.   Highlight nvme0n1p1 in the main window of gparted then click on the Partition tab at the top of the window and mouse down to the option Manage Flags and make sure the check boxes for boot and esp are checked.  Beginning at Line 11 of boot repair you see the correct entries for both Ubuntu and windows so they should boot.  If you have been booting both Ubuntu and windows EFI, those boxes should have been checked.

---

### Post by uciricu on 2021-01-14
Hi all,

Thanks for your input. I took your advice first, oldfred, and tried booting from recovery. Recovery mode worked.

I then discovered the problem when I was in Ubuntu. My partition was so low on space that it was malfunctioning (a little less than 1 GB). I deleted some packages and restarted into the regular mode, and now everything is working just fine.

Case closed! Much appreciated to all of you.

-B

---

### Post by yancek on 2021-01-14
> My partition was so low on space that it was malfunctioning (a little less than 1 GB). 

For future use, be aware that the system will generally work a lot better if you have 10% free space available on a LInux system, more on a windows OS.

---

### Post by grahammechanical on 2021-01-14
@uciricu

And so we all learn. :) We all have stories to tell of our learning experiences. 

Regards

---

