---
title: "how can i know if my HD is SATA or IDE?"
date: 2008-12-02
forum: New to Ubuntu
---

### Post by jsf_pp on 2008-12-02
how can i know if my HD is SATA or IDE?

i dont want to open my lappie.
thanks.

---

### Post by taurus on 2008-12-02
Does the BIOS tell you which type you have?

---

### Post by Paqman on 2008-12-02
If it has big fat ribbon cables (bigger than about 1cm/0.5in) then it's IDE.

IDE:
[IMG]http://upload.wikimedia.org/wikipedia/commons/thumb/c/c4/Ata_20070127_002.jpg/150px-Ata_20070127_002.jpg[/IMG]

SATA:
[IMG]http://upload.wikimedia.org/wikipedia/commons/thumb/e/ef/SATA_Data_Cable.jpg/150px-SATA_Data_Cable.jpg[/IMG]

EDIT: Ah, sorry, laptop! Do you know what model it is?

---

### Post by Kinetic777 on 2008-12-02
type this command 

sudo fdisk -1

if it says sda, it is SATA
If it says hda at the end, it is IDE

---

### Post by jsf_pp on 2008-12-02
i'll see, rebooting now.

---

### Post by Paqman on 2008-12-02
> **Kinetic777 said:**
> type this command 

sudo fdisk -1

if it says sda, it is SATA
If it says hda at the end, it is IDE

I thought everything showed up as sda these days?

---

### Post by Kinetic777 on 2008-12-02
> **Paqman said:**
> I thought everything showed up as sda these days?

I'm not sure about all systems, but my drives showed up as hda

---

### Post by sydbat on 2008-12-02
> **Paqman said:**
> I thought everything showed up as sda these days?Yup. I have both SATA and IDE and they both show up as sd...one as sda the other sdb.

---

### Post by jsf_pp on 2008-12-02
@taurus
Device: HARD DISK
Vendor: ST980811AS
Size: 80.0gb
LBA Mode: Supported
Block Mode: 16
PIO Mode: 4
Async DMA: MultiWord DMA-2
Ultra DMA: Ultra DMA-6
S.M.A.R.T.: Supported

_______

thats my bois info...
does its said there if its SATA or IDE?

---

### Post by jsf_pp on 2008-12-02
> **Kinetic777 said:**
> type this command 

sudo fdisk -1

if it says sda, it is SATA
If it says hda at the end, it is IDE

so i did:

```
julio@julio-laptop:~$ sudo fdisk -1
[sudo] password for julio:
fdisk: invalid option -- 1

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

```

so, im a SATAN now? i mean SATA... haha

---

### Post by sydbat on 2008-12-02
SATA. [http://www.seagate.com/ww/v/index.jsp?vgnextoid=7227c9d3f5d83110VgnVCM100000f5ee0a0aRCRD&locale=en-US](http://www.seagate.com/ww/v/index.jsp?vgnextoid=7227c9d3f5d83110VgnVCM100000f5ee0a0aRCRD&locale=en-US)

And the code was mistyped...should have been l (small L) not 1 (number one).

---

### Post by taurus on 2008-12-02
Or another link from newegg.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16822148260&Tpk=ST980811AS](http://www.newegg.com/Product/Product.aspx?Item=N82E16822148260&Tpk=ST980811AS)

---

### Post by porchrat on 2008-12-02
You can't tell using fdisk anymore.  For years now Linux has used the SCSI drivers regardless of whether the drive is IDE, SATA or SCSI.  They will all show up as "sd" followed by a letter.

I'm afraid you may need to open the laptop up and check the connector.  Although it should tell you online what the laptop was sold with.  Just look up the manual for the lappie.

By the way I think he meant use "sudo fdisk -l" not "sudo fdisk -1"

EDIT: ah I see others have already given you these pieces of information

---

### Post by jsf_pp on 2008-12-02
> **Paqman said:**
> If it has big fat ribbon cables (bigger than about 1cm/0.5in) then it's IDE.

IDE:
[IMG]http://upload.wikimedia.org/wikipedia/commons/thumb/c/c4/Ata_20070127_002.jpg/150px-Ata_20070127_002.jpg[/IMG]

SATA:
[IMG]http://upload.wikimedia.org/wikipedia/commons/thumb/e/ef/SATA_Data_Cable.jpg/150px-SATA_Data_Cable.jpg[/IMG]

EDIT: Ah, sorry, laptop! Do you know what model it is?

i know i should, but nope.
all i know is what i can read from here:

Packard Bell
EasyNote

thats it.

---

### Post by stepol on 2008-12-02
Google ST90811AS ==> 80Gb SATA 5400RPM

---

### Post by sydbat on 2008-12-02
> **stepol said:**
> Google ST90811AS ==> 80Gb SATA 5400RPMThat is the link I posted...from Seagate. It says the drive is SATA.

---

### Post by Kinetic777 on 2008-12-02
Nevermind >.<

---

### Post by Paqman on 2008-12-02
> **jsf_pp said:**
> @taurus
Device: HARD DISK
**Vendor: ST980811AS**
Size: 80.0gb
LBA Mode: Supported
Block Mode: 16
PIO Mode: 4
Async DMA: MultiWord DMA-2
Ultra DMA: Ultra DMA-6
S.M.A.R.T.: Supported

_______

thats my bois info...
does its said there if its SATA or IDE?

That part number seems to be an [80GB Seagate SATA disk]("http://www.seagate.com/ww/v/index.jsp?vgnextoid=7227c9d3f5d83110VgnVCM100000f5ee0a0aRCRD&locale=en-US").

---

