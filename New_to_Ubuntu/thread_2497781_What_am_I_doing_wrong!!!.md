---
title: "What am I doing wrong!!!"
date: 2024-05-17
forum: New to Ubuntu
---

### Post by jkett08 on 2024-05-17
Hi I am completely new to Ubuntu and am currently taking a class where we install and Ubuntu onto virtual machine. I am in the process of installing and I keep getting the following message failed unmounting cdrom.mount - /cdrom. Please remove the installation medium, then press enter.
Some one please break this down for me so I can understand and learn.
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293783&stc=1[/IMG]

---

### Post by The Cog on 2024-05-17
In a real machine, you would press the button on the drive to eject it. In a VM, maybe the host VM manager has a way to remove the disc from the guest? If not you could try the command "eject", or just reboot anyway. It will probably boot into the installed system rather than the installer CD.

---

### Post by Rubi1200 on 2024-05-17
Press Enter and the virtual machine should reboot or you can restart it.

I have noticed, sometimes, that even after a restart the CD-ROM drive appears to be connected. Usually, unmounting it removes the icon.

Nothing to be concerned about, this behaviour seems to be normal.

---

### Post by ActionParsnip on 2024-05-17
If Ubuntu is installed then this is fine. Just send CTRL + ALT + DEL then boot from the internal disk rather than the CD

---

