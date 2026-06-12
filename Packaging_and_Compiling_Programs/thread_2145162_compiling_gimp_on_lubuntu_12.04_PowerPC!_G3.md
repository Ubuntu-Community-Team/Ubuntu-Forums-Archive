---
title: "compiling gimp on lubuntu 12.04 PowerPC! G3"
date: 2013-05-14
forum: Packaging and Compiling Programs
---

### Post by imacg3ppc on 2013-05-14
Before I undertake this project, I want to see if you all can answer some basic compiling questions for me!

Want to install gimp 2.8. I will settle for 2.0 if i have to. I've been  reading documentation and i want to make sure the procedure will be the  same or similar for PPC machines. I am on a g3 imac slot load with  12.04. I have not yet run sudo apt-get update... i have no internet  connection at home yet. So i'm sure i'll want to do this first.
-if i 'apt-get install gimp' will this install all the required packages and will this work for ppc?
-if i download the source code from gimp.org can i compile the source  out of the box without downloading additional development tools? ("make"  command)
-anyone who has gimp on a ppc with 12.04 what info could you give me?

Everyone have a great day. Great community here.

---

### Post by schragge on 2013-05-15
> **imacg3ppc said:**
> -if i 'apt-get install gimp' will this install all the required packages and will this work for ppc?
There [are](http://ports.ubuntu.com/pool/main/g/gimp/) GIMP packages for PPC on *ports.ubuntu.com*, so I suppose yes, it should work. The GIMP in Ubuntu 12.04 is version 2.6.12.

---

### Post by SeijiSensei on 2013-05-15
I recently tried compiling GIMP 2.6.12 on my 13.04 machine with source from gimp.org and encountered persistent versioning problems with the GEGL dependency.  After half-an-hour or so of trying different solutions, I just gave up. I recommend sticking to pre-compiled versions if you can find them.

I think 12.04 has the correct versioning to compile 2.6, since that was the standard package for that release.  Make sure to run "sudo apt-get build-dep gimp" before you begin to install all the source dependencies.  You'll also need to install the **build-essential** package if you have not yet done so.

---

### Post by imacg3ppc on 2013-05-16
i thank you folks for your helpful information! i think i'm going to try both the port and give a shot at compiling as well.

---

### Post by steeldriver on 2013-05-16
I was contemplating *trying *to build gimp from source (to enable debugging for some plugins I'm developing) - I got as far as searching out some how-tos but I can't vouch for them as I stopped short of actually doing it - you may find this helpful though, it seems to have some good information on prerequisites

[http://www.gregorystrike.com/2012/05/03/how-to-build-gimp-2-8-from-source-in-ubuntu-12-04/](http://www.gregorystrike.com/2012/05/03/how-to-build-gimp-2-8-from-source-in-ubuntu-12-04/)

Good luck

---

