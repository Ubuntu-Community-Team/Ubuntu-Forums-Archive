---
title: "probrem with GRUB2, cannot choose the OS."
date: 2016-07-26
forum: New to Ubuntu
---

### Post by hosal on 2016-07-26
Hello everyone.
I`ve got a PC with pre-installed Win 8 OS, later I upgraded it to Windows 10. One day I decided to try something new, and installed and Ubuntu 14.04 distro.
I booted it from the flash drive, succesfully installed it and rebooted the PC. The GRUB2 menu appeared, I chose Ubuntu and all was nice. The next day I turned te computer on, saw the loading screen and Win 10 OS without any choices.
I asked the question on the forum, serached some help in the Internet and I found a post with the same problem: [https://ubuntuforums.org/showthread.php?t=2272927](https://ubuntuforums.org/showthread.php?t=2272927)
That was helpful, I loaded from the flash drive, used Boot-Repair, and it helped, but after reboot Win 10 loaded again.
When I tried to use Boot-Repair one more time, he wrote this:
 GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again.
I did what he asked me to do, and he again installed GRUB2 only for one reboot. 
How can I install GRUB once and for a long time?
The first Boot Info Summary: [http://paste.ubuntu.com/20745521/]("https://vk.com/away.php?to=http%3A%2F%2Fpaste.ubuntu.com%2F20745521%2F")
The second one: [https://yadi.sk/i/9V1R1o46tdVN3](https://yadi.sk/i/9V1R1o46tdVN3) (I don`t know why, but it was given to me as a text file)
Sorry for mistakes, English is not my native language.
Thanks in advance.

---

### Post by Bucky Ball on 2016-07-26
Welcome to the OS and the forums. Hopefully, this is a simple fix. When you boot the computer, after the manufacturer's flash screen, if you get one, start hitting the Shift key. That should bring up a menu page. Do you have all of the options for your installed OSs there?

Sounds like you are not seeing the OS options at boot and the machine is set to default to Windows if nothing is selected, which of course it isn't because you can't. :)

If this works, let us know and we can make the selection screen happen on boot 'automagically'.

---

### Post by hosal on 2016-07-26
Thank you for your reply and for welcoming :)
I tried to use your advice, but it did not help. I pressed Shift at the first screen, but it only gave me an option to start BIOS, which is F12. After that, the screen went dark for a second, and the Windows started, as usual.
Should I start the BIOS menu and try to change something in there?
I can send you a video of the loading process, if it would help.

---

### Post by grahammechanical on 2016-07-26
When a machine comes with windows 8 pre-installed then windows 8 will be installed in EFI mode and that means that Ubuntu must also be installed in EFI mode.

Originally you had Windows 8/10 installed in EFI mode on the first hard disk (sda) but you installed Ubuntu in BIOS/Legacy/CSM mode on the second hard disk (sdb). And that meant that you could either load Ubuntu or Windows 10. And you had to enter the UEFI settings to change boot modes to do that.

Boot Repair fixed that by putting Ubuntu efi boot files into the first partition of the first hard disk (sda1) which is where the Windows efi boot files are also kept. There is nothing wrong with this. The efi boot files of both Windows & Ubuntu can exist side by side.

Boot Repair gave this advice.

> Please do not forget to make your BIOS boot on sdb (1000GB) disk!

Is the BIOS/UEFI set to boot from the second hard disk (sdb)? And have you set the UEFI to boot from EFI mode or is it set to boot in BIOS/Legacy/CSM mode?

You might want to re-consider the set up of that machine. The first hard disk has GPT partitioning. The second hard disk has MBR partitioning and partitions relating to Windows 7 which does not seem to be installed. What do you plan to do with the second hard disk? You might want to consider re-installing Ubuntu on to the second hard disk but with GPT partitioning on the hard disk and Ubuntu installed in EFI mode. If you choose to do that then you will need to direct the Ubuntu installer to install the Grub boot loader into the second hard disk (sdb).

Regards.

---

### Post by hosal on 2016-07-26
Thank you very much for your advice.
I don`t know, what I was thinking, when I was parting disks, but I never thought, that I have got two different hard disks.
[http://i.imgur.com/RrfP6Ic.jpg](http://i.imgur.com/RrfP6Ic.jpg)
I am sorry for stealing your time, the problem is in my stupid head and bad hands.
And one last question: how to put BIOS boot on my 2nd HDD?
The only thing thah BIOS shows is Windows Boot Manager.
[https://webattach.mail.yandex.net/message_part_real/IMG_0024.JPG?sid=G%2AXICSY4dd16hfwe9vavLPPmXZQk%2Ai91tGnRyeDcA15QA%2A9lpCsOnnbOMSNuOfZqIOzfLa3rbQjARkZ7U5h%2FVg%3D%3D&_uid=60437896&exif_rotate=y&hid=1.2&ids=159314836818233399&name=IMG_0024.JPG&no_disposition=y](https://webattach.mail.yandex.net/message_part_real/IMG_0024.JPG?sid=G%2AXICSY4dd16hfwe9vavLPPmXZQk%2Ai91tGnRyeDcA15QA%2A9lpCsOnnbOMSNuOfZqIOzfLa3rbQjARkZ7U5h%2FVg%3D%3D&_uid=60437896&exif_rotate=y&hid=1.2&ids=159314836818233399&name=IMG_0024.JPG&no_disposition=y)
Thanks :)

---

