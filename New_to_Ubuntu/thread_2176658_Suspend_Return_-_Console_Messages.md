---
title: "Suspend Return - Console Messages"
date: 2013-09-25
forum: New to Ubuntu
---

### Post by stevenjrees on 2013-09-25
When i press a key in suspend mode, the screen comes back in non-graphics mode with messages ... something about firmware and switches back to the graphics password screen before i can read them. 

Where can i find these messages pls? i.e. are they logged somewhere?

---

### Post by peertje on 2013-09-25
Perhaps this appears in one of the ttys? You can access them by pressing ctrl+alt+F1 to ctrl+alt+F12 (F7 is usually where the desktop manager resides)

---

### Post by whitesmith on 2013-09-25
It would help to post the messages for examination.

---

### Post by stevenjrees on 2013-09-25
@whitesmith, i believe i am asking how to see the messages in a log file because the screen switches from text to graphics too quick.......i can see one of the messages in about a firmware bug on 3 of the 4 AMD CPUs

---

### Post by Bashing-om on 2013-09-25
stevenjrees; Hi !

Depending on the nature of the messages they Might appear:
If desk top related look in your home directory at " .xsession-errors";
If it is related to X, look into /var/log/Xorg.0.log;
If system related, look into /var/log/syslog, or, /var/log/kern.log, or, /var/log/dmesg .

[INDENT][INDENT]cheers
[/INDENT][/INDENT]

---

### Post by stevenjrees on 2013-09-26
Thanks Bashing-om, it was in the kern.log. 

smpboot: Booting Node 0 Processor 2 APIC 0x2
[Firmware Bug]: cpu 2, try to use APIC500 (LVT offset 0) for vector 0x400, but the register is already in use for vector 0xf9 on another cpu perf: IBS APIC setup failed on cpu #2
seems to be a known issue with the kernel and a forthcoming fix.

ata2: softreset failed (device not ready)
ata2: applying PMP SRST workaround and retrying
SATA link up 1.5 Gbps (SStatus 113 SControl 300)
This one i am not so sure about

---

### Post by Bashing-om on 2013-09-26
stevenjrees; Well,

From what little investigating I did :
> 
ata2: softreset failed (device not ready)
ata2: applying PMP SRST workaround and retrying
SATA link up 1.5 Gbps (SStatus 113 SControl 300)

seems to indicate that the system is not happy with settings in bios in respect to busing ...IDE/AHCI settings.
Are you running the system with mixed drives - IDE SATA - ?

[INDENT][INDENT]hey, just a thought
[/INDENT][/INDENT]

---

### Post by stevenjrees on 2013-10-02
Bashng-om, all my drives are SATA. 
I have three of the same Seagate 350Gb drives. 
I use one for the boot drive and the other two are software raid where the home path has been moved.

---

### Post by Bashing-om on 2013-10-02
stevenjrees; Hey .

This is above my skill level, if playing about with your bios settings has no effect,
I can relate, I also have a slightly similar situation on my system I have yet to correct. System on occasion screams a hollers about ATA3 at boot up. I too have 3 identical drives installed. I have yet to isolate it to either buss contention or just the system confused as to where/what it is trying to access.

[INDENT][INDENT]some things just nag nag nag
[/INDENT][/INDENT]

---

