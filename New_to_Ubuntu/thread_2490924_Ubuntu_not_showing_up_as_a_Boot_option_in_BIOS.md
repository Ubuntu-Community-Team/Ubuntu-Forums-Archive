---
title: "Ubuntu not showing up as a Boot option in BIOS"
date: 2023-09-20
forum: New to Ubuntu
---

### Post by p1k1p1k1 on 2023-09-20
Hey guys,
so I recently installed Ubuntu 23.04 on my HP Omen 15 as a dual boot with Windows 10 and my BIOS doesn't seem to recognize Ubuntu as a viable boot options. However when I press F9 before startup and access the HP boot override it is listed there. Is there any way to fix this? I have tried updating grub already.

---

### Post by tea for one on 2023-09-20
Can you successfully boot Ubuntu via the dedicated boot key F9?

---

### Post by p1k1p1k1 on 2023-09-21
Yes I can normally boot into grub using F9

---

### Post by tea for one on 2023-09-21
I'm struggling to fully understand what you want to accomplish.
As Ubuntu appears in your PC boot menu via F9, it is, therefore, recognised by the HP UEFI settings.

Do you want Ubuntu to be the priority boot and allow grub to also control booting Windows?

---

### Post by ajgreeny on 2023-09-21
See **Boot-Repair** in my signature below and follow the instructions there to run the Boot-Info-Script.	 

**Do not run the default repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system.

---

### Post by p1k1p1k1 on 2023-09-22
Right, sorry for taking so long I had to deal with irl stuff, here's the pastebin : [https://paste.ubuntu.com/p/kXgVqWfzW7/](https://paste.ubuntu.com/p/kXgVqWfzW7/)

---

### Post by oldfred on 2023-09-22
HP seems to be the only vendor to not recognize boot order changes with efibootmgr.
Grub install uses efibootmgr to change boot order. 

You can see boot order here, Same as shown starting at line 63 in report.:
sudo efibootmgr -v

Most with HP find they can change boot order in UEFI settings (not UEFI boot menu). There should be a boot tab in the settings menu.
 HP - escape + F9 for UEFI boot menu, F10 for UEFI/bios settings
One of many HP users:
hp 250 g3  Change boot order in UEFI settings
[https://ubuntuforums.org/showthread.php?t=2467077](https://ubuntuforums.org/showthread.php?t=2467077)

Note that Windows updates may reset boot order or UEFI settings back to defaults. It may also update Windows settings to turn on fast startup & then grub will not boot Windows.
Both Windows & Ubuntu/grub on major updates reset boot order. But HP is exception.

---

### Post by p1k1p1k1 on 2023-09-22
Right, I can't do that, is there anything else I can try or am I doomed to spamming f9 to start Ubuntu?

---

### Post by oldfred on 2023-09-22
Some with HP posted it was under a sub-menu or they had to turn off Secure Boot.
You may need to review manual from HP for your model.

---

### Post by tea for one on 2023-09-23
> **p1k1p1k1 said:**
> Right, I can't do that, is there anything else I can try or am I doomed to spamming f9 to start Ubuntu?
Not sure yet, let's investigate further.

Can you access your UEFI settings via F10
Disable TPM
Disable Secure Boot
Disable Legacy Support
System Configuration > Boot Options > OS Boot Manager
Any options under OS Boot Manager?

---

### Post by tea for one on 2023-09-29
I've attached a screenshot to show both Ubuntu and Windows under OS boot manager.
Ubuntu is the default in this picture.

Power on and press F10 to access HP UEFI set up
System Configuration > Boot Options > OS Boot manager (under UEFI Boot Order)

If Ubuntu is the first option, then the PC will boot Ubuntu first.
You can change the default with F5 and F6 keys.

---

### Post by yancek on 2023-10-01
If you have not resolved this issue, some HP computers do not have a System Configuration tab in the BIOS but do have a Boot Options tab with UEFI boot order below it and OS Boot Manager below that.  Arrow down to OS Boot Manager and highlight and hit the Enter Key and it will show any options for different operating systems. If you want to move a highlighted entry down, hit the F5 key, to move it up, hit the F6 key.

---

### Post by pbear42 on 2023-10-18
Looks like the OP has abandoned the thread.  I'll mention another solution anyway.  Perhaps regular helpers will want to bookmark for next time. A lot of early-UEFI HPs (mine was originally Win 8.1) were hard-coded to boot Windows.  One could modify the boot order (as discussed above) but the change didn't survive reboot, i.e., Windows automatically popped back to top of the list.  What worked for me was an idea posted at [Unix & Linux]("https://unix.stackexchange.com/a/242219"), to wit, leave Windows in first place but deactivate it.  Seems absurd that's permitted but not changing boot order, but it worked for me and has for several others on Linux forums to whom I've suggested the fix.

---

### Post by Cushie on 2024-06-17
Just a little more help please.
I have HP250 quite a few years old now and have suffered this topic for many years, it is a nuisance!
I do get System Configeration settings in bios and have is set up as shown inthe  jpg screen shot shown previously but sub option that lists Windows/ubuntu does not appear after highlighting OS BOOT MGR so I cannot change the boot order. Can I edit the Os boot manager direct and place Ubuntu back on top as I don't use Windows very often  .

---

### Post by yancek on 2024-06-17
Are you referring to the image in post 11?  How do you boot now and which version of windows and Ubuntu do you use?  Did you disable secure boot?  Did you check your manual online for your specific HP?  The OS Boot Manager option should have an arrrow/triangle next to it to indicate more than one option available and if none shows, that would indicate there  are not multiple options.

---

