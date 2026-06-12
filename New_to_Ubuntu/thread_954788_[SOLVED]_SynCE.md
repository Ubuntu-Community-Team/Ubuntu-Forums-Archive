---
title: "[SOLVED] SynCE"
date: 2008-10-21
forum: New to Ubuntu
---

### Post by Deldo on 2008-10-21
Hello

I got some problems with the installing of SynCE on my laptop. I have downloaded SynCE and installed in on my laptop. But when I going through the SyncEngine setup I get this message if I type "sync-engine" in a terminal:
[I]"rune@Rune:~$ sync-engine
bash: sync-engine: command not found
rune@Rune:~$"[/I]
But if I launch Nautilus, I get this message:
[I]"rune@Rune:~$ sudo nautilus
[sudo] password for rune: 
Sorry, try again.
[sudo] password for rune: 
seahorse nautilus module initialized
Initializing nautilus-share extension

(nautilus:28551): Gtk-WARNING **: Theme file for default has no name


(nautilus:28551): Gtk-WARNING **: Theme file for default has no directories

Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


** (nautilus:28551): WARNING **: Unable to add monitor: Operationen understøttes ikke
seahorse nautilus module shutdown
rune@Rune:~$ sync-engine
bash: sync-engine: command not found
rune@Rune:~$"[/I]

What is wrong here?

---

### Post by eks on 2008-10-21
Have you tried?

```
synce-sync-engine
```

You can also try searching Synaptic for SynCE, there are other tools that might be helpful (like synce-trayicon).

I never used it though. Even had a Windows Mobile device myself that threw away for a netbook.

Another tool that you might find useful, but for the device, is *wm5torage*. Try searching for it on Google.

---

### Post by Deldo on 2008-10-22
*"synce-synce-engine"* didn't work either. I still get the message: *"bash: synce-sync-engine: command not found"*
I will try your other adwises. Thank you.

---

### Post by Deldo on 2008-10-22
It worked with vm5storage. Thanks a lot.

---

