---
title: "GLaux for Ubuntu"
date: 2006-12-16
forum: Programming Talk
---

### Post by cyberslayer on 2006-12-16
Anyone know where I can get GLaux (the OpenGL auxiliary library) for ubuntu?  I didn't see it in the repositories under the keywords I tried searching for.  I also tried several google searches but I didn't find anywhere I could download it.  Normally I would just use glut but I need it so I can compile another library that requires GLaux.  

Thanks

---

### Post by Wybiral on 2006-12-16
I've never seen it either... If your other library isn't too big you might be able to wrap around it with GLUT or SDL... (I highly recommend SDL). By that, I mean make your own "glaux" or at least a small library that wraps glaux calls into SDL or GLUT. Just find the ones you need and wrap them in.

This is just incase someone doesn't find a linux gluax.

---

### Post by hod139 on 2006-12-16
> **Wybiral said:**
> I've never seen it either... If your other library isn't too big you might be able to wrap around it with GLUT or SDL... (I highly recommend SDL). By that, I mean make your own "glaux" or at least a small library that wraps glaux calls into SDL or GLUT. Just find the ones you need and wrap them in.

This is just incase someone doesn't find a linux gluax.

glaux is unsupported in Linux and deprecated in Windows.  You should not be using it anymore.  The NeHe group has a [GLaux replacement]("http://nehe.gamedev.net/counter.asp?file=files/misc/nehe_glaux_replacement.zip") available, though I have never tried it in Linux and I don't even know if it will work.  Again, you really should not be using GLaux anymore.

---

### Post by cyberslayer on 2006-12-17
Ok thanks.  I think I will just find something else that doesn't require glaux.  I know not to use glaux; I only wanted it because another library I found required it.

---

