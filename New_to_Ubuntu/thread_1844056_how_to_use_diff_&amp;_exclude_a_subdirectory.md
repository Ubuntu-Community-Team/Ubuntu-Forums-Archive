---
title: "how to use diff &amp; exclude a subdirectory?"
date: 2011-09-14
forum: New to Ubuntu
---

### Post by erinod on 2011-09-14
Hi,
I want to use diff to compare two directories, but I want to leave out one of the subdirectories. THe instructions I see online state, "To ignore some files while comparing directories, use the --exclude=pattern (-x pattern) option.  This option ignores any files or subdirectories whose base names match the shell pattern pattern."

I'm confused about what the base name is?

I want to diff the directories:
/home/erin/Documents/GRP/ProjectsDatabase/grpProjects.09_08_2011
/home/erin/Documents/GRP/ProjectsDatabase/grpProjects

And exclude the subdirectories:
/home/erin/Documents/GRP/ProjectsDatabase/grpProjects.09_08_2011/files
/home/erin/Documents/GRP/ProjectsDatabase/grpProjects/files

Would I do **-x='files'** ?

Thanks

---

