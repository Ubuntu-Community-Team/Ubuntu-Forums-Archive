---
title: "Readouts and Error Logs"
date: 2008-09-22
forum: New to Ubuntu
---

### Post by grewolf on 2008-09-22
I'm having a problem understanding the readouts and error messages that are in the logs.  I will attach an example.  What is normal what is a problem?  I have searched by copy and paste but when I read what is written it is asked by people who know what they are talking about.  I am not sure in tips in the right direction please.  

```
[   17.857883] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)

[   17.858019] ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)

[   17.858151] ACPI: PCI Interrupt Link [LNK3] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.

[   17.858284] ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)

[   17.858416] ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)

[   17.858548] ACPI: PCI Interrupt Link [LUBA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)

[   17.858685] ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)

[   17.858817] ACPI: PCI Interrupt Link [LMAC] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.

[   17.858948] ACPI: PCI Interrupt Link [LAPU] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.

[   17.859080] ACPI: PCI Interrupt Link [LACI] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.

[   17.859212] ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.

[   17.859345] ACPI: PCI Interrupt Link [LSMB] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)

[   17.859479] ACPI: PCI Interrupt Link [LUB2] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)

[   17.859615] ACPI: PCI Interrupt Link [LFIR] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.

[   17.859747] ACPI: PCI Interrupt Link [L3CM] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.

[   17.859879] ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.

[   17.860017] ACPI: PCI Interrupt Link [LSID] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.

[   17.860164] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0

[   17.860305] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0

[   17.860446] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.

[   17.860588] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0

[   17.860688] ACPI: PCI Interrupt Link [APC5] (IRQs *16)

[   17.860832] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22) *0

[   17.860975] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22) *0

[   17.861118] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22) *0, disabled.

[   17.861262] ACPI: PCI Interrupt Link [APCI] (IRQs 20 21 22) *0, disabled.

[   17.861406] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22) *0, disabled.

[   17.861549] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22) *0, disabled.

[   17.861651] ACPI: PCI Interrupt Link [APCS] (IRQs *23)

[   17.861793] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22) *0

[   17.861937] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22) *0, disabled.

[   17.862080] ACPI: PCI Interrupt Link [AP3C] (IRQs 20 21 22) *0, disabled.

[   17.862224] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22) *0, disabled.

[   17.862373] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22) *0, disabled.

[   17.862469] ACPI: Power Resource [ISAV] (on)

[   17.862484] Linux Plug and Play Support v0.97 (c) Adam Belay

```

---

### Post by willca on 2008-09-23
The message does seem to be annoying if you keep seeing that over and over in your logfiles.

What would interest me is that what does it show when you bootup?

Is there any errors in dmesg?

---

