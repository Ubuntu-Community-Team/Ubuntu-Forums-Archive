---
title: "Installed windows, Lost NTFS read/Write permission in ubuntu"
date: 2018-09-22
forum: New to Ubuntu
---

### Post by weirdygeekpsych on 2018-09-22
Alright, 

Now this is the problem.

Ubuntu and Windows shares the same hard disk(Half of size for each) - A separate Hard disk  - which contain only system files

Rest of the files are in another drive which is commonly shared by Ubuntu & Windows which is in NTFS format

After installing windows I lost the read/write permission in ubuntu 18.04 LTS.
  
***Note: I don't rely on tools for solving the problem.***

Please suggest some procedures as list, it will be helpful

---

### Post by westie457 on 2018-09-22
Which version of Windows?
Is Windows fully shutdown? ie Not in hibernation
Have you run a Windows 'chkdsk' on the NTFS partition?

---

### Post by weirdygeekpsych on 2018-09-22
I made a shutdown everytime. 

Nope havent run chkdsk

Windows 10

---

### Post by westie457 on 2018-09-22
Check this procedure while Windows is running,[COLOR=#000000] Control Panel > Power Options > Change what the power button does > Change settings currently unavailable > un-tick the Fast Start up box > also empty the Allow Hibernation box > Apply. Close the Control Panel.[/COLOR]

---

### Post by weirdygeekpsych on 2018-09-22
Ran chkdsk, problem solved thanks man @westie457

---

