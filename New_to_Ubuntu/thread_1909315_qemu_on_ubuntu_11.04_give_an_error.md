---
title: "qemu on ubuntu 11.04 give an error"
date: 2012-01-15
forum: New to Ubuntu
---

### Post by shan88 on 2012-01-15
im using ubuntu 11.04.i`m doing L4 based development for my project.i made an iso of l4-pistachio and i loaded it to qemu with following command

[B]qemu -fda fdimage.img
[/B]


it booted and gave an error 

[B]open /dev/kvm: No such file or directory
Could not initialize KVM, will disable KVM support
kvm: pci_add_option_rom: failed to find romfile "pxe-rtl8139.bin"[/B]

im in a real trouble now.please somebody help me.i cant move forward with my project with this situation.please help me

---

### Post by shan88 on 2012-01-15
please some body help me

---

### Post by jabbadoo on 2012-01-16
in your terminal run:
```
cat /etc/cpuinfo | egrep '(vmx|svm)'
```
paste the output or tell us if there is no output at all.

---

