---
title: "Licencing question about linking to LGPL library with GPL changes from Debian"
date: 2009-09-28
forum: Programming Talk
---

### Post by ENOTTY on 2009-09-28
Hi,

Say I'm developing a closed source application that links against an LGPL library. AFAIK, this is kosher, and I don't have to release the source to my closed source application upon redistribution.

Then either a Debian or Ubuntu maintainer contributes a patch and packages it into the Ubuntu package, but this patch is licensed under GPL. AFAICT, this makes the entire library GPL, which means if I link against it, I will need to release the source.

Has anybody dealt with this kind of issue before? How did you work around it?

---

### Post by winch on 2009-09-28
As long as you are not developing against the GPL version and are not distributing it then I don't see how you have a problem.
Allowing users to replace the LGPL libs your program uses with their own versions is pretty much the point to the LGPL.

This basically means you have to develop on a distro with a different policy towards patching or build you own package without the GPL patch.

You might also consider filing a bug report against the package. Maintainers adding patches that go against the license wishes of the upstream developers usually are not a good thing. Chances are pointing that out to the maintainer isn't going to get you are new friend but there isn't really anything else you can do.

Of course there are plenty of grey areas here.

---

### Post by nvteighen on 2009-09-28
Hm... you're pretty lost there. If you want to benefit from the LGPL terms, you have to avoid those GPL patches, whether using the upstream version and patching the library by yourself if needed...

---

### Post by engla on 2009-09-28
Well this is difficult. All lies in how you distribute your software. If you distribute binaries compiled against Ubuntu's version of the library it may well be totally against the terms of the license. You will then have to distribute a license-clean version of the library yourself, or link statically against the clean library.

And I too think that you should at least bring this up with the maintainer. I don't know if I have sympathy though; GPL patches are fair game and it is part of the rules; if you don't play by the rules (release code), you can't benefit from the patches.

Edit: I suppose the patched and unpatched versions of the library are ABI compatible. Then you have to build your distributed binaries against the clean library, but if they are ABI compatible, the end user can choose to combine the program with the GPL library on the own computer. Most ISVs would choose to simply statically link against the clean version of the library though.

---

