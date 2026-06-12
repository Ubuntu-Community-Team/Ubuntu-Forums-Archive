---
title: "[SOLVED] gedit ~ files"
date: 2008-10-09
forum: New to Ubuntu
---

### Post by luckydeveloper on 2008-10-09
hi,

whenever i work in gedit and create some sourcefiles say new.c and when i go to terminal and check the files,, there is another file with the same name ~new.c with the symbol ~ attached to it. there is also my original file present there. it becomes as two files and is becoming nasty in that directory, i mean for every file i create there are two files created one with the original name and the other with ~ symbol attached like(new.c and ~new.c) . how should i prevent this.....

please help

---

### Post by SunnyRabbiera on 2008-10-09
the files with a ~ are usually backup files.

---

### Post by dhtseany on 2008-10-09
(Now I could totally be wrong but) I think those are temporary files used when you makes changes to a file and then after you save the changes that file should disappear. 

Someone else step in if I'm wrong :)

Peace
Sean

---

### Post by OutOfReach on 2008-10-09
Like SunnyRabbiera said, they are backup files in case you need to revert to an older state.
You can prevent gedit from saving these backup files by going into gedit's preferences and the Editor tab and unselect the 'Create a backup copy of files before saving'

---

### Post by luckydeveloper on 2008-10-09
> **dhtseany said:**
> (Now I could totally be wrong but) I think those are temporary files used when you makes changes to a file and then after you save the changes that file should disappear. 

Someone else step in if I'm wrong :)

Peace
Sean
hey they dont disappear..i have tried them several times. after saving my source files, they are still there.

any way, editing my preference should be the solution, i ll let u know if it works. thanks for the help people

---

### Post by luckydeveloper on 2008-10-09
yeah , it worked, i just disabled the setting in the prefences for not to make backups... thanks.

---

