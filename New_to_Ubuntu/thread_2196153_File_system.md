---
title: "File system"
date: 2013-12-28
forum: New to Ubuntu
---

### Post by tcryder16 on 2013-12-28
There are four paper looking icons in the file system that are not in folders.These icons all have black arrows at the bottom, is it normal for these to be there?If not how do I remove them?Here's how they read  1.initrd.img 2.initrd.img.old 3.vmlinuz 4.vmlinuz.old

---

### Post by coffeecat on 2013-12-28
You mean this?

[img]http://ubuntuforums.org/attachment.php?attachmentid=248971&d=1388226628[/img]

They are links to the system kernel and are updated each time the kernel is updated. They are normal. Do not remove them. The arrow on the icon tells you that it is a link, more-or-less analogous to a Windows shortcut. 

[ATTACH=CONFIG]248971[/ATTACH]

---

### Post by Lars Noodén on 2013-12-28
If these are the ones in root (/) then they are only symbolic links to files in /boot  You need to keep them.  But you can look at "properties" to see more information about these links and where they are pointing to.

---

### Post by tcryder16 on 2013-12-28
> **coffeecat said:**
> You mean this?

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=248971&d=1388226628[/IMG]

They are links to the system kernel and are updated each time the kernel is updated. They are normal. Do not remove them. The arrow on the icon tells you that it is a link, more-or-less analogous to a Windows shortcut. 

[ATTACH=CONFIG]248971[/ATTACH]

Thank-you for such a quick response

---

### Post by tcryder16 on 2013-12-28
Thank you for your response;)

---

