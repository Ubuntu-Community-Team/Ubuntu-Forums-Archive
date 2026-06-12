---
title: "Help with CUPS printing"
date: 2015-06-04
forum: New to Ubuntu
---

### Post by raido2 on 2015-06-04
Hello,

I have cups 1.7 set up. And have a printer LaserJet P1606DN configured. But with one user, every morning the first printing gets errror "Unable to write print data: Broken pipe". After that printing works fine. Printer is set with maximum sleep time "after 1 hour".

Any ideas, what to check?

---

### Post by DuckHook on 2015-06-04
There is more than one state that some printers can go into, and I suspect that your printer is capable of both sleep and hibernate. During the day, you may print enough that it only goes into sleep mode, but overnight, it goes into hibernation, which takes longer to wake from and must reinitialize the NIC/USB port. If so, then each morning your computer will detect no response on the port it expects to be active, hence the "broken pipe". But the printer does receive a signal, starts the process of reviving from hibernation, and once it reinitializes enough to have a fully functioning NIC/USB port, it will process subsequent print jobs normally. If this is the problem, then sleep time settings won't help unless you can turn hibernation off entirely. However, this would waste a lot of electricity and possibly wear out your printer faster too. I don't have your printer model, so all of above is just an educated guess. Please take it with a healthy dose of scepticism.

How is your printer attached? Network? USB?

Try looking at your logs, especially *dmesg*, *syslog* and the *cups* error log which can be found at:
```
/var/log/cups/error_log
```

Can you temporarily disable sleep/hibernation entirely (at least for one night) and see if this helps?

---

### Post by tgalati4 on 2015-06-05
If this printer has an IP address, try pinging it from the computer that is having problems.  Take note of the ping time and compare it to the other computers on the network.  It could be a network issue that is causing the broken pipe.

---

### Post by raido2 on 2015-06-08
Hello,

ping from this computer to printer is fine. It is odd that printing fails when printer stays idle all night. Maybe something that [COLOR=#000000]DuckHook described.[/COLOR]

---

### Post by raido2 on 2015-06-18
in cups error_log there is same line:
"Unable to write print data: Broken pipe".
And I have to restart printer in order to be able to print.
Syslog shows nothing and from dmesg I don't know what to look for (beacause I can not see log entries date and time).

I will run ping overnight and see if that helps or not. Alo upgraded HP firmware, no help.

---

### Post by tgalati4 on 2015-06-18
For the user that is having problems, delete the printer, then reinstall the printer, then install any updates to Ubuntu, then reboot and try printing.

---

