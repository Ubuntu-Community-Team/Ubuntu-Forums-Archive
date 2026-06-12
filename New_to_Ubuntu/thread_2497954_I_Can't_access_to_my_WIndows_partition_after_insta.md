---
title: "I Can't access to my WIndows partition after installing Ubuntu"
date: 2024-05-23
forum: New to Ubuntu
---

### Post by kogarashi on 2024-05-23
Hello, I don't really know how the things are done here but I would really appreciate some help if anyone knows what to do in this situation.

The thing is, I needed Linux for some reasons and I just installed Ubuntu since it's the most well known distribution but after installing and turning off and on my laptop just boots Ubuntu directly  not the GRUB, then I repaired the GRUB using boot-repair but after I tried selecting windows from the GRUB it only sent me an error about not finding the boot of Windows, I really need help and I'm sorry if I'm not explaining myself coherently, I'm really stressed out and also, english is not my first language. The error it sents me is this: "error: fichero <</EFI/Microsoft/Boot/bootmgfw.efi>> no encontrado" I assume it's just the boot archives that are not where they are supposed to be but I don't know what to do to recover them, I already re assured myself that all of my Windows partition data is still there but there's no way to boot WIndows, Can anyone help me please?

---

### Post by grahammechanical on 2024-05-23
Welcome to Ubuntu forums

We do like to know what version of Ubuntu you are using. All things about Linux Ubuntu are being improved all the time and different versions sometimes do things differently.

Do you know what the Terminal is and how to load it? Open the terminal and type

```
sudo update-grub
```

You will be required to put in the password you set when you installed Ubuntu. Watch the printout. Does it show Windows in the list?

We also like to see the boot repair summary before you allow boot repair to do the repair. It helps us to understand the situation before boot repair does its stuff. After running the repair the situation has changed.

Please run boot repair again and select the summary report option and post the internet link to the pastebin location. That summary report will tell us a lot about the setup of your machine.

Regards

---

### Post by yancek on 2024-05-24
> then I repaired the GRUB using boot-repair 

The instructions on the boot repair page specifically state that if you are unfamiliar with the Grub bootloader, to use the Create BootInfo Summary option and NOT try any repairs.  You need to do that now as suggested if you still need help.  The file that is not found is the primary windows boot file necessary to boot windows in EFI mode.  You can easily check if that file exists by opening a terminal and using this command to output information:

```
sudo ls /boot/efi/EFI/Microsoft/Boot
```

If that file is not there or is corrupted, you will need some windows software to repair it.  There are different possibilities as to what the problem is so you do need to post the boot repair summary.

---

