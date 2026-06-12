---
title: "Unable to run Ubuntu from disk"
date: 2012-02-21
forum: New to Ubuntu
---

### Post by RedNinja on 2012-02-21
I'm running ubuntu from disk in an attempt to get time files off a dell  laptop I'm having issues with. However, when I start up the os all I see  is a desktop and clicking, right clicking, or pressing any number of  buttons does nothing. After closing the lid and coming back to it later,  4 firmware warn messages come up ([Firmware Warn]: MTRR: CPU 0: SYSCFG[MtrrFixDramModEn] not cleared by BIOS, clearing this bit), and so does "ata1: soft reset failed  (device not ready)" I'm hoping this is a symptom of the problem with the  computer I've been having all along, and is therefore solvable, but I'm  worried that if I can't even get ubuntu to run, I'm basically up a  creek and it's over my head with swill. Any help will be met with  nauseating amounts of appreciation.

---

### Post by roelforg on 2012-02-21
> **RedNinja said:**
> I'm running ubuntu from disk in an attempt to get time files off a dell  laptop I'm having issues with. However, when I start up the os all I see  is a desktop and clicking, right clicking, or pressing any number of  buttons does nothing. After closing the lid and coming back to it later,  4 firmware warn messages come up ([Firmware Warn]: MTRR: CPU 0: SYSCFG[MtrrFixDramModEn] not cleared by BIOS, clearing this bit), and so does "ata1: soft reset failed  (device not ready)" I'm hoping this is a symptom of the problem with the  computer I've been having all along, and is therefore solvable, but I'm  worried that if I can't even get ubuntu to run, I'm basically up a  creek and it's over my head with swill. Any help will be met with  nauseating amounts of appreciation.
The ata message shouldn't cause this, as you say you're running from livecd.
The SYSCFG message leads me to believe there might be a ram problem, i'd try running a memcheck, google it for instructions.

---

