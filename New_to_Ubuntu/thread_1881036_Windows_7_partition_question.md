---
title: "Windows 7 partition question"
date: 2011-11-14
forum: New to Ubuntu
---

### Post by tahitiwibble on 2011-11-14
I use Windows because of Dragon Naturally Speaking otherwise wouldn't go near it ever again.

I was trying to improve performance of my wifi card in an Asus PR05 (an Atheros AR9285 which seems to be generally considered as rubbish). Whilst in Windows I started tinkering around with the wifi driver and eventually got to the point where it doesn't function any more, however when I boot 10.04 everything works like a charm. I've tried to reinstall the driver 'et all' in Windows to no avail.

The question is; If I delete everything on the Windows partition and then copy/paste the backup of it, which was made just before the catastrophe (by simple copy/paste), is everything going to come back in order?

A big thanks in advance for any help.

---

### Post by Mark Phelps on 2011-11-15
> **tahitiwibble said:**
> The question is; If I delete everything on the Windows partition and then copy/paste the backup of it, which was made just before the catastrophe (by simple copy/paste), is everything going to come back in order?

Probably NOT.  Why? Because Windows relies on a lot of files and directories that are hidden by default -- and simple file/directory copying overlooks these.

Since you're having Win7 problems, I strongly advise that you post your problem in the Windows 7 forum: sevenforums.com.  They can help you solve the driver problem there.

---

### Post by coffeecat on 2011-11-15
> **tahitiwibble said:**
> 
The question is; If I delete everything on the Windows partition and then copy/paste the backup of it, which was made just before the catastrophe (by simple copy/paste), is everything going to come back in order?

If you mean a straight drag and drop copy, then absolutely not. If you need to take snapshots of Windows then you need imaging software. If you don't want paid for, Macrium Reflect Free is good and I can recommend it, but this won't help now as you won't have an image from when the driver was working.

But why not simply use Windows' system restore? Do you have a restore point from before you tinkered with the wireless driver?

---

