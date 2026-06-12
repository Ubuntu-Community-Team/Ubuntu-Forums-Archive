---
title: "Multi-boot Windows 10/Ubuntu"
date: 2017-01-31
forum: New to Ubuntu
---

### Post by peha1507 on 2017-01-31
Hi, I have tried to make a multiboot with Windows 10 & Ubuntu but now Windows 10 isn't starting up anymore. I have tried with boot-repair to repair the startup but that doesn't work. I have a paste2 link [http://paste2.org/Kc6PhB4C](http://paste2.org/Kc6PhB4C).

Can anybody help me?

Thanks

---

### Post by TheFu on 2017-01-31
Welcome to the forums.

I don't know **anything** about Win10 or UEFI.

However, looking at the data you posted, it appears the machine has a 1TB disk and 979GB is used by Linux according to the **parted** output.  That isn't good, if you intended to leave a working Win10 setup.  I believe that win10 install is gone, overwritten for some reason.

Hopefully, you created a complete backup for anything you need first. 

Let some others review the pastebin data and respond before doing anything. They often have solutions that I do not.

---

### Post by oldfred on 2017-01-31
You must not have used the erase everything option as it looks like you still have the HP Windows recovery partition.

HP also puts many HP tools .efi boot entries into UEFI and then Boot-Repair sees .efi files adds them all to grub menu cluttering grub menu. You probably want to remove most or all of those from 25_custom.

HP also is not UEFI dual boot friendly. It violates UEFI standard that specifically says not to use description as part of boot. And of course only valid description is "Windows Boot Manager". But multiple work arounds, some better depending on configuration.

If you want to restore Windows, you may have to have the original NTFS partition for it to reinstall into. Or it may just totally redo drive. Not sure how HP's recovery works. 
Always better to have your own full backup of the Windows install. 

You should be able to use HP's one time boot key, probably escape & f10 or f9 to directly boot Ubuntu from UEFI boot menu.
And ubuntu entry probably cannot be set as default boot, due to description check. If only booting Ubuntu, we change Windows boot description to boot Ubuntu file. It only checks description not actual boot file.
If dual booting HP usually has a fallback or hard drive boot entry that is a copy of Windows boot .efi file. We can make that be Ubuntu/grub's boot file and use the hard drive entry. Boot-Repair may have already copied that file as now you show /EFI/Boot/bkpbootx64.efi (probably Windows file) and /EFI/Boot/bootx64.efi. 

See if any of the internal hard drive entries work, or directly booting Ubuntu from UEFI boot menu.

If restoring Windows you may have to redo partitions and erase Ubuntu temporarily, Then use Windows tools to shrink the NTFS Windows partition and reboot so it can run chkdsk. Then create new /, swap, /home and any other partitions you want. Or default install of / & swap.

More details on UEFI in link in my signature. And links to even more info.

---

### Post by peha1507 on 2017-02-02
I am not getting it done. I can start Ubuntu but I can not recover Windows 10. I don't see any drives or so.

---

### Post by TheFu on 2017-02-02
> **TheFu said:**
> looking at the data you posted, it appears the machine has a 1TB disk and 979GB is used by Linux according to the **parted** output.  That isn't good, if you intended to leave a working Win10 setup.  I believe that win10 install is gone, overwritten for some reason.

979G for Linux on a 1TB disk doesn't leave much room for the old Windows install. Basically, it is gone. Think I remember seeing a Win recovery partition. Don't know hot to use it, but I'm almost positive it will wipe Linux from the machine. 

Before you do anything, make a backup or 2 of the things you need. This will probably get ugly.

---

