---
title: "Vista blue screen flash after installing Ubuntu 12.04"
date: 2012-09-27
forum: New to Ubuntu
---

### Post by Vindows Wista on 2012-09-27
Hi all,

I recently installed Precise next to my Vista. Now when I try to boot into Vista it attempts to load and then the bsod flashes and goes back to the grub loader. I then tried to boot into Precise and the boot just started to hang for a couple of minutes. It eventually gave me a screen notifying me that it could not locate /tmp. I chose the option to fix the issue and ubuntu eventually booted and I was able to log in. I attempted to boot into vista again but with the same result. I'm currently performing a startup repair for vista but if anyone has any info or a solution to this problem it will be greatly appreciated.

---

### Post by Vindows Wista on 2012-09-27
Ok so the startup repair seems to have worked and now I just need to remove Precise but I need to know if this will affect Vista again. So does anyone has any advice on removing ubuntus partition without affecting vista? or will it be perfectly harmless to do so.

---

### Post by Mark Phelps on 2012-09-27
Just use the Disk Management utility in Vista to delete the Ubuntu partition.  That will not harm MS Windows in any way.

---

### Post by Vindows Wista on 2012-09-27
Thanks Mark, I was going to use gparted but I've never come across this problem before and was unsure.

---

### Post by YannBuntu on 2012-09-27
> **Vindows Wista said:**
> I recently installed Precise next to my Vista. Now when I try to boot into Vista it attempts to load and then the bsod flashes and goes back to the grub loader.

Did you completely shutdown (no hibernating) Vista before installing Ubuntu?

---

### Post by Vindows Wista on 2012-09-28
It was properly shut down no hibernate. I deleted the partition but now Vista wont boot. I just get a black screen. Any Ideas?

---

### Post by Vindows Wista on 2012-09-28
It now shows me "unknown filesystem" Grub rescue.....

---

### Post by Vindows Wista on 2012-09-28
This sucks I tried to introduce Ubuntu to someone and this happens.......I recovered windows and now I trying to recover it again..........

---

### Post by Vindows Wista on 2012-09-28
I found a solution. [http://askubuntu.com/questions/133533/how-to-remove-ubuntu-and-put-windows-back-on](http://askubuntu.com/questions/133533/how-to-remove-ubuntu-and-put-windows-back-on)

---

