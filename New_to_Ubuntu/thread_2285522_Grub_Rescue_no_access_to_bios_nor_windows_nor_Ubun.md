---
title: "Grub Rescue no access to bios nor windows nor Ubuntu"
date: 2015-07-06
forum: New to Ubuntu
---

### Post by simone20 on 2015-07-06
Dears, sorry for bothering you with Grub problems. I have seen houndreds of threads of this, here. Unfortunately none of them seem to fit my problem, this is why i open a new one, please redirect me if i am wrong!

I have installed Wondows 7 and Ubuntu 12.04 with Grub 2 to manage them in the bios.
I am totally newbie and this is also the reason why i am here.

In  the last days i tried to migrate windows from an HDD to a SDD, in doing so, i probably moved accidently some grub files or anyway i corrupted it. When i restarted the PC i found only the wording:

"error: the symbol 'grub_xputs' not found
grub rescue>"

I tried to use a Ubuntu USB bootable version (14.04), hoping to use it to skip Grub and trying to fix it from Ubuntu. No way.
What can i do? As it is now i can also take the extreme action of fully deleting GRUB and ubuntu in order to access Win7, so that i can rein stal them later on, but i do not know how.
Can you please help me?

---

### Post by yancek on 2015-07-06
Not enough information to get any real help.  If you moved your windows from one drive to another did you update grub so that it was aware of the new location for windows?  I would suggest you go to the site below and download boot repair and select the option to "Create a BootInfo Summary" and post the output which will have much more detailed information and should give someone an idea of what the problem is to make a suggestion.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by simone20 on 2015-07-07
Thanks! I will do asap and share the outcome!
In the meantime a clarification. I did not yet start moving Win7 file systems, I only moved general HDD content to a temporary HD to make space. I am in a really initial step for my OS migration yet! :(

---

### Post by grahammechanical on 2015-07-07
Can I give a piece of advice? If it is not too late, restore the Windows boot loader before removing Ubuntu. Restoring the Windows boot manager will delete Grub. Once you can load into Windows you can delete Ubuntu by deleting the Linux partitions.

Do, things the other way around and we end up with a Grub rescue prompt.

Regards

---

