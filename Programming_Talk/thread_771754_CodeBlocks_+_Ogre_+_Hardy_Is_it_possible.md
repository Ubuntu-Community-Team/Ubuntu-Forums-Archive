---
title: "CodeBlocks + Ogre + Hardy: Is it possible?"
date: 2008-04-27
forum: Programming Talk
---

### Post by aidave on 2008-04-27
Been trying to run OGRE in CodeBlocks, but to even compile one of the examples has been a major hurdle.  After finally get that done, the problems running the output file have been never-ending.  All of the tutorials I've found are too outdated to work.

Is there an up-to-date tutorial to get this setup running on Ubuntu Hardy?

---

### Post by aidave on 2008-04-28
bump

---

### Post by aidave on 2008-05-06
I guess it isnt possible then

---

### Post by Ferrat on 2008-05-06
Could you paste the first say 10 lines of the output?

---

### Post by Mickeysofine1972 on 2008-05-06
Have you been able to do it on Gutsy? or is this a first time with Code::Blocks?

Mike

---

### Post by bunyk on 2009-04-14
I am also using Code::Blocks. I install Ogre through Synaptic. Packages ogre-tools, ogre-doc, libogremain-1.4.9, libogre-dev.

I use wizard to create new Ogre project. But when I trying to build it occures error:
```
/home/bunyk/projects/ogre1/main.cpp|12|error: ExampleApplication.h: No such file or directory|
```

I select stupid solution, because I can not find any another. I find source of ExampleApplication.h in internet, create it in /projects/ogre1/ , and changed #include <ExampleApplication.h> to #include "ExampleApplication.h". But then appears:
```
/home/bunyk/projects/ogre1/ExampleApplication.h|26|error: ExampleFrameListener.h: No such file or directory|
```

Prewious my project in Code::Blocks using GLUT worked fine.

May be I do something wrong with installation? I will be glad to hear any suggestions.

---

