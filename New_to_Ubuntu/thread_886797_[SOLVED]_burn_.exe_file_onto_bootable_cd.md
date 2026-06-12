---
title: "[SOLVED] burn .exe file onto bootable cd"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by LRT on 2008-08-11
even though this question is not directly related to ubuntu or even linux in general, i'm posting this question here because i know how helpful this forum can be. i have used this forum various times and i've been happy with the help every time. hope someone can help me.

what i'm trying to do is burn an .exe file onto a bootable CD. i know how to burn .iso files onto CDs but what do i have to do to burn .exe files??? i want to do a firmware upgrade on some of our hard drives and all the western digital knowledge base gives me is an .exe file and tells me to put it on a bootable CD. is this even possible?? here is a link to directions, maybe it will make more sense to someone else... [http://support.wdc.com/product/download.asp?groupid=605&sid=57&lang=en]("http://support.wdc.com/product/download.asp?groupid=605&sid=57&lang=en"). this hard drive is part of a RAID array. all drives in the array are the same model (WD5000YS). sometimes the drives fail for no apparent reason. this firmware upgrade is supposed to fix that. 

this RAID array is attached to a linux file server so i guess this question is somewhat relevant to this forum. any help on this would be dandy :) thanks.

---

### Post by bumanie on 2008-08-11
The instructions seem fairly clear. As it is an extracted zip you will be using, it should just be a matter of burning the extracted file as a data cd. Then ensure your bios is set to boot from cd-rom and boot with the cd in the optical drive. According to the link, the rest is automatic after typing the <drivename.exe> at the command prompt.

---

### Post by fahadsadah on 2008-08-11
1) This is irrelevant here.
2) This is not helpful to _Linux_ servers.

Ask WD if they have a similar fix for Linux

---

### Post by LRT on 2008-08-11
bumanie,

i did extract the .exe file to a data CD but it won't boot and the bios looks good. that's why i was maybe thinking i'm missing something. any other ideas?

---

### Post by alzie on 2008-08-11
It looks like you need to burn a bootable dos CD.  (unless you have a floppy drive)

I'm not sure if you can add your firmware update to that CD or if that would require a 2nd CD.

If you have a disk repair CD like Barts or UBCD you should be able to boot into a DOS environment and then use the CD with the update on it.

I think that will do it.

---

### Post by LRT on 2008-08-11
yeah i was looking at Bart's (never heard of it until i ran into this issue). i just didn't think i would have to go through all this trouble to get this firmware upgrade working. actually, i do have a floppy drive... i'll try it first.. thanks!

---

### Post by prshah on 2008-08-11
> **LRT said:**
> 
what i'm trying to do is burn an .exe file onto a bootable CD.

You're on the right track with BartPE. Bart will create a working "live" CD of Windows from your current installation. You can choose to create an ISO. You can add your .exe (and any other) file to that ISO via Bart's GUI.

---

### Post by cgkades on 2008-08-11
seems like you could just hook this drive into a windows computer and boot into the command prompt, or boot a floppy with cdrom support and insert a cd with the file on it. i'm not sure exactly why they say you need to boot from a cd or floppy, unless they are figuring you arnt running windows in the first place...

you also might want to leave some feedback with the problems and questions you are having, so that they can fix their material.

---

### Post by LRT on 2008-08-11
ok, i fixed this. i made a bootable dos disk (on floppy) and also copied the .exe file to the floppy. i then booted off the floppy and then executed the .exe file. very easy. thanks for everyone's help even though this wasn't a linux question. hopefully it will benefit someone else.

---

