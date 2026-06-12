---
title: "Can Not Delete Wubi installed Unbuntu 11.04"
date: 2013-11-12
forum: New to Ubuntu
---

### Post by lrayetal on 2013-11-12
I had installed Unbuntu 11.04 using Wubi Installer on a Windows Vista pc. Some time later I purchased and downloaded Windows 8 from MS on-line on the Windows Vista PC. Now I would like to
delete the Unbuntu 11.04 because I can not update it, and install Unbuntu 12.04 LTS. However I can not delete Unbuntu 11.04 as Windows 8 does not list Wubi in Programs/Uninstall of Control Panel.

Anyone know how I can delete Unbuntu 11.04 now that I have updated Vista to Win 8? I am a very senior senior and slow in learning Unbuntu.

Thank you for any help.

---

### Post by fantab on 2013-11-12
Perhaps this will help: [https://help.ubuntu.com/community/Wubi#Uninstall_from_Windows_8](https://help.ubuntu.com/community/Wubi#Uninstall_from_Windows_8)

---

### Post by bcbc on 2013-11-12
Or this: [https://wiki.ubuntu.com/WubiGuide#How_do_I_manually_uninstall_Wubi.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_manually_uninstall_Wubi.3F)

For information about the bcdedit change (to remove the Ubuntu entry from the Windows boot manager) if required see this [http://askubuntu.com/questions/145444/how-do-i-remove-the-extra-ubuntu-option-on-the-windows-boot-manager-menu]("http://askubuntu.com/a/145605/14916")

---

### Post by thesleash on 2013-11-15
you could use technet.microsoft.com to download some apps to help from within windows, or you could use a live cd and delete files pretty easily from ntfs

---

### Post by lrayetal on 2013-11-16
fantab, Thank you for your reply and suggestion; however Ubuntu is not listed in Programs and Features using this procedure. I do see Ubuntu listed under C:\Programs/Ubuntu. Under Unbunt here there
is a Wubi uninstaller, but I can not use the uninstaller by double clicking it and deleting Wubi, nor by right clicking and trying the same as "Administrator."

---

### Post by lrayetal on 2013-11-16
bcbc, Thank you for your reply and links to delete my Wubi installed Ubuntu in Win8. However they are too complex for my old brain to understand. I am not familiar at all with the registry. I do not see wubi in programs and features.
However I do see Ubuntu in C:\programs/ubunu. If I open this ubuntu file I see a wubi uninstaller, but double clicking the wubi uninstaller does nothing nor doing the same as Administrator. You mentioned using a Live CD to uninstall it.
I have read how to boot to a device in Win8 and I have a Live Ubuntu CD. I don't understand how to delete wubi ubuntu using the Live Ubuntu CD...where to go and how to delete it. Is there a way to delete/uninstall Wubi Ubuntu without going into the registry?

---

### Post by lrayetal on 2013-11-16
Thanks for your reply theleash. I am old and know nothing about the registry. I have a Live Ubuntu CD but wouldn't know where to look to delete Wubi ubuntu. Although I don't see wubi ubuntu in programs and features, I do see it
in C:\programs/ubuntu. If I open this file I can see a wubi uninstaller, but clicking on it does nothing nor trying to open the uninstaller as "Administrator." How could I use some downloaded aps to delete it from within windows?
Thanks again for your time.

---

### Post by bcbc on 2013-11-16
The folder should be C:\ubuntu which contains most of what you need to remove. Deleting it will free up the space taken by the virtual disk.
I doubt there is any registry entry since you upgraded to Windows 8.

If you get the Windows boot manager every time you boot (sometimes these live through upgrades) then there are ways to remove it or suppress it. If not, then there is nothing more to do.

---

