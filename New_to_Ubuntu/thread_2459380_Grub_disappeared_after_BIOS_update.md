---
title: "Grub disappeared after BIOS update"
date: 2021-03-17
forum: New to Ubuntu
---

### Post by ronmuron on 2021-03-17
I use Ubuntu 20.10 and Windows 10 (as a dualboot - on one computer). While on Windows 10 I updated the BIOS and unfortunately after a reboot I no longer have the choice between running Ubuntu or Windows :(

How can I restore the grub? Currently I only have access to Windows 10, which boots automatically.

My laptop: Lenovo ideapad 320S.

I tried to find an answer on the forum, but the solution I found didn't work.

```
C:\WINDOWS\system32>bcdedit /set '{bootmgr}' path \EFI\ubuntu\grubx64.efi
The element data type specified is not recognized, or does not apply to the
specified entry.
Run "bcdedit /?" for command line assistance.

```

---

### Post by tea for one on 2021-03-17
Has your UEFI (née BIOS) or alternatively a Windows 10 update re-activated Fast Start Up (i.e hibernation)?

---

### Post by CelticWarrior on 2021-03-17
> **tea for one said:**
> Has your UEFI (née BIOS) or alternatively a Windows 10 update re-activated Fast Start Up (i.e hibernation)?

This and reset UEFI settings.
Please open the UEFI settings > Boot and change it back to Ubuntu. That should be all. Whenever possible avoid changing those settings from a running OS.

---

### Post by yancek on 2021-03-17
Are you referring to updating the BIOS firmware?  If so, the suggestions above should work.  Other things you need to watch for with windows updates are turning hibernation back on and setting Secure Boot back to on.  The 2nd Secure boot shouldn't be a problem.  I've had this happen and the other Linux failed to boot as it requires Secure Boot off.  I've read posts here that indicate windows also sets itself first in boot order but have not seen that myself.

---

### Post by oldfred on 2021-03-17
Windows updates may update UEFI/BIOS, and will reset UEFI boot order to have Windows first.

Major grub update or install also resets boot order to have ubuntu first, so not really different, just something you have to manage.
But a few systems like HP, do not recognized anything outside of Windows updates. Then you usually have to change boot order from within UEFI settings and boot tab, (not UEFI one time boot selection).

---

