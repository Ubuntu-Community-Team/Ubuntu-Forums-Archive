---
title: "Grub/restart issue after last update"
date: 2014-11-02
forum: New to Ubuntu
---

### Post by Norm24 on 2014-11-02
I've been using 14.04 for some time now and its the only OS on my machine.I found it curious that I never had a grub menu since install but it affected nothing so I didn't care.

Now here's the problem:after the last update I was asked to restart the computer and I did.Low and behold I now have a grub menu that happens to be the beta version 2.02,so I click on *Ubuntu and assume it will now load the OS but it instead restarts the computer and the grub menu is loaded again.I tried several times with the same result.I also keep the last couple of kernal versions in case of issues and when clicking on those under "advanced options" I get the same result...the machine restarts and the grub menu appears.

I'm at a loss on this one.Any help would be greatly appreciated.

---

### Post by grahammechanical on 2014-11-02
Just to clear things up a bit. It is normal not to get a Grub boot menu when we only have Ubuntu on the machine. We do not need a boot menu unless we have more than one OS. The boot menu is still there but it is hidden.

A beta version of Grub 2.02 has been with Ubuntu for more than 6 months. There is nothing strange there. I have had it on my machine all that time. What is strange is the restarting. If there is something wrong with the boot parameters we usually get dumped at a Grub rescue prompt.

Have you tried Recovery mode and then Resume at the recovery mode menu? I am at a loss as to what to suggest. You could try

1) load a Ubuntu live session
2) make a connection to the internet
3) use the file manager to examine folders on the hard disk. That will mount the partitions.
4) open the terminal and run

```
sudo update-grub
sudo grub-install /dev/sda
```

that will rewrite the Grub configuration files and reinstall Grub into the MBR of the hard disk.

You give no information about the hardware of your machine. Is it BIOS or UEFI? If it is UEFI and there is something in those  settings that is causing this, then I cannot help as I have no experience of UEFI.

Regards.

---

### Post by Bucky Ball on 2014-11-02
You need to boot into the recover kernel from the boot menu (under Advanced Options on the list) and when at the options, drop to a shell (choose the 'root with shell' option) and remove:

.iceauthority
.xauthority

Reboot. Can you log in? Hopefully it's magic.

You can also try this in a shell if the above doesn't work:

```
sudo chown -R user:user .ICEauthority
```

---

### Post by Norm24 on 2014-11-03
Bucky even when I click on recover under Advanced Options,grub still restarts the computer.No matter what I click on the computer still restarts and I'm always back at the grub menu.

---

### Post by Norm24 on 2014-11-03
Graham I'm fairly sure its BIOS being that the machine originally came with Vista Home Basic as the OS.Tried the Live Session and opening a terminal and was able to mount the partitions on the harddisk but have no way of being root without a password in a live session...I have no way of affecting my 14.04 installation without running a terminal within that installation.Opening a terminal in live session I am never prompted to enter a password when entering a sudo command because its a live session and a password does not exist.

---

### Post by oldfred on 2014-11-03
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Did you have an abnormal shutdown? Then fsck may be all that is required, but best to see details first.

---

### Post by Bucky Ball on 2014-11-03
Did you try deleting .iceauthority and .xauthority and rebooting, as I suggested earlier?

---

### Post by Norm24 on 2014-11-06
> **oldfred said:**
> Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Did you have an abnormal shutdown? Then fsck may be all that is required, but best to see details first.

None of this worked.The computer restarts after inserting the boot-repair disc and I am presented with a grub menu that does nothing but restart and then again presents me with a grub menu that is useless.When I put the boot-repair disc it is accessed and then restart like usual.

Oldfred what is fsck?

---

### Post by Norm24 on 2014-11-06
> **Bucky Ball said:**
> Did you try deleting .iceauthority and .xauthority and rebooting, as I suggested earlier?

You simply did not read what I posted,I can't boot my machine.How the hell can I delete something I can't even boot into?!There is no access to booting into a recovery kernal.Please read next time.

---

### Post by Bucky Ball on 2014-11-06
> **Norm24 said:**
> You simply did not read what I posted,I can't boot my machine.How the hell can I delete something I can't even boot into?!There is no access to booting into a recovery kernal.Please read next time.

So that means you can't boot from Live media either? Yes, I'm reading, so while I understand your frustration, take it easy. ;)

---

### Post by oldfred on 2014-11-06
Are you trying to boot the Ubuntu live installer or the Boot-Repair liveCD? 
Some find that the Ubuntu live installer and adding Boot-Repair works better.

You just add the ppa and download Boot-Repair into the live installer.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

