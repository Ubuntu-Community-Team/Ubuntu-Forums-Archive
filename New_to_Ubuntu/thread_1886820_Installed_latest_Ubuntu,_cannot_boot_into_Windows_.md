---
title: "Installed latest Ubuntu, cannot boot into Windows 7"
date: 2011-11-25
forum: New to Ubuntu
---

### Post by dmeadows013 on 2011-11-25
I have recently installed Ubuntu side by side with Windows 7. The installation completed fine, but now I cannot boot into Windows. As soon as the boot goes through the Bios loader, It boots into Ubuntu. I would like to set it up so that it shows the Win7 Bootloader asking me which OS I would like to boot into, as it did with Wubi. If anyone could help me with this, that would be great.

---

### Post by batharoy on 2011-11-25
In a terminal
```
sudo update-grub

```

---

### Post by BC59 on 2011-11-25
You could repair it with Boot-Repair.

Check here:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Mark Phelps on 2011-11-25
You probably don't need to repair the boot; instead, do the terminal command.  That will regenerate the GRUB menu and add an entry for Windows.

---

### Post by dmeadows013 on 2011-11-25
Tried both, and neither worked. Just goes straight from the BIOS to a screen that says "Video Mode Not Supported", hangs there for a few seconds, and then boots into 11.10.

---

### Post by drs305 on 2011-11-25
It could be the error is preventing the Grub menu from displaying. When it appears to 'hang', it may be doing the 10 second timeout and you just can't see the Grub menu. Press ESC to see if the menu appears.

After booting into Ubuntu (either with or without the error):
Open the Grub settings file, /etc/default/grub and try removing the # symbol from the start of the GRUB_GFXMODE=640x480 line. This will force Grub to use the standard resolution.
```

gksu gedit /etc/default/grub
```

Remove the # symbol from the beginning of this line:
> GRUB_GFXMODE=640x480
Save the file, then:
```
sudo update-grub
```

There may be other Grub video issues, but this is the easiest to try first.

---

### Post by bluexrider on 2011-11-25
> **Mark Phelps said:**
> You probably don't need to repair the boot; instead, do the terminal command.  That will regenerate the GRUB menu and add an entry for Windows.

Mark, what would that command be? I'm sure he could use the help!

---

### Post by dmeadows013 on 2011-11-25
> **bluexrider said:**
> Mark, what would that command be? I'm sure he could use the help!

I assume he was talking about the Grub update command. I tried that and it did nothing. I am trying the edit to the Grub file now.

---

### Post by dmeadows013 on 2011-11-25
> **bluexrider said:**
> Mark, what would that command be? I'm sure he could use the help!

Awesome! Worked perfectly! Thanks!

Now, is there a way to have it boot straight into Windows instead of having it bring me to the Windows Bootloader? I selected Windows 7 in Grub, and it brings me to another boot menu. Not a major problem, as I can boot both operating systems fine now, just wondering if there is a way. Thanks again!

---

### Post by lolpenguin on 2011-11-26
You probably can't do this, unless you delete C:\BOOTMGR (DON'T TRY THIS) but it will probably mean you won't be able to boot Windows.

---

### Post by drs305 on 2011-11-26
> **dmeadows013 said:**
> Awesome! Worked perfectly! Thanks!

Now, is there a way to have it boot straight into Windows instead of having it bring me to the Windows Bootloader? I selected Windows 7 in Grub, and it brings me to another boot menu. Not a major problem, as I can boot both operating systems fine now, just wondering if there is a way. Thanks again!

You could probably edit the Windows 7 boot settings to change the timeout to 0 or 1 second in the Windows menu. 

I think you can use Bcdedit.exe in the Windows terminal or change the timeout by right clicking My Computer. Select "Properties". then on the left, Advanced System Settings > Advanced > Startup & Recovery settings.

I'm not a Windows user so those instructions may not be exact, but you should be able to get there from here.

---

