---
title: "grub2 error"
date: 2012-05-17
forum: New to Ubuntu
---

### Post by lokisapocalypse on 2012-05-17
Hi all, 

I've seen online that a lot of people got a grub error when upgrading to 11.04. I'm getting that too but the difference is that I am running this on a virtual machine so I'm not sure if I can do the LiveCD thing.

I've found a few guides on how to do it but I keep getting a message:

grub rescue> insmod /boot/grub/linux.mod
error: the symbol 'grub_mm_base' not found

So it seems like the best thing at this point would be to do it from the LiveCD but how do you do that with a VMWare installation?

---

### Post by wilee-nilee on 2012-05-17
You can use a live cd in virtual box, just set the cd as the boot like when you installed. Use the settings-storage to have the cd read. Then download this script and extract it to the desktop, and run the command. A results.txt will appear, copy and paste it to a reply on this thread. When you open the reply click on the # in the reply panel generating code tags paste the text in between them.

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)     

```
sudo bash ~/Desktop/bootinfoscript
```

With vmware not sure, if this is a vdi though you can use vbox to do this with the .vdi I believe. You just have to set up the machine to use that ,vdi rather then making one.

---

### Post by kc1di on 2012-05-17
> **lokisapocalypse said:**
> Hi all, 

I've seen online that a lot of people got a grub error when upgrading to 11.04. I'm getting that too but the difference is that I am running this on a virtual machine so I'm not sure if I can do the LiveCD thing.

I've found a few guides on how to do it but I keep getting a message:

grub rescue> insmod /boot/grub/linux.mod
error: the symbol 'grub_mm_base' not found

So it seems like the best thing at this point would be to do it from the LiveCD but how do you do that with a VMWare installation?
Try boot repair it can be run from within the VM.
get it here:

[http://www.ubuntugeek.com/boot-repair-simple-tool-to-repair-frequent-boot-problems.html]("http://www.ubuntugeek.com/boot-repair-simple-tool-to-repair-frequent-boot-problems.html")

---

### Post by lokisapocalypse on 2012-05-17
I can't get past the grub rescue> 
screen into Ubuntu to run the boot repair though.

---

### Post by kc1di on 2012-05-17
Do you have a lot of important files in the Ubuntu on the VM. I Don't remember which one your using.  But if it V.B. I'd just uninstall and reinstall Ubuntu.

---

### Post by lokisapocalypse on 2012-05-17
> **kc1di said:**
> Do you have a lot of important files in the Ubuntu on the VM. I Don't remember which one your using.  But if it V.B. I'd just uninstall and reinstall Ubuntu.

Unfortunately I do so I'd rather not just reinstall if I can help it.

---

### Post by kc1di on 2012-05-17
have you tried wilee-nilee suggestion yet?

---

