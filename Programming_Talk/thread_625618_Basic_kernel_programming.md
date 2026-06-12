---
title: "Basic kernel programming"
date: 2007-11-28
forum: Programming Talk
---

### Post by kvorion on 2007-11-28
I started with making a couple of hello world kernel modules. One thing I couldn't figure out is why is it that I always need to cat the /var/log/messages file to read any messages. Why won't the messages display on my console?

Whenever I use the KERN_INFO macro, the messages get logged in that file. When I use KERN_ALERT, the message doesnt even show up in the log.

What can I do so that the messages always show up on my console window?

---

### Post by volanin on 2007-11-28
Edit **/etc/syslog.conf** and add the following line:

```
kern.=info       /dev/tty1
```

Change **/dev/tty1** to any other file to suit your needs.
This will output any KERN_INFO messages in this file.
Check the **syslog.conf** manpage for more options.
:)

---

### Post by dwhitney67 on 2007-11-28
Does anybody know of a simple way to have the system re-create /var/log/messages on every reboot, rather than just append to it?

---

### Post by geirha on 2007-11-28
why not just use dmesg? ```
dmesg|less
```

---

### Post by dwhitney67 on 2007-11-28
That won't do.

Let me explain a little more thoroughly.  I have a Linux system with a 1GB primary partition (/dev/hda1).

Everytime I reboot, the file /var/log/messages keeps growing in size.  I would prefer if the system would re-create (from scratch) this file at every boot-up, rather than use the existing file to which it appends messages.

My concern is that after N reboots, my primary partition will be filled to capacity.

P.S.  I suppose I could insert a statement into a startup script to remove the file, however I have no idea how this will affect the system.  As for using a script during the shutdown, well this won't work because the system I operate is shutdown using the power-button... not a graceful shutdown as done on a typical desktop PC.

---

### Post by geirha on 2007-11-28
It gets rotated once a week by logrotate. I doubt it will ever take more than 1MiB, you can add a special section for it in /etc/logrotate.conf though, and set a max size for 500KiB or something ...

---

### Post by dwhitney67 on 2007-11-28
Geirha,

Would you by chance know which source package provides the logrotate utility?  My system does not offer that binary.

P.S.  The questions I am asking are not for my Ubuntu system.  They are for my Cross-Compiled Linux From Scratch (CLFS) system.

-----------------------------------------------

I think I may have found it here:  [http://packages.ubuntu.com/dapper/source/logrotate](http://packages.ubuntu.com/dapper/source/logrotate)

---

### Post by Tuna-Fish on 2007-11-28
> **geirha said:**
> It gets rotated once a week by logrotate. I doubt it will ever take more than 1MiB, you can add a special section for it in /etc/logrotate.conf though, and set a max size for 500KiB or something ...

Oh, you'd be surprised. I had a 7 GB kernel log file once.

---

### Post by kvorion on 2007-12-09
> **volanin said:**
> Edit **/etc/syslog.conf** and add the following line:

```
kern.=info       /dev/tty1
```

Change **/dev/tty1** to any other file to suit your needs.
This will output any KERN_INFO messages in this file.
Check the **syslog.conf** manpage for more options.
:)

I tried doing that, but still my KERN_INFO messages to to /var/log/messages, and I dont know where my KERN_ALERT messages go. Please help.

---

### Post by geirha on 2007-12-09
> **kvorion said:**
> I tried doing that, but still my KERN_INFO messages to to /var/log/messages, and I dont know where my KERN_ALERT messages go. Please help.

Do you need to stop the messages from also being sent to /var/log/messages? You don't see those messages in terminal 1 (CTRL+ALT+F1)?

---

### Post by kvorion on 2007-12-09
I am running Ubuntu on a virtual machine, and for some reason, ctrl alt f1 does not change my terminal.

I have another question, how do I install the man pages for the Linux Kernel API?

I already have manpages-dev package installed.

---

