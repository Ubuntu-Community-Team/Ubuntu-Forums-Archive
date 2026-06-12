---
title: "Implications of compiling source packages?"
date: 2015-03-23
forum: New to Ubuntu
---

### Post by garycheng12 on 2015-03-23
I've read documentation titled "CompilingSoftware" and "CompilingEasyHowTo" but I still don't have a good understanding of the end result and implications and need some clarification. All I know is that source code needs to be compiled to binary files specific to a certain architecture. Probably best to ask a list of questions rather than a giant wall of text:

**1.** An application like Intellij IDEA IDE is a available as a pre-compiled binary package--I just download the tar.gz file from the website, extract it, and run a script to run the program (no installation required). Is this exactly what I would get if I were to simply get the source code and do "./configure" and then "make"? Is this to be avoided solely because of the potential situation where the package manager may need to update a dependency of a package managed by the package system that may also be a dependency of the compiled binary files (but is not yet installed)? 

**2. **Would there be a way to have a package with two different versions where one version is maintained by the packaging system as a dependency for installed packages and another version as a dependency for the compiled binary files that is not installed assuming the compiled binary files may need a specific version of the dependency? Or a good solution in this situation?

**3. **Does "checkinstall" now install the compiled binary files as if it was any other package managed by the packaging system? If there are differences, what are the implications of these differences (in terms of stability, compatibility, etc.)? I feel like I grouped the "./configure, make, checkinstall" method with ".run installation" method as both methods to avoid and now suspect that the former method is 100% safe and the latter method to be avoided solely to be avoided because the package manager can't track these bunch of files scattered all over your system (would this be the only reason to avoid ".run installation" and is the .run script only extracting these files as opposed to installing them)?

**4. **Continuation of #3: How would you go about updating whatever you get after "checkinstall" if it's not a package that is treated the same as any other package managed by the packaging system? 

**5. **Any further tips/words of caution regarding this topic? 

Thanks!

P.S. Semi-unrelated question: If I wanted to isolate a package from the PPA and keep the rest of the system stable so that I can easily know that the package from the PPA is causing problems and revert changes, which packages do I have to pin? I don't understand the advice: > You do _not_ want to pull  the whole dependency chain of a package from Testing/Sid, but only the  "relevant pieces" from it. And even then, you should carefully analyse  the possibilities and see if the upgrade is worth doing.
You have to  concentrate on the repercussions of the dependencies that are not yet  installed or need to be upgraded to a newer version.
 given on the first post here: [http://forums.debian.net/viewtopic.php?p=435453](http://forums.debian.net/viewtopic.php?p=435453)

---

### Post by Impavidus on 2015-03-24
As a rule, there are no rules for getting software from outside the package manager. There are only guidelines.

1: Downloading a precompiled binary usually give more or less the same result as using make. The difference I can imagine is that the precompiled binary is most likely to be statically linked, whereas the home compiled one is more likely to be dynamically linked. That is, the precompiled binary has no or few dependencies, the home compiled one has many. But not always.

When something like a library is upgraded by the package manager, it doesn't break all applications depending on that library. That would only happen when the interface to the library changes, which only happens in Ubuntu during a release upgrade. Simple bugfixes in a library don't break applications. As you may have noticed, when you receive an upgrade to some heavily used library, you don't get upgrades to everything that depends on it.

2: That would depend on the package. But if you're talking about libraries, it is possible to have multiple versions of a library installed at the same time. By default the compiler will link the home compiled application to the latest version of the library, but you can tell it to link to a different version. You may have to manually edit the Makefile though, and there are no simple rules on how to do that.

It doesn't matter whether the libraries or the applications are properly installed or not, as long as they don't conflict with the managed software. Installing them in /usr/local is fine, as that directory is meant for such things.

---

### Post by sandyd on 2015-03-24
> **garycheng12 said:**
> I've read documentation titled "CompilingSoftware" and "CompilingEasyHowTo" but I still don't have a good understanding of the end result and implications and need some clarification. All I know is that source code needs to be compiled to binary files specific to a certain architecture. Probably best to ask a list of questions rather than a giant wall of text:

**1.** An application like Intellij IDEA IDE is a available as a pre-compiled binary package--I just download the tar.gz file from the website, extract it, and run a script to run the program (no installation required). Is this exactly what I would get if I were to simply get the source code and do "./configure" and then "make"? Is this to be avoided solely because of the potential situation where the package manager may need to update a dependency of a package managed by the package system that may also be a dependency of the compiled binary files (but is not yet installed)? 

**2. **Would there be a way to have a package with two different versions where one version is maintained by the packaging system as a dependency for installed packages and another version as a dependency for the compiled binary files that is not installed assuming the compiled binary files may need a specific version of the dependency? Or a good solution in this situation?

**3. **Does "checkinstall" now install the compiled binary files as if it was any other package managed by the packaging system? If there are differences, what are the implications of these differences (in terms of stability, compatibility, etc.)? I feel like I grouped the "./configure, make, checkinstall" method with ".run installation" method as both methods to avoid and now suspect that the former method is 100% safe and the latter method to be avoided solely to be avoided because the package manager can't track these bunch of files scattered all over your system (would this be the only reason to avoid ".run installation" and is the .run script only extracting these files as opposed to installing them)?

**4. **Continuation of #3: How would you go about updating whatever you get after "checkinstall" if it's not a package that is treated the same as any other package managed by the packaging system? 

**5. **Any further tips/words of caution regarding this topic? 

Thanks!

P.S. Semi-unrelated question: If I wanted to isolate a package from the PPA and keep the rest of the system stable so that I can easily know that the package from the PPA is causing problems and revert changes, which packages do I have to pin? I don't understand the advice:  given on the first post here: [http://forums.debian.net/viewtopic.php?p=435453](http://forums.debian.net/viewtopic.php?p=435453)
Some additional info

1. Intellij IDEA IDE in particular is a proprietary product, and as a result is not open source. Since it is not open source, we do not know if they even use a configure script to compile their application.

2. Some applications bundle their libraries as to not use the system libraries for one reason or another. They can compile against specific system libraries if necessary.

3. I *think* checkinstall simply bundles up the files that make install would install.

4. You have to update manually. This is one of the reasons that PPAs are a bit discouraged - you are relying on the person behind the PPA to keep things updated. If he/she forgets, then your software will become out of date, and may be insecure.

---

