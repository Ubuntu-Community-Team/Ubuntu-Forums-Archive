---
title: "ACPI Error: Please send DMI"
date: 2022-12-07
forum: New to Ubuntu
---

### Post by oblithian on 2022-12-07
What is DMI (just to confirm I have the right thing), and how do I send it if 'dmidecode -t system' tells me I do not have permission? Also is there a particular format or protocols to send it in (text file, paste in e-mail, subject line, etc.?).

This is part of the following error log:

11:35:15 kernel: iommu ivhd0: AMD-Vi: Event logged [INVALID_DEVICE_REQUEST device=12:00.1 pasid=0x00000 address=0xfffffffdf8000000 flags=0x0a00]
11:34:16 systemd: Failed to start Firmware update daemon.
11:31:33 pulseaudio: GetManagedObjects() failed: org.freedesktop.DBus.Error.TimedOut: Failed to activate service 'org.bluez': timed out (service_start_timeout=25000ms)
11:31:13 kernel: iommu ivhd0: AMD-Vi: Event logged [INVALID_DEVICE_REQUEST device=30:00.6 pasid=0x00000 address=0xfffffffdf8000000 flags=0x0a00]
11:31:13 gdm-session-wor: gkr-pam: unable to locate daemon control file
11:31:07 kernel: iommu ivhd0: AMD-Vi: Event logged [INVALID_DEVICE_REQUEST device=30:00.6 pasid=0x00000 address=0xfffffffdf8000000 flags=0x0a00]
11:31:07 kernel: ACPI Error: Please send DMI info to [EMAIL="linux-acpi@vger.kernel.org"]linux-acpi@vger.kernel.org[/EMAIL]
If system does not work as expected, please boot with acpi=copy_dsdt (20210730/tbutils-94)
11:31:03 kernel: iommu ivhd0: AMD-Vi: Event logged [INVALID_DEVICE_REQUEST device=30:00.6 pasid=0x00000 address=0xfffffffdf8000000 flags=0x0a00]
11:31:02 kernel: ACPI Error: (PRT[0]) Need package of length 4, found length 1 (20210730/rscreate-248)

---

### Post by grahammechanical on 2022-12-07
> how do I send it if 'dmidecode -t system' tells me I do not have permission?

You are to pre-fix the dmidecode -t system command with "sudo" and then enter your password when requested. Then you will see something like this:

> graham@graham-Hybris:~$ sudo dmidecode -t system
[sudo] password for graham: 
# dmidecode 3.2
Getting SMBIOS data from sysfs.
SMBIOS 3.2.0 present.

Handle 0x0001, DMI type 1, 27 bytes
System Information
    Manufacturer: Entroware
    Product Name: Hybris
    Version: EL05R4
    Serial Number: Not Applicable
    UUID: f0960000-0000-1000-8000-80fa5b9db05c
    Wake-up Type: Power Switch
    SKU Number: EL05R4
    Family: Hybris

Handle 0x0016, DMI type 12, 5 bytes
System Configuration Options
    Option 1: <BAD INDEX>

Handle 0x001A, DMI type 15, 29 bytes
System Event Log
    Area Length: 0 bytes
    Header Start Offset: 0x0000
    Header Length: 8192 bytes
    Data Start Offset: 0x2000
    Access Method: General-purpose non-volatile data functions
    Access Address: 0x0000
    Status: Valid, Not Full
    Change Token: 0x12345678
    Header Format: OEM-specific
    Supported Log Type Descriptors: 3
    Descriptor 1: POST memory resize
    Data Format 1: None
    Descriptor 2: POST error
    Data Format 2: POST results bitmap
    Descriptor 3: Log area reset/cleared
    Data Format 3: None

Handle 0x0027, DMI type 32, 11 bytes
System Boot Information
    Status: No errors detected

That information does not enlighten me.

Regards

---

### Post by oblithian on 2022-12-07
Ah, thank you that was missing from the one resource I managed to find.

---

### Post by oblithian on 2023-01-13
The e-mail bounced back, I assume I typed it wrong or the mailbox is no-longer active? Either way the initial problem was resolved, though the second question remains unanswered.

---

