---
title: "Wubi install of Edbuntu"
date: 2013-10-25
forum: New to Ubuntu
---

### Post by EpidemikE on 2013-10-25
Need a little help. I installed Edbuntu 12.04 LTS using Wubi on a Dell Vostro 1000. Everything was good, got prompted for the reboot after the installation finished. Laptop rebooted and GRUB came up and 5 secs later my screen was not blank but was not displaying anything. 

I have a feeling that it may be that my install failed while using Wubi. I may just have to wipe the HD and do a complete install.  I also have a feeling it may be my ATi card installed that also be giving some of the problem.

---

### Post by Old_Grey_Wolf on 2013-10-25
You don't need to wipe the HDD.

"How do I uninstall Wubi?

Run the uninstaller in "Control Panel > Add or Remove Programs" for Windows XP or lower or "Control Panel > Programs and Features" for Windows Vista or Windows 7. Alternatively, you can run: C:\ubuntu\Uninstall-Ubuntu.exe."

This is from: [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

Edit: someone else may address the ATI card as I have avoided having them.

---

### Post by EpidemikE on 2013-10-25
I meant wipe the drive as in booting in dual mode doesn't seem to be working. There is no real pertinent data on the Windows partition.

Im more concerned about the video issue, TBH. I have a sneaky suspicion that the 12.04 may be too advanced for my Dell Vostro 1000.

---

### Post by monkeybrain20122 on 2013-10-25
Forget about WUBI, it is first of all meant as a demo, secondly it works in a Windows folder and has size limitations. It doesn't do justice to Ubuntu. Make a true dual boot by giving it its own partition.

---

### Post by Old_Grey_Wolf on 2013-10-25
> **EpidemikE said:**
> I have a sneaky suspicion that the 12.04 may be too advanced for my Dell Vostro 1000.

I have looked a the specs for the Dell Vostro 1000. It looks like it is a notebook and has a maximum of 1GB RAM. You may want to look at Xubuntu or Lubuntu that are lighter. 

If you have an ATI graphics card, I would suggest that you look into what it will take to make that card work.

Forget about WUBI as it is no longer supported after 12.04. It also doesn't work with MS Windows 8 machines.

---

