---
title: "Error in Synaptics Package Manager"
date: 2008-10-05
forum: New to Ubuntu
---

### Post by Beth1957 on 2008-10-05
[FONT="Georgia"][SIZE="3"]Hi there,
When I try to run Synaptics Package Manager I'm getting the following error message :-

> E: Unable to write mmap - msync (28 No space left on device)
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

I'm completely baffled; can anyone help? I suspect that somethink has gone wrong during an automatic backup procedure (Quickstart) which ran for the first time today, as I also can't get Firefox to start and I'm suddenly getting an error message on Open Office. In fact the reason I was trying to use Synaptics was to uninstall/reinstall Firefox!
I'm running HH.
Cheers,[/SIZE][/FONT]

---

### Post by mrtomservo on 2008-10-05
I could be way off here, but the nature of the error message you received probably means your out of free space on your hard drive.

"E: Unable to write mmap - msync (28 No space left on device)"

If you open up a terminal and type "df" it should tell you what's going on with your hard drive usage.  My guess would be that your backup ate up all your free space.

---

### Post by Beth1957 on 2008-10-05
> **mrtomservo said:**
> I could be way off here, but the nature of the error message you received probably means your out of free space on your hard drive.

"E: Unable to write mmap - msync (28 No space left on device)"

If you open up a terminal and type "df" it should tell you what's going on with your hard drive usage.  My guess would be that your backup ate up all your free space.

Ouch; yes, you're right. Why didn't I think of that?:lolflag:
I'll sort that out (it would explain the weird Open Office error message too) and then try to find out what went wrong with firefox... Cheers!

---

