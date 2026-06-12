---
title: "lost+found folder"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by adhuvi on 2008-05-15
hello, 

i have kubuntu installed and i have my data in different partitions that i mount on /home, for example. But whenever i go into this folder, there's a 'lost+found' locked folder that is empty. Can someone please tell me what is it for and if it would be a bad idea to erase it.

thanks!

---

### Post by PinkFloyd102489 on 2008-05-15
It's recovered files that fsck gathers.

---

### Post by Oldsoldier2003 on 2008-05-15
> **adhuvi said:**
> hello, 

i have kubuntu installed and i have my data in different partitions that i mount on /home, for example. But whenever i go into this folder, there's a 'lost+found' locked folder that is empty. Can someone please tell me what is it for and if it would be a bad idea to erase it.

thanks!

lost+found is a system folder. If you crash,Fsck will go through the system and try to recover any corrupt files that it finds. The files are placed in Lost+Found.

---

### Post by ChrisR1982 on 2008-12-30
My OpenOffice Word Processor is in the Lost and Found folder... how do I get it back to where it should be?

---

### Post by scorp123 on 2008-12-30
> **ChrisR1982 said:**
> My OpenOffice Word Processor is in the Lost and Found folder...  Hard to imagine. Can you please post the output of "ls -al" inside that folder? Or a screenshot taken from the filemanager showing the contents of that folder?

---

