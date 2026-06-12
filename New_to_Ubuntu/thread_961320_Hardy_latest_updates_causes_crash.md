---
title: "Hardy latest updates causes crash"
date: 2008-10-28
forum: New to Ubuntu
---

### Post by Hookheathen on 2008-10-28
Hi,

The latest updates for Hardy 8.04.1 squirted down the line today from Mission Control appear to cause my laptop to crash when typing in Firefox and Skype. I do not get an error message, just total lock up. The screen, keyboard and mouse freeze and the only solution is to reboot. Am I the only one to report this and what can be done to fix it?

---

### Post by Zzl1xndd on 2008-10-28
just upgraded and haven't had any issues yet.

---

### Post by philinux on 2008-10-28
> **Hookheathen said:**
> Hi,

The latest updates for Hardy 8.04.1 squirted down the line today from Mission Control appear to cause my laptop to crash when typing in Firefox and Skype. I do not get an error message, just total lock up. The screen, keyboard and mouse freeze and the only solution is to reboot. Am I the only one to report this and what can be done to fix it?

Ok.
1. for hard lockups use this. [http://lifehacker.com/software/linux-tip/gently-restart-a-frozen-system-298891.php](http://lifehacker.com/software/linux-tip/gently-restart-a-frozen-system-298891.php)

2. Have a look through dmesg and /var/log/messages

---

### Post by aeiah on 2008-10-28
since you arent getting any errors come up in the terminal due to the freeze, try looking in your error logs
```
dmesg
```

you might want to filter it with grep or something
```
dmesg | grep firefox
```

---

### Post by Hookheathen on 2008-10-29
Many thanks Philinux & aeiah for your suggestions. 

Thankfully the freeze has not repeated itself today - so far. Should it happen again I have taken note of the soft reboot using REISUB.

FYI dmesg did not record any var/log messages.So it remains a mystery and if it never repeats itself one that can die on the vine.
[COLOR="DarkRed"]
Regards,Michael.[/COLOR]

---

