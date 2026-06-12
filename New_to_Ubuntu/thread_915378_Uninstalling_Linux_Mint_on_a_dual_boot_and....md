---
title: "Uninstalling Linux Mint on a dual boot and..."
date: 2008-09-09
forum: New to Ubuntu
---

### Post by h8uthemost on 2008-09-09
Hey guys,

I'm running XP with Mint as a dual boot. Now, I want to uninstall Mint, and go back to Ubuntu. But...I want to go back to using Ubuntu through Wubi. So I want to get rid of the Mint partition, and the Swap partition altogether.

So, can I just delete those two partitions, then install Ubuntu through Wubi, and Ubuntu will take care of Grub by itself? Or am I going to have to fix Grub or something before I install Ubuntu through Wubi?

Also, what is a good way to go about deleting those two partitions?

Thank you for your help.

EDIT: Would Norton Partition Magic be a good way about deleting these partitions? Or is there a better way?

---

### Post by kk0sse54 on 2008-09-09
Through Gparted from a Ubuntu LiveCD you will be able to delete the two partitions and expand your windows partition then from Windows you can install Ubuntu through Wubi. Just make sure to restore the MBR otherwise it will keep looking for grub and you won't be able to boot into windows.
This link could be some help to you [https://lists.ubuntu.com/archives/ubuntu-users/2006-December/102255.html](https://lists.ubuntu.com/archives/ubuntu-users/2006-December/102255.html)

---

### Post by h8uthemost on 2008-09-09
Thank you C!oud. Unfortuntely I don't think I have the XP cd anymore, so is there any other way to restore MBR? The link you gave me isn't coming up, so I don't know if it explains it in there.

So what I do is download Ubuntu, burn it to a cd. Then start it up and delete the two partitions. Then, exit out of the cd and restart Windows and install Ubuntu through Wubi?

But of course I gotta restore MBR before I do all of that, right?

Thank you.

EDIT: Ok, i got the link to come up in FF. And it does tell me to restore MBR through the Windows setup cd. But I don't think I have that anymore. Is there any other way(easy way) to restore MBR?

EDIT AGAIN: All I can find is a Restore cd that came with my computer(Emachines). It says that it will restore on software on the computer. I remember that someone in the house used this to restore Windows when I first tried doing a dual boot and deleted my Windows partition. Would this by any chance restore my MBR?

Or I guess I can use this: [http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/](http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/)

Or this looks even easier: [http://users.bigpond.net.au/hermanzone/p18.htm#MbrFix.exe](http://users.bigpond.net.au/hermanzone/p18.htm#MbrFix.exe)

Ok, I restored MBR with  MBRfix. That is an amazing little tool. You just paste it to your C: drive, paste a line in the command prompt, and that's it. It's completely restored. Now I'll go about deleting the partitions.

---

### Post by h8uthemost on 2008-09-10
Nevermind, did everything with Norton Partition Magic.

---

### Post by kk0sse54 on 2008-09-10
:lolflag: sorry mate was kinda asleep, as long as everything worked out for ya

---

