---
title: "Plymouth not working Kubuntu 23.10"
date: 2024-01-21
forum: New to Ubuntu
---

### Post by azbro on 2024-01-21
So I'm new to Linux. I used Ubuntu for about a week on a duel booting laptop using rEFInd to pick my OS on boot. Yesterday I decided to install Kubuntu instead because of the desktop interface and customization. I'm loving it but I have a problem and can't figure it out for the life of me. When I boot into linux from rEFInd I get multiple pages of lines of ok checks saying everything is working. This actually helped me resolve a problem once but now everything is saying its ok and the pages of fast moving text aren't visually appealing. I'd like to use Plymouth to replace it with a boot splash screen like I had in ubuntu, but no matter what i do it doesn't seem to stick. I've installed plymouth and have the boot splash screen option in my global theme settings. But when I select the boot screen option it doesn't actually apply. I've tried the solutions from multiple threads but nothing works for me. So many threads in fact I don't know all I did so I'm hoping to start from scratch here and try anything any everything you all think I should do. Below will be my etc/default/grub file as I saw that mentioned in alot of other threads, and also my system info.

> GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""


[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293320&stc=1[/IMG]

---

### Post by guiverc on 2024-01-21
Any changes you make to GRUB won't impact your boot, as you're not using it (you're using rEFind)

Your changes will have taken effect IF you were using grub as your bootloader, as that is where changes are written, such as using plymouth or not to use plymouth etc; however these changes can be, and I bet are are being overruled by rEFind passing parameters to the boot process.

Sorry I can't help you with your chosen bootloader, I've not used it.  You'll need to wait for others to assist.  I'm betting its rEFind configuration required.

( the options you do want is `quiet splash` as shown in your paste of a grub config; but you need to give that detail to your bootloader, ie. rEFind )

---

### Post by azbro on 2024-01-21
You are probably right. I just checked the /boot/efi/EFI/refind/refind.conf and maybe the answer is in this line:
> # Launch specified OSes in graphics mode. By default, rEFInd switches
# to text mode and displays basic pre-launch information when launching
# all OSes except macOS. Using graphics mode can produce a more seamless
# transition, but displays no information, which can make matters
# difficult if you must debug a problem. Also, on at least one known
# computer, using graphics mode prevents a crash when using the Linux
# kernel's EFI stub loader. You can specify an empty list to boot all
# OSes in text mode.
# Valid options:
#   osx     - macOS
#   linux   - A Linux kernel with EFI stub loader
#   elilo   - The ELILO boot loader
#   grub    - The GRUB (Legacy or 2) boot loader
#   windows - Microsoft Windows
# Default value: osx
#
#use_graphics_for osx,linux

I don't know how to edit this in order for it to work properly.

For more info here are examples of the lines of text I get once I select linux in rEFInd on boot:
[IMG]https://i.imgur.com/oZl4Xq5.jpeg[/IMG]
[IMG]https://i.imgur.com/8xDM7oq.jpeg[/IMG]

As well as the lines i get on shutdown and reboot:
[IMG]https://i.imgur.com/hM39uR7.jpeg[/IMG]

---

### Post by caroleskiles on 2024-01-22
Thanks for the info.

---

### Post by azbro on 2024-01-28
Solved my issue, was pretty simple. Just edited the refind_linux.conf file in the boot folder to include "quiet splash" in the standard options.

---

