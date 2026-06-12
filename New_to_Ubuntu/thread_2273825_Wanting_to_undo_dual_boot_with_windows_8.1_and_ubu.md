---
title: "Wanting to undo dual boot with windows 8.1 and ubuntu 14.04"
date: 2015-04-15
forum: New to Ubuntu
---

### Post by StarFawks_ on 2015-04-15
so set up a dual boot for my windows 8.1 and ubuntu 14.04, but then realized that i dont really have use for the ubuntu side and want the space back for the windows side. I had tried to do this before and ended up bricking my computer for a little bit, someone please help! taking up 70 gigs that I need

---

### Post by Vladlenin5000 on 2015-04-15
Perhaps this will refresh your memory: [http://ubuntuforums.org/showthread.php?t=2270625](http://ubuntuforums.org/showthread.php?t=2270625)

---

### Post by Geoffrey_Arndt on 2015-04-15
Are you able to boot successfully into Windows now  . . . ?  Yes or No?

---

### Post by StarFawks_ on 2015-04-16
Yes I can boot into ubuntu and Windows, last time I tried deleting the ubuntu partition cause I was following a tutorial and that's what bricked my computer

---

### Post by Kenneth_Benson on 2015-04-16
It depends on if you are using grub to dual boot or the windows bootmgr. Deleting the Ubuntu partition if you are using grub will brick it. The easiest way that I have found is as follows:  Download EasyBCD and install it in Windows. Read the help/docs that come with it. One of the menus will allow you to replace grub with the windows manager and will add the windows partition automatically. Once you have done that you can wipe the Ubuntu partition. If you are using the windows bootmgr then this same program will allow you to remove the Ubuntu selection. To regain the open space that was Ubuntu, I recommend just using windows disk manager to make the space a new drive letter. Trying to add it to the existing drive letter can be done but you need a program like Partition Magic to do it.

Checked my memories; click on bcd backup/repair, select Re-create/Repair boot files, then click perform action. That will put Windows back in control. Click on edit menu and remove the Ubuntu selection if it showed up.
Now that windows is in control, you want to open the disk manager and delete the non-windows partition, then create a new volume in that free space, let it format it as ntfs and there you go.

---

### Post by Geoffrey_Arndt on 2015-04-16
> **StarFawks_ said:**
> Yes I can boot into ubuntu and Windows, last time I tried deleting the ubuntu partition cause I was following a tutorial and that's what bricked my computer

Here is one method (from MS-Website Forums)  [http://answers.microsoft.com/en-us/windows/forum/windows_8-system/how-do-i-manually-remove-ubuntu-from-my-windows-8/6cce0918-f049-42b4-879a-5903af47f45d](http://answers.microsoft.com/en-us/windows/forum/windows_8-system/how-do-i-manually-remove-ubuntu-from-my-windows-8/6cce0918-f049-42b4-879a-5903af47f45d)

Here is another method:  [http://www.makeuseof.com/tag/how-to-safely-uninstall-ubuntu-in-windows-dual-boot-environment/](http://www.makeuseof.com/tag/how-to-safely-uninstall-ubuntu-in-windows-dual-boot-environment/)

Here is YAUM (Yet Another Uninstall Method):  [http://askubuntu.com/questions/133533/how-to-remove-ubuntu-and-put-windows-back-on](http://askubuntu.com/questions/133533/how-to-remove-ubuntu-and-put-windows-back-on)

Do a print of each method, get comfortable, get a large cup of great coffee, get a yellow-highlighter & read-highlight each article (print-out).

---

### Post by Vladlenin5000 on 2015-04-16
Oh yes, me too, you'd have to pay me to use Windows (any Windows) and no, I don't come cheap...
That say, as you can see from the last post, everything points to Windows tutorials as it should be. As soon as you delete the partitions where Ubuntu used to run from, you no longer have Ubuntu, just a leftover Grub. All you have to do is boot from the Windows installation media (or a Windows recovery media) to "repair" the boot process. This and everything else you need to do can and should be done from Windows, including the expansion of the current main Windows partition to the now unallocated space.

So, all hings considered, again my question, the one you conveniently ignored before, what support do you need from us, exactly?

---

