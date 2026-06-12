---
title: "[SOLVED] Fixing xsane broke my printer"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by ageer1 on 2008-06-28
So I could´t get xsane to start this morning, it would give me the ¨scanning for devices¨ message then quit. Thanks to drs305 on this forum, we got it working by deleting the home/esky/.sane folder and letting xsane rebuild it when it restarted.

Now I can´t print from any program. Neither a document nor a test page from admin/printing. I tried to install a new printer but can no longer find my printer in the list. It is a HP5650 deskjet by the way, accessed on my wifes XP box via samba.

Admin/printing shows the printer and says it´s state is idle. 

If I try to use the admin/printing troubleshooter to print a test page, it shows ¨processing¨ momentarily then ¨stopped¨, and ¨There are status messages associated with this queue. Printer´s state message: Cannot get the ticket cache for esky. Printer´s state reasons: none.

Both this printer and the scanner worked ¨out of the box¨ with both Feisty and Gutsy. I just upgraded, I thought I gave it enough time to get over it´s teething pains, but now I am wondering what else won´t work in Hardy. Perhaps I should just reinstall Gutsy for another couple of months.

Thanks for any help or advice,
     Joe

---

### Post by ageer1 on 2008-06-28
Anyone have any thoughts?

Thanks,
    Joe

---

### Post by ageer1 on 2008-06-28
I seem to have stumbled on a fix! I had noticed that my printer, HP Deskjet 5650, was no longer listed in the list of drivers when I tried to install it as a new printer. I checked the synaptic package manager and found that the hpijs printer driver wasn´t installed, so I installed it and, viola, the printer now prints.

Amazingly, xsane continued to start and work normally also.

I remain concerned that Hardy is too flaky for production work and would appreciate any views confirming or refuting this conclusion.

Thanks,     Joe

---

