---
title: "Editing Grub 12.04.1"
date: 2013-06-04
forum: New to Ubuntu
---

### Post by MichelleH on 2013-06-04
I am trying to follow instructions on how to run my machine on only one cpu. I am required to add the following line to the boot command

```

GRUB_CMDLINE_LINUX_DEFAULT="maxcpus=1"


```

I tried using "gksu gedit /etc/default/grub" to edit the file but the following appears. 

```

** (gksu:2258): WARNING **: The connection is closed

(gksu:2258): GConf-WARNING **: Client failed to connect to the D-BUS daemon:
Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
GConf Error: No D-BUS daemon running


(gksu:2258): GConf-WARNING **: Client failed to connect to the D-BUS daemon:
Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
GConf Error: No D-BUS daemon running


(gksu:2258): GConf-WARNING **: Client failed to connect to the D-BUS daemon:
Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
GConf Error: No D-BUS daemon running


(gksu:2258): GConf-WARNING **: Client failed to connect to the D-BUS daemon:
Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
GConf Error: No D-BUS daemon running


(gksu:2258): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

** (gedit:2261): WARNING **: The connection is closed

(gedit:2261): EggSMClient-WARNING **: Failed to connect to the session manager: None of the authentication protocols specified are supported


** (gedit:2261): WARNING **: Could not connect to session bus
root@hatch-System-Product-Name:/home/hatch# 


```

Is there another way to edit the files and am I attempting to edit the correct thing?

Thanks for any help.

---

### Post by MidnightGrey on 2013-06-04
Are you running the command in a command-line-only environment? IE: you dont have a desktop.
Try typing the command:
$ sudo vim /etc/default/grub

Quick VIM101:
```

To edit in vim: press the 'i' key.
To exit out of edit-mode: press 'esc'.
To save and exit: type ":x" and hit enter (you cannot do this while in edit-mode).
To exit without saving: type ":q!" and hit enter.
```

---

### Post by MichelleH on 2013-06-04
I have a desktop, and I just found the grub folder. 
Thank you

---

