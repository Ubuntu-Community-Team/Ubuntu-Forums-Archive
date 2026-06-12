---
title: "Anjuta queries"
date: 2011-05-08
forum: Programming Talk
---

### Post by farproc on 2011-05-08
Im trying to use Anjuta in place of Code::Blocks for Ubuntu C & C++ Dev. However, I have some questions I hope can be resolved:

1. Anjuta's "create project from sources" seems only able to accept what I understand to be an autoconf generated project? Whats the easiest way to add files from a Visual Sutdio or XCode project to an Anjuta project?

2. When I create a project with Anjuta it creates a lot of files. Which files need to be added to SCM?

3. When I moved an Anjuta project on my system from ~/Prj1 to ~/Projects/Project, Anjuta kept looking for ~/Prj1/makefile.am as required for generate makefile.in When I reconfigured the project it built the new makefiles, but now can't compile as its looking for ~/Prj1/src/main.c and ~/prj1/src/events.c - If I can't move projects on my own system how can other people expect to fetch the project by svn and build it?

4. Is there some way to create an Anjuta project with multiple binaries? Or create multiple dependent projects?

---

