---
title: "How to show splash screen when rebooting throught terminal?"
date: 2008-09-29
forum: New to Ubuntu
---

### Post by Fixman on 2008-09-29
There are many times I use a script that finishes rebooting the computer using the "reboot" command on bash. However, the only thing that bothers me about it is that when I reboot it this way, the splash screen (Ubuntu's brown line shrinking) doesn't show. Is there any way to show Ubuntu splash screen when rebooting thought the terminal (or to somehow reboot "like in the GUI" thought the terminal)?

---

### Post by baruch60610 on 2008-09-29
Hi, I'm not quite sure what you're looking for.  Have you tried editing the /boot/grub/menu.lst file to add "splash" to your boot options?  

My only hesitation in mentioning that is that I don't see why you'd be getting a different boot result based on whether you rebooted from a terminal or the GUI.  I'd assume you'd get the same result whichever way you started the boot.

---

### Post by Fixman on 2008-09-30
> **baruch60610 said:**
> Hi, I'm not quite sure what you're looking for.  Have you tried editing the /boot/grub/menu.lst file to add "splash" to your boot options?  

My only hesitation in mentioning that is that I don't see why you'd be getting a different boot result based on whether you rebooted from a terminal or the GUI.  I'd assume you'd get the same result whichever way you started the boot.

No, I have the splash when the computer turns on, what I want is the splash hen the computer turns off.

---

