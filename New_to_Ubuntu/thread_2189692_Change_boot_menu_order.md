---
title: "Change boot menu order"
date: 2013-11-23
forum: New to Ubuntu
---

### Post by manudo on 2013-11-23
I just installed Ubuntu 12.04 LTS in my computer but I share it with other people that use Windows so I need when someone turn on the computer, on the boot menu the Windows 7 loader will be highlighted for automatic booting.
How I can do that?
Thank you. :)

---

### Post by electrohandyman501 on 2013-11-23
What boot loader are you using.

---

### Post by deadflowr on 2013-11-23
I can think of three different ways you can do this.

1) change the grub_default in the file /etc/default/grub.
Open that file as root
```
gksu gedit /etc/default/grub
```
and change the line
```
GRUB_DEFAULT=0
```
to what ever number in the line the windows7 entry is.
Note that 0(zero) is the first entry, so it might take a try or two to figure out grubs numbering.

2)Install grub-customizer
[https://launchpad.net/grub-customizer](https://launchpad.net/grub-customizer)

3)Make custom grub scripts
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen#Making_the_custom_Grub2_Menu_entries](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen#Making_the_custom_Grub2_Menu_entries)
Note on custom scripts
If you go this route, make sure the entires have no spaces in between them
Like so
```
menuentry "Ubuntu" {    set root=(hd0,1)
        linux /vmlinuz root=/dev/sda1 ro quiet splash
        initrd /initrd.img
}
menuentry "Windows" {
  insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set WindowsUUIDHERE
    chainloader +1
}
```
instead of
```
menuentry "Ubuntu" {    set root=(hd0,1)
        linux /vmlinuz root=/dev/sda1 ro quiet splash
        initrd /initrd.img
}

menuentry "Windows" {
  insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set WindowsUUIDHERE
    chainloader +1
}
```

Notice the space after the } and before the menuentry for Windows.
If there is a space, then the file won't load and will generate a syntax error.
Also note that these are simple generic entries for examples only.

Of the three options, you might do best with grub-customizer.
If any problems happen look over this for help fixing them
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Good Luck, in which ever way the wind blows you.

---

### Post by manudo on 2013-11-23
My god, what an answer!
Thank you very much!

---

### Post by deadflowr on 2013-11-23
Two things I forgot to mention.

1) If using wubi, then I don't know if any of what I posted would work.

2) At least with the custom option and the editing of the /etc/default/grub file (not sure about the grub-customizer option), any changes made won't become part of the system until the command
```
sudo update-grub
```
is run.

---

### Post by manudo on 2013-11-24
> **deadflowr said:**
> Two things I forgot to mention.

1) If using wubi, then I don't know if any of what I posted would work.

2) At least with the custom option and the editing of the /etc/default/grub file (not sure about the grub-customizer option), any changes made won't become part of the system until the command
```
sudo update-grub
```
is run.

I've used the grub-customizer, it's so easy.
Thank you very much! :)

---

