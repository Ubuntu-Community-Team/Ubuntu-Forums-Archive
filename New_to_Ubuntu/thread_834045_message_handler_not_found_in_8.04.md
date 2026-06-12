---
title: "message handler not found in 8.04"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by myotis on 2008-06-19
After ugradiing from gutsy to Hardy. The log is showing (/var/log/messages) is showing a few error messages including these about message handler:


Jun 14 23:48:19 Antec-Linux kernel: [ 71.448981] skge eth0: Link is up at 100 Mbps, full duplex, flow control both
Jun 14 23:48:19 Antec-Linux dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jun 14 23:48:22 Antec-Linux kernel: [ 73.669134] NET: Registered protocol family 17
Jun 14 23:48:22 Antec-Linux dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.domain_name
Jun 14 23:48:22 Antec-Linux dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Jun 14 23:48:22 Antec-Linux dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Jun 14 23:48:22 Antec-Linux dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu
Jun 14 23:48:23 Antec-Linux kernel: [ 75.190500] NET: Registered protocol family 10
Jun 14 23:48:23 Antec-Linux kernel: [ 75.190800] lo: Disabled Privacy Extensions
Jun 14 23:48:23 Antec-Linux kernel: [ 75.192014] ADDRCONF(NETDEV_UP): eth1: link is not ready
Jun 14 23:48:56 Antec-Linux pulseaudio[6273]: alsa-util.c: Device hw:2 doesn't support 44100 Hz, changed to 16000 Hz.
Jun 14 23:48:56 Antec-Linux pulseaudio[6273]: alsa-util.c: Device hw:2 doesn't support 2 channels, changed to 1.

Can anyone explain what this is about and how I can fix it.

The other errors are about ACPI.

Many thanks

Graham

---

### Post by Ausmosis on 2008-06-20
I'm getting the same ever since upgrading to Hardy. Hope someone can help us here?

Rgds

Ausmosis

---

### Post by myotis on 2008-06-20
Are you also having the ACPI errors adn problems shutting down?

Graham

---

### Post by philinux on 2008-06-20
I and I think everybody gets these errors. If things are working ok then disregard them.

I did start a thread about the red hat message but no one could give me an answer.

---

### Post by myotis on 2008-06-20
> **philinux said:**
> I and I think everybody gets these errors. If things are working ok then disregard them.

I did start a thread about the red hat message but no one could give me an answer.


Thanks, but in fact I am having shut down problems, but as no one has been able to help me with the shut down problem, I thought I would try and extract some of the error messages that may have had something to do with the problem.


Graham

---

### Post by Ausmosis on 2008-06-20
> **myotis said:**
> Thanks, but in fact I am having shut down problems, but as no one has been able to help me with the shut down problem, I thought I would try and extract some of the error messages that may have had something to do with the problem.


Graham

I'm not getting ACPI errors. I get the message handler errors as well as the following error when shutting down:

```
Jun 20 17:55:04 falcidi-desktop NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))
```

Not sure why its coming up but I assume its trying to find 'nscd' which definitely isn't under /usr/sbin. Is there a way to stop NetworkManager from trying to execute 'nscd'??

Rgds

Ausmosis

---

### Post by markbuntu on 2008-06-20
You need to install nscd to get rid of that message. It is a bug in Network Manager that effects only some installs. It happened to me along with a pam_smbpass (missing ok) error that was fixed by installing libpam_smbpass which is also a bug in Network Manager. 

 There is a bug report on it in launchpad.

The redhat thing is on the low priority list for bug repair. Ignore it.

---

