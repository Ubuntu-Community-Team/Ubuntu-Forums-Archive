---
title: "FAQ: Disabling ACPI in Hoary 5.01"
date: 2005-03-20
forum: Outdated Tutorials &amp; Tips
---

### Post by Cybermagellan on 2005-03-20
I'm new to Linux and I have searched high and low on these forums to find out how to disable ACPI on Hoary (because my computer was shutting down every half hour or so) and so after doinking around for awhile I was able to come up with something.

At the loading screen (Grub menu or otherwise) tap on the "e" key to edit your loading parameters.

At the next screen you will see where it says 
```
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda1 ro splash
``` Highlight that using your arrow keys and then once again type "e" to Edit this line.

After the "ro" sentance add:

acpi=off

then tap the enter key on the keyboard. This will bring you back to the menu that has the Kernel line. At this screen tap on the "b" key to boot with that string. This will disable ACPI in Hoary. I'm proud to report that my computer has stayed on aprox 5 straight hours after doing this.

**NOTE:** If this resolves your issue and then you restart the computer you will lose this string however to add it for good then edit the...

/boot/grub/menu.lst file as root and at the end you should see...

```

title		Ubuntu, kernel 2.6.10-5-386 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot
``` 

add the acpi=off between the "ro" and the "quiet" and then save. Now everytime the computer starts it will disable ACPI.

If anyone has any better ideas or thoughts on how to do this please edit my entry OR reply with the better method

---

### Post by hap0 on 2005-03-22
I'm experiencing random and spontaneous "power off" instantly without killing any processes. Needless to say this is a severe problem. Even worse it happens only after a couple of minutes, and thus making it near impossible to fiddle with the settings.

---

### Post by hap0 on 2005-03-22
Oh I should have mentioned that the reason I posted this here was because I tried the options for turning ACPI off but that didn't help.

---

### Post by hcf on 2005-03-22
If I pass acpi=off to the kernel, my wireless stops working. I use ipw2200. Anyone who knows how to solve this? Is it a problem with ipw2200 only?

---

### Post by jkka on 2005-03-22
I have similar problem, allthough the acpi=off option is not an option for me. More about that:

[http://ubuntuforums.org/showthread.php?t=18345](http://ubuntuforums.org/showthread.php?t=18345) 
[http://bugzilla.ubuntu.com/show_bug.cgi?id=7377](http://bugzilla.ubuntu.com/show_bug.cgi?id=7377)

---

