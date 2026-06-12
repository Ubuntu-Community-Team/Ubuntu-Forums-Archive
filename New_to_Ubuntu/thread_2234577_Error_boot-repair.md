---
title: "Error boot-repair"
date: 2014-07-15
forum: New to Ubuntu
---

### Post by pbaudi on 2014-07-15
Soy nuevo en esto de ubuntu y no consigo hacer un arranque dual con windows 8.1
Boot Repair me da esta dirección. [http://paste.ubuntu.com/7799183](http://paste.ubuntu.com/7799183)

gracias

---

### Post by oldfred on 2014-07-15
You are in the English language part of the forums.
There are Local Lo_Co sub-forums for Spanish depending on the region you are in. 
I can move thread to another forum if you are not comfortable with English.

[http://ubuntuforums.org/forumdisplay.php?f=183](http://ubuntuforums.org/forumdisplay.php?f=183)

Script did not show the efi boot files in your sda2 efi partition. Not sure why.
Can you boot from UEFI menu either or both Windows and Ubuntu entries?

---

### Post by pbaudi on 2014-07-16
Oldfred Hi, thanks for the reply. 
Just start with windows. 
To start with ubuntu should I enter the boot menu with F9 and select ubuntu, after it featured a menu where I can launch ubuntu, windows, etc.. 

Sorry for my English.

Hola oldfred, gracias por la respuesta.
Sólo arranca con windows.
Para arrancar con ubuntu debo entrar al menu de la boot con F9 y seleccionar ubuntu, tras esto aparece un menu donde puedo lanzar ubuntu, windows, etc.

Lo siento por mi inglés.

---

### Post by yancek on 2014-07-16
> Just start with windows

Does that mean you can boot windows 8?  Do you see an option when using the F9 key for Ubuntu?  If you do, you could try selecting it to see what happens.  The post above by oldfred is asking  what you can boot because there are no efi files in its partition, sda2.  Did you use uefi to boot on windows 8 and Ubuntu?

---

### Post by oldfred on 2014-07-16
Just to clarify, are there these folders with efi files and it was just script for some reason did not show them?

       /EFI/Boot
/EFI/Microsoft
/EFI/ubuntu

Several users posted UEFI screens showing Windows and/or Ubuntu. You should have similar boot options in your UEFI, although every company's UEFI menu looks different.

---

