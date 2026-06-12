---
title: "[HELP] Ubuntu 9.10 Can't Powerdown After Shutting it Down"
date: 2010-03-26
forum: Philippine Team
---

### Post by itagomo on 2010-03-26
Marami nako pinuntahan na ubuntuforums section pero lahat ng solution na tinry ko sa PC ko walang nangyari.

If I shutdown my PC by clicking the username and choosing 'Shutdown' or with the use of a command(sudo shutdown -h -P now) in the terminal, it goes blackscreen and post something like this:


Ubuntu 9.10 myname-desktop tty1

myname-desktop login: [xx.xxxxxx] System halted.

tapos dun lang and naka-on pa rin un PC & monitor.
I think I'm running Karmic 32bit.
Wala pa ko right solution until now. Thanks for someone who can help.

---

### Post by Samhain13 on 2010-03-26
Nasubukan mo na: "sudo shutdown -h now" lang, walang -P?

---

### Post by itagomo on 2010-03-26
Yeh, nasubukan ku na un -h lang, pro same lang nangyari.
Yun mga nabasa kong same problem pati reboot nila di pwede, pro sakin ok naman, shutdown lang talaga problem.

---

### Post by jepong on 2010-03-27
parang ganyan yung HP Pavilion 750n ko sa bahay... ang solution is edit mo yung boot string and add mo "acpi=off" then try mo restart...

---

### Post by itagomo on 2010-03-27
Same tayo jepong, HP Pavilion din sakin.
Anung file ba yun boot string? Pede pakipost yun code. Thanks.

---

### Post by itagomo on 2010-03-30
I solved this issue after reading so many threads.
By adding acpi=force in the /etc/default/grub, my CPU and monitor can now be turned off.
```

I appended the argument acpi=force to this line:
GRUB_CMDLINE_LINUX=""
>
GRUB_CMDLINE_LINUX="acpi=force"

```
And, syempre, the system needs to be updated(sudo update-grub) and rebooted to see changes.

I still want to credit jepong and Samhain13 for some suggestions they gave.

---

### Post by Samhain13 on 2010-03-30
Niye, wala naman naitulong yung suggestment ko. Hehehe! Good that you found a solution. :D

---

### Post by itagomo on 2010-03-31
i mean, thanks for your effort to help me!
:)

---

