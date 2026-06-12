---
title: "Clamtk Quarantined file"
date: 2015-06-26
forum: New to Ubuntu
---

### Post by dee7 on 2015-06-26
Ran Clamtk : message possible virus . Was in a hurry + tired Didn't engage brain and opted for quarantine Logged off . Next log on : No icons just text . Difficult to do anything. [COLOR=#ff0000]I've quarantined mime.cache[/COLOR]! ClamTK won't run so can't do restore . Found where clamTK has quarantined dossier . History log reads 1 virus potentiel(s) trouvé(s) menace (737 fichiers analysés). /usr/share/mime/mime.cache      PUA.Win.Exploit.CVE_2012_0110  . Computer is effectively unusable.

---

### Post by Frogs Hair on 2015-06-26
This has been reported on Ask Ubuntu and here as well. This a windows exploit and won't execute in Linux although Wine or Play on Linux could be affected if in use.  

 [http://askubuntu.com/questions/611291/pua-win-exploit-cve-2012-0110-found](http://askubuntu.com/questions/611291/pua-win-exploit-cve-2012-0110-found)

[http://ubuntuforums.org/showthread.php?t=2274088](http://ubuntuforums.org/showthread.php?t=2274088)

---

### Post by dee7 on 2015-06-26
Read threads : doesn't seem to be exactly the same problem. Same virus but I'm not sure that the virus is the direct cause of my problem . It looks as if when I quarantined it ClamTK quarantined the whole dossier . Computer almost impossible to use.

---

### Post by cariboo on 2015-06-26
You've probably broken something else, as the malware has no affect when running a distribution. Years back there was a forum member who tried to infect his wine directory with malware, he had no luck.

---

### Post by dee7 on 2015-06-28
Yes, I know that I have broken something else . I've quarantined the directory mime.cache and am guessing that's my real problem. I'm was hoping that I could restore mime.cache (Ok and the virus)  . I know where Clamtk has put it , but Clamtk won't run . Tried copy and paste but I seem to have 'lost' privilges .

---

### Post by cariboo on 2015-06-28
Can't you copy it manually back to it's original location.

---

### Post by dee7 on 2015-06-29
No, tried that.

---

