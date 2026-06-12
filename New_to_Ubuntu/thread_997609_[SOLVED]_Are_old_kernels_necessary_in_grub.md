---
title: "[SOLVED] Are old kernels necessary in grub?"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by nakama85 on 2008-11-30
Are old kernels necessary to have in the grub menu.lst 

If so then why?

I was just wondering because if they are not necessary then I was going to remove them. Call me crazy but I don't like clutter. Not even on boot:lolflag:

Thanks for your input

---

### Post by wilbbe01 on 2008-11-30
Agreed, I hate clutter as well.  You really don't need them listed in Grub once you know the newly installed kernel functions as you expect.  You can comment out the lines in /boot/grub/menu.lst by adding a # to the front of all the lines in the section for which kernels you do not want.  Does this help?  Simply commenting them out here does make it easier in the future should you realize some module doesn't work with a newer kernel like you thought it did initially.

---

### Post by StevoG7 on 2008-11-30
Old kernels are absolutely not necessary in your menu.lst file.  You only need to have entries in menu.lst for options you would like to have the option of booting with.

You could remove them from menu.lst to remove eye clutter, or if you are happy with the current kernel, you could uninstall the old kernels that are cluttering your grub entries.  This would automatically remove them from menu.lst as well I believe.

To remove the old kernels just go to the synaptic package manager and search for linux-image.  There will be several linux-image packages with different versions, and you can just remove the versions that correspond to the kernels you no longer want.

---

### Post by SunnyRabbiera on 2008-11-30
Mainly they are for recovery/backup, though with the recent kernel vulnerabilities maybe there should be cut out.

---

### Post by OutOfReach on 2008-11-30
You can delete some kernels, but it is a good idea to keep at least one kernel that worked well for you. Just incase your current kernel fails somehow.

---

### Post by nakama85 on 2008-11-30
> **wilbbe01 said:**
> Agreed, I hate clutter as well.  You really don't need them listed in Grub once you know the newly installed kernel functions as you expect.  You can comment out the lines in /boot/grub/menu.lst by adding a # to the front of all the lines in the section for which kernels you do not want.  Does this help?  Simply commenting them out here does make it easier in the future should you realize some module doesn't work with a newer kernel like you thought it did initially.
 Cool thanks I did not even think about commenting out the lines. That's a great idea.

Only question in response is, when you say the new kernel functions as I would expect. Is there anything in particular I should look for and do people often have problems with new kernels?

Thanks

---

### Post by nakama85 on 2008-11-30
> **SunnyRabbiera said:**
> Mainly they are for recovery/backup, though with the recent kernel vulnerabilities maybe there should be cut out.

What kind of vulnerabilities do you speak of. Anything I should worry about?

---

### Post by Xiong Chiamiov on 2008-11-30
If you can boot, you're pretty much fine.  Other things to pay attention to are wireless and sound.

> **nakama85 said:**
> What kind of vulnerabilities do you speak of. Anything I should worry about?

[These ones]("http://news.softpedia.com/news/Newly-Discovered-Kernel-Vulnerabilities-Affect-All-Ubuntu-Users-98864.shtml").

---

### Post by SunnyRabbiera on 2008-11-30
> **nakama85 said:**
> What kind of vulnerabilities do you speak of. Anything I should worry about?

[http://news.softpedia.com/news/Newly-Discovered-Kernel-Vulnerabilities-Affect-All-Ubuntu-Users-98864.shtml](http://news.softpedia.com/news/Newly-Discovered-Kernel-Vulnerabilities-Affect-All-Ubuntu-Users-98864.shtml)

This is the big kernel vulnerability report right now, but if you constantly upgrade you should be fine.

---

