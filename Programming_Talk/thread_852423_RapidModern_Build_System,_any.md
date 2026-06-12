---
title: "Rapid/Modern Build System, any?"
date: 2008-07-07
forum: Programming Talk
---

### Post by dernob on 2008-07-07
Hi,

for a lot of small projects I made the makefiles by hand. But now I'm coming into more complex areas currently struggling with Eclipse and want to ask if there are more intuitiv systems around and which you would suggest? My idea of a good one starts at the one of XCode. There you define your targets (graphically) and then drop in alle the files you need to be inside. Then you drop the targets into other, and so there are dependant. Your libs are also framework icons you can put as you want, and so you create library references. Also you can define project-settings which are automatically mapped to all the subsystems.

So far I tried out
**Makefiles by Hand** Works well, on small projects
**Autogen/Automake** (with the help of KDevelop). Looks heavy cryptic, small projects gets much bigger (IMHO a build system shall be installed on the target system, not being delivered by the program itself). I did not yet figure out, how I can split up a project into different static files which are then linked to a big executable, maybe a KDevelop issue.

**SCons** Pretty cool on medium sized; but you have to update a FileList-Page by Hand. When you automatically scan for .cpp Files, then you get problems when you distinct your src path with your target path (as the script copies first and let you search from your target path - relative links won't work anymore). This design looks not too well planned. Also, the copying issue makes live harder while debugging (as you have to set up your breakpoints at the copied location)

**Eclipse CDT Builder** Usable on bigger projects, graphically (automatically builds all .cpp files, you have to deselect them if you dont want to), but slow, building takes much longer time, as Makefiles are always recreated. A bit stupid: You have to put in your .project file in the topmost folder; not good if your company ask you to put it into a specific subfolder (the same problem with KDevelop!). If you want to change one thing in 20 Projects at once, you have to go through them all - no supersettings per workspace.

---

### Post by haTem on 2008-07-09
You could try [cmake]("http://www.cmake.org/"). I believe it has a gui, but writing the files by hand isn't too difficult. It's certainly simpler than automake &co.

---

