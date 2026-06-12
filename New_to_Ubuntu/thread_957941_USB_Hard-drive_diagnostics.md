---
title: "USB Hard-drive diagnostics"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by bpowell2005 on 2008-10-24
Hello all!

I have a Western Digital Passport external hard drive (a laptop drive in a fancy box) that connects to the computer via USB. It's formatted NTFS, but it's having all sorts of problems...data goes missing, computer says there is only 1 file, but 60 gig is consumed, etc.

I ran an extended checkdisk in Windows, and it completed (looking for bad sectors)...I'm not sure what the result was (I'm talking third person here, I'm not actually the person with the drive, helping somebody else).

My question is: I found a program from WD that will run diagnostics on the drive (and presumably read the SMART data) however, are there any programs like that that can run under LINUX? Remember, this is a USB connected drive, not connected to the IDE.

Thanks!

---

### Post by nhasian on 2008-10-25
how about smartmontools?

[http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

---

### Post by bpowell2005 on 2008-10-25
> **nhasian said:**
> how about smartmontools?

[http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

Hi Nhasian, thanks for the suggestion!

Unfortunately, Smartmontools does not seem to work too well with USB drives...this is the dilemma. Smartmontools pulls information from the laptop drive inside the laptop (on the IDE bus) but reports errors when trying to poll the WD USB drive.

(from the Smartmontools web site):

As for USB and FireWire (IEEE 1394) disks and tape drives, the news is not good. They appear to the operating system as SCSI devices but their implementations do not usually support those SCSI commands needed by smartmontools. A consortium associated with IEEE 1394 certified some external enclosures (containing a ATA disk and a protocol bridge) as being compliant to the relevant standards. Even still, that compliance means that they tend to only support the bare minimum of commands needed for device operation (i.e. SMART support is an unsupported extra). Hopefully external USB and Firewire devices will support SAT in the future, see below. Some USB device based on cypress chips support a proprietary protocol (ATACB) that allow to send raw ATA commands (i.e. SMART support).

---

