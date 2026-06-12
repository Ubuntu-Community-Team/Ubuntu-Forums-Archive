---
title: "always show gnu grub version 2.06 during boot"
date: 2022-10-20
forum: New to Ubuntu
---

### Post by yiwei520 on 2022-10-20
Hello everyone,

I'm new to Ubuntu and after I installed Ubuntu alongside Windows, the computer always show gun grub version 2.06 problem. I tried to use "ls" command to find boot/grub following the tutorial from Askubuntu. However, I still can't find it.:(

So I tried boot-repair[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291148&stc=1[/IMG]and I hope you can help me with this. I attached file and you can also visit URL [https://paste.ubuntu.com/p/gBWXNwfrzC/](https://paste.ubuntu.com/p/gBWXNwfrzC/) to see it.

Best Regards,
Yiwei

---

### Post by yancek on 2022-10-20
Line 125 shows the current system booted is 0000 and line 120 shows that 0000 is Ubuntu.  Additionally line 109 shows OS in use is Ubuntu.  Do you see the gnu grub message on screen but are still able to boot?

You have both Ubuntu and windows efi files present on nvme0n1p1 so they both should boot.  sda4 shows as a vfat fllesystem, what is that?
Could you be more specific as to what the problem is?  Can you boot Ubuntu?  Can you boot windows? What exactly happens when you see the gnu grub message?

---

### Post by yiwei520 on 2022-10-20
Hello,

When I press F2 during boot and set Ubuntu's priority higher, I can choose which OS I want to boot(Ubuntu or Windows). When I choose Ubuntu, it seems to work.  However when I reboot, it shows gnu grub version 2.06 and grub>. I tried to use 'ls' to find root partition as this tutorial says([https://askubuntu.com/questions/883992/stuck-at-grub-command-line](https://askubuntu.com/questions/883992/stuck-at-grub-command-line)) but I couldn't find it. And I can't boot Ubuntu again. 

And when I press F2 during boot and set Windows' priority higher, it can only boot Windows, which means I don't have the option, which OS I boot.

---

### Post by oldfred on 2022-10-20
The f2 would be UEFI settings.
Does f12 (or maybe other key) give UEFI boot menu. And then do both systems boot from that?
Windows will not offer to boot Ubuntu.

You show UEFI Secure boot on.
Grub did not normally boot Windows with UEFI Secure boot on. But it may now?

Not sure why first boot & then reboot give different results.

---

### Post by yiwei520 on 2022-10-20
Hello,

I reinstall Ubuntu and it seems work well. I chose Windows Boot Manager for boot loader installation other than the default device during install.

I get this idea from this tutorial([https://www.youtube.com/watch?v=Z-Hv9hOaKso](https://www.youtube.com/watch?v=Z-Hv9hOaKso)). 

Thank you for all your help!

---

