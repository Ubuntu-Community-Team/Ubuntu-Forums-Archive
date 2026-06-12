---
title: "cURLpp not included in Ubuntu repositories"
date: 2010-08-28
forum: Programming Talk
---

### Post by James78 on 2010-08-28
This topic is here to discuss one of my major frustrations at the moment. It has to do with the fact that cURLpp, the C++ bindings for cURL, are not inside the Ubuntu repository.

I'm making a C++ program right now, and although I can use cURL, using cURLpp would be much more helpful because of it's OOP design and exception safe code. Not only that, but it's easier to use in the first place.

Yes, I could download cURLpp, and configure, make, and make install (which I already did), but this requires me to link with an additional library, -lcurlpp, which is technically fine, I understand, it should be linked, but the problem is that when I distribute my finished program, I can't just ask people to download the cURLpp tar, unpack, then configure, make, and make install. My program is supposed to be ready to be used, that means I need the dependencies INSIDE the repository!! Doing it any other way would be way too sloppy and unprofessional.

It's a really frustrating thing, and could've been easily fixed by including cURLpp in the repositories.

What are your guys thoughts on this?

---

### Post by dwhitney67 on 2010-08-28
One, stop whining.  Just kidding.  :D

Two, static link libcurlpp with your application.

Three, you implied that you would be delivering an application, not source code.  So, even if you don't static link libcurlpp with your application, the end-user would still need to go out of their way to  install libcurlpp before attempting to execute your application.

Many applications have dependencies that require the end-use to obtain runtime libraries.  Why do you feel your application should be any different?

P.S.  To conclude, yes, it would be nice if libcurlpp was available in the repos.  But your audience on this forum probably is not the place to bring this up.  Maybe there's a different forum, or maybe you can contact Canonical directly?

---

### Post by James78 on 2010-08-28
> **dwhitney67 said:**
> Two, static link libcurlpp with your application.
That'd fix the problem. :)

> **dwhitney67 said:**
> Three, you implied that you would be delivering an application, not source code.  So, even if you don't static link libcurlpp with your application, the end-user would still need to go out of their way to  install libcurlpp before attempting to execute your application.
See below.

> **dwhitney67 said:**
> Many applications have dependencies that require the end-use to obtain runtime libraries.  Why do you feel your application should be any different?
It's just easier if the dependency can be installed automatically with the program from the repos. Keeps everything the latest version too. I try to keep things the simplest possible when I distribute a program, so that the users don't have to do work obtaining dependencies they need. I don't want to assume the end user is always smart enough to obtain, untar, configure, make, and make install an application. :)

---

### Post by Bachstelze on 2010-08-28
<snip>

The vast majority of packages in Ubuntu are maintained by people like you and me.  Found a package that isn't there?  Make a package, then it will be.  That's how all packages eventually ended there.

---

