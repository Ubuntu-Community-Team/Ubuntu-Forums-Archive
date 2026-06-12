---
title: "Freezing... just a CD issue?"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by Auspicious on 2008-08-15
So, someone explained what to do instead of the old ctrl-alt-del... but my computer did freeze again.  Again, ctrl-alt-backspace and ctrl-alt-F1 didn't work; ctrl-alt-prtscreen-REISUB did work.

The first freeze was after closing Firefox, the second was when experimenting with Fontwork in the Open Office word processor.

The front of my computer says:
"Intel Pentium 4 processor 641" and "512 MB DDR2"

The person who helped me before said that my computer has what it needs to be running Ubuntu off the live CD.  The check CD thing said the CD has no errors.  So... how safe am I assuming that the freezing issue is just from the CD and it won't keep happening if/when I install Ubuntu?

---

### Post by tech0007 on 2008-08-15
Please don't double post. Stick to your first thread [http://ubuntuforums.org/showthread.php?t=891128](http://ubuntuforums.org/showthread.php?t=891128).

---

### Post by Auspicious on 2008-08-15
Sorry, I thought that this was a new question and the other title didn't fit anymore... I was trying to follow the advice of having a descriptive title.

---

### Post by Liquidtricity on 2008-08-15
Have you tried looking at the logs to see if there are any issues. In particular check the sys log and the messages. If there are things that look like they are talking about broken things followed by a time gap then post those here and I'll see if I can find an answer for you.

---

### Post by tech0007 on 2008-08-15
It's unlikely a CD issue. You can try installing Ubuntu without making changes to Windows thru Wubi. See this link: [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by Auspicious on 2008-08-16
> **Liquidtricity said:**
> Have you tried looking at the logs to see if there are any issues. In particular check the sys log and the messages. If there are things that look like they are talking about broken things followed by a time gap then post those here and I'll see if I can find an answer for you.

I'm not sure what I'm looking for, of course.  There's a lot about "ACPI: PCI interrupt..."  and several things like, "ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.*something*

In the syslog, there's quite a bit about eth0, the first bit is:

Aug 16 17:45:16 ubuntu NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Aug 16 17:45:16 ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Aug 16 17:45:16 ubuntu NetworkManager: <info>  Will activate connection 'eth0'. 

a couple of other things:

Aug 16 17:45:27 ubuntu NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  

Aug 17 00:46:21 ubuntu NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 

(We have a wireless router, but I thought that only affected the laptop, not this desktop computer.)

Any other keywords I should skim for?

---

