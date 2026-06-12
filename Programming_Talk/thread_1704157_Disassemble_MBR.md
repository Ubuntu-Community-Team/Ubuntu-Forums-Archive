---
title: "Disassemble MBR"
date: 2011-03-10
forum: Programming Talk
---

### Post by YesWeCan on 2011-03-10
I would like to learn how master boot records work.
Having copied the first sector to a file using dd I would like to disassemble the binary into assembly mnemonics.
What is the best tool for this? Thanks.

---

### Post by matt_symes on 2011-03-10
Hi

If you are interested in a hexdump try something like

```
sudo dd if=/dev/sda count=1 | hexdump -C
```

change if= as appropriate. Not all the 512 bytes of the MBR holds code. It also holds the primary partition table. If you want to see grubs first stage boot loader why don't you disassemble 

```
/boot/grub/boot.img
```

and for the second stage disassemble

```
/boot/grub/core.img
```

I believe core.img get placed at sector 63 odd (but i might be wrong)

Kind regards

---

### Post by matt_symes on 2011-03-10
Hi

My second post seems to have to lost somewhere in the ether. :confused:

Anyhow to disassemble boot.img, core.img

```
sudo apt-get install nasm
ndisasm /boot/grub/boot.img
```

Kind regards

---

### Post by YesWeCan on 2011-03-10
nasm is exactly what I was looking for.
Thanks muchly. :smile:

---

