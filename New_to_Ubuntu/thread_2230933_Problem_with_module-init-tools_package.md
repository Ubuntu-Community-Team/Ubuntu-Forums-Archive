---
title: "Problem with module-init-tools package"
date: 2014-06-22
forum: New to Ubuntu
---

### Post by Mansi_M on 2014-06-22
[COLOR=#000000]I am new to Ubuntu and currently learning to write Linux kernel modules. [/COLOR][COLOR=#333333][FONT=arial]Just to make sure that I have all the correct tools installed, I ran the command "$depmod -v" following a documentation. Instead of the version number, I got a big log of warnings (or maybe, errors).[/FONT][/COLOR]
[COLOR=#333333][FONT=arial]Part of it looked like this:[/FONT][/COLOR]

[COLOR=#333333][FONT=arial]/lib/modules/3.13.0-24-ge[/FONT][/COLOR][COLOR=#333333][FONT=arial]neric/kernel/net/appletal[/FONT][/COLOR][COLOR=#333333][FONT=arial]k/appletalk.ko needs "unregister_snap_client": /lib/modules/3.13.0-24-ge[/FONT][/COLOR][COLOR=#333333][FONT=arial]neric/kernel/net/802/psna[/FONT][/COLOR][COLOR=#333333][FONT=arial]p.ko[/FONT][/COLOR]
[COLOR=#333333][FONT=arial]depmod: ERROR: openat(/lib/modules/3.13.0-24-generic, modules.dep.tmp, 1101, 644): Permission denied

How do I fix this? Will I need to re-install and download the module-init-tools package? If yes, kindly help me with the procedure.

Thanks...[/FONT][/COLOR]

---

### Post by Vladlenin5000 on 2014-06-22
Fix what exactly? It already gave you the version number.

---

### Post by Gyokuro on 2014-06-22
Hi

You have a simple permission problem and for depmod you forgot sudo:

**sudo depmod -v**

---

### Post by Mansi_M on 2014-06-23
> **Gyokuro said:**
> Hi

You have a simple permission problem and for depmod you forgot sudo:

**sudo depmod -v**

Thanks for the response.
I tried the command with sudo and this time I got even a bigger list I am not able to comprehend. A part of it looks like this...

/lib/modules/3.13.0-24-generic/kernel/net/caif/caif_socket.ko needs "caif_connect_client": /lib/modules/3.13.0-24-generic/kernel/net/caif/caif.ko
/lib/modules/3.13.0-24-generic/kernel/net/caif/caif_usb.ko needs "caif_enroll_dev": /lib/modules/3.13.0-24-generic/kernel/net/caif/caif.ko
/lib/modules/3.13.0-24-generic/kernel/net/mac802154/mac802154.ko needs "ieee802154_nl_start_confirm": /lib/modules/3.13.0-24-generic/kernel/net/ieee802154/ieee802154.ko
/lib/modules/3.13.0-24-generic/kernel/net/mac802154/mac802154.ko needs "crc_ccitt": /lib/modules/3.13.0-24-generic/kernel/lib/crc-ccitt.ko
/lib/modules/3.13.0-24-generic/kernel/net/ceph/libceph.ko needs "crc32c": /lib/modules/3.13.0-24-generic/kernel/lib/libcrc32c.ko
/lib/modules/3.13.0-24-generic/kernel/net/batman-adv/batman-adv.ko needs "crc32c": /lib/modules/3.13.0-24-generic/kernel/lib/libcrc32c.ko
/lib/modules/3.13.0-24-generic/kernel/net/nfc/nci/nci.ko needs "nfc_unregister_device": /lib/modules/3.13.0-24-generic/kernel/net/nfc/nfc.ko
/lib/modules/3.13.0-24-generic/kernel/net/nfc/nci/nci.ko needs "crc_ccitt": /lib/modules/3.13.0-24-generic/kernel/lib/crc-ccitt.ko
/lib/modules/3.13.0-24-generic/kernel/net/nfc/hci/hci.ko needs "nfc_unregister_device": /lib/modules/3.13.0-24-generic/kernel/net/nfc/nfc.ko
/lib/modules/3.13.0-24-generic/kernel/net/nfc/nfc_digital.ko needs "nfc_unregister_device": /lib/modules/3.13.0-24-generic/kernel/net/nfc/nfc.ko
/lib/modules/3.13.0-24-generic/kernel/net/nfc/nfc_digital.ko needs "crc_ccitt": /lib/modules/3.13.0-24-generic/kernel/lib/crc-ccitt.ko

What should I do?

---

### Post by Mansi_M on 2014-06-23
> **Vladlenin5000 said:**
> Fix what exactly? It already gave you the version number.

Thanks for the response...
I get this output whenever I run the command depmod -v

/lib/modules/3.13.0-24-generic/kernel/net/nfc/hci/hci.ko needs "nfc_unregister_device": /lib/modules/3.13.0-24-generic/kernel/net/nfc/nfc.ko
/lib/modules/3.13.0-24-generic/kernel/net/nfc/nfc_digital.ko needs "nfc_unregister_device": /lib/modules/3.13.0-24-generic/kernel/net/nfc/nfc.ko
/lib/modules/3.13.0-24-generic/kernel/net/nfc/nfc_digital.ko needs "crc_ccitt": /lib/modules/3.13.0-24-generic/kernel/lib/crc-ccitt.ko
/lib/modules/3.13.0-24-generic/kernel/net/nfc/nfc_digital.ko needs "crc_itu_t": /lib/modules/3.13.0-24-generic/kernel/lib/crc-itu-t.ko
/lib/modules/3.13.0-24-generic/kernel/net/openvswitch/openvswitch.ko needs "vxlan_sock_release": /lib/modules/3.13.0-24-generic/kernel/drivers/net/vxlan.ko
/lib/modules/3.13.0-24-generic/kernel/net/openvswitch/openvswitch.ko needs "gre_cisco_register": /lib/modules/3.13.0-24-generic/kernel/net/ipv4/gre.ko
/lib/modules/3.13.0-24-generic/kernel/net/openvswitch/openvswitch.ko needs "crc32c": /lib/modules/3.13.0-24-generic/kernel/lib/libcrc32c.ko
/lib/modules/3.13.0-24-generic/kernel/net/vmw_vsock/vmw_vsock_vmci_transport.ko needs "vsock_enqueue_accept": /lib/modules/3.13.0-24-generic/kernel/net/vmw_vsock/vsock.ko
/lib/modules/3.13.0-24-generic/kernel/net/vmw_vsock/vmw_vsock_vmci_transport.ko needs "vmci_datagram_create_handle_priv": /lib/modules/3.13.0-24-generic/kernel/drivers/misc/vmw_vmci/vmw_vmci.ko
/lib/modules/3.13.0-24-generic/kernel/lib/cpu-notifier-error-inject.ko needs "notifier_err_inject_init": /lib/modules/3.13.0-24-generic/kernel/lib/notifier-error-inject.ko
depmod: ERROR: openat(/lib/modules/3.13.0-24-generic, modules.dep.tmp, 1101, 644): Permission denied
depmod: ERROR: openat(/lib/modules/3.13.0-24-generic, modules.dep.bin.tmp, 1101, 644): Permission denied
depmod: ERROR: openat(/lib/modules/3.13.0-24-generic, modules.alias.tmp, 1101, 644): Permission denied
depmod: ERROR: openat(/lib/modules/3.13.0-24-generic, modules.alias.bin.tmp, 1101, 644): Permission denied
depmod: ERROR: openat(/lib/modules/3.13.0-24-generic, modules.softdep.tmp, 1101, 644): Permission denied
depmod: ERROR: openat(/lib/modules/3.13.0-24-generic, modules.symbols.tmp, 1101, 644): Permission denied
depmod: ERROR: openat(/lib/modules/3.13.0-24-generic, modules.symbols.bin.tmp, 1101, 644): Permission denied
depmod: ERROR: openat(/lib/modules/3.13.0-24-generic, modules.builtin.bin.tmp, 1101, 644): Permission denied
depmod: ERROR: openat(/lib/modules/3.13.0-24-generic, modules.devname.tmp, 1101, 644): Permission denied

I don't see the version number in this and it seem all these warnings and errors would need to be fixed but I don't know how!

---

### Post by Vladlenin5000 on 2014-06-23
Again, the errors appear because you're running it without previledges -> That's what "sudo" is for...
Here's what you need to understand what "depmod" does: [https://wiki.debian.org/depmod](https://wiki.debian.org/depmod)
And here is what the several arguments do: [http://manpages.debian.org/cgi-bin/man.cgi?sektion=8&query=depmod&apropos=0&manpath=sid&locale=en](http://manpages.debian.org/cgi-bin/man.cgi?sektion=8&query=depmod&apropos=0&manpath=sid&locale=en)
(Please note that -v and -V are two different arguments)

---

### Post by Mansi_M on 2014-06-23
Thank you for the links, sir. I finally figured out the stupid mistake I was making, using the argument -v instead of -V.

---

