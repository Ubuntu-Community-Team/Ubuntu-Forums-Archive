---
title: "Wich are the packages that provide gdict?"
date: 2009-01-25
forum: Packaging and Compiling Programs
---

### Post by amrlima on 2009-01-25
I'm compiling a package (gtranslator) which requires gdict-1.0 >= 0.11.0 as a build dependency for a plugin. Which package in Ubuntu provides it? I guess gnome-utils could provide this dependency but including it as a build dependency does not solve the problem, there must be some other dependency.

Also the package is built only in English although other po files are present. Is there a way so specify with which language the package should build? sorry for the noob question. Still learning to package!

Thanks!

---

### Post by amrlima on 2009-01-25
I'll answer myself :). Just found out that the library is libgdict-1.0-dev. But it's only present in jaunty so that's why I never found it in intrepid! So I guess I won't have this plugin build in intrepid.

But I still don't have the answer for my language issue with the build. EDIT Now I know the reason for it not being in translated. The po file is ancient and in damned lies its only 5% translated... :)

---

