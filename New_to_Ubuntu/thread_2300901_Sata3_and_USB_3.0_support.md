---
title: "Sata3 and USB 3.0 support"
date: 2015-10-29
forum: New to Ubuntu
---

### Post by lukasz15 on 2015-10-29
Dear All!

I use Ubuntu from over a month and happy because of that but have two issues can not resolve.
My hardware is Pentium N3700 on this motherboard:
[http://www.asrock.com/mb/Intel/N3700-ITX/](http://www.asrock.com/mb/Intel/N3700-ITX/)

I've installed now 15.10 and still cannot reach the full transfer speed between my disc. It is about max. 30 MB/s, on windows the same hardware can reach about 160.
Also cannot use any USB 3.0 port on this MB.

Are there any known issue with supporting this hardware on ubuntu? Can I find some better than standard drivers?

Thanks a lot!
Lukasz

---

### Post by Shreyesh_Chaudhary on 2015-10-29
Hello Lukas

Firstly perform update and upgrade
Secondly install 'apt-get install linux-firmware-nonfree'
Thirdly Enable partner repository [http://askubuntu.com/questions/14629/how-do-i-enable-the-partner-repository](http://askubuntu.com/questions/14629/how-do-i-enable-the-partner-repository)

test the transfer speed if you dont get desired result

DO AT YOUR OWN RISK

update the BIOS of your motherboard

Regards
sacviper

---

### Post by sandyd on 2015-10-29
Can you post the output of
```

sudo hdparm -I /dev/sda
sudo hdparm -T /dev/sda

```

Sample output:
```

~$ sudo hdparm -I /dev/sda

/dev/sda:

ATA device, with non-removable media
        Model Number:       INTEL SSDSC2BW120A4                     
        Serial Number:      CVDA413207YZ1207GN  
        Firmware Revision:  DC32    
        Transport:          Serial, ATA8-AST, SATA 1.0a, SATA II Extensions, SATA Rev 2.5, SATA Rev 2.6, SATA Rev 3.0
Standards:
        Used: unknown (minor revision code 0xffff) 
        Supported: 9 8 7 6 5 
        Likely used: 9
Configuration:
        Logical         max     current
        cylinders       16383   16383
        heads           16      16
        sectors/track   63      63
        --
        CHS current addressable sectors:   16514064
        LBA    user addressable sectors:  234441648
        LBA48  user addressable sectors:  234441648
        Logical  Sector size:                   512 bytes
        Physical Sector size:                   512 bytes
        Logical Sector-0 offset:                  0 bytes
        device size with M = 1024*1024:      114473 MBytes
        device size with M = 1000*1000:      120034 MBytes (120 GB)
        cache/buffer size  = unknown
        Nominal Media Rotation Rate: Solid State Device
Capabilities:
        LBA, IORDY(can be disabled)
        Queue depth: 32
        Standby timer values: spec'd by Standard, no device specific minimum
        R/W multiple sector transfer: Max = 16  Current = 16
        Advanced power management level: 128
        DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
             Cycle time: min=120ns recommended=120ns
        PIO: pio0 pio1 pio2 pio3 pio4 
             Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
        Enabled Supported:
           *    SMART feature set
           *    Security Mode feature set
           *    Power Management feature set
           *    Write cache
           *    Look-ahead
           *    Host Protected Area feature set
           *    WRITE_BUFFER command
           *    READ_BUFFER command
           *    NOP cmd
           *    DOWNLOAD_MICROCODE
           *    Advanced Power Management feature set
                Power-Up In Standby feature set
           *    48-bit Address feature set
           *    Mandatory FLUSH_CACHE
           *    FLUSH_CACHE_EXT
           *    SMART error logging
           *    SMART self-test
           *    General Purpose Logging feature set
           *    WRITE_{DMA|MULTIPLE}_FUA_EXT
           *    64-bit World wide name
           *    IDLE_IMMEDIATE with UNLOAD
           *    WRITE_UNCORRECTABLE_EXT command
           *    {READ,WRITE}_DMA_EXT_GPL commands
           *    Segmented DOWNLOAD_MICROCODE
           *    Gen1 signaling speed (1.5Gb/s)
           *    Gen2 signaling speed (3.0Gb/s)
           *    Gen3 signaling speed (6.0Gb/s)
           *    Native Command Queueing (NCQ)
           *    Host-initiated interface power management
           *    Phy event counters
                DMA Setup Auto-Activate optimization
           *    Device-initiated interface power management
           *    Software settings preservation
                Device Sleep (DEVSLP)
           *    SMART Command Transport (SCT) feature set
           *    SCT Write Same (AC2)
           *    SCT Data Tables (AC5)
           *    reserved 69[4]
           *    Data Set Management TRIM supported (limit 1 block)
           *    Deterministic read data after TRIM
Security: 
        Master password revision code = 65534
                supported
                enabled
        not     locked
                frozen
        not     expired: security count
                supported: enhanced erase
        Security level high
        4min for SECURITY ERASE UNIT. 2min for ENHANCED SECURITY ERASE UNIT. 
Logical Unit WWN Device Identifier: 55cd2e404b9caad4
        NAA             : 5
        IEEE OUI        : 5cd2e4
        Unique ID       : 04b9caad4
Checksum: correct
Device Sleep:
        DEVSLP Exit Timeout (DETO): 20 ms (drive)
        Minimum DEVSLP Assertion Time (MDAT): 10 ms (drive)
~$ sudo hdparm -T /dev/sda

/dev/sda:
 Timing cached reads:   10404 MB in  2.00 seconds = 5204.12 MB/sec
```

---

### Post by lukasz15 on 2015-12-03
Hi!

Sorry for the late answer, I had some issue with my hardware. In the meantime I installed ubuntu 15.10 server and there the issue did not occur, transfer was fast.
But I installed lubuntu 15.10 again and again have the issue.

I've preformed all steps suggested by [COLOR=#000000]Shreyesh_Chaudhary but it didn't help.

Below I posted output from hdparm for both my HD:

Sda:
[/COLOR]```


/dev/sda:


ATA device, with non-removable media
    Model Number:       Crucial_CT128MX100SSD1                  
    Serial Number:      14280C969BCF
    Firmware Revision:  MU01    
    Transport:          Serial, ATA8-AST, SATA 1.0a, SATA II Extensions, SATA Rev 2.5, SATA Rev 2.6, SATA Rev 3.0
Standards:
    Used: unknown (minor revision code 0x0028) 
    Supported: 9 8 7 6 5 
    Likely used: 9
Configuration:
    Logical        max    current
    cylinders    16383    16383
    heads        16    16
    sectors/track    63    63
    --
    CHS current addressable sectors:   16514064
    LBA    user addressable sectors:  250069680
    LBA48  user addressable sectors:  250069680
    Logical  Sector size:                   512 bytes
    Physical Sector size:                  4096 bytes
    Logical Sector-0 offset:                  0 bytes
    device size with M = 1024*1024:      122104 MBytes
    device size with M = 1000*1000:      128035 MBytes (128 GB)
    cache/buffer size  = unknown
    Form Factor: 2.5 inch
    Nominal Media Rotation Rate: Solid State Device
Capabilities:
    LBA, IORDY(can be disabled)
    Queue depth: 32
    Standby timer values: spec'd by Standard, with device specific minimum
    R/W multiple sector transfer: Max = 16    Current = 16
    Advanced power management level: 254
    DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
         Cycle time: min=120ns recommended=120ns
    PIO: pio0 pio1 pio2 pio3 pio4 
         Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
    Enabled    Supported:
       *    SMART feature set
            Security Mode feature set
       *    Power Management feature set
       *    Write cache
       *    Look-ahead
       *    Host Protected Area feature set
       *    WRITE_BUFFER command
       *    READ_BUFFER command
       *    NOP cmd
       *    DOWNLOAD_MICROCODE
       *    Advanced Power Management feature set
            SET_MAX security extension
       *    48-bit Address feature set
       *    Device Configuration Overlay feature set
       *    Mandatory FLUSH_CACHE
       *    FLUSH_CACHE_EXT
       *    SMART error logging
       *    SMART self-test
       *    General Purpose Logging feature set
       *    WRITE_{DMA|MULTIPLE}_FUA_EXT
       *    64-bit World wide name
       *    IDLE_IMMEDIATE with UNLOAD
            Write-Read-Verify feature set
       *    WRITE_UNCORRECTABLE_EXT command
       *    {READ,WRITE}_DMA_EXT_GPL commands
       *    Segmented DOWNLOAD_MICROCODE
       *    Gen1 signaling speed (1.5Gb/s)
       *    Gen2 signaling speed (3.0Gb/s)
       *    Gen3 signaling speed (6.0Gb/s)
       *    Native Command Queueing (NCQ)
       *    Phy event counters
       *    NCQ priority information
       *    READ_LOG_DMA_EXT equivalent to READ_LOG_EXT
       *    DMA Setup Auto-Activate optimization
            Device-initiated interface power management
            Asynchronous notification (eg. media change)
       *    Software settings preservation
            Device Sleep (DEVSLP)
       *    SMART Command Transport (SCT) feature set
       *    SCT Write Same (AC2)
       *    SCT Features Control (AC4)
       *    SCT Data Tables (AC5)
       *    reserved 69[4]
       *    reserved 69[7]
       *    Data Set Management TRIM supported (limit 8 blocks)
       *    Deterministic read ZEROs after TRIM
Security: 
    Master password revision code = 65534
        supported
    not    enabled
    not    locked
        frozen
    not    expired: security count
        supported: enhanced erase
    2min for SECURITY ERASE UNIT. 2min for ENHANCED SECURITY ERASE UNIT. 
Logical Unit WWN Device Identifier: 500a07510c969bcf
    NAA        : 5
    IEEE OUI    : 00a075
    Unique ID    : 10c969bcf
Checksum: correct
Device Sleep:
    DEVSLP Exit Timeout (DETO): 50 ms (drive)
    Minimum DEVSLP Assertion Time (MDAT): 10 ms (drive)



```[COLOR=#000000]
[/COLOR]
```


/dev/sda:
 Timing cached reads:   2508 MB in  2.00 seconds = 1253.61 MB/sec



```[COLOR=#000000]



Sdb:

[/COLOR]```


/dev/sdb:


ATA device, with non-removable media
    Model Number:       ST3000DM001-1ER166                      
    Serial Number:      Z500DGVH
    Firmware Revision:  CC25    
    Transport:          Serial, SATA 1.0a, SATA II Extensions, SATA Rev 2.5, SATA Rev 2.6, SATA Rev 3.0
Standards:
    Used: unknown (minor revision code 0x001f) 
    Supported: 9 8 7 6 5 
    Likely used: 9
Configuration:
    Logical        max    current
    cylinders    16383    16383
    heads        16    16
    sectors/track    63    63
    --
    CHS current addressable sectors:   16514064
    LBA    user addressable sectors:  268435455
    LBA48  user addressable sectors: 5860533168
    Logical  Sector size:                   512 bytes
    Physical Sector size:                  4096 bytes
    Logical Sector-0 offset:                  0 bytes
    device size with M = 1024*1024:     2861588 MBytes
    device size with M = 1000*1000:     3000592 MBytes (3000 GB)
    cache/buffer size  = unknown
    Form Factor: 3.5 inch
    Nominal Media Rotation Rate: 7200
Capabilities:
    LBA, IORDY(can be disabled)
    Queue depth: 32
    Standby timer values: spec'd by Standard, no device specific minimum
    R/W multiple sector transfer: Max = 16    Current = 16
    Advanced power management level: 254
    Recommended acoustic management value: 208, current value: 208
    DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
         Cycle time: min=120ns recommended=120ns
    PIO: pio0 pio1 pio2 pio3 pio4 
         Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
    Enabled    Supported:
       *    SMART feature set
            Security Mode feature set
       *    Power Management feature set
       *    Write cache
       *    Look-ahead
       *    Host Protected Area feature set
       *    WRITE_BUFFER command
       *    READ_BUFFER command
       *    DOWNLOAD_MICROCODE
       *    Advanced Power Management feature set
            Power-Up In Standby feature set
       *    SET_FEATURES required to spinup after power up
            SET_MAX security extension
       *    48-bit Address feature set
       *    Device Configuration Overlay feature set
       *    Mandatory FLUSH_CACHE
       *    FLUSH_CACHE_EXT
       *    SMART error logging
       *    SMART self-test
       *    General Purpose Logging feature set
       *    WRITE_{DMA|MULTIPLE}_FUA_EXT
       *    64-bit World wide name
            Write-Read-Verify feature set
       *    WRITE_UNCORRECTABLE_EXT command
       *    {READ,WRITE}_DMA_EXT_GPL commands
       *    Segmented DOWNLOAD_MICROCODE
            unknown 119[6]
       *    Gen1 signaling speed (1.5Gb/s)
       *    Gen2 signaling speed (3.0Gb/s)
       *    Gen3 signaling speed (6.0Gb/s)
       *    Native Command Queueing (NCQ)
       *    Phy event counters
       *    READ_LOG_DMA_EXT equivalent to READ_LOG_EXT
       *    DMA Setup Auto-Activate optimization
            Device-initiated interface power management
       *    Software settings preservation
            unknown 78[7]
       *    SMART Command Transport (SCT) feature set
       *    SCT Write Same (AC2)
            unknown 206[7]
            unknown 206[12] (vendor specific)
Security: 
    Master password revision code = 65534
        supported
    not    enabled
    not    locked
        frozen
    not    expired: security count
        supported: enhanced erase
    314min for SECURITY ERASE UNIT. 314min for ENHANCED SECURITY ERASE UNIT. 
Logical Unit WWN Device Identifier: 5000c500794901f3
    NAA        : 5
    IEEE OUI    : 000c50
    Unique ID    : 0794901f3
Checksum: correct



```[COLOR=#000000]


[/COLOR]```


/dev/sdb:
 Timing cached reads:   2460 MB in  2.00 seconds = 1230.33 MB/sec



```[COLOR=#000000]



Thanks in advance![/COLOR]

---

