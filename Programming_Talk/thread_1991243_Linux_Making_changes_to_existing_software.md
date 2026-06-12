---
title: "Linux: Making changes to existing software"
date: 2012-05-30
forum: Programming Talk
---

### Post by sid.mallya on 2012-05-30
Hey guys!

I don't have much experience with Linux programming.

I am a student and for my Masters dissertation, I need to prompt users with error messages. Now, say if I use an existing software package like, LibreOffice writer, can i make changes in the software to trigger error messages on certain actions or looped on time? Yes, I am saying I want to alter the actual working of the software.

Any help or nudge in the right direction is greatly appreciated. I have a programming background, so I probably will be able to make changes without killing myself. 

:popcorn:

Cheers,

Sid

---

### Post by ofnuts on 2012-05-30
For LibreOffice, the answer is yes: [http://www.libreoffice.org/download/license/](http://www.libreoffice.org/download/license/)

For most Open Source software the answer is also yes. There may be strings attached here and there, but they usually only apply if you redistribute the code... 

This said, "open source" means you are given access to the source code, but doesn't mean that rebuilding the whole thing, even from the unaltered source, is so easy. Not speaking of finding you way in the source to make workable modifications :)

---

### Post by sid.mallya on 2012-05-30
Oh I know that about open source, hence my choice of trying to implement this stuff in Linux. 

Since u mention the difficulty in building the source-code, do u reckon any other method for doing the same?

---

### Post by ofnuts on 2012-05-30
> **sid.mallya said:**
> Oh I know that about open source, hence my choice of trying to implement this stuff in Linux. 

Since u mention the difficulty in building the source-code, do u reckon any other method for doing the same?It depends a lot on the package and you own system. You'll find that you have dependencies on the various development packages for various libs. If you take a recent version of the package and you have an old Linux, you may be subject to a dependencies avalanche... I never tried to build OO, though (my biggest endevaor was Gimp). Miracles happen. But be also ready for the opposite :)

---

