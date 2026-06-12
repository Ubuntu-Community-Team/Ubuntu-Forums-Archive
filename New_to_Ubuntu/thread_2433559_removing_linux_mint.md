---
title: "removing linux mint"
date: 2019-12-20
forum: New to Ubuntu
---

### Post by kendor22 on 2019-12-20
Hello,I have Ubuntu and Linux Mint dual booting on my HD, how can i remove Mint without reinstalling Ubuntu, can i just delete the partition without too much trouble or do i have to use command input.  Regards

---

### Post by oldfred on 2019-12-20
Which ever you installed last controls booting. If you delete Mint & it was last installed, then its grub will try to boot and fail.
You want to make sure Ubuntu is in control of boot.

Is system UEFI or BIOS?

       May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Impavidus on 2019-12-21
> **kendor22 said:**
> ... can i just delete the partition without too much trouble or do i have to use command input.Command input shouldn't be that much trouble.

> **oldfred said:**
> Which ever you installed last controls booting.Usually, but don't count on it. When grub is reinstalled (may happen during an update), the system that last reinstalled grub may take over control. Boot-repair will tell and a simple command can put Ubuntu in control of booting. Then you can simply delete Mint's partition.

---

### Post by yancek on 2019-12-21
>  					Which ever you installed last controls booting

Default behavior on almost any OS installation but not necessarily the case.

> When grub is reinstalled (may happen during an update), the system that last reinstalled grub may take over control

Interesting, I've updated grub on a number of systems and never seen that behavior, if the OS in question did not already have Grub code in the MBR.  EFI of course, totally different.

Boot repair is probably the best way to determine this.  Booting Ubuntu and installing Grub to the MBR or putting it first in boot order if it is EFI before formatting/deleting the Mint partition.  THe latter could obviously be done after as you would simply access the BIOS firmware to make the change.

---

### Post by cpt-ankitsharma on 2019-12-21
Boot into Ubuntu > Delete the partition containing Mint > Do Boot repair before rebooting the system.

---

### Post by yetimon_64 on 2019-12-22
> **cpt-ankitsharma said:**
> Boot into Ubuntu > Delete the partition containing Mint > Do Boot repair before rebooting the system.

It would be a much better idea to give control of the grub boot screen over to the system to remain before deleting the mint partition thus avoiding the need to run boot repair at all.

One command in terminal from within Ubuntu can do so very easily. The exact command would depend on whether the OP is on an MBR installation or on a UEFI installation. An example of the command for UEFI that I use here is...
```
sudo grub-install --efi-directory=/boot/efi /dev/sd**X**
```

"/dev/sd**X**" above would need to be changed to suit the OP's installation, here on my installation it is "/dev/sd**a**"

oldfred has already asked the OP...
> Is system UEFI or BIOS?

When the OP returns and replies to that question the exact command can be given to switch to grub on Ubuntu. That is IF mint has control of the boot screen at present. If Ubuntu controls the boot screen already simply deleting the mint partition is safe to do. Basically we need more info from the OP here.

Regards, yeti.

---

