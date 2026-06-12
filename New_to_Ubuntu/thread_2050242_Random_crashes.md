---
title: "Random crashes"
date: 2012-08-30
forum: New to Ubuntu
---

### Post by pi1973 on 2012-08-30
Hello all,

I'm using UBUNTU DESKTOP 12.04.1 on my desktop machine and sometimes it simply freezes without any type of visible warning or error message. In those cases the only solution is to cut the machine power and reboot it. To make things worse, this problem is intermitent: Sometimes weeks go-by without a single freeze; sometimes it keeps hanging 10 minutes after I boot the system.  

Because I made no changes to the system I have no clue about what may be wrong, so I kindly ask this forum to please guide me to some tutorial/manual on how to troubleshoot my system in order to find out the cause (or causes) of this issue.

Here are the specs of my machine (ACER Aspire M5711) just in case:
CPU: Intel Core2 Quad CPU Q9550
MB: ACER FMCP7AM
Mem: 6GB DDR2 800MHz
Video: NVIDIA GEForce GT 130 (running the nouveau driver)
Disk: Seagate ATA Disk  750GB


Thanks in advance.

---

### Post by GreatDanton on 2012-08-30
Maybe your log files will tell us more about crashes.  [https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles) .This link will help you to learn something more about. Look for system logs. You will find it in  /var/log/syslog. Post the output between code tags #, or post it via pastebin &#8594; [http://paste.ubuntu.com/](http://paste.ubuntu.com/)

Regards.

---

### Post by pi1973 on 2012-08-30
> **GreatDanton said:**
> Maybe your log files will tell us more about crashes.  [https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles) .This link will help you to learn something more about. Look for system logs. You will find it in  /var/log/syslog. Post the output between code tags #, or post it via pastebin &#8594; [http://paste.ubuntu.com/](http://paste.ubuntu.com/)

Regards.
I run into several failures today... Here are the contents of the syslog
 file for one of the failures. I can post further entries although 
they're quite similar to this one. <br><br>In the meantime I'm going through all the other logs you mentioned in your reply and I already executed memtest with no errors found.<br>
<br>Thanks in advance for your help.<br><br>
```
Aug 30 11:49:23 server kernel: imklog 5.8.6, log source = /proc/kmsg started.<br>
Aug 30 11:49:23 server rsyslogd: [origin software="rsyslogd" 
swVersion="5.8.6" x-pid="1171" x-info="http://www.rsyslog.com"] start<br>
Aug 30 11:49:23 server rsyslogd: rsyslogd's groupid changed to 102<br>
Aug 30 11:49:23 server rsyslogd: rsyslogd's userid changed to 101<br>
Aug 30 11:49:23 server rsyslogd-2039: Could not open output pipe '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] Initializing cgroup subsys cpuset<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] Initializing cgroup subsys cpu<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] Linux version 
2.6.32-41-generic (buildd@yellow) (gcc version 4.4.3 (Ubuntu 
4.4.3-4ubuntu5.1) ) #90-Ubuntu SMP Tue May 22 11:29:51 UTC 2012 (Ubuntu 
2.6.32-41.90-generic 2.6.32.59+drm33.24)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] Command line: 
BOOT_IMAGE=/boot/vmlinuz-2.6.32-41-generic 
root=UUID=d717c92e-7164-4685-a823-6109a6498140 ro vga=792 splash quiet 
splash<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] KERNEL supported cpus:<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] &nbsp; Intel GenuineIntel<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] &nbsp; AMD AuthenticAMD<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] &nbsp; Centaur CentaurHauls<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] BIOS-provided physical RAM map:<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] &nbsp;BIOS-e820: 0000000000000000 - 000000000009bc00 (usable)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] &nbsp;BIOS-e820: 000000000009bc00 - 00000000000a0000 (reserved)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] &nbsp;BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] &nbsp;BIOS-e820: 0000000000100000 - 00000000cffa0000 (usable)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] &nbsp;BIOS-e820: 00000000cffa0000 - 00000000cffae000 (ACPI data)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] &nbsp;BIOS-e820: 00000000cffae000 - 00000000cfff0000 (ACPI NVS)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] &nbsp;BIOS-e820: 00000000cfff0000 - 00000000d0000000 (reserved)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] &nbsp;BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] &nbsp;BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] &nbsp;BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] &nbsp;BIOS-e820: 0000000100000000 - 00000001b0000000 (usable)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] DMI present.<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==&gt; (reserved)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] last_pfn = 0x1b0000 max_arch_pfn = 0x400000000<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] MTRR default type: uncachable<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] MTRR fixed ranges enabled:<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] &nbsp; 00000-9FFFF write-back<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] &nbsp; A0000-BFFFF uncachable<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] &nbsp; C0000-DBFFF write-protect<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] &nbsp; DC000-DFFFF uncachable<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] &nbsp; E0000-EFFFF write-through<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] &nbsp; F0000-FFFFF write-protect<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] MTRR variable ranges enabled:<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] &nbsp; 0 base 000000000 mask F80000000 write-back<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] &nbsp; 1 base 080000000 mask FC0000000 write-back<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] &nbsp; 2 base 0C0000000 mask FF0000000 write-back<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] &nbsp; 3 base 100000000 mask F80000000 write-back<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] &nbsp; 4 base 180000000 mask FE0000000 write-back<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] &nbsp; 5 base 1A0000000 mask FF0000000 write-back<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] &nbsp; 6 disabled<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] &nbsp; 7 disabled<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] e820 update range: 00000000d0000000 - 0000000100000000 (usable) ==&gt; (reserved)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] last_pfn = 0xcffa0 max_arch_pfn = 0x400000000<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] Scanning 0 areas for low memory corruption<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] modified physical RAM map:<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] &nbsp;modified: 0000000000000000 - 0000000000010000 (reserved)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] &nbsp;modified: 0000000000010000 - 000000000009bc00 (usable)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] &nbsp;modified: 000000000009bc00 - 00000000000a0000 (reserved)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] &nbsp;modified: 00000000000e0000 - 0000000000100000 (reserved)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] &nbsp;modified: 0000000000100000 - 00000000cffa0000 (usable)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] &nbsp;modified: 00000000cffa0000 - 00000000cffae000 (ACPI data)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] &nbsp;modified: 00000000cffae000 - 00000000cfff0000 (ACPI NVS)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] &nbsp;modified: 00000000cfff0000 - 00000000d0000000 (reserved)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] &nbsp;modified: 00000000fec00000 - 00000000fec01000 (reserved)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] &nbsp;modified: 00000000fee00000 - 00000000fee01000 (reserved)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] &nbsp;modified: 00000000fff00000 - 0000000100000000 (reserved)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] &nbsp;modified: 0000000100000000 - 00000001b0000000 (usable)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] initial memory mapped : 0 - 20000000<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] init_memory_mapping: 0000000000000000-00000000cffa0000<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] NX (Execute Disable) protection: active<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] &nbsp;0000000000 - 00cfe00000 page 2M<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] &nbsp;00cfe00000 - 00cffa0000 page 4k<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] kernel direct mapping tables up to cffa0000 @ 10000-16000<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] init_memory_mapping: 0000000100000000-00000001b0000000<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] NX (Execute Disable) protection: active<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] &nbsp;0100000000 - 01b0000000 page 2M<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] kernel direct mapping tables up to 1b0000000 @ 14000-1c000<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] RAMDISK: 36fe9000 - 37fef463<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] ACPI: RSDP 00000000000fa800 00014 (v00 ACPIAM)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] ACPI: RSDT 00000000cffa0000 0004C (v01 ACRSYS ACRPRDCT 20081201 MSFT 00000097)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] ACPI: FACP 00000000cffa0200 00084 (v01 ACRSYS FACP1145 20081201 MSFT 00000097)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] ACPI: DSDT 00000000cffa0620 07CB7 (v01 &nbsp;81EA1 81EA1P12 00000004 INTL 20051117)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] ACPI: FACS 00000000cffae000 00040<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] ACPI: APIC 00000000cffa0390 00080 (v01 ACRSYS APIC1145 20081201 MSFT 00000097)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] ACPI: MCFG 00000000cffa0410 0003C (v01 ACRSYS OEMMCFG &nbsp;20081201 MSFT 00000097)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] ACPI: SLIC 00000000cffa0450 00176 (v01 ACRSYS ACRPRDCT 20081201 MSFT 00000097)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] ACPI: WDRT 00000000cffa05d0 00047 (v01 ACRSYS NV-WDRT &nbsp;20081201 MSFT 00000097)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] ACPI: OEMB 00000000cffae040 0007A (v01 ACRSYS OEMB1145 20081201 MSFT 00000097)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] ACPI: HPET 00000000cffaa620 00038 (v01 ACRSYS OEMHPET0 20081201 MSFT 00000097)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] ACPI: NVHD 00000000cffae0c0 00284 (v01 ACRSYS &nbsp;NVHDCP &nbsp;20081201 MSFT 00000097)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] ACPI: AWMI 00000000cffae350 0004E (v01 ACRSYS OEMB1145 20081201 MSFT 00000097)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] ACPI: SSDT 00000000cffaeca0 00A7C (v01 DpgPmm &nbsp; &nbsp;CpuPm 00000012 INTL 20051117)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] ACPI: Local APIC address 0xfee00000<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] No NUMA configuration found<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] Faking a node at 0000000000000000-00000001b0000000<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] Bootmem setup node 0 0000000000000000-00000001b0000000<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] &nbsp; NODE_DATA [0000000000017000 - 000000000001bfff]<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] &nbsp; bootmap [000000000001c000 - &nbsp;0000000000051fff] pages 36<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] (8 early reservations) ==&gt; bootmem [0000000000 - 01b0000000]<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] &nbsp; #0 [0000000000 - 0000001000] &nbsp; BIOS data page ==&gt; [0000000000 - 0000001000]<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] &nbsp; #1 [0000006000 - 0000008000] &nbsp; &nbsp; &nbsp; TRAMPOLINE ==&gt; [0000006000 - 0000008000]<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] &nbsp; #2 [0001000000 - 0001a37ac4] &nbsp; &nbsp;TEXT DATA BSS ==&gt; [0001000000 - 0001a37ac4]<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] &nbsp; #3 [0036fe9000 - 0037fef463] &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;RAMDISK ==&gt; [0036fe9000 - 0037fef463]<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] &nbsp; #4 [000009bc00 - 0000100000] &nbsp; &nbsp;BIOS reserved ==&gt; [000009bc00 - 0000100000]<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] &nbsp; #5 [0001a38000 - 0001a381dc] &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;BRK ==&gt; [0001a38000 - 0001a381dc]<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] &nbsp; #6 [0000010000 - 0000014000] &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;PGTABLE ==&gt; [0000010000 - 0000014000]<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] &nbsp; #7 [0000014000 - 0000017000] &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;PGTABLE ==&gt; [0000014000 - 0000017000]<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] found SMP MP-table at [ffff8800000ff780] ff780<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] 
&nbsp;[ffffea0000000000-ffffea0005ffffff] PMD -&gt; 
[ffff880028600000-ffff88002dbfffff] on node 0<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] Zone PFN ranges:<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] &nbsp; DMA &nbsp; &nbsp; &nbsp;0x00000010 -&gt; 0x00001000<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] &nbsp; DMA32 &nbsp; &nbsp;0x00001000 -&gt; 0x00100000<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] &nbsp; Normal &nbsp; 0x00100000 -&gt; 0x001b0000<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] Movable zone start PFN for each node<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] early_node_map[3] active PFN ranges<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] &nbsp; &nbsp; 0: 0x00000010 -&gt; 0x0000009b<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] &nbsp; &nbsp; 0: 0x00000100 -&gt; 0x000cffa0<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] &nbsp; &nbsp; 0: 0x00100000 -&gt; 0x001b0000<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] On node 0 totalpages: 1572651<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] &nbsp; DMA zone: 56 pages used for memmap<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] &nbsp; DMA zone: 110 pages reserved<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] &nbsp; DMA zone: 3813 pages, LIFO batch:0<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] &nbsp; DMA32 zone: 14280 pages used for memmap<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] &nbsp; DMA32 zone: 833496 pages, LIFO batch:31<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] &nbsp; Normal zone: 9856 pages used for memmap<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] &nbsp; Normal zone: 711040 pages, LIFO batch:31<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] ACPI: PM-Timer IO Port: 0x4008<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] ACPI: Local APIC address 0xfee00000<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] IOAPIC[0]: apic_id 4, version 17, address 0xfec00000, GSI 0-23<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] ACPI: IRQ0 used by override.<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] ACPI: IRQ2 used by override.<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] ACPI: IRQ9 used by override.<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] ACPI: IRQ14 used by override.<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] ACPI: IRQ15 used by override.<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] Using ACPI (MADT) for SMP configuration information<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] nr_irqs_gsi: 24<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] PM: Registered nosave memory: 000000000009b000 - 000000000009c000<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] PM: Registered nosave memory: 000000000009c000 - 00000000000a0000<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] PM: Registered nosave memory: 00000000cffa0000 - 00000000cffae000<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] PM: Registered nosave memory: 00000000cffae000 - 00000000cfff0000<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] PM: Registered nosave memory: 00000000cfff0000 - 00000000d0000000<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] PM: Registered nosave memory: 00000000d0000000 - 00000000fec00000<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fee00000<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000fff00000<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] PM: Registered nosave memory: 00000000fff00000 - 0000000100000000<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] Allocating PCI resources starting at d0000000 (gap: d0000000:2ec00000)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] Booting paravirtualized kernel on bare hardware<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:4 nr_node_ids:1<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] PERCPU: Embedded 30 pages/cpu @ffff880028200000 s91608 r8192 d23080 u524288<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] pcpu-alloc: s91608 r8192 d23080 u524288 alloc=1*2097152<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] pcpu-alloc: [0] 0 1 2 3 <br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] Built 1 zonelists in Node order, mobility grouping on. &nbsp;Total pages: 1548349<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] Policy zone: Normal<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] Kernel command line: 
BOOT_IMAGE=/boot/vmlinuz-2.6.32-41-generic 
root=UUID=d717c92e-7164-4685-a823-6109a6498140 ro vga=792 splash quiet 
splash<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] Initializing CPU#0<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] Checking aperture...<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] No AGP bridge found<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] Calgary: detecting Calgary via BIOS EBDA area<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] Placing 64MB software IO TLB between ffff880020000000 - ffff880024000000<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] software IO TLB at phys 0x20000000 - 0x24000000<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] Memory: 6108896k/7077888k 
available (5438k kernel code, 787284k absent, 181708k reserved, 2987k 
data, 884k init)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] Hierarchical RCU implementation.<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] NR_IRQS:4352 nr_irqs:440<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] spurious 8259A interrupt: IRQ7.<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] Console: colour VGA+ 80x25<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] console [tty0] enabled<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] allocated 62914560 bytes of page_cgroup<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] hpet clockevent registered<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] Fast TSC calibration failed<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] TSC: PIT calibration matches HPET. 1 loops<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.000000] Detected 2833.284 MHz processor.<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.010007] Calibrating delay loop 
(skipped), value calculated using timer frequency.. 5666.56 BogoMIPS 
(lpj=28332840)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.010034] Security Framework initialized<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.010053] AppArmor: AppArmor initialized<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.010621] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.025457] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.028168] Mount-cache hash table entries: 256<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.028322] Initializing cgroup subsys ns<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.028328] Initializing cgroup subsys cpuacct<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.028331] Initializing cgroup subsys memory<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.028339] Initializing cgroup subsys devices<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.028341] Initializing cgroup subsys freezer<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.028343] Initializing cgroup subsys net_cls<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.028365] CPU: L1 I cache: 32K, L1 D cache: 32K<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.028367] CPU: L2 cache: 6144K<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.028370] CPU 0/0x0 -&gt; Node 0<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.028372] CPU: Physical Processor ID: 0<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.028373] CPU: Processor Core ID: 0<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.028375] mce: CPU supports 6 MCE banks<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.028383] CPU0: Thermal monitoring enabled (TM2)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.028387] using mwait in idle threads.<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.028389] Performance Events: Core2 events, Intel PMU driver.<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.028394] ... version: &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;2<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.028395] ... bit width: &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;40<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.028397] ... generic registers: &nbsp; &nbsp; &nbsp;2<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.028398] ... value mask: &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 000000ffffffffff<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.028399] ... max period: &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 000000007fffffff<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.028400] ... fixed-purpose events: &nbsp; 3<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.028401] ... event mask: &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 0000000700000003<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.030561] ACPI: Core revision 20090903<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.040008] ftrace: converting mcount calls to 0f 1f 44 00 00<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.040012] ftrace: allocating 22588 entries in 89 pages<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.048007] Setting APIC routing to flat<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.048394] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.149151] CPU0: Intel(R) Core(TM)2 Quad CPU &nbsp; &nbsp;Q9550 &nbsp;@ 2.83GHz stepping 0a<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.150000] Booting processor 1 APIC 0x1 ip 0x6000<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.020000] Initializing CPU#1<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.020000] CPU: L1 I cache: 32K, L1 D cache: 32K<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.020000] CPU: L2 cache: 6144K<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.020000] CPU 1/0x1 -&gt; Node 0<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.020000] CPU: Physical Processor ID: 0<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.020000] CPU: Processor Core ID: 1<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.020000] CPU1: Thermal monitoring enabled (TM2)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.300105] CPU1: Intel(R) Core(TM)2 Quad CPU &nbsp; &nbsp;Q9550 &nbsp;@ 2.83GHz stepping 0a<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.300115] checking TSC synchronization [CPU#0 -&gt; CPU#1]: passed.<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.310116] Booting processor 2 APIC 0x2 ip 0x6000<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.020000] Initializing CPU#2<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.020000] CPU: L1 I cache: 32K, L1 D cache: 32K<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.020000] CPU: L2 cache: 6144K<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.020000] CPU 2/0x2 -&gt; Node 0<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.020000] CPU: Physical Processor ID: 0<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.020000] CPU: Processor Core ID: 2<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.020000] CPU2: Thermal monitoring enabled (TM2)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.470102] CPU2: Intel(R) Core(TM)2 Quad CPU &nbsp; &nbsp;Q9550 &nbsp;@ 2.83GHz stepping 0a<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.470112] checking TSC synchronization [CPU#0 -&gt; CPU#2]: passed.<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.480071] Booting processor 3 APIC 0x3 ip 0x6000<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.020000] Initializing CPU#3<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.020000] CPU: L1 I cache: 32K, L1 D cache: 32K<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.020000] CPU: L2 cache: 6144K<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.020000] CPU 3/0x3 -&gt; Node 0<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.020000] CPU: Physical Processor ID: 0<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.020000] CPU: Processor Core ID: 3<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.020000] CPU3: Thermal monitoring enabled (TM2)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.640088] CPU3: Intel(R) Core(TM)2 Quad CPU &nbsp; &nbsp;Q9550 &nbsp;@ 2.83GHz stepping 0a<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.640098] checking TSC synchronization [CPU#0 -&gt; CPU#3]: passed.<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.650011] Brought up 4 CPUs<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.650014] Total of 4 processors activated (22694.94 BogoMIPS).<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.653905] CPU0 attaching sched-domain:<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.653909] &nbsp;domain 0: span 0-1 level MC<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.653911] &nbsp; groups: 0 1<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.653914] &nbsp; domain 1: span 0-3 level CPU<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.653916] &nbsp; &nbsp;groups: 0-1 (cpu_power = 2048) 2-3 (cpu_power = 2048)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.653922] CPU1 attaching sched-domain:<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.653923] &nbsp;domain 0: span 0-1 level MC<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.653925] &nbsp; groups: 1 0<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.653928] &nbsp; domain 1: span 0-3 level CPU<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.653929] &nbsp; &nbsp;groups: 0-1 (cpu_power = 2048) 2-3 (cpu_power = 2048)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.653934] CPU2 attaching sched-domain:<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.653935] &nbsp;domain 0: span 2-3 level MC<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.653937] &nbsp; groups: 2 3<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.653939] &nbsp; domain 1: span 0-3 level CPU<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.653941] &nbsp; &nbsp;groups: 2-3 (cpu_power = 2048) 0-1 (cpu_power = 2048)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.653945] CPU3 attaching sched-domain:<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.653946] &nbsp;domain 0: span 2-3 level MC<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.653948] &nbsp; groups: 3 2<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.653950] &nbsp; domain 1: span 0-3 level CPU<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.653952] &nbsp; &nbsp;groups: 2-3 (cpu_power = 2048) 0-1 (cpu_power = 2048)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.654061] devtmpfs: initialized<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.654061] regulator: core version 0.5<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.654061] Time: 11:48:39 &nbsp;Date: 08/30/12<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.654061] NET: Registered protocol family 16<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.654061] ACPI: bus type pci registered<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.654061] Trying to unpack rootfs image as initramfs...<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.654061] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.654061] PCI: Not using MMCONFIG.<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.654061] PCI: Using configuration type 1 for base access<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.654061] bio: create slab &lt;bio-0&gt; at 0<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.654061] ACPI: EC: Look up EC in DSDT<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.664209] ACPI: Executed 1 blocks of module-level executable AML code<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.671094] ACPI: Interpreter enabled<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.671096] ACPI: (supports S0 S3 S4 S5)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.671111] ACPI: Using IOAPIC for interrupt routing<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.671165] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.680952] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.686475] PCI: Using MMCONFIG at e0000000 - efffffff<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.703135] ACPI Warning: Incorrect 
checksum in table [OEMB] - B9, should be B6 (20090903/tbutils-314)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.703330] ACPI: No dock devices found.<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.703487] ACPI: PCI Root Bridge [PCI0] (0000:00)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.703717] pci 0000:00:03.0: reg 10 io port: [0x4f00-0x4fff]<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.703810] pci 0000:00:03.2: reg 10 io port: [0x4900-0x493f]<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.703822] pci 0000:00:03.2: reg 20 io port: [0x4d00-0x4d3f]<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.703826] pci 0000:00:03.2: reg 24 io port: [0x4e00-0x4e3f]<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.703856] pci 0000:00:03.2: PME# supported from D3hot D3cold<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.703861] pci 0000:00:03.2: PME# disabled<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.704020] pci 0000:00:03.5: reg 10 32bit mmio: [0xf9f80000-0xf9ffffff]<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.704113] pci 0000:00:04.0: reg 10 32bit mmio: [0xf9f7f000-0xf9f7ffff]<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.704144] pci 0000:00:04.0: supports D1 D2<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.704146] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.704149] pci 0000:00:04.0: PME# disabled<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.704174] pci 0000:00:04.1: reg 10 32bit mmio: [0xf9f7ec00-0xf9f7ecff]<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.704216] pci 0000:00:04.1: supports D1 D2<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.704217] pci 0000:00:04.1: PME# supported from D0 D1 D2 D3hot D3cold<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.704220] pci 0000:00:04.1: PME# disabled<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.704248] pci 0000:00:06.0: reg 10 32bit mmio: [0xf9f7d000-0xf9f7dfff]<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.704279] pci 0000:00:06.0: supports D1 D2<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.704280] pci 0000:00:06.0: PME# supported from D0 D1 D2 D3hot D3cold<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.704283] pci 0000:00:06.0: PME# disabled<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.704307] pci 0000:00:06.1: reg 10 32bit mmio: [0xf9f7e800-0xf9f7e8ff]<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.704346] pci 0000:00:06.1: supports D1 D2<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.704348] pci 0000:00:06.1: PME# supported from D0 D1 D2 D3hot D3cold<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.704351] pci 0000:00:06.1: PME# disabled<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.704382] pci 0000:00:08.0: reg 10 32bit mmio: [0xf9f78000-0xf9f7bfff]<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.704413] pci 0000:00:08.0: PME# supported from D3hot D3cold<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.704416] pci 0000:00:08.0: PME# disabled<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.704472] pci 0000:00:0a.0: reg 10 32bit mmio: [0xf9f7c000-0xf9f7cfff]<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.704476] pci 0000:00:0a.0: reg 14 io port: [0xd480-0xd487]<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.704479] pci 0000:00:0a.0: reg 18 32bit mmio: [0xf9f7e400-0xf9f7e4ff]<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.704483] pci 0000:00:0a.0: reg 1c 32bit mmio: [0xf9f7e000-0xf9f7e00f]<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.704513] pci 0000:00:0a.0: supports D1 D2<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.704514] pci 0000:00:0a.0: PME# supported from D0 D1 D2 D3hot D3cold<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.704518] pci 0000:00:0a.0: PME# disabled<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.704540] pci 0000:00:0b.0: reg 10 io port: [0xd400-0xd407]<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.704544] pci 0000:00:0b.0: reg 14 io port: [0xd080-0xd083]<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.704547] pci 0000:00:0b.0: reg 18 io port: [0xd000-0xd007]<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.704551] pci 0000:00:0b.0: reg 1c io port: [0xcc00-0xcc03]<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.704554] pci 0000:00:0b.0: reg 20 io port: [0xc880-0xc88f]<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.704558] pci 0000:00:0b.0: reg 24 32bit mmio: [0xf9f76000-0xf9f77fff]<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.704857] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.704864] pci 0000:00:0c.0: PME# disabled<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.705174] pci 0000:00:15.0: PME# supported from D0 D1 D2 D3hot D3cold<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.705181] pci 0000:00:15.0: PME# disabled<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.705482] pci 0000:00:16.0: PME# supported from D0 D1 D2 D3hot D3cold<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.705489] pci 0000:00:16.0: PME# disabled<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.705790] pci 0000:00:17.0: PME# supported from D0 D1 D2 D3hot D3cold<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.705797] pci 0000:00:17.0: PME# disabled<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.706102] pci 0000:00:18.0: PME# supported from D0 D1 D2 D3hot D3cold<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.706109] pci 0000:00:18.0: PME# disabled<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.706186] pci 0000:00:09.0: transparent bridge<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.706221] pci 0000:02:00.0: reg 10 32bit mmio: [0xfd000000-0xfdffffff]<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.706228] pci 0000:02:00.0: reg 14 64bit mmio pref: [0xd0000000-0xdfffffff]<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.706237] pci 0000:02:00.0: reg 1c 64bit mmio: [0xfa000000-0xfbffffff]<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.706242] pci 0000:02:00.0: reg 24 io port: [0xec00-0xec7f]<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.706246] pci 0000:02:00.0: reg 30 32bit mmio pref: [0xfea80000-0xfeafffff]<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.706332] pci 0000:00:0c.0: bridge io port: [0xe000-0xefff]<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.706339] pci 0000:00:0c.0: bridge 32bit mmio: [0xfa000000-0xfeafffff]<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.706352] pci 0000:00:0c.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.706548] pci 0000:05:00.0: reg 10 32bit mmio: [0xfebff800-0xfebfffff]<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.706556] pci 0000:05:00.0: reg 14 32bit mmio: [0xfebff400-0xfebff47f]<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.706577] pci 0000:05:00.0: reg 20 32bit mmio: [0xfebff000-0xfebff07f]<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.706585] pci 0000:05:00.0: reg 24 32bit mmio: [0xfebff480-0xfebff4ff]<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.706710] pci 0000:00:17.0: bridge 32bit mmio: [0xfeb00000-0xfebfffff]<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.706862] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.707025] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PBB0._PRT]<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.707118] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR0._PRT]<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.707197] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P6._PRT]<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.707263] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P7._PRT]<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.707328] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P8._PRT]<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.707394] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.723209] ACPI: PCI Interrupt Link [LNKA] (IRQs 16 17 18 19) *0, disabled.<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.723454] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 17 18 19) *0, disabled.<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.723696] ACPI: PCI Interrupt Link [LNKC] (IRQs 16 17 18 19) *0, disabled.<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.723940] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 17 18 19) *0, disabled.<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.724185] ACPI: PCI Interrupt Link [LN0A] (IRQs 16 17 18 19) *7<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.724426] ACPI: PCI Interrupt Link [LN0B] (IRQs 16 17 18 19) *0, disabled.<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.724669] ACPI: PCI Interrupt Link [LN0C] (IRQs 16 17 18 19) *0, disabled.<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.724908] ACPI: PCI Interrupt Link [LN0D] (IRQs 16 17 18 19) *0, disabled.<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.725149] ACPI: PCI Interrupt Link [LN1A] (IRQs 16 17 18 19) *0, disabled.<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.725392] ACPI: PCI Interrupt Link [LN1B] (IRQs 16 17 18 19) *0, disabled.<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.725634] ACPI: PCI Interrupt Link [LN1C] (IRQs 16 17 18 19) *0, disabled.<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.725873] ACPI: PCI Interrupt Link [LN1D] (IRQs 16 17 18 19) *0, disabled.<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.726113] ACPI: PCI Interrupt Link [LN2A] (IRQs 16 17 18 19) *0, disabled.<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.726352] ACPI: PCI Interrupt Link [LN2B] (IRQs 16 17 18 19) *0, disabled.<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.726594] ACPI: PCI Interrupt Link [LN2C] (IRQs 16 17 18 19) *0, disabled.<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.726834] ACPI: PCI Interrupt Link [LN2D] (IRQs 16 17 18 19) *0, disabled.<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.727074] ACPI: PCI Interrupt Link [LN3A] (IRQs 16 17 18 19) *0, disabled.<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.727313] ACPI: PCI Interrupt Link [LN3B] (IRQs 16 17 18 19) *0, disabled.<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.727552] ACPI: PCI Interrupt Link [LN3C] (IRQs 16 17 18 19) *0, disabled.<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.727797] ACPI: PCI Interrupt Link [LN3D] (IRQs 16 17 18 19) *0, disabled.<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.728036] ACPI: PCI Interrupt Link [LN4A] (IRQs 16 17 18 19) *0, disabled.<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.728275] ACPI: PCI Interrupt Link [LN4B] (IRQs 16 17 18 19) *0, disabled.<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.728519] ACPI: PCI Interrupt Link [LN4C] (IRQs 16 17 18 19) *0, disabled.<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.728760] ACPI: PCI Interrupt Link [LN4D] (IRQs 16 17 18 19) *0, disabled.<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.729007] ACPI: PCI Interrupt Link [LN5A] (IRQs 16 17 18 19) *10<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.729251] ACPI: PCI Interrupt Link [LN5B] (IRQs 16 17 18 19) *0, disabled.<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.729490] ACPI: PCI Interrupt Link [LN5C] (IRQs 16 17 18 19) *0, disabled.<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.729733] ACPI: PCI Interrupt Link [LN5D] (IRQs 16 17 18 19) *0, disabled.<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.730004] ACPI: PCI Interrupt Link [LN6A] (IRQs 16 17 18 19) *0, disabled.<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.730247] ACPI: PCI Interrupt Link [LN6B] (IRQs 16 17 18 19) *0, disabled.<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.730490] ACPI: PCI Interrupt Link [LN6C] (IRQs 16 17 18 19) *0, disabled.<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.730733] ACPI: PCI Interrupt Link [LN6D] (IRQs 16 17 18 19) *0, disabled.<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.730985] ACPI: PCI Interrupt Link [LUB0] (IRQs 20 21 22 23) *9<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.731232] ACPI: PCI Interrupt Link [LUB2] (IRQs 20 21 22 23) *15<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.731479] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22 23) *15<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.731723] ACPI: PCI Interrupt Link [LAZA] (IRQs 20 21 22 23) *9<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.731963] ACPI: PCI Interrupt Link [SGRU] (IRQs 20 21 22 23) *0, disabled.<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.732210] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *10<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.732455] ACPI: PCI Interrupt Link [LPMU] (IRQs 20 21 22 23) *11<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.732699] ACPI: PCI Interrupt Link [LSA0] (IRQs 20 21 22 23) *5<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.732980] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22 23) *0, disabled.<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.733227] ACPI: PCI Interrupt Link [UB11] (IRQs 20 21 22 23) *10<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.733470] ACPI: PCI Interrupt Link [UB12] (IRQs 20 21 22 23) *11<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.733715] ACPI: PCI Interrupt Link [LRP0] (IRQs 20 21 22 23) *10<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.733954] ACPI: PCI Interrupt Link [LRP1] (IRQs 20 21 22 23) *0, disabled.<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.734199] ACPI: PCI Interrupt Link [LRP2] (IRQs 20 21 22 23) *0, disabled.<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.734446] ACPI: PCI Interrupt Link [LRP3] (IRQs 20 21 22 23) *11<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.734692] ACPI: PCI Interrupt Link [LRP4] (IRQs 20 21 22 23) *9<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.734942] ACPI: PCI Interrupt Link [LRP5] (IRQs 20 21 22 23) *15<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.735187] ACPI: PCI Interrupt Link [LRP6] (IRQs 20 21 22 23) *14<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.735301] vgaarb: device added: PCI:0000:02:00.0,decodes=io+mem,owns=io+mem,locks=none<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.735303] vgaarb: loaded<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.735387] SCSI subsystem initialized<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.735436] libata version 3.00 loaded.<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.735436] usbcore: registered new interface driver usbfs<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.735436] usbcore: registered new interface driver hub<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.735436] usbcore: registered new device driver usb<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.735436] ACPI: WMI: Mapper loaded<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.735436] PCI: Using ACPI for IRQ routing<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.735436] NetLabel: Initializing<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.735436] NetLabel: &nbsp;domain hash size = 128<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.735436] NetLabel: &nbsp;protocols = UNLABELED CIPSOv4<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.735436] NetLabel: &nbsp;unlabeled traffic allowed by default<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.735436] HPET: 4 timers in total, 0 timers will be used for per-cpu timer<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.735436] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31, 31<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.735436] hpet0: 4 comparators, 64-bit 25.000000 MHz counter<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.750030] Switching to clocksource tsc<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.751791] AppArmor: AppArmor Filesystem Enabled<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.751813] pnp: PnP ACPI init<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.751836] ACPI: bus type pnp registered<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.760298] pnp: PnP ACPI: found 15 devices<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.760299] ACPI: ACPI bus type pnp unregistered<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.760313] system 00:06: ioport range 0x4d0-0x4d1 has been reserved<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.760315] system 00:06: ioport range 0x800-0x80f has been reserved<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.760317] system 00:06: ioport range 0x4000-0x407f has been reserved<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.760319] system 00:06: ioport range 0x4080-0x40ff has been reserved<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.760321] system 00:06: ioport range 0x4400-0x447f has been reserved<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.760323] system 00:06: ioport range 0x4480-0x44ff has been reserved<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.760325] system 00:06: ioport range 0x4800-0x487f has been reserved<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.760327] system 00:06: ioport range 0x4880-0x48ff has been reserved<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.760330] system 00:06: iomem range 0xfefe2000-0xfefe3fff has been reserved<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.760332] system 00:06: iomem range 0xfefe1000-0xfefe1fff has been reserved<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.760334] system 00:06: iomem range 0xfee01000-0xfeefffff has been reserved<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.760339] system 00:09: iomem range 0xfec00000-0xfec00fff could not be reserved<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.760341] system 00:09: iomem range 0xfee00000-0xfee00fff has been reserved<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.760346] system 00:0c: ioport range 0xa00-0xa0f has been reserved<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.760347] system 00:0c: ioport range 0xa10-0xa1f has been reserved<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.760349] system 00:0c: ioport range 0xa20-0xa2f has been reserved<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.760351] system 00:0c: ioport range 0xa30-0xa3f has been reserved<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.760355] system 00:0d: iomem range 0xe0000000-0xefffffff has been reserved<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.760359] system 00:0e: iomem range 0x0-0x9ffff could not be reserved<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.760361] system 00:0e: iomem range 0xc0000-0xcffff has been reserved<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.760363] system 00:0e: iomem range 0xe0000-0xfffff could not be reserved<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.760365] system 00:0e: iomem range 0x100000-0xcfffffff could not be reserved<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.760367] system 00:0e: iomem range 0xfec00000-0xffffffff could not be reserved<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.765189] pci 0000:00:09.0: PCI bridge, secondary bus 0000:01<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.765191] pci 0000:00:09.0: &nbsp; IO window: disabled<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.765194] pci 0000:00:09.0: &nbsp; MEM window: disabled<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.765196] pci 0000:00:09.0: &nbsp; PREFETCH window: disabled<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.765200] pci 0000:00:0c.0: PCI bridge, secondary bus 0000:02<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.765205] pci 0000:00:0c.0: &nbsp; IO window: 0xe000-0xefff<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.765215] pci 0000:00:0c.0: &nbsp; MEM window: 0xfa000000-0xfeafffff<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.765222] pci 0000:00:0c.0: &nbsp; PREFETCH window: 0x000000d0000000-0x000000dfffffff<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.765234] pci 0000:00:15.0: PCI bridge, secondary bus 0000:03<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.765235] pci 0000:00:15.0: &nbsp; IO window: disabled<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.765245] pci 0000:00:15.0: &nbsp; MEM window: disabled<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.765251] pci 0000:00:15.0: &nbsp; PREFETCH window: disabled<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.765263] pci 0000:00:16.0: PCI bridge, secondary bus 0000:04<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.765265] pci 0000:00:16.0: &nbsp; IO window: disabled<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.765274] pci 0000:00:16.0: &nbsp; MEM window: disabled<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.765280] pci 0000:00:16.0: &nbsp; PREFETCH window: disabled<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.765293] pci 0000:00:17.0: PCI bridge, secondary bus 0000:05<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.765294] pci 0000:00:17.0: &nbsp; IO window: disabled<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.765303] pci 0000:00:17.0: &nbsp; MEM window: 0xfeb00000-0xfebfffff<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.765310] pci 0000:00:17.0: &nbsp; PREFETCH window: disabled<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.765322] pci 0000:00:18.0: PCI bridge, secondary bus 0000:06<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.765323] pci 0000:00:18.0: &nbsp; IO window: disabled<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.765333] pci 0000:00:18.0: &nbsp; MEM window: disabled<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.765340] pci 0000:00:18.0: &nbsp; PREFETCH window: disabled<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.765358] pci 0000:00:09.0: setting latency timer to 64<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.765712] ACPI: PCI Interrupt Link [LRP0] enabled at IRQ 23<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.765718] &nbsp; alloc irq_desc for 23 on node -1<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.765720] &nbsp; alloc kstat_irqs on node -1<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.765725] pci 0000:00:0c.0: PCI INT A
 -&gt; Link[LRP0] -&gt; GSI 23 (level, low) -&gt; IRQ 23<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.765733] pci 0000:00:0c.0: setting latency timer to 64<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.766071] ACPI: PCI Interrupt Link [LRP3] enabled at IRQ 22<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.766074] &nbsp; alloc irq_desc for 22 on node -1<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.766075] &nbsp; alloc kstat_irqs on node -1<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.766078] pci 0000:00:15.0: PCI INT A
 -&gt; Link[LRP3] -&gt; GSI 22 (level, low) -&gt; IRQ 22<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.766085] pci 0000:00:15.0: setting latency timer to 64<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.766422] ACPI: PCI Interrupt Link [LRP4] enabled at IRQ 21<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.766424] &nbsp; alloc irq_desc for 21 on node -1<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.766425] &nbsp; alloc kstat_irqs on node -1<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.766428] pci 0000:00:16.0: PCI INT A
 -&gt; Link[LRP4] -&gt; GSI 21 (level, low) -&gt; IRQ 21<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.766436] pci 0000:00:16.0: setting latency timer to 64<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.766772] ACPI: PCI Interrupt Link [LRP5] enabled at IRQ 20<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.766774] &nbsp; alloc irq_desc for 20 on node -1<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.766775] &nbsp; alloc kstat_irqs on node -1<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.766778] pci 0000:00:17.0: PCI INT A
 -&gt; Link[LRP5] -&gt; GSI 20 (level, low) -&gt; IRQ 20<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.766786] pci 0000:00:17.0: setting latency timer to 64<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.767125] ACPI: PCI Interrupt Link [LRP6] enabled at IRQ 23<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.767127] pci 0000:00:18.0: PCI INT A
 -&gt; Link[LRP6] -&gt; GSI 23 (level, low) -&gt; IRQ 23<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.767135] pci 0000:00:18.0: setting latency timer to 64<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.767141] pci_bus 0000:00: resource 0 io: &nbsp;[0x00-0xffff]<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.767142] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.767144] pci_bus 0000:01: resource 3 io: &nbsp;[0x00-0xffff]<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.767146] pci_bus 0000:01: resource 4 mem: [0x000000-0xffffffffffffffff]<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.767148] pci_bus 0000:02: resource 0 io: &nbsp;[0xe000-0xefff]<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.767150] pci_bus 0000:02: resource 1 mem: [0xfa000000-0xfeafffff]<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.767152] pci_bus 0000:02: resource 2 pref mem [0xd0000000-0xdfffffff]<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.767153] pci_bus 0000:05: resource 1 mem: [0xfeb00000-0xfebfffff]<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.767186] NET: Registered protocol family 2<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.767397] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.768793] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.774932] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.775718] TCP: Hash tables configured (established 524288 bind 65536)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.775720] TCP reno registered<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.775857] NET: Registered protocol family 1<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.776317] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 22<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.776327] pci 0000:00:04.0: PCI INT A
 -&gt; Link[LUB0] -&gt; GSI 22 (level, low) -&gt; IRQ 22<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.899525] pci 0000:00:04.0: PCI INT A disabled<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.899945] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 21<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.899950] pci 0000:00:04.1: PCI INT B
 -&gt; Link[LUB2] -&gt; GSI 21 (level, low) -&gt; IRQ 21<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.899995] pci 0000:00:04.1: PCI INT B disabled<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.900329] ACPI: PCI Interrupt Link [UB11] enabled at IRQ 20<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.900331] pci 0000:00:06.0: PCI INT A
 -&gt; Link[UB11] -&gt; GSI 20 (level, low) -&gt; IRQ 20<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.979392] pci 0000:00:06.0: PCI INT A disabled<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.979798] ACPI: PCI Interrupt Link [UB12] enabled at IRQ 23<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.979803] pci 0000:00:06.1: PCI INT B
 -&gt; Link[UB12] -&gt; GSI 23 (level, low) -&gt; IRQ 23<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.979846] pci 0000:00:06.1: PCI INT B disabled<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.980026] pci 0000:02:00.0: Boot video device<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.980322] Scanning for low memory corruption every 60 seconds<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.980451] audit: initializing netlink socket (disabled)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.980462] type=2000 audit(1346327318.979:1): initialized<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.987393] Freeing initrd memory: 16409k freed<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.988014] HugeTLB registered 2 MB page size, pre-allocated 0 pages<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.989424] VFS: Disk quotas dquot_6.5.2<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.989499] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.990130] fuse init (API version 7.13)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.990211] msgmni has been set to 11945<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.990636] alg: No test for stdrng (krng)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.990704] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.990708] io scheduler noop registered<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.990710] io scheduler anticipatory registered<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.990711] io scheduler deadline registered<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.990762] io scheduler cfq registered (default)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.991115] &nbsp; alloc irq_desc for 24 on node -1<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.991117] &nbsp; alloc kstat_irqs on node -1<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.991143] pcieport 0000:00:0c.0: irq 24 for MSI/MSI-X<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.991163] pcieport 0000:00:0c.0: setting latency timer to 64<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.991522] &nbsp; alloc irq_desc for 25 on node -1<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.991523] &nbsp; alloc kstat_irqs on node -1<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.991540] pcieport 0000:00:15.0: irq 25 for MSI/MSI-X<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.991559] pcieport 0000:00:15.0: setting latency timer to 64<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.991920] &nbsp; alloc irq_desc for 26 on node -1<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.991922] &nbsp; alloc kstat_irqs on node -1<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.991938] pcieport 0000:00:16.0: irq 26 for MSI/MSI-X<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.991957] pcieport 0000:00:16.0: setting latency timer to 64<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.992313] &nbsp; alloc irq_desc for 27 on node -1<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.992314] &nbsp; alloc kstat_irqs on node -1<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.992331] pcieport 0000:00:17.0: irq 27 for MSI/MSI-X<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.992350] pcieport 0000:00:17.0: setting latency timer to 64<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.992705] &nbsp; alloc irq_desc for 28 on node -1<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.992707] &nbsp; alloc kstat_irqs on node -1<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.992724] pcieport 0000:00:18.0: irq 28 for MSI/MSI-X<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.992743] pcieport 0000:00:18.0: setting latency timer to 64<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.992920] pci_hotplug: PCI Hot Plug PCI Core version: 0.5<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.992946] pciehp: PCI Express Hot Plug Controller Driver version: 0.4<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.993151] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.993164] ACPI: Power Button [PWRB]<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.993224] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.993226] ACPI: Power Button [PWRF]<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.994095] ACPI: SSDT 00000000cffae3a0 00235 (v01 DpgPmm &nbsp;P001Ist 00000011 INTL 20051117)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.994448] processor LNXCPU:00: registered as cooling_device0<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.994812] ACPI: SSDT 00000000cffae5e0 00235 (v01 DpgPmm &nbsp;P002Ist 00000012 INTL 20051117)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.995098] processor LNXCPU:01: registered as cooling_device1<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.995417] ACPI: SSDT 00000000cffae820 00235 (v01 DpgPmm &nbsp;P003Ist 00000012 INTL 20051117)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.995699] processor LNXCPU:02: registered as cooling_device2<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.996021] ACPI: SSDT 00000000cffaea60 00235 (v01 DpgPmm &nbsp;P004Ist 00000012 INTL 20051117)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;0.996299] processor LNXCPU:03: registered as cooling_device3<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.004155] thermal LNXTHERM:01: registered as thermal_zone0<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.004160] ACPI: Thermal Zone [THRM] (28 C)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.005252] Linux agpgart interface v0.103<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.005278] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.005368] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.005452] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.005652] 00:04: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.005764] 00:05: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.006561] brd: module loaded<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.006905] loop: module loaded<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.006962] input: Macintosh mouse button emulation as /devices/virtual/input/input2<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.007244] Fixed MDIO Bus: probed<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.007268] PPP generic driver version 2.4.2<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.007291] tun: Universal TUN/TAP device driver, 1.6<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.007292] tun: (C) 1999-2004 Max Krasnyansky &lt;maxk@qualcomm.com&gt;<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.007341] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.007353] ehci_hcd 0000:00:04.1: PCI
 INT B -&gt; Link[LUB2] -&gt; GSI 21 (level, low) -&gt; IRQ 21<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.007370] ehci_hcd 0000:00:04.1: setting latency timer to 64<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.007376] ehci_hcd 0000:00:04.1: EHCI Host Controller<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.007401] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 1<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.007425] ehci_hcd 0000:00:04.1: debug port 1<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.007432] ehci_hcd 0000:00:04.1: cache line size of 32 is not supported<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.007445] ehci_hcd 0000:00:04.1: irq 21, io mem 0xf9f7ec00<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.018844] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.018933] usb usb1: configuration #1 chosen from 1 choice<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.018960] hub 1-0:1.0: USB hub found<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.018967] hub 1-0:1.0: 6 ports detected<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.019016] ehci_hcd 0000:00:06.1: PCI
 INT B -&gt; Link[UB12] -&gt; GSI 23 (level, low) -&gt; IRQ 23<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.019026] ehci_hcd 0000:00:06.1: setting latency timer to 64<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.019028] ehci_hcd 0000:00:06.1: EHCI Host Controller<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.019059] ehci_hcd 0000:00:06.1: new USB bus registered, assigned bus number 2<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.019076] ehci_hcd 0000:00:06.1: debug port 1<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.019083] ehci_hcd 0000:00:06.1: cache line size of 32 is not supported<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.019093] ehci_hcd 0000:00:06.1: irq 23, io mem 0xf9f7e800<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.038810] ehci_hcd 0000:00:06.1: USB 2.0 started, EHCI 1.00<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.038886] usb usb2: configuration #1 chosen from 1 choice<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.038911] hub 2-0:1.0: USB hub found<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.038916] hub 2-0:1.0: 6 ports detected<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.038966] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.038978] ohci_hcd 0000:00:04.0: PCI
 INT A -&gt; Link[LUB0] -&gt; GSI 22 (level, low) -&gt; IRQ 22<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.038990] ohci_hcd 0000:00:04.0: setting latency timer to 64<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.038992] ohci_hcd 0000:00:04.0: OHCI Host Controller<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.039023] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 3<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.039040] ohci_hcd 0000:00:04.0: irq 22, io mem 0xf9f7f000<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.070816] usb usb3: configuration #1 chosen from 1 choice<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.070833] hub 3-0:1.0: USB hub found<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.070839] hub 3-0:1.0: 6 ports detected<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.070873] ohci_hcd 0000:00:06.0: PCI
 INT A -&gt; Link[UB11] -&gt; GSI 20 (level, low) -&gt; IRQ 20<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.070881] ohci_hcd 0000:00:06.0: setting latency timer to 64<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.070883] ohci_hcd 0000:00:06.0: OHCI Host Controller<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.070906] ohci_hcd 0000:00:06.0: new USB bus registered, assigned bus number 4<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.070921] ohci_hcd 0000:00:06.0: irq 20, io mem 0xf9f7d000<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.132053] usb usb4: configuration #1 chosen from 1 choice<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.132070] hub 4-0:1.0: USB hub found<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.132075] hub 4-0:1.0: 6 ports detected<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.132110] uhci_hcd: USB Universal Host Controller Interface driver<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.132155] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.132566] serio: i8042 KBD port at 0x60,0x64 irq 1<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.132572] serio: i8042 AUX port at 0x60,0x64 irq 12<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.132650] mice: PS/2 mouse device common for all mice<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.132746] rtc_cmos 00:08: RTC can wake from S4<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.132781] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.132828] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.132923] device-mapper: uevent: version 1.0.3<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.133016] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.133248] device-mapper: multipath: version 1.1.0 loaded<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.133255] device-mapper: multipath round-robin: version 1.0.0 loaded<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.133714] cpuidle: using governor ladder<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.133720] cpuidle: using governor menu<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.133974] TCP cubic registered<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.134082] NET: Registered protocol family 10<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.134589] NET: Registered protocol family 17<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.135714] PM: Resume from disk failed.<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.135723] registered taskstats version 1<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.136248] &nbsp; Magic number: 8:221:834<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.136335] rtc_cmos 00:08: setting system clock to 2012-08-30 11:48:39 UTC (1346327319)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.136342] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.136344] EDD information not available.<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.136392] Freeing unused kernel memory: 884k freed<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.136597] Write protecting the kernel read-only data: 7720k<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.152153] &lt;30&gt;udevd[105]: starting version 175<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.174451] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.174908] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 22<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.174913] forcedeth 0000:00:0a.0: 
PCI INT A -&gt; Link[LMAC] -&gt; GSI 22 (level, low) -&gt; IRQ 22<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.174918] forcedeth 0000:00:0a.0: setting latency timer to 64<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.183221] ACPI: PCI Interrupt Link [LN5A] enabled at IRQ 19<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.183230] &nbsp; alloc irq_desc for 19 on node -1<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.183233] &nbsp; alloc kstat_irqs on node -1<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.183244] firewire_ohci 
0000:05:00.0: PCI INT A -&gt; Link[LN5A] -&gt; GSI 19 (level, low) -&gt;
 IRQ 19<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.183252] firewire_ohci 0000:05:00.0: setting latency timer to 64<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.218790] [drm] Initialized drm 1.1.0 20060810<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.239257] ACPI: PCI Interrupt Link [LN0A] enabled at IRQ 18<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.239263] &nbsp; alloc irq_desc for 18 on node -1<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.239264] &nbsp; alloc kstat_irqs on node -1<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.239272] nouveau 0000:02:00.0: PCI 
INT A -&gt; Link[LN0A] -&gt; GSI 18 (level, low) -&gt; IRQ 18<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.239277] nouveau 0000:02:00.0: setting latency timer to 64<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.241852] [drm] nouveau 0000:02:00.0: Detected an NV50 generation card (0x094300a1)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.242611] [drm] nouveau 0000:02:00.0: Attempting to load BIOS image from PRAMIN<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.254940] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 3, addr 00:22:68:62:84:91<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.254943] forcedeth 0000:00:0a.0: highdma csum pwrctl gbit lnktim msi desc-v3<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.255062] ahci 0000:00:0b.0: version 3.0<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.255463] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 21<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.255468] ahci 0000:00:0b.0: PCI INT
 A -&gt; Link[LSA0] -&gt; GSI 21 (level, low) -&gt; IRQ 21<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.255515] &nbsp; alloc irq_desc for 29 on node -1<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.255517] &nbsp; alloc kstat_irqs on node -1<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.255525] ahci 0000:00:0b.0: irq 29 for MSI/MSI-X<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.255574] ahci 0000:00:0b.0: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl RAID mode<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.255576] ahci 0000:00:0b.0: flags: 64bit ncq sntf led pmp pio slum part boh <br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.255579] ahci 0000:00:0b.0: setting latency timer to 64<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.255865] scsi0 : ahci<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.255981] scsi1 : ahci<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.256033] scsi2 : ahci<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.256084] scsi3 : ahci<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.256131] scsi4 : ahci<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.256174] scsi5 : ahci<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.256297] ata1: SATA max UDMA/133 abar m8192@0xf9f76000 port 0xf9f76100 irq 29<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.256299] ata2: SATA max UDMA/133 abar m8192@0xf9f76000 port 0xf9f76180 irq 29<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.256301] ata3: SATA max UDMA/133 abar m8192@0xf9f76000 port 0xf9f76200 irq 29<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.256303] ata4: SATA max UDMA/133 abar m8192@0xf9f76000 port 0xf9f76280 irq 29<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.256305] ata5: SATA max UDMA/133 abar m8192@0xf9f76000 port 0xf9f76300 irq 29<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.256306] ata6: SATA max UDMA/133 abar m8192@0xf9f76000 port 0xf9f76380 irq 29<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.290728] [drm] nouveau 0000:02:00.0: ... appears to be valid<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.290731] [drm] nouveau 0000:02:00.0: BIT BIOS found<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.290733] [drm] nouveau 0000:02:00.0: Bios version 62.94.21.00<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.290736] [drm] nouveau 0000:02:00.0: TMDS table revision 2.0 not currently supported<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.290738] [drm] nouveau 0000:02:00.0: Found Display Configuration Block version 4.0<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.290740] [drm] nouveau 0000:02:00.0: DCB connector table: VHER 0x40 5 16 4<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.290742] [drm] nouveau 0000:02:00.0: &nbsp; 0: 0x00000000: type 0x00 idx 0 tag 0xff<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.290744] [drm] nouveau 0000:02:00.0: &nbsp; 1: 0x00001130: type 0x30 idx 1 tag 0x07<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.290746] [drm] nouveau 0000:02:00.0: &nbsp; 2: 0x00002261: type 0x61 idx 2 tag 0x08<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.290748] [drm] nouveau 0000:02:00.0: Raw DCB entry 0: 04000310 00000028<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.290750] [drm] nouveau 0000:02:00.0: Raw DCB entry 1: 01011302 00000030<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.290752] [drm] nouveau 0000:02:00.0: Raw DCB entry 2: 02011300 00000028<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.290753] [drm] nouveau 0000:02:00.0: Raw DCB entry 3: 02022332 00020020<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.290760] [drm] nouveau 0000:02:00.0: Parsing VBIOS init table 0 at offset 0xD21E<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.300014] firewire_ohci: Added fw-ohci device 0000:05:00.0, OHCI version 1.10<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.392638] [drm] nouveau 0000:02:00.0: Parsing VBIOS init table 1 at offset 0xD633<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.433755] [drm] nouveau 0000:02:00.0: Parsing VBIOS init table 2 at offset 0xE624<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.433764] [drm] nouveau 0000:02:00.0: Parsing VBIOS init table 3 at offset 0xE76D<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.450078] [drm] nouveau 0000:02:00.0: Parsing VBIOS init table 4 at offset 0xE9A9<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.450084] [drm] nouveau 0000:02:00.0: Parsing VBIOS init table at offset 0xEA0E<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.480036] [drm] nouveau 
0000:02:00.0: 0xEA0E: Condition still not met after 20ms, skipping 
following opcodes<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.480046] [drm] nouveau 0000:02:00.0: 0xC1EE: parsing output script 0<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.480052] [drm] nouveau 0000:02:00.0: 0xC1EE: parsing output script 0<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.601244] ata3: SATA link down (SStatus 0 SControl 300)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.601275] ata4: SATA link down (SStatus 0 SControl 300)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.601282] ata5: SATA link down (SStatus 0 SControl 300)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.601307] ata6: SATA link down (SStatus 0 SControl 300)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.601438] [TTM] Zone &nbsp;kernel: Available graphics memory: 3063096 kiB.<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.601440] [TTM] Zone &nbsp; dma32: Available graphics memory: 2097152 kiB.<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.601448] [drm] nouveau 0000:02:00.0: 1536 MiB VRAM<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.615766] [drm] nouveau 0000:02:00.0: 512 MiB GART (aperture)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.619895] [drm] nouveau 0000:02:00.0: Allocating FIFO number 1<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.623358] [drm] nouveau 0000:02:00.0: nouveau_channel_alloc: initialised FIFO 1<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.623851] [drm] nouveau 0000:02:00.0: Detected a DAC output<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.623853] [drm] nouveau 0000:02:00.0: Detected a TMDS output<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.623854] [drm] nouveau 0000:02:00.0: Detected a DAC output<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.623856] [drm] nouveau 0000:02:00.0: Detected a TMDS output<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.623859] [drm] nouveau 0000:02:00.0: Detected a VGA connector<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.623906] [drm] nouveau 0000:02:00.0: Detected a DVI-I connector<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.623928] [drm] nouveau 0000:02:00.0: Detected a DVI-D connector<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.631259] usb 3-1: new full speed USB device using ohci_hcd and address 2<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.780019] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.780032] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.780504] ata2.00: ATAPI: ATAPI &nbsp; DVD A &nbsp;DH16A6S, YA16, max UDMA/100<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.781190] ata2.00: configured for UDMA/100<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.781506] ata1.00: ATA-8: ST3750630AS, SD46, max UDMA/133<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.781508] ata1.00: 1465149168 sectors, multi 16: LBA48 NCQ (depth 31/32)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.783433] ata1.00: configured for UDMA/133<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.783539] scsi 0:0:0:0: Direct-Access &nbsp; &nbsp; ATA &nbsp; &nbsp; &nbsp;ST3750630AS &nbsp; &nbsp; &nbsp;SD46 PQ: 0 ANSI: 5<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.783708] sd 0:0:0:0: [sda] 1465149168 512-byte logical blocks: (750 GB/698 GiB)<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.783722] sd 0:0:0:0: Attached scsi generic sg0 type 0<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.783740] sd 0:0:0:0: [sda] Write Protect is off<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.783742] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.783760] sd 0:0:0:0: [sda] Write 
cache: enabled, read cache: enabled, doesn't support DPO or FUA<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.783878] &nbsp;sda:<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.784804] scsi 1:0:0:0: CD-ROM &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;ATAPI &nbsp; &nbsp;DVD A &nbsp;DH16A6S &nbsp; YA16 PQ: 0 ANSI: 5<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.790203] sr0: scsi3-mmc drive: 48x/12x writer dvd-ram cd/rw xa/form2 cdda tray<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.790205] Uniform CD-ROM driver Revision: 3.20<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.790233] &nbsp;sda1 sda2 sda3 sda4 &lt;<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.790305] sr 1:0:0:0: Attached scsi CD-ROM sr0<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.790355] sr 1:0:0:0: Attached scsi generic sg1 type 5<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.806454] firewire_core: created device fw0: GUID 00cd6a1e00016c20, S400<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.810422] [drm] nouveau 
0000:02:00.0: allocated 1280x1024 fb: 0x40250000, bo ffff8801a34d1a00<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.810458] fb0: nouveaufb frame buffer device<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.810459] registered panic notifier<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.810463] [drm] Initialized nouveau 0.0.15 20090420 for 0000:02:00.0 on minor 0<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.821177] &nbsp;sda5 sda6 &gt;<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.840071] sd 0:0:0:0: [sda] Attached SCSI disk<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.846440] [drm] nouveau 0000:02:00.0: 0x11F1: parsing clock script 0<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.846699] Console: switching to colour frame buffer device 160x64<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.878849] usb 3-1: configuration #1 chosen from 1 choice<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.951657] usbcore: registered new interface driver hiddev<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.974838] input: Roland EDIROL UA-3D
 as /devices/pci0000:00/0000:00:04.0/usb3/3-1/3-1:1.3/input/input3<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.974934] generic-usb 
0003:0582:001A.0001: input,hidraw0: USB HID v1.00 Device [Roland EDIROL 
UA-3D] on usb-0000:00:04.0-1/input3<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.974969] usbcore: registered new interface driver usbhid<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;1.974971] usbhid: v2.6:USB HID core driver<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;2.180012] usb 2-5: new high speed USB device using ehci_hcd and address 3<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;2.893315] usb 2-5: configuration #1 chosen from 1 choice<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;2.898907] Initializing USB Mass Storage driver...<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;2.899050] scsi6 : SCSI emulation for USB Mass Storage devices<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;2.899145] usb-storage: device found at 3<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;2.899147] usb-storage: waiting for device to settle before scanning<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;2.899164] usbcore: registered new interface driver usb-storage<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;2.899166] USB Mass Storage support registered.<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;3.226377] EXT4-fs (sda5): mounted filesystem with ordered data mode<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;3.240020] usb 4-2: new full speed USB device using ohci_hcd and address 2<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;3.466115] usb 4-2: configuration #1 chosen from 1 choice<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;3.469050] hub 4-2:1.0: USB hub found<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;3.472022] hub 4-2:1.0: 4 ports detected<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;3.781023] usb 4-2.1: new low speed USB device using ohci_hcd and address 3<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;3.909090] usb 4-2.1: configuration #1 chosen from 1 choice<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;4.001024] usb 4-2.3: new low speed USB device using ohci_hcd and address 4<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;4.144074] usb 4-2.3: configuration #1 chosen from 1 choice<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;4.167120] input: No brand 2Port 
KVMSwicther as 
/devices/pci0000:00/0000:00:06.0/usb4/4-2/4-2.3/4-2.3:1.0/input/input4<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;4.167185] generic-usb 
0003:10D5:55A2.0004: input,hidraw1: USB HID v1.10 Keyboard [No brand 
2Port KVMSwicther] on usb-0000:00:06.0-2.3/input0<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;4.170036] usbhid 4-2.3:1.1: couldn't find an input interrupt endpoint<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;5.448916] ureadahead: sending ioctl 127c to a partition!<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;5.448919] ureadahead: sending ioctl 127c to a partition!<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;7.890168] usb-storage: device scan complete<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;7.897389] scsi 6:0:0:0: Direct-Access &nbsp; &nbsp; Generic- Compact Flash &nbsp; &nbsp;1.00 PQ: 0 ANSI: 0 CCS<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;7.903634] scsi 6:0:0:1: Direct-Access &nbsp; &nbsp; Generic- SM/xD-Picture &nbsp; &nbsp;1.00 PQ: 0 ANSI: 0 CCS<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;7.909883] scsi 6:0:0:2: Direct-Access &nbsp; &nbsp; Generic- SD/MMC &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 1.00 PQ: 0 ANSI: 0 CCS<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;7.916135] scsi 6:0:0:3: Direct-Access &nbsp; &nbsp; Generic- MS/MS-Pro &nbsp; &nbsp; &nbsp; &nbsp;1.00 PQ: 0 ANSI: 0 CCS<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;7.916437] sd 6:0:0:0: Attached scsi generic sg2 type 0<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;7.916529] sd 6:0:0:1: Attached scsi generic sg3 type 0<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;7.916636] sd 6:0:0:2: Attached scsi generic sg4 type 0<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;7.916736] sd 6:0:0:3: Attached scsi generic sg5 type 0<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;7.920254] sd 6:0:0:0: [sdb] Attached SCSI removable disk<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;7.921003] sd 6:0:0:1: [sdc] Attached SCSI removable disk<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;7.921753] sd 6:0:0:2: [sdd] Attached SCSI removable disk<br>
Aug 30 11:49:23 server kernel: [ &nbsp; &nbsp;7.922500] sd 6:0:0:3: [sde] Attached SCSI removable disk<br>
Aug 30 11:49:23 server kernel: [ &nbsp; 35.865813] &lt;30&gt;udevd[472]: starting version 175<br>
Aug 30 11:49:23 server kernel: [ &nbsp; 35.875291] lp: driver loaded but no devices found<br>
Aug 30 11:49:23 server kernel: [ &nbsp; 35.899428] i2c i2c-4: nForce2 SMBus adapter at 0x4d00<br>
Aug 30 11:49:23 server kernel: [ &nbsp; 35.899434] ACPI: resource 
nForce2_smbus [0x4e00-0x4e3f] conflicts with ACPI region SM00 
[0x004e00-0x004e3f]<br>
Aug 30 11:49:23 server kernel: [ &nbsp; 35.899435] ACPI: If an ACPI driver is
 available for this device, you should use it instead of the native 
driver<br>
Aug 30 11:49:23 server kernel: [ &nbsp; 35.899437] nForce2_smbus 0000:00:03.2: Error probing SMB2.<br>
Aug 30 11:49:23 server kernel: [ &nbsp; 35.938379] Adding 6458088k swap on /dev/sda6. &nbsp;Priority:-1 extents:1 across:6458088k <br>
Aug 30 11:49:23 server kernel: [ &nbsp; 36.004360] input: Logitech USB 
Receiver as 
/devices/pci0000:00/0000:00:06.0/usb4/4-2/4-2.1/4-2.1:1.0/input/input5<br>
Aug 30 11:49:23 server kernel: [ &nbsp; 36.004466] logitech 
0003:046D:C517.0002: input,hidraw2: USB HID v1.10 Keyboard [Logitech USB
 Receiver] on usb-0000:00:06.0-2.1/input0<br>
Aug 30 11:49:23 server kernel: [ &nbsp; 36.024063] logitech 0003:046D:C517.0003: fixing up Logitech keyboard report descriptor<br>
Aug 30 11:49:23 server kernel: [ &nbsp; 36.024829] input: Logitech USB 
Receiver as 
/devices/pci0000:00/0000:00:06.0/usb4/4-2/4-2.1/4-2.1:1.1/input/input6<br>
Aug 30 11:49:23 server kernel: [ &nbsp; 36.025145] logitech 
0003:046D:C517.0003: input,hiddev96,hidraw3: USB HID v1.10 Mouse 
[Logitech USB Receiver] on usb-0000:00:06.0-2.1/input1<br>
Aug 30 11:49:23 server kernel: [ &nbsp; 36.040796] acer-wmi: Acer Laptop ACPI-WMI Extras<br>
Aug 30 11:49:23 server kernel: [ &nbsp; 36.040806] acer-wmi: No or unsupported WMI interface, unable to load<br>
Aug 30 11:49:23 server kernel: [ &nbsp; 36.043158] type=1505 
audit(1346323754.406:2): &nbsp;operation="profile_load" pid=680 
name="/sbin/dhclient"<br>
Aug 30 11:49:23 server kernel: [ &nbsp; 36.043481] type=1505 
audit(1346323754.406:3): &nbsp;operation="profile_load" pid=680 
name="/usr/lib/NetworkManager/nm-dhcp-client.action"<br>
Aug 30 11:49:23 server kernel: [ &nbsp; 36.043667] type=1505 
audit(1346323754.406:4): &nbsp;operation="profile_load" pid=680 
name="/usr/lib/connman/scripts/dhclient-script"<br>
Aug 30 11:49:23 server kernel: [ &nbsp; 36.048642] type=1505 
audit(1346323754.406:5): &nbsp;operation="profile_replace" pid=742 
name="/sbin/dhclient"<br>
Aug 30 11:49:23 server kernel: [ &nbsp; 36.048963] type=1505 
audit(1346323754.406:6): &nbsp;operation="profile_replace" pid=742 
name="/usr/lib/NetworkManager/nm-dhcp-client.action"<br>
Aug 30 11:49:23 server kernel: [ &nbsp; 36.049147] type=1505 
audit(1346323754.406:7): &nbsp;operation="profile_replace" pid=742 
name="/usr/lib/connman/scripts/dhclient-script"<br>
Aug 30 11:49:23 server kernel: [ &nbsp; 36.073207] &nbsp; alloc irq_desc for 30 on node -1<br>
Aug 30 11:49:23 server kernel: [ &nbsp; 36.073210] &nbsp; alloc kstat_irqs on node -1<br>
Aug 30 11:49:23 server kernel: [ &nbsp; 36.073222] forcedeth 0000:00:0a.0: irq 30 for MSI/MSI-X<br>
Aug 30 11:49:23 server kernel: [ &nbsp; 36.101730] HDA Intel 0000:00:08.0: power state changed by ACPI to D0<br>
Aug 30 11:49:23 server kernel: [ &nbsp; 36.101771] HDA Intel 0000:00:08.0: power state changed by ACPI to D0<br>
Aug 30 11:49:23 server kernel: [ &nbsp; 36.102137] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 20<br>
Aug 30 11:49:23 server kernel: [ &nbsp; 36.102141] HDA Intel 0000:00:08.0: 
PCI INT A -&gt; Link[LAZA] -&gt; GSI 20 (level, low) -&gt; IRQ 20<br>
Aug 30 11:49:23 server kernel: [ &nbsp; 36.102144] hda_intel: Disable MSI for Nvidia chipset<br>
Aug 30 11:49:23 server kernel: [ &nbsp; 36.102189] HDA Intel 0000:00:08.0: setting latency timer to 64<br>
Aug 30 11:49:23 server kernel: [ &nbsp; 36.216258] usbcore: registered new interface driver snd-usb-audio<br>
Aug 30 11:49:23 server kernel: [ &nbsp; 36.217683] fsck.ext4: sending ioctl 127c to a partition!<br>
Aug 30 11:49:23 server kernel: [ &nbsp; 36.217686] fsck.ext4: sending ioctl 127c to a partition!<br>
Aug 30 11:49:23 server kernel: [ &nbsp; 36.217782] fsck.ext4: sending ioctl 127c to a partition!<br>
Aug 30 11:49:23 server kernel: [ &nbsp; 36.217784] fsck.ext4: sending ioctl 127c to a partition!<br>
Aug 30 11:49:23 server kernel: [ &nbsp; 37.433761] hda_codec: ALC1200: BIOS auto-probing.<br>
Aug 30 11:49:23 server kernel: [ &nbsp; 38.030074] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:08.0/input/input7<br>
Aug 30 11:49:23 server kernel: [ &nbsp; 45.179909] RPC: Registered udp transport module.<br>
Aug 30 11:49:23 server kernel: [ &nbsp; 45.179912] RPC: Registered tcp transport module.<br>
Aug 30 11:49:23 server kernel: [ &nbsp; 45.179913] RPC: Registered tcp NFSv4.1 backchannel transport module.<br>
Aug 30 11:49:23 server kernel: [ &nbsp; 45.208198] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).<br>
Aug 30 11:49:23 server kernel: [ &nbsp; 45.212751] Bluetooth: Core ver 2.15<br>
Aug 30 11:49:23 server kernel: [ &nbsp; 45.212810] NET: Registered protocol family 31<br>
Aug 30 11:49:23 server kernel: [ &nbsp; 45.212812] Bluetooth: HCI device and connection manager initialized<br>
Aug 30 11:49:23 server kernel: [ &nbsp; 45.212814] Bluetooth: HCI socket layer initialized<br>
Aug 30 11:49:23 server kernel: [ &nbsp; 45.215981] Bluetooth: L2CAP ver 2.14<br>
Aug 30 11:49:23 server kernel: [ &nbsp; 45.215983] Bluetooth: L2CAP socket layer initialized<br>
Aug 30 11:49:23 server kernel: [ &nbsp; 45.218870] Bluetooth: BNEP (Ethernet Emulation) ver 1.3<br>
Aug 30 11:49:23 server kernel: [ &nbsp; 45.218872] Bluetooth: BNEP filters: protocol multicast<br>
Aug 30 11:49:23 server kernel: [ &nbsp; 45.221698] Bluetooth: SCO (Voice Link) ver 0.6<br>
Aug 30 11:49:23 server kernel: [ &nbsp; 45.221699] Bluetooth: SCO socket layer initialized<br>
Aug 30 11:49:23 server kernel: [ &nbsp; 45.295646] ppdev: user-space parallel port driver<br>
Aug 30 11:49:23 server kernel: [ &nbsp; 45.307523] type=1505 
audit(1346323763.663:8): &nbsp;operation="profile_load" pid=1197 
name="/usr/lib/cups/backend/cups-pdf"<br>
Aug 30 11:49:23 server kernel: [ &nbsp; 45.307895] type=1505 
audit(1346323763.663:9): &nbsp;operation="profile_load" pid=1197 
name="/usr/sbin/cupsd"<br>
Aug 30 11:49:23 server kernel: [ &nbsp; 45.319098] Bluetooth: RFCOMM TTY layer initialized<br>
Aug 30 11:49:23 server kernel: [ &nbsp; 45.319102] Bluetooth: RFCOMM socket layer initialized<br>
Aug 30 11:49:23 server kernel: [ &nbsp; 45.319103] Bluetooth: RFCOMM ver 1.11<br>
Aug 30 11:49:23 server dbus[1132]: [system] Activating service name='org.freedesktop.ColorManager' (using servicehelper)<br>
Aug 30 11:49:23 server dbus[1132]: [system] Successfully activated service 'org.freedesktop.ColorManager'<br>
Aug 30 11:49:24 server kernel: [ &nbsp; 46.140005] eth0: no IPv6 routers present<br>
Aug 30 11:49:24 server kernel: [ &nbsp; 46.210309] init: failsafe main process (1104) killed by TERM signal<br>
Aug 30 11:49:24 server modem-manager[1300]: &lt;info&gt; &nbsp;ModemManager (version 0.5.2.0) starting...<br>
Aug 30 11:49:24 server modem-manager[1300]: &lt;info&gt; &nbsp;Loaded plugin AnyData<br>
Aug 30 11:49:24 server modem-manager[1300]: &lt;info&gt; &nbsp;Loaded plugin Huawei<br>
Aug 30 11:49:24 server modem-manager[1300]: &lt;info&gt; &nbsp;Loaded plugin Gobi<br>
Aug 30 11:49:24 server modem-manager[1300]: &lt;info&gt; &nbsp;Loaded plugin Option<br>
Aug 30 11:49:24 server modem-manager[1300]: &lt;info&gt; &nbsp;Loaded plugin Option High-Speed<br>
Aug 30 11:49:24 server modem-manager[1300]: &lt;info&gt; &nbsp;Loaded plugin Generic<br>
Aug 30 11:49:24 server modem-manager[1300]: &lt;info&gt; &nbsp;Loaded plugin Nokia<br>
Aug 30 11:49:24 server modem-manager[1300]: &lt;info&gt; &nbsp;Loaded plugin Linktop<br>
Aug 30 11:49:24 server modem-manager[1300]: &lt;info&gt; &nbsp;Loaded plugin Novatel<br>
Aug 30 11:49:24 server modem-manager[1300]: &lt;info&gt; &nbsp;Loaded plugin ZTE<br>
Aug 30 11:49:24 server modem-manager[1300]: &lt;info&gt; &nbsp;Loaded plugin Ericsson MBM<br>
Aug 30 11:49:24 server modem-manager[1300]: &lt;info&gt; &nbsp;Loaded plugin Wavecom<br>
Aug 30 11:49:24 server modem-manager[1300]: &lt;info&gt; &nbsp;Loaded plugin MotoC<br>
Aug 30 11:49:24 server modem-manager[1300]: &lt;info&gt; &nbsp;Loaded plugin Samsung<br>
Aug 30 11:49:24 server modem-manager[1300]: &lt;info&gt; &nbsp;Loaded plugin Sierra<br>
Aug 30 11:49:24 server modem-manager[1300]: &lt;info&gt; &nbsp;Loaded plugin SimTech<br>
Aug 30 11:49:24 server modem-manager[1300]: &lt;info&gt; &nbsp;Loaded plugin X22X<br>
Aug 30 11:49:24 server modem-manager[1300]: &lt;info&gt; &nbsp;Loaded plugin Longcheer<br>
Aug 30 11:49:24 server NetworkManager[1309]: &lt;info&gt; NetworkManager (version 0.9.4.0) is starting...<br>
Aug 30 11:49:24 server NetworkManager[1309]: &lt;info&gt; Read config file /etc/NetworkManager/NetworkManager.conf<br>
Aug 30 11:49:24 server NetworkManager[1309]: &lt;info&gt; VPN: loaded org.freedesktop.NetworkManager.openconnect<br>
Aug 30 11:49:24 server NetworkManager[1309]: &lt;info&gt; VPN: loaded org.freedesktop.NetworkManager.openvpn<br>
Aug 30 11:49:24 server NetworkManager[1309]: &lt;info&gt; VPN: loaded org.freedesktop.NetworkManager.vpnc<br>
Aug 30 11:49:24 server NetworkManager[1309]: &lt;info&gt; VPN: loaded org.freedesktop.NetworkManager.pptp<br>
Aug 30 11:49:24 server NetworkManager[1309]: &lt;info&gt; DNS: loaded plugin dnsmasq<br>
Aug 30 11:49:24 server dbus[1132]: [system] Activating service name='org.freedesktop.PolicyKit1' (using servicehelper)<br>
Aug 30 11:49:24 server kernel: [ &nbsp; 46.228839] type=1505 
audit(1346323764.584:10): &nbsp;operation="profile_load" pid=1326 
name="/usr/share/gdm/guest-session/Xsession"<br>
Aug 30 11:49:24 server kernel: [ &nbsp; 46.229035] type=1505 
audit(1346323764.584:11): &nbsp;operation="profile_replace" pid=1328 
name="/sbin/dhclient"<br>
Aug 30 11:49:24 server kernel: [ &nbsp; 46.229358] type=1505 
audit(1346323764.584:12): &nbsp;operation="profile_replace" pid=1328 
name="/usr/lib/NetworkManager/nm-dhcp-client.action"<br>
Aug 30 11:49:24 server kernel: [ &nbsp; 46.229544] type=1505 
audit(1346323764.584:13): &nbsp;operation="profile_replace" pid=1328 
name="/usr/lib/connman/scripts/dhclient-script"<br>
Aug 30 11:49:24 server kernel: [ &nbsp; 46.231120] type=1505 
audit(1346323764.584:14): &nbsp;operation="profile_load" pid=1327 
name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper"<br>
Aug 30 11:49:24 server kernel: [ &nbsp; 46.232152] type=1505 
audit(1346323764.594:15): &nbsp;operation="profile_load" pid=1334 
name="/usr/lib/telepathy/mission-control-5"<br>
Aug 30 11:49:24 server kernel: [ &nbsp; 46.232510] type=1505 
audit(1346323764.594:16): &nbsp;operation="profile_load" pid=1334 
name="/usr/lib/telepathy/telepathy-*"<br>
Aug 30 11:49:24 server kernel: [ &nbsp; 46.233144] type=1505 
audit(1346323764.594:17): &nbsp;operation="profile_load" pid=1333 
name="/usr/bin/freshclam"<br>
Aug 30 11:49:24 server polkitd[1319]: started daemon version 0.104 using authority implementation `local' version `0.104'<br>
Aug 30 11:49:24 server dbus[1132]: [system] Successfully activated service 'org.freedesktop.PolicyKit1'<br>
Aug 30 11:49:24 server NetworkManager[1309]: &nbsp; &nbsp;SCPlugin-Ifupdown: init!<br>
Aug 30 11:49:24 server NetworkManager[1309]: &nbsp; &nbsp;SCPlugin-Ifupdown: update_system_hostname<br>
Aug 30 11:49:24 server NetworkManager[1309]: &nbsp; &nbsp;SCPluginIfupdown: guessed connection type (eth0) = 802-3-ethernet<br>
Aug 30 11:49:24 server NetworkManager[1309]: &nbsp; &nbsp;SCPlugin-Ifupdown: 
update_connection_setting_from_if_block: name:eth0, type:802-3-ethernet,
 id:Ifupdown (eth0), uuid: 681b428f-beaf-8932-dce4-687ed5bae28e<br>
Aug 30 11:49:24 server NetworkManager[1309]: &nbsp; &nbsp;SCPlugin-Ifupdown: addresses count: 1<br>
Aug 30 11:49:24 server NetworkManager[1309]: &nbsp; &nbsp;SCPlugin-Ifupdown: adding eth0 to iface_connections<br>
Aug 30 11:49:24 server NetworkManager[1309]: &nbsp; &nbsp;SCPlugin-Ifupdown: adding iface eth0 to well_known_interfaces<br>
Aug 30 11:49:24 server NetworkManager[1309]: &nbsp; &nbsp;SCPlugin-Ifupdown: autoconnect<br>
Aug 30 11:49:24 server NetworkManager[1309]: &nbsp; &nbsp;SCPluginIfupdown: management mode: unmanaged<br>
Aug 30 11:49:24 server NetworkManager[1309]: &nbsp; &nbsp;SCPlugin-Ifupdown: 
devices added (path: /sys/devices/pci0000:00/0000:00:0a.0/net/eth0, 
iface: eth0)<br>
Aug 30 11:49:24 server NetworkManager[1309]: &nbsp; &nbsp;SCPluginIfupdown: locking wired connection setting<br>
Aug 30 11:49:24 server NetworkManager[1309]: &nbsp; &nbsp;SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)<br>
Aug 30 11:49:24 server NetworkManager[1309]: &nbsp; &nbsp;SCPlugin-Ifupdown: 
device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown
 configuration found.<br>
Aug 30 11:49:24 server NetworkManager[1309]: &nbsp; &nbsp;SCPlugin-Ifupdown: end _init.<br>
Aug 30 11:49:24 server NetworkManager[1309]: &lt;info&gt; Loaded plugin 
ifupdown: (C) 2008 Canonical Ltd. &nbsp;To report bugs please use the 
NetworkManager mailing list.<br>
Aug 30 11:49:24 server NetworkManager[1309]: &lt;info&gt; Loaded plugin 
keyfile: (c) 2007 - 2010 Red Hat, Inc. &nbsp;To report bugs please use the 
NetworkManager mailing list.<br>
Aug 30 11:49:24 server NetworkManager[1309]: &nbsp; &nbsp;Ifupdown: get unmanaged devices count: 1<br>
Aug 30 11:49:24 server NetworkManager[1309]: &nbsp; &nbsp;SCPlugin-Ifupdown: (30691120) ... get_connections.<br>
Aug 30 11:49:24 server NetworkManager[1309]: &nbsp; &nbsp;SCPlugin-Ifupdown: 
(30691120) ... get_connections (managed=false): return empty list.<br>
Aug 30 11:49:24 server NetworkManager[1309]: &nbsp; &nbsp;keyfile: parsing CSW Lisboa ... <br>
Aug 30 11:49:24 server NetworkManager[1309]: &nbsp; &nbsp;keyfile: &nbsp; &nbsp; read connection 'CSW Lisboa'<br>
Aug 30 11:49:24 server NetworkManager[1309]: &nbsp; &nbsp;keyfile: parsing eth0 ... <br>
Aug 30 11:49:24 server NetworkManager[1309]: &nbsp; &nbsp;keyfile: &nbsp; &nbsp; read connection 'eth0'<br>
Aug 30 11:49:24 server NetworkManager[1309]: &nbsp; &nbsp;keyfile: parsing CSW Coimbra &nbsp;... <br>
Aug 30 11:49:24 server NetworkManager[1309]: &nbsp; &nbsp;keyfile: &nbsp; &nbsp; read connection 'CSW Coimbra '<br>
Aug 30 11:49:24 server NetworkManager[1309]: &nbsp; &nbsp;Ifupdown: get unmanaged devices count: 1<br>
Aug 30 11:49:24 server NetworkManager[1309]: &lt;info&gt; modem-manager is now available<br>
Aug 30 11:49:24 server NetworkManager[1309]: &lt;info&gt; monitoring kernel firmware directory '/lib/firmware'.<br>
Aug 30 11:49:24 server NetworkManager[1309]: &lt;info&gt; WiFi enabled by radio killswitch; enabled by state file<br>
Aug 30 11:49:24 server NetworkManager[1309]: &lt;info&gt; WWAN enabled by radio killswitch; enabled by state file<br>
Aug 30 11:49:24 server NetworkManager[1309]: &lt;info&gt; WiMAX enabled by radio killswitch; enabled by state file<br>
Aug 30 11:49:24 server NetworkManager[1309]: &lt;info&gt; Networking is enabled by state file<br>
Aug 30 11:49:24 server NetworkManager[1309]: &lt;warn&gt; failed to allocate link cache: (-10) Operation not supported<br>
Aug 30 11:49:24 server NetworkManager[1309]: &lt;info&gt; (eth0): carrier is ON<br>
Aug 30 11:49:24 server NetworkManager[1309]: &lt;info&gt; (eth0): new Ethernet device (driver: 'forcedeth' ifindex: 2)<br>
Aug 30 11:49:24 server NetworkManager[1309]: &lt;info&gt; (eth0): exported as /org/freedesktop/NetworkManager/Devices/0<br>
Aug 30 11:49:24 server cron[1404]: (CRON) INFO (pidfile fd = 3)<br>
Aug 30 11:49:24 server acpid: starting up with proc fs<br>
Aug 30 11:49:24 server anacron[1439]: Anacron 2.3 started on 2012-08-30<br>
Aug 30 11:49:24 server acpid: 35 rules loaded<br>
Aug 30 11:49:24 server acpid: waiting for events: event logging is off<br>
Aug 30 11:49:24 server kernel: [ &nbsp; 46.445730] init: kdm main process (1421) killed by TERM signal<br>
Aug 30 11:49:24 server kernel: [ &nbsp; 46.452944] init: gdm main process (1438) killed by TERM signal<br>
Aug 30 11:49:24 server automount[1453]: syntax error in nsswitch config near [ syntax error ]<br>
Aug 30 11:49:24 server NetworkManager[1309]: &lt;info&gt; Unmanaged 
Device found; state CONNECTED forced. (see 
http://bugs.launchpad.net/bugs/191889)<br>
Aug 30 11:49:24 server NetworkManager[1309]: &lt;info&gt; Unmanaged 
Device found; state CONNECTED forced. (see 
http://bugs.launchpad.net/bugs/191889)<br>
Aug 30 11:49:24 server cron[1501]: (CRON) STARTUP (fork ok)<br>
Aug 30 11:49:24 server pulseaudio[1508]: [pulseaudio] authkey.c: Failed 
to open cookie file '/etc/timidity/.pulse-cookie': No such file or 
directory<br>
Aug 30 11:49:24 server pulseaudio[1508]: [pulseaudio] authkey.c: Failed 
to load authorization key '/etc/timidity/.pulse-cookie': No such file or
 directory<br>
Aug 30 11:49:24 server pulseaudio[1508]: [autospawn] core-util.c: Home directory /etc/timidity not ours.<br>
Aug 30 11:49:24 server pulseaudio[1508]: [autospawn] lock-autospawn.c: Cannot access autospawn lock.<br>
Aug 30 11:49:24 server pulseaudio[1508]: [pulseaudio] main.c: Failed to acquire autospawn lock<br>
Aug 30 11:49:24 server cron[1501]: (CRON) INFO (Running @reboot jobs)<br>
Aug 30 11:49:25 server anacron[1439]: Will run job `cron.daily' in 5 min.<br>
Aug 30 11:49:25 server anacron[1439]: Will run job `cron.weekly' in 10 min.<br>
Aug 30 11:49:25 server anacron[1439]: Jobs will be executed sequentially<br>
Aug 30 11:49:25 server acpid: client connected from 1488[0:0]<br>
Aug 30 11:49:25 server acpid: 1 client rule loaded<br>
Aug 30 11:49:25 server dbus[1132]: [system] Activating service name='org.freedesktop.Accounts' (using servicehelper)<br>
Aug 30 11:49:25 server dbus[1132]: [system] Successfully activated service 'org.freedesktop.Accounts'<br>
Aug 30 11:49:25 server accounts-daemon[1591]: started daemon version 0.6.15<br>
Aug 30 11:49:26 server dbus[1132]: [system] Activating service name='org.freedesktop.ConsoleKit' (using servicehelper)<br>
Aug 30 11:49:26 server dbus[1132]: [system] Successfully activated service 'org.freedesktop.ConsoleKit'<br>
Aug 30 11:49:26 server dbus[1132]: [system] Activating service name='org.freedesktop.UPower' (using servicehelper)<br>
Aug 30 11:49:26 server dbus[1132]: [system] Successfully activated service 'org.freedesktop.UPower'<br>
Aug 30 11:49:28 server /etc/mysql/debian-start[1840]: Upgrading MySQL tables if necessary.<br>
Aug 30 11:49:28 server /etc/mysql/debian-start[1844]: /usr/bin/mysql_upgrade: the '--basedir' option is always ignored<br>
Aug 30 11:49:28 server /etc/mysql/debian-start[1844]: Looking for 'mysql' as: /usr/bin/mysql<br>
Aug 30 11:49:28 server /etc/mysql/debian-start[1844]: Looking for 'mysqlcheck' as: /usr/bin/mysqlcheck<br>
Aug 30 11:49:28 server /etc/mysql/debian-start[1844]: This installation 
of MySQL is already upgraded to 5.5.24, use --force if you still need to
 run mysql_upgrade<br>
Aug 30 11:49:28 server /etc/mysql/debian-start[1875]: Checking for insecure root accounts.<br>
Aug 30 11:49:28 server /etc/mysql/debian-start[1880]: Triggering myisam-recover for all MyISAM tables<br>
Aug 30 11:49:28 server dbus[1132]: [system] Activating service name='org.freedesktop.RealtimeKit1' (using servicehelper)<br>
Aug 30 11:49:28 server dbus[1132]: [system] Successfully activated service 'org.freedesktop.RealtimeKit1'<br>
Aug 30 11:49:28 server rtkit-daemon[1890]: Successfully called chroot.<br>
Aug 30 11:49:28 server rtkit-daemon[1890]: Successfully dropped privileges.<br>
Aug 30 11:49:28 server rtkit-daemon[1890]: Successfully limited resources.<br>
Aug 30 11:49:28 server rtkit-daemon[1890]: Running.<br>
Aug 30 11:49:28 server rtkit-daemon[1890]: Canary thread running.<br>
Aug 30 11:49:28 server rtkit-daemon[1890]: Watchdog thread running.<br>
Aug 30 11:49:28 server rtkit-daemon[1890]: Successfully made thread 1888
 of process 1888 (n/a) owned by '114' high priority at nice level -11.<br>
Aug 30 11:49:28 server rtkit-daemon[1890]: Supervising 1 threads of 1 processes of 1 users.<br>
Aug 30 11:49:28 server NetworkManager[1309]: &lt;info&gt; Unmanaged 
Device found; state CONNECTED forced. (see 
http://bugs.launchpad.net/bugs/191889)<br>
Aug 30 11:49:28 server rtkit-daemon[1890]: Successfully made thread 1896 of process 1888 (n/a) owned by '114' RT at priority 5.<br>
Aug 30 11:49:28 server rtkit-daemon[1890]: Supervising 2 threads of 1 processes of 1 users.<br>
Aug 30 11:49:28 server rtkit-daemon[1890]: Successfully made thread 1897 of process 1888 (n/a) owned by '114' RT at priority 5.<br>
Aug 30 11:49:28 server rtkit-daemon[1890]: Supervising 3 threads of 1 processes of 1 users.<br>
Aug 30 11:49:30 server rtkit-daemon[1890]: Successfully made thread 1994 of process 1888 (n/a) owned by '114' RT at priority 5.<br>
Aug 30 11:49:30 server rtkit-daemon[1890]: Supervising 4 threads of 1 processes of 1 users.<br>
Aug 30 11:49:30 server rtkit-daemon[1890]: Successfully made thread 2014 of process 1888 (n/a) owned by '114' RT at priority 5.<br>
Aug 30 11:49:30 server rtkit-daemon[1890]: Supervising 5 threads of 1 processes of 1 users.<br>
Aug 30 11:49:30 server pptpd[2140]: MGR: Manager process started<br>
Aug 30 11:49:30 server pptpd[2140]: MGR: Maximum of 100 connections available<br>
Aug 30 11:49:38 server ntpdate[1234]: step time server 91.189.94.4 offset 6.088913 sec<br>
Aug 30 11:49:40 server named[2262]: starting BIND 9.8.1-P1 -u bind<br>
Aug 30 11:49:40 server named[2262]: built with '--prefix=/usr' 
'--mandir=/usr/share/man' '--infodir=/usr/share/info' 
'--sysconfdir=/etc/bind' '--localstatedir=/var' '--enable-threads' 
'--enable-largefile' '--with-libtool' '--enable-shared' 
'--enable-static' '--with-openssl=/usr' '--with-gssapi=/usr' 
'--with-gnu-ld' '--with-geoip=/usr' '--enable-ipv6' 
'CFLAGS=-fno-strict-aliasing -DDIG_SIGCHASE -O2' 
'LDFLAGS=-Wl,-Bsymbolic-functions -Wl,-z,relro' 
'CPPFLAGS=-D_FORTIFY_SOURCE=2'<br>
Aug 30 11:49:40 server named[2262]: adjusted limit on open files from 1024 to 1048576<br>
Aug 30 11:49:40 server named[2262]: found 4 CPUs, using 4 worker threads<br>
Aug 30 11:49:40 server named[2262]: using up to 4096 sockets<br>
Aug 30 11:49:40 server named[2262]: loading configuration from '/etc/bind/named.conf'<br>
Aug 30 11:49:40 server named[2262]: reading built-in trusted keys from file '/etc/bind/bind.keys'<br>
Aug 30 11:49:40 server named[2262]: using default UDP/IPv4 port range: [1024, 65535]<br>
Aug 30 11:49:40 server named[2262]: using default UDP/IPv6 port range: [1024, 65535]<br>
Aug 30 11:49:40 server named[2262]: listening on IPv4 interface lo, 127.0.0.1#53<br>
Aug 30 11:49:40 server named[2262]: listening on IPv4 interface eth0, 192.168.1.10#53<br>
Aug 30 11:49:40 server named[2262]: generating session key for dynamic DNS<br>
Aug 30 11:49:40 server named[2262]: sizing zone task pool based on 1 zones<br>
Aug 30 11:49:40 server named[2262]: set up managed keys zone for view _default, file 'managed-keys.bind'<br>
Aug 30 11:49:40 server named[2262]: Warning: 'empty-zones-enable/disable-empty-zone' not set: disabling RFC 1918 empty zones<br>
Aug 30 11:49:40 server named[2262]: automatic empty zone: 0.IN-ADDR.ARPA<br>
Aug 30 11:49:40 server named[2262]: automatic empty zone: 127.IN-ADDR.ARPA<br>
Aug 30 11:49:40 server named[2262]: automatic empty zone: 254.169.IN-ADDR.ARPA<br>
Aug 30 11:49:40 server named[2262]: automatic empty zone: 2.0.192.IN-ADDR.ARPA<br>
Aug 30 11:49:40 server named[2262]: automatic empty zone: 100.51.198.IN-ADDR.ARPA<br>
Aug 30 11:49:40 server named[2262]: automatic empty zone: 113.0.203.IN-ADDR.ARPA<br>
Aug 30 11:49:40 server named[2262]: automatic empty zone: 255.255.255.255.IN-ADDR.ARPA<br>
Aug 30 11:49:40 server named[2262]: automatic empty zone: 
0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA<br>
Aug 30 11:49:40 server named[2262]: automatic empty zone: 
1.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA<br>
Aug 30 11:49:40 server named[2262]: automatic empty zone: D.F.IP6.ARPA<br>
Aug 30 11:49:40 server named[2262]: automatic empty zone: 8.E.F.IP6.ARPA<br>
Aug 30 11:49:40 server named[2262]: automatic empty zone: 9.E.F.IP6.ARPA<br>
Aug 30 11:49:40 server named[2262]: automatic empty zone: A.E.F.IP6.ARPA<br>
Aug 30 11:49:40 server named[2262]: automatic empty zone: B.E.F.IP6.ARPA<br>
Aug 30 11:49:40 server named[2262]: automatic empty zone: 8.B.D.0.1.0.0.2.IP6.ARPA<br>
Aug 30 11:49:40 server named[2262]: command channel listening on 127.0.0.1#953<br>
Aug 30 11:49:40 server named[2262]: command channel listening on ::1#953<br>
Aug 30 11:49:40 server named[2262]: the working directory is not writable<br>
Aug 30 11:49:40 server named[2262]: zone pirucas.com/IN: loaded serial 2012082901<br>
Aug 30 11:49:40 server named[2262]: managed-keys-zone ./IN: loading from master file managed-keys.bind failed: file not found<br>
Aug 30 11:49:40 server named[2262]: managed-keys-zone ./IN: loaded serial 0<br>
Aug 30 11:49:40 server named[2262]: running<br>
Aug 30 11:49:40 server named[2262]: zone pirucas.com/IN: sending notifies (serial 2012082901)<br>
Aug 30 11:49:40 server kernel: [ &nbsp; 56.353056] /dev/vmmon[2318]: Module vmmon: registered with major=10 minor=165<br>
Aug 30 11:49:40 server kernel: [ &nbsp; 56.353071] /dev/vmmon[2318]: Initial 
HV check: anyNotCapable=0 anyUnlocked=0 anyEnabled=1 anyDisabled=0<br>
Aug 30 11:49:40 server kernel: [ &nbsp; 56.353078] /dev/vmmon[2318]: HV 
check: anyNotCapable=0 anyUnlocked=0 anyEnabled=1 anyDisabled=0<br>
Aug 30 11:49:40 server kernel: [ &nbsp; 56.353080] /dev/vmmon[2318]: Module vmmon: initialized<br>
Aug 30 11:49:40 server kernel: [ &nbsp; 56.370074] [2327]: VMCI: shared components initialized.<br>
Aug 30 11:49:40 server kernel: [ &nbsp; 56.370125] [2327]: VMCI: host components initialized.<br>
Aug 30 11:49:40 server kernel: [ &nbsp; 56.370224] [2327]: VMCI: Module registered (name=vmci,major=10,minor=54).<br>
Aug 30 11:49:40 server kernel: [ &nbsp; 56.370226] [2327]: VMCI: Using host personality<br>
Aug 30 11:49:40 server kernel: [ &nbsp; 56.370228] [2327]: VMCI: Module (name=vmci) is initialized<br>
Aug 30 11:49:41 server named[2262]: error (network unreachable) resolving 'server/A/IN': 2001:503:ba3e::2:30#53<br>
Aug 30 11:49:41 server named[2262]: error (network unreachable) resolving './NS/IN': 2001:503:ba3e::2:30#53<br>
Aug 30 11:49:41 server gnome-session[2421]: WARNING: Session 'ubuntu' runnable check failed: Exited with code 1<br>
Aug 30 11:49:41 server vmnetBridge: Bridge process created.<br>
Aug 30 11:49:41 server vmnetBridge: RTM_NEWLINK: name:eth0 index:2 flags:0x00011043<br>
Aug 30 11:49:41 server vmnetBridge: Adding interface eth0 index:2<br>
Aug 30 11:49:41 server vmnetBridge: Started bridge eth0 to virtual network 0.<br>
Aug 30 11:49:41 server vmnetBridge: RTM_NEWROUTE: index:2<br>
Aug 30 11:49:41 server gnome-session[2421]: WARNING: Could not parse 
desktop file /etc/xdg/autostart/vmware-user.desktop: No such file or 
directory<br>
Aug 30 11:49:41 server gnome-session[2421]: WARNING: could not read /etc/xdg/autostart/vmware-user.desktop<br>
Aug 30 11:49:41 server kernel: [ &nbsp; 57.332718] /dev/vmnet: open called by PID 2494 (vmnet-bridge)<br>
Aug 30 11:49:41 server kernel: [ &nbsp; 57.332729] /dev/vmnet: hub 0 does not exist, allocating memory.<br>
Aug 30 11:49:41 server kernel: [ &nbsp; 57.332744] /dev/vmnet: port on hub 0 successfully opened<br>
Aug 30 11:49:41 server kernel: [ &nbsp; 57.332757] bridge-eth0: up<br>
Aug 30 11:49:41 server kernel: [ &nbsp; 57.332761] bridge-eth0: attached<br>
Aug 30 11:49:41 server vmnet-detect[2498]: NetDetectDaemonInit: No host policy file found. Not initializing filter.<br>
Aug 30 11:49:41 server vmnet-detect[2498]: Unable to initialize the daemon<br>
Aug 30 11:49:41 server pgpool: 2012-08-30 11:49:41 ERROR: pid 2538: 
pool_init_pool_passwd: couldn't open /etc/pgpool2/pool_passwd. reason: 
Permission denied<br>
Aug 30 11:49:41 server pgpool: 2012-08-30 11:49:41 LOG: &nbsp; pid 2538: pgpool-II successfully started. version 3.1.1 (hatsuiboshi)<br>
Aug 30 11:49:41 server kernel: [ &nbsp; 57.482718] init: plymouth-stop pre-start process (2608) terminated with status 1<br>
Aug 30 11:49:43 server rtkit-daemon[1890]: Successfully made thread 2642
 of process 2642 (n/a) owned by '1000' high priority at nice level -11.<br>
Aug 30 11:49:43 server rtkit-daemon[1890]: Supervising 6 threads of 2 processes of 2 users.<br>
Aug 30 11:49:43 server dbus[1132]: [system] Activating service name='org.freedesktop.UDisks' (using servicehelper)<br>
Aug 30 11:49:43 server dbus[1132]: [system] Successfully activated service 'org.freedesktop.UDisks'<br>
Aug 30 11:49:43 server NetworkManager[1309]: &lt;info&gt; Unmanaged 
Device found; state CONNECTED forced. (see 
http://bugs.launchpad.net/bugs/191889)<br>
Aug 30 11:49:45 server named[2262]: error (network unreachable) resolving 'client45.dropbox.com/A/IN': 2001:503:231d::2:30#53<br>
Aug 30 11:49:45 server NetworkManager[1309]: &lt;info&gt; Unmanaged 
Device found; state CONNECTED forced. (see 
http://bugs.launchpad.net/bugs/191889)<br>
Aug 30 11:49:48 &nbsp;NetworkManager[1309]: last message repeated 2 times<br>
Aug 30 11:49:48 server named[2262]: error (network unreachable) resolving './A/IN': 2001:503:c27::2:30#53<br>
Aug 30 11:49:48 server named[2262]: error (network unreachable) resolving './NS/IN': 2001:503:c27::2:30#53<br>
Aug 30 11:49:58 server goa[3051]: goa-daemon version 3.4.0 starting [main.c:112, main()]<br>
Aug 30 11:50:00 server NetworkManager[1309]: &lt;info&gt; Unmanaged 
Device found; state CONNECTED forced. (see 
http://bugs.launchpad.net/bugs/191889)<br>
Aug 30 11:50:46 server dbus[1132]: [system] Activating service name='org.freedesktop.PackageKit' (using servicehelper)<br>
Aug 30 11:50:49 server AptDaemon: INFO: Initializing daemon<br>
Aug 30 11:50:50 server AptDaemon.PackageKit: INFO: Initializing PackageKit compat layer<br>
Aug 30 11:50:50 server dbus[1132]: [system] Successfully activated service 'org.freedesktop.PackageKit'<br>
Aug 30 11:50:50 server AptDaemon.PackageKit: INFO: Initializing PackageKit transaction<br>
Aug 30 11:50:50 server AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/ed99ed1e572f486a87c07627791de460<br>
Aug 30 11:50:50 server AptDaemon.Worker: INFO: Processing transaction 
/org/debian/apt/transaction/ed99ed1e572f486a87c07627791de460<br>
Aug 30 11:55:52 server kernel: imklog 5.8.6, log source = /proc/kmsg started.<br>

```

---

### Post by GreatDanton on 2012-08-30
Well I see some errors, however I am not expert in this waters. Hopefully more experienced user will see this and help you. 

Good luck with your problem!

Regards.

---

### Post by pi1973 on 2012-08-31
Thanks again for your help...
Some of the errors in my previous post were related with a change in the hostname of the machine. I fixed those but today I got another mysterious freeze... 
The syslog also shows some errors related with pgpool but I'd be very surprised if an error in pgpool would cause the machine to completely freeze. Anyway, I'll fix the pgpool problem to make sure syslog is not polluted by any misleading error entries.

Regards

---

### Post by Bashing-om on 2012-09-01
pi1973;

As you have not installed any other apps (i installed the indicator-weather app; my 12.04.1 froze up on my next boot) //and known errors from syslog resolved; how about forcing a file system check on next boot. I have resorted to this shotgun -in- the- dark method a few times to fix  problems I could not isolate.
```
sudo touch forcefsck
```

In the event one knows what he is doing e2fsck method would prove more prolific on errors and what gets fixed.

[INDENT]hth >==BDQ
[/INDENT]

---

### Post by pi1973 on 2012-09-04
Bashing-om;

Thanks for your help.
I already did several file system checks. But the problem recurred... Also checked memory
Now I disconnected all my USB devices and, to this day, zero crashes... 
I connected my USB mouse/keyboard and HDD on another Linux box (similar to the one which is breaking my nerves) and the HW seems to be working perfectly. It may be a problem with my MB  USB controller... But it's too soon for any conclusions.

Thanks again for your help.

---

### Post by Bashing-om on 2012-09-04
Hey no problem, in this free open source movement, we are all in this together!

  I recently also had the problem with files getting corrupted for no discernible reason.

When I moved the drives around the problem went away ...maybe the sata cables bent to much, bad connections. sata controller unhappy... to this time I do not know//Needless to say I am relieved that my system is fully operational !

[INDENT]my best to ya <==BDQ
[/INDENT]

---

### Post by shreepads on 2012-09-05
Try the NVidia proprietary drivers... This assumes there are no hardware problems (I think you mentioned you are using the same hardware as before?)...

Does the PSU provide sufficient power for your setup? Power consumption could have gone up post move to 12.04... What OS was running this hardware before w/o any problems?

---

### Post by Bashing-om on 2012-09-05
+1 yeah, the power supply is a real good point!

[INDENT]BDQ

[/INDENT]

---

### Post by pi1973 on 2012-09-05
In fact after I updated my machine from 10.04 to 12.04 I noticed the fan of my PSU got a bit noisier. But how can one be sure about the condition of the PSU without buying a new one?

I had trouble running the NVIDIA proprietary drivers in UBUNTU 10.04 that's why I've changed to nouveau. It was running ok... If the video HW fails how can I diagnose it? I see no suspicious items in my Xorg log files... 
Well, I suppose I can use the system in 'text' mode (i.e with no GUI), and see whether it keeps crashing.     

BTW: since I got rid of all the USB devices: zero crashes... The USB HW is working fine in my laptop (it runs UBUNTU 12.04)... Weird but true!

Thanks again for your support!

---

### Post by shreepads on 2012-09-06
> **pi1973 said:**
> In fact after I updated my machine from 10.04 to 12.04 I noticed the fan of my PSU got a bit noisier. But how can one be sure about the condition of the PSU without buying a new one?

BTW: since I got rid of all the USB devices: zero crashes... The USB HW is working fine in my laptop (it runs UBUNTU 12.04)... Weird but true!



USB devices consume power both directly and indirectly (extra CPU utilisation) so I think it's safe to say the PSU COULD be the source of the problems (assuming you haven't done any CPU/ GPU/ Memory overclocks)...

Check out one of the online PSU capacity calculators (based on your hardware) and compare against your existing PSU specs...

To be absolutely certain you would need to subject the system to full load (including all USB devices) and use a voltmeter on the PSU outputs... Not recommended unless you're an electronics engineer!

---

