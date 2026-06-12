---
title: "Unknown symbols - known in kallsyms"
date: 2008-01-02
forum: Programming Talk
---

### Post by bbackx on 2008-01-02
I'm in the progress of developping a new driver and I'm almost able to insmod the module, almost, but not yet.

First of all, when I make my module, I’m getting the following warnings:

WARNING: "ieee1394_bus_type" [/file-location/driver.ko] undefined!
WARNING: "hpsb_send_packet_and_wait" [/file-location/driver.ko] undefined!
WARNING: "dvb_usercopy" [/file-location/driver.ko] undefined!

Just warnings, no errors.
Now, when I try to insmod driver.ko, I’m getting the following errors in dmesg:

driver: Unknown symbol dvb_usercopy
driver: Unknown symbol hpsb_send_packet_and_wait
driver: Unknown symbol ieee1394_bus_type
driver: disagrees about version of symbol dvb_unregister_frontend
driver: Unknown symbol dvb_unregister_frontend
driver: disagrees about version of symbol dvb_register_frontend
driver: Unknown symbol dvb_register_frontend

The first 3 errors are to be expected when you see the warnings in the make-process, the last 4 are new.
But I don’t get why I get those errors... When I look in /proc/kallsyms, those functions exist:

$ cat /proc/kallsyms | grep dvb_usercopy
f8de4080 t dvb_usercopy [dvb_core]
$ cat /proc/kallsyms | grep ieee1394_bus_type
f88eb420 d ieee1394_bus_type    [ieee1394]
$ cat /proc/kallsyms | grep hpsb_send_packet_and_wait
f88d6600 t hpsb_send_packet_and_wait    [ieee1394]

$ cat /proc/kallsyms | grep dvb_unregister_frontend
f8df0814 r __ksymtab_dvb_unregister_frontend    [dvb_core]
f8df0bdc r __kstrtab_dvb_unregister_frontend    [dvb_core]
f8df08f0 r __kcrctab_dvb_unregister_frontend    [dvb_core]
f8dea540 T dvb_unregister_frontend      [dvb_core]
6bc0e425 a __crc_dvb_unregister_frontend        [dvb_core]

$ cat /proc/kallsyms | grep dvb_register_frontend
f8df081c r __ksymtab_dvb_register_frontend      [dvb_core]
f8df0bf4 r __kstrtab_dvb_register_frontend      [dvb_core]
f8df08f4 r __kcrctab_dvb_register_frontend      [dvb_core]
1f556d1c a __crc_dvb_register_frontend  [dvb_core]
f8dead60 T dvb_register_frontend        [dvb_core]

I had more unknown symbols, but by insmodding dvb-core.ko, most of them were gone.

Hopefully someone can help me out with those last errors, cause I'm rather stuck for the moment :(

PS: I'm using Ubuntu 7.10, standard kernel (2.6.22-14), 32-bit

---

