---
title: "windows 10 seems as windows 8 at kubuntu grub"
date: 2015-10-31
forum: New to Ubuntu
---

### Post by umut6 on 2015-10-31
Hello everyone,

I am a kubuntu user and i have 2 operating systems in my laptop (windows for work and kubuntu for personal).How did i make it?

1) I installed windows 8
2) I installed kubuntu 15.04 over it

windows has 250 gb of my hard disc and kubuntu has the other 250gb.I have no technical problems with them.(Total 500 gb hard disc)

yesterday i set up windows 10 and it did not spoil my kubuntu grub as i thought it would.However, there is no windows 10 in the menu, instead windows 8; and when i select windows 8, then windows 10 starts.

I know its not a big deal but is there a way to edit the menu list as "windows 10" instead of "windows 8".

Sorry for my english and thanks very much from now.

---

### Post by yancek on 2015-10-31
> yesterday i set up windows 10 and it did not spoil my kubuntu grub as i thought it would.

While your luck holds out, time to buy a lottery ticket!

To change your menu, go to the /etc/grub.d directory and you should see a file name 40_custom.  Open it as root (use sudo) and copy the windows 8 entry from /boot/grub/grub.cfg file and change the 8 to 10, or whatever other change you might want.  Save the file and run:  sudo update-grub.  Watch the output for the change.

You could manually edit the grub.cfg file but as it says at the top of the file, when you run update-grub, any changes made in that file will not be saved so the above is the way to do it.

---

### Post by grahammechanical on 2015-10-31
Is this the Grub boot menu? If so, then open a terminal and run

```
sudo update-grub
```

and watch the printout. See if it detects a Windows boot loader and labels it as Windows 10. If you upgraded Windows 8.1 to Windows 10, then it is possible that the same boot loader for Windows is being used.

Regards.

---

### Post by umut6 on 2015-10-31
I did exactly the same what you told me to do, but it did not work:

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows 10 (loader) (on /dev/sda1)' --class windows --class os $menuentry_id_option 'osprober-chain-1020B45120B43F90' {
    insmod part_msdos
    insmod ntfs
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  1020B45120B43F90
    else
      search --no-floppy --fs-uuid --set=root 1020B45120B43F90
    fi
    parttool ${root} hidden-
    drivemap -s (hd0) ${root}
    chainloader +1
}
set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=30
fi
### END /etc/grub.d/30_os-prober ###

This is the part i copied and edited, is it wrong?

Note: after updating grub, it still shows windows 8.

---

### Post by oldfred on 2015-10-31
Did you overwrite the script in 30_os-prober?

You were supposed to copy boot stanza from grub.cfg and copy into 40_custom. Then you can edit description.

Once you know it works, then you turn off os-prober, not overwrite it with either of these:
 gksudo gedit /etc/default/grub:
GRUB_DISABLE_OS_PROBER=true
or
sudo chmod a-x /etc/grub.d/30_os-prober
sudo update-grub

---

### Post by umut6 on 2015-11-01
Before your reply i got a notice of that i can upgrade my kubuntu from 15.04 to 15.10; and i accepted it.

After the installation previous problem has been disappeared, i now can see windows 10 instead of windows 8.

However, now i can't open Kubuntu regularly, it stucks at kubuntu logo for a while, the laptop gets too hot and it shuts off.

i tried too many times, its repeating; but i can open kubuntu via recovery mode.Why does it open in recovery mode but not in regular mode, any help please?

By the way, in recovery mode my desktop is 1024-768, is it normal? When i click to "start" button, it covers the half of the screen, takes too much space.it looked a little weird to me.[ATTACH=CONFIG]265311[/ATTACH]

---

### Post by yancek on 2015-11-01
Because you upgraded to a new version, you may need to install graphic drivers again.  I don't use Kubuntu so I'm not sure how you would do this but there should be a software center or system settings option somewhere and look for an "Additional Drivers" option.

---

