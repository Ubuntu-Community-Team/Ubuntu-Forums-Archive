---
title: "Where is my RAR and 7zip"
date: 2012-07-11
forum: New to Ubuntu
---

### Post by czgirb on 2012-07-11
As title.
Cos I wish to extract a un-compresed my **RAR** file, which have a 'broken'.

By default it was extracted by **Archiv Manager** ... but said cos its "broke", so unable to un-compressed it.
I wish to change the default, by **Properties** => **Open With** ... but I found neither **RAR** and **7zip** there. I tried to go to **Ubuntu Software Center**, but it said both **RAR** and **7zip** are installed.
I tried to run **Terminal** and type **rar** ... but the application do not show-up. All show-up is command line only. Type **RAR** ... command not found.

Please help me ...

---

### Post by SlugSlug on 2012-07-11
archive manager handles them all, if rar and 7zip are installed they are controlled via archive manager.

It seems like your rar may be corrupt?

type in terminal

file /path/to/file

---

### Post by mikewhatever on 2012-07-11
Both rar and 7zip are command line programs in Ubuntu. The GUI for both is provided by the Archive Manager.
You probably need to deal the the 'broken' problem first. If the archive have several parts, make sure you have them all in the same folder. If not, you might need to re-download an archive, and sometimes, there is no way to repair it.

---

### Post by SeijiSensei on 2012-07-11
You need to use unrar to extract from RAR files.  There are two versions of unrar because the algorithm is encumbered by software patents.  The free version can be installed with "sudo apt-get install unrar-free".

---

### Post by czgirb on 2012-07-11
> **mikewhatever said:**
> 
... you probably need to deal the the 'broken' problem first. If the archive have several parts, make sure you have them all in the same folder. If not, you might need to re-download an archive, and sometimes, there is no way to repair it.

How can I deal with the 'broken' problem?
I just **right-click** and **extracted here**.

In windows, with **WinRAR** I able to **keep the broken file** ... and **have all the complete parts** only ... **the corrupt one is not**.
Am I able for having this feature in Ubuntu?

---

### Post by mikewhatever on 2012-07-11
> **czgirb said:**
> How can I deal with the 'broken' problem?
I just **right-click** and **extracted here**.

In windows, with **WinRAR** I able to **keep the broken file** ... and **have all the complete parts** only ... **the corrupt one is not**.
Am I able for having this feature in Ubuntu?

Well, for better or worse, Ubuntu is not Windows, and unrar is not WinRar. You may, or may not be able to solve it. How? Learn to program, study the code, looks for the problem, find it, solve it.

---

### Post by Vaphell on 2012-07-11
try running winrar in wine

---

