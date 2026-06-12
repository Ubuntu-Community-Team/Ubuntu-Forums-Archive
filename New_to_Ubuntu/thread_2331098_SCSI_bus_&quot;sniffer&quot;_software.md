---
title: "SCSI bus &quot;sniffer&quot; software?"
date: 2016-07-18
forum: New to Ubuntu
---

### Post by mossyrock on 2016-07-18
Hello,

I'm new to Ubuntu but have been a hardware and Windows sysadmin guy for 20 years. 

I'm also a retro-hardware enthusiast and have acquired an old Qualstar 1260S reel-to-reel tape drive with a SCSI interface.  I've got it working well via an Adaptec 2930 Ultra SCSI card on my Ubuntu (Desktop) 16.04 system.  Using the "mt" command I am able to write to the tape and read it back without issue.

So, I'm building a custom cabinet for this drive and would like to add some bells and whistles to show it off.  I'd like to add an Arduino-driven alphanumeric display (probably 2 lines of 40 chars) that will show the current tape drive status, such as Ready, Online, Reading, Writing, Rewinding, Unloading, etc., the way some old mainframe IBM tape drives did like the IBM 3480.

To do this I need to find a way in Linux to "sniff" the SCSI bus or otherwise get the current drive operation and pipe it to the Arduino.  

I've tried lsscsi and scsiinfo but it doesn't return enough information to work with.

Does anyone know of any commands, programs or methodology that will return this information?  I've come across some software called "SCSI Bus Analyzer Solution" on sourceforge but there is no documentation and I don't trust stuff outside the repository anyway.

Thanks.

---

### Post by mossyrock on 2016-07-18
Hmmm... nearly 100 views on my question and no responses.  I guess that means it's not very do-able or practical.  Thanks anyway!

---

