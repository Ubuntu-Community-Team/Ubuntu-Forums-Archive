---
title: "Performing a sudo command each boot"
date: 2012-01-30
forum: New to Ubuntu
---

### Post by Flynsarmy on 2012-01-30
I've got a laptop with NVidia Optimus which doesn't work too well in Linux for the moment so I installed the acpi_call kernel module and created a cardoff.sh file to shut the discrete GPU down containing:
```
modprobe acpi_call
echo "\_SB.PCI0.PEG0.PEGP._DSM {0xF8,0xD8,0x86,0xA4,0xDA,0x0B,0x1B,0x47,0xA7,0x2B,0x60,0x42,0xA6,0xB5,0xBE,0xE0} 0x100 0x1A {0x1,0x0,0x0,0x3}" > /proc/acpi/call
echo "\_SB.PCI0.PEG0.PEGP._PS3" > /proc/acpi/call
```
which I execute manually each boot with a ```
sudo ./cardoff.sh
```

Is there a way I can perform this command automatically each boot? sudo obviously asks for a password so up until now I haven't been sure how to do it.

---

### Post by anewguy on 2012-01-30
If you just add this to startup items (system startup, not your login) what happens?  I thought it would be run as root then.  

Dave ;)

---

### Post by Flynsarmy on 2012-01-30
> **anewguy said:**
> If you just add this to startup items (system startup, not your login)...

By system startup do you mean dropping into /etc/init.d/ as mentioned [here]("http://embraceubuntu.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/")? I'll give it a shot

---

### Post by Flynsarmy on 2012-01-30
Worked fine. For the record I dropped it into /etc/init.d, added 
```
#! /bin/sh
```
to the top and ran a 
```
sudo update-rc.d /etc/init.d/cardoff defaults
```
I also added an
```
echo hmm >> /var/log/test.log
```
and rebooted and noticed 'hmm' appears twice each boot. Any particular reason for that?

The first time running the update-rc.d I didn't use sudo - perhaps I added it twice or something?

---

### Post by SeijiSensei on 2012-01-30
Just for future reference, you can put commands that need to run with root privileges at boot into the file /etc/rc.local.  rc.local is run after all other init.d scripts have completed.

---

### Post by anewguy on 2012-01-30
Glad it worked for you!

Dave ;)

---

