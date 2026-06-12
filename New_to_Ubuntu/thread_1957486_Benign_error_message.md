---
title: "Benign error message?"
date: 2012-04-12
forum: New to Ubuntu
---

### Post by Boyntonstu on 2012-04-12
On Boot into 11.10 fro USB flash I see:

error: HD0 out of disk

Press any key to continue....

If I do nothing, the boot continues into Ubuntu.

---

### Post by kc1di on 2012-04-12
> **Boyntonstu said:**
> On Boot into 11.10 fro USB flash I see:

error: HD0 out of disk

Press any key to continue....

If I do nothing, the boot continues into Ubuntu.

Are you saying your getting this error on a live boot or a H.D. installed to a usb flash drive?

In any event if it's installed seems that the problem is that
hd0 does not actually exist as the hardrives have been renamed as sd0 so if grub is looking for hd0 it won't find it. The problem seem to be related to grub being install to the usb flash instead of a harddrive.

---

### Post by Gleichsnerd on 2012-04-12
Either that, or if it is a live boot, you simply don't have any more space on the jump drive.

As long as you don't need to save anything large to HD0, you'll be fine. The only problem you might run into is a massive update where the packages need installed first.

---

### Post by Boyntonstu on 2012-04-12
> **Gleichsnerd said:**
> Either that, or if it is a live boot, you simply don't have any more space on the jump drive.

As long as you don't need to save anything large to HD0, you'll be fine. The only problem you might run into is a massive update where the packages need installed first.
 

Boot from 8 GB USB flash dive.

This is what System  Monitor says:

[http://i348.photobucket.com/albums/q.../df-121112.jpg]("http://i348.photobucket.com/albums/q339/BoyntonStu/df-121112.jpg")

[http://s348.photobucket.com/albums/q...=df-121112.jpg]("http://s348.photobucket.com/albums/q339/BoyntonStu/?action=view&current=df-121112.jpg")

Images captured from screen using KSnapshot

---

### Post by justin.perkins on 2012-04-18
I can verify this is happening with me as well. I might add, that I only see it, when I boot a usb-pen installed-ubuntu using plop. Either the plop.iso or plop installed to a tiny virtual hd in vmware, then grub will show that exact error. I suspected initially that it WAS the tiny hd with plop on it, and the grub on the usb-pen not knowing about that, but then I observed the same behavior when I used the .iso and vmware's bios CAN boot a mounted .iso. Plop also has some very interesting custom bios-rom or network card replace-the-pxe-boot-rom ways I'm excited to try out, but I digress. 

I've wondered what this error was, and because it has no obvious negative impact, and the very same usb-pen install will not output this error when loaded on actual metal, I've ignored it. I would like to either quiet or remove the cause of it though. 

[FONT=Courier New]error: hd0 out of disk.[/FONT]

[FONT=Courier New]Press any key to continue[/FONT]

[FONT=Verdana]But... Where's the Any key? *sob*
:p
[/FONT]

---

### Post by Boyntonstu on 2012-04-18
> **justin.perkins said:**
> I can verify this is happening with me as well. I might add, that I only see it, when I boot a usb-pen installed-ubuntu using plop. Either the plop.iso or plop installed to a tiny virtual hd in vmware, then grub will show that exact error. I suspected initially that it WAS the tiny hd with plop on it, and the grub on the usb-pen not knowing about that, but then I observed the same behavior when I used the .iso and vmware's bios CAN boot a mounted .iso. Plop also has some very interesting custom bios-rom or network card replace-the-pxe-boot-rom ways I'm excited to try out, but I digress. 

I've wondered what this error was, and because it has no obvious negative impact, and the very same usb-pen install will not output this error when loaded on actual metal, I've ignored it. I would like to either quiet or remove the cause of it though. 

[FONT=Courier New]error: hd0 out of disk.[/FONT]




[FONT=Courier New]Press any key to continue[/FONT]

[FONT=Verdana]But... Where's the Any key? *sob*
:p
[/FONT]


Thanks,

It is nice to know that I am not the only person who sees this hiccup on boot.

Perhaps a Guru can figure it out.

---

