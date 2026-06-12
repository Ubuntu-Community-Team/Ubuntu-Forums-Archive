---
title: "Deleting modules in SourceForge's CVS"
date: 2005-05-18
forum: Programming Talk
---

### Post by Hikaru79 on 2005-05-18
Although I am not a new programmer, these last few days have been my first stab at using CVS (as a developer, that is). Although I've gotten the hang of it mostly, I made quite a bit of a mess in my repositry -- mainly a lot of modules (directories) that shouldn't be there. The sourceforge documentation covers the deletion of individual FILES, but not entire modules. Can anyone please give me a quick primer to mass-deleting folders from SourceForge's CVS? Please note that I am NOT interested in keeping the files' history or anything like that -- I couldn't care less, I'll just re-commit them correctly. It's a young project. I just want to clean out all my "practice commits" for back when I had absolutely no idea what I was doing (aka a few days ago).

Any help is greatly appreciated :D Thanks!

---

### Post by vague- on 2005-05-19
Okay, I could be talking complete lies as I have not used CVS in a while.  However, I do not think you delete directories in CVS, because of their "Attic" system for storing deleted files.  Instead, you provide parameters to the CVS command line to make it ignore the empty folders.  Any CVS wizards that see a flaw in the previous paragraph, feel free to correct it.

---

### Post by mayco on 2005-05-19
[QUOTE=vague-]Okay, I could be talking complete lies as I have not used CVS in a while.  However, I do not think you delete directories in CVS, because of their "Attic" system for storing deleted files.  Instead, you provide parameters to the CVS command line to make it ignore the empty folders.  Any CVS wizards that see a flaw in the previous paragraph, feel free to correct it.[/QUOTE]
 if you want to remove a module in cvs, you have to contact the sourceforge-team, it is explained in the documentation somewhere. you can't do it yourself (as with directories)

---

### Post by Hikaru79 on 2005-05-19
Ah, I see =/ Thanks guys!

---

