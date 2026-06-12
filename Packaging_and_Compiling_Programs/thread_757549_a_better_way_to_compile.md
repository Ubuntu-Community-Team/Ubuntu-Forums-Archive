---
title: "a better way to compile?"
date: 2008-04-17
forum: Packaging and Compiling Programs
---

### Post by Zyphrexi on 2008-04-17
poorly documented requirements, output that isnt specific. It's always a pain to compile stuff on a new system, so my question is this, is there a better way to compile than just your 'make makefile'?

I know gentoo is really great for building stuff, but really I'm just looking for a better solution to the dependency problem.

---

### Post by Jussi Kukkonen on 2008-04-17
> **Zyphrexi said:**
> I know gentoo is really great for building stuff, but really I'm just looking for a better solution to the dependency problem.

Better solution than what? Debian packaging takes care of build dependency handling, and so do configure scripts to some extent -- they're not perfect solutions but they do work... what exactly is not working for you?

---

### Post by Zyphrexi on 2008-04-17
well i'm building eduke, plus some other stuff, and it's all handled by make, there's no configure script, and one isn't needed afaik.

i built it fine before on gutsy, but this is a fresh install on hardy, so I don't remember what all dev packages I had installed. building stuff I don't always get helpful messages telling me what the Makefile is missing, since that's up to the author of said Makefile.

---

### Post by Jussi Kukkonen on 2008-04-17
> **Zyphrexi said:**
> there's no configure script, and one isn't needed afaik.

Well, you're having trouble getting the source to build on a new machine... that's a pretty good indication it does need a configure script. A well written (or autotools generated) configure file would check for build dependencies.

---

### Post by Zyphrexi on 2008-04-17
so should I generate a configure script? I always figured that was kind of up to the maintainer, and I wouldn't be able to generate one.

---

### Post by Jussi Kukkonen on 2008-04-18
> **Zyphrexi said:**
> so should I generate a configure script? I always figured that was kind of up to the maintainer, and I wouldn't be able to generate one.

You're right, a developer should do it, and for you the path of least work is just finding out the dependencies and installing them: configure (or configure.am for autotools) needs to be written, not generated  -- my comments we're just meant to say "the reason for your build pains is not having configure or autotools" (not to say they don't bring their own kind of pain along...)

---

