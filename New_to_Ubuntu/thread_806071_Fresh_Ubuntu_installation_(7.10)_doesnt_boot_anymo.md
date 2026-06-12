---
title: "Fresh Ubuntu installation (7.10) doesnt boot anymore"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by stefanos1990 on 2008-05-24
Hi all,

I recently installed Ubuntu 7.10 (I burned it a while ago), and I used it once or twice, and after that when I tried starting the os, I only get a black screen with a command line, saying I should press control+D to continue, but when I do that nothing happens. What should I do?

Thanks!

---

### Post by logos34 on 2008-05-24
I'd reinstall

---

### Post by Sarah L on 2008-05-24
If you haven't used your Gusty partition much, then it probably shouldn't hurt to reinstall. I've screwed up and reinstalled many, many times. If you have any files on the partition that you still want to keep, boot up from a liveCD and copy them out to another partition or to another medium (such as a flashdrive).

---

### Post by TeoBigusGeekus on 2008-05-24
And before you reinstall, check the cds integrity, will you?

---

### Post by stefanos1990 on 2008-05-24
So if I just install my new 8.04 cd on the old 7.10 partition, that doesn't result in problems with Grub?

---

### Post by TeoBigusGeekus on 2008-05-24
No, just make sure you get the new grub written on the same partition as your older one. There is an option at the last stages of installation, called advanced or something, which lets you choose whether you will install grub and where...

---

### Post by sayakb on 2008-05-24
Ofcourse not. Grub would just be overwritten and the Gutsy option will be removed if it is not found while configuring Grub at the end of the installation process.

---

### Post by stefanos1990 on 2008-05-25
Thanks, it works again!
And 8.04 is much better!

---

