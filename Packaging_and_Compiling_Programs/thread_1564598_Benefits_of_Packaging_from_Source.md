---
title: "Benefits of Packaging from Source?"
date: 2010-08-30
forum: Packaging and Compiling Programs
---

### Post by dodle on 2010-08-30
Are there any benefits for packaging debs from source?  I have done some packaging, and most of my programs have been written in Python.  I just take those scripts and place them in a deb with:
```
dpkg -b
```

With C++, I just compile my program, then take the binaries and do the same.  It seems like there are a multitude of ways to build packages from source, and it is a little confusing to me which is the best.  The only experimenting I've done is with dh_make.  But I have heard of other options such as checkinstall and pbuilder.  

I understand that in order to get a project into the official Debian/Ubuntu repositories, the original source needs to be included along with the .dsc and .diff.gz files, but can't all this be done without packaging from source?  Is there something that I don't know about packaging from source?  The answer to that is probably "yes" :).

Maybe the problem here is that I don't know anything about patching.

**Edit:** Okay, I realize now how stupid this question was.  It's just a pain to package for Debian/Ubuntu.

---

### Post by cariboo on 2010-08-30
When submitting packages you don't have to package them first, all you have to do is submit the source, dsg and .diff.gz the build farm creates the package. The only reason I can see for creating a package first is to make sure it will build properly.

---

### Post by dodle on 2010-08-31
I didn't know that, thanks.  That makes my life easier.

---

