---
title: "I need help &quot;to disable boot password&quot;"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by mksboysal on 2008-10-01
Before Ubuntu OS opens up asks: user name and password. 

Can anyone tell me how I can disable this? 

Thanks

mksboysal.

---

### Post by The Cog on 2008-10-01
Is this password orompt in the GRUB bootloader, or do you mean the username/password Ubuntu GUI prompt with the brown background?

If the former, you need to edit /boot/grub/menu.lst. Ask back here for more details.

If the latter, menu System -> Administration -> Login Window, go to the Security tab and enable automatic login.

---

### Post by mksboysal on 2008-10-01
> **The Cog said:**
> Is this password orompt in the GRUB bootloader, or do you mean the username/password Ubuntu GUI prompt with the brown background?

If the former, you need to edit /boot/grub/menu.lst. Ask back here for more details.

If the latter, menu System -> Administration -> Login Window, go to the Security tab and enable automatic login.

Yes, the username/password Ubuntu GUI prompt with the brown background?
this is the one that I like to disable.

thanks

---

### Post by shifty_powers on 2008-10-01
**menu System -> Administration -> Login Window, go to the Security tab and enable automatic login.**

---

