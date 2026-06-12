---
title: "Radeon HD6450 graphics card and drivers - Put where/how?"
date: 2013-05-26
forum: New to Ubuntu
---

### Post by RickFAA on 2013-05-26
System: 2009 Dell Inspiron 537s(slim), Core Duo E8400(3.3GHz OC), 4GB, WD 320GB HD, Radeon HD6450 graphic, Dual boot:Vista/Ubuntu12.04LTS

Noob Question#1:  Got the new graphic card 2 weeks a ago.  Has a driver CD, but said: Only for Windows! 
                          I know I could put the CD in Windows (Vista). (Not yet though.)

                          But in boot time, Ubuntu, my display stopped dead, have to start boot with Linux 'Recover Mode'......
 
                          Do I have to get a Radeon driver in a Ubuntu version?  In [www.radeon.com](www.radeon.com) or someplace else? 
                          (Vista starts fine any time.)

Thanks,
Rick

                          












p

---

### Post by 3rdalbum on 2013-05-27
The Additional Drivers program in Ubuntu will download and install the official AMD driver for you.

---

### Post by mastablasta on 2013-05-27
> **RickFAA said:**
> But in boot time, Ubuntu, my display stopped dead, have to start boot with Linux 'Recover Mode'......


first things first. to boot use one of the boot options. try nomodeset first and see if that boots you to desktop. [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

then you can download linux drivers from AMD website and compile them manually. this way you can insall beta drivers. porblem is this has to be repeated on each kernel update. and they happen about once a week maybe once every two weeks. [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

my opinion though is that you do not need beta drivers. stable drivers can be installed in a more easy way.in softweare center with additional drivers utility. these would then get automatic updates along with system updates. stable version. [http://www.psychocats.net/ubuntu/drivers](http://www.psychocats.net/ubuntu/drivers)

---

### Post by Mark Phelps on 2013-05-27
Ubuntu automatically installs the default Radeon drivers for you.  Unless you need GPU temp control or advanced features offered by Catalyst Control Center, there is no reason to struggle with installing the restricted AMD drivers.

---

