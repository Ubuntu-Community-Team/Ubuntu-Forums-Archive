---
title: "Installing Windows"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by tubularBell on 2008-04-29
I currently run Ubuntu Gutsy, and I've decided it's time for me to install Windows XP on my separate 20gb empty partition.

The thing is, I want to have the option to choose which OS to boot at startup. Dualbooting perhaps?

I've looked around here and there and figured I need something known as Grub. I also figured that I already have Grub, but I don't have a clue of how to use it.

Any sort of help appreciated!

---

### Post by Cypher on 2008-04-29
As you've figured out, you already have GRUB that came during the installation of Linux. The problem of having Linux installed first and then install Windows is that upon completing the Windows installation, GRUB will be replaced by the Windows boot loader. 

Your Linux is still in-tact, and you'll have to [recovery GRUB]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") to make it now the primary loader to give you the option of booting into Linux or Windows.

---

### Post by tubularBell on 2008-04-29
Thanks for the quick reply!

I'll look into it :)

---

