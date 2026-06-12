---
title: "Photran with ifort?"
date: 2007-02-02
forum: Programming Talk
---

### Post by mrphd on 2007-02-02
Hi, 

Has anyone managed to get Photran ([www.eclipse.org/photran/](www.eclipse.org/photran/)) working properly with the intel fortran compiler (I'm using version 9.1)? I'm struggling a bit and could do with some help...

Thank you!

---

### Post by mrphd on 2007-02-04
I've sorted my problem out (I think). It was complaining that it could not find ifort when i tried to compile, and in the end all I had to do was create a link for it in /bin/. It seems to work now, and I look forward to trying this out some more.

---

### Post by OvelhaNegra on 2007-02-25
> **mrphd said:**
> I've sorted my problem out (I think). It was complaining that it could not find ifort when i tried to compile, and in the end all I had to do was create a link for it in /bin/. It seems to work now, and I look forward to trying this out some more.

Can you please detail how did you create the link in /bin/? Sorry, I am a totally newbie on linux :(

By the way, with Photran can you use debug capabilities?

Thanks!
ON

---

