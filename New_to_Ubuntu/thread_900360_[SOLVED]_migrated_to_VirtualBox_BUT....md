---
title: "[SOLVED] migrated to VirtualBox BUT..."
date: 2008-08-25
forum: New to Ubuntu
---

### Post by macvr on 2008-08-25
hi,
i'v migrated from qemu to VirtualBox Full[PUEL] edition from the SUN Download site[ not via synaptics]
1-BUT when i check in the synaptics, it shows in the Status section:
_virtual box 1.6.4 as INSTALLED[local or obsolete]_, this is the first time i got that in the status
that is the latest version available!

what does that mean? i checked for a glossary on synaptics statuses but couldnt find any!

2-now that i have shifted to VirtualBox can i uninstall qemu,kqemu?
or does VirtualBox need them ? why i got this doubt is ,since i used qemu to convert the .img file to .vdi

3-can i use archive manager to compress the .vdi file , to save the .vdi as a backup?
which format of compression is best for this purpose & also gives the max compression?

---

### Post by tangibleorange on 2008-08-25
> **macvr said:**
> hi,
i'v migrated from qemu to VirtualBox Full[PUEL] edition from the SUN Download site[ not via synaptics]
1-BUT when i check in the synaptics, it shows in the Status section:
_virtual box 1.6.4 as INSTALLED[local or obsolete]_, this is the first time i got that in the status
that is the latest version available!

what does that mean? i checked for a glossary on synaptics statuses but couldnt find any!

2-now that i have shifted to VirtualBox can i uninstall qemu,kqemu?
or does VirtualBox need them ? why i got this doubt is ,since i used qemu to convert the .img file to .vdi

3-can i use archive manager to compress the .vdi file , to save the .vdi as a backup?
which format of compression is best for this purpose & also gives the max compression?

1. 'Local or Obsolete' simply refers to the fact that you installed the .deb manually and not from one of synaptic's repos. you don't need to worry - all is well with your system :)

2. I'm not at all sure on this one, but because Virtualbox is based on QEMU, it's probably best to leave them. someone else probably knows for sure however.

3. the two most common types of compression I know are .tar.gz and .tar.bz2. .gz compresses and decompresses faster but reduces the filesize by less, and bz2 compresses and decompresses slower but reduces the filesize by more. so, you have a choice there.

---

### Post by Elfy on 2008-08-25
I have PUEL vbox and have never installed qemu or kqemu.

Can't help with 3 though ,and as tangibleorange says 1 is no worry.

---

### Post by Thelasko on 2008-08-25
for #2 if you installed VirtualBox via a .deb file, synaptic should warn you if you try to uninstall QEMU and VirtualBox depends on it.  It should say something to the effect of:
> Mark additional required changes?
The chosen action also affects other packages.  The following changes are required in order to proceed.
To be removed.
VirtualBox
Cancel Mark?

That's what makes Ubuntu (and Debian) so awesome!

[Here's a picture]("http://img61.imageshack.us/img61/8512/screenshot4an.png") of what it looks like.

---

### Post by macvr on 2008-08-25
so i'm rest assured that it will NEVER REMOVE virtualbox dependant files?

*i'm new to ubuntu & just getting the hang of it*

just check out the screenshot of the auto removable files,after i'v removed qemu, kqemu
 the first few in the list seem regular system required[i dont know for sure just guessing:confused: but there is a html2text!]

---

### Post by Elfy on 2008-08-25
All I can say is that I have none of those installed.

---

### Post by macvr on 2008-08-25
^^^thats good enough for me to remove them

---

