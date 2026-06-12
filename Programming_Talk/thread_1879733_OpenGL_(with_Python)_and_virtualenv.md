---
title: "OpenGL (with Python) and virtualenv"
date: 2011-11-12
forum: Programming Talk
---

### Post by Evil_Cid on 2011-11-12
Earlier today I had install PyOpenGL on Ubuntu. According to this:

 [http://pyopengl.sourceforge.net/documentation/installation.html](http://pyopengl.sourceforge.net/documentation/installation.html)

 I have to keep my OpenGL isolated from the rest of python using virtualenv. Is that really necessary? Does PyOpenGL 'mess around' with other python stuff?

---

### Post by simeon87 on 2011-11-12
virtualenv is very useful if you're working with on multiple projects that each have their own dependencies. You don't want to install different versions of the same dependency on your computer without virtualenv because they might interfere and cause trouble.

---

### Post by Evil_Cid on 2011-11-12
> **simeon87 said:**
> virtualenv is very useful if you're working with on multiple projects that each have their own dependencies. You don't want to install different versions of the same dependency on your computer without virtualenv because they might interfere and cause trouble.

Ah, okay. So it's only a real problem when you have multiple versions of the same dependencies on one system...In that case, I too think that it is better to use virtualenv when working with multiple projects. However, I'm only going to work on a single project with OpenGL at the moment so it should not be too much of a concern and I can always create virtual-environments if I want to create more projects, where each project can have its own set of dependencies and I can link the packages from python 2.7 to virtualenv.

Would you agree?

---

### Post by MadCow108 on 2011-11-12
> **Evil_Cid said:**
> Ah, okay. So it's only a real problem when you have multiple versions of the same dependencies on one system...In that case, I too think that it is better to use virtualenv when working with multiple projects. However, I'm only going to work on a single project with OpenGL at the moment so it should not be too much of a concern and I can always create virtual-environments if I want to create more projects, where each project can have its own set of dependencies and I can link the packages from python 2.7 to virtualenv.

Would you agree?

I'd still use virtualenv. its not complicated, you just have to execute a short command before starting to work.
at some point in the future you may have a different project and then your global installation might interfer with that.
Also local python installations sometimes don't play nice with package managed modules.
and they are hard to remove completely again.

---

### Post by Evil_Cid on 2011-11-12
> **MadCow108 said:**
> I'd still use virtualenv. its not complicated, you just have to execute a short command before starting to work.
at some point in the future you may have a different project and then your global installation might interfer with that.
Also local python installations sometimes don't play nice with package managed modules.
and they are hard to remove completely again.

Okay. I'll use virtualenv to keep my project-specific package separate from global ones. Thanks a lot for the advice.

***Update***: Turns out PyOpenGL exists in the repostiories..although that is version 3.0.1 and the one mentioned in the webpage is 3.0.2a. Anyhow, I just realised I've wasted 20mins of my life trying to install PyOpenGL from source, whereas I could've just got it from Synaptic Package Manager or apt-get :(

---

