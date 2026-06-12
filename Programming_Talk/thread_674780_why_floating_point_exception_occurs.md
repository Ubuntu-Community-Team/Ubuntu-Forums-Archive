---
title: "why floating point exception occurs?"
date: 2008-01-22
forum: Programming Talk
---

### Post by SandyKhan on 2008-01-22
hi,
    i have copied a set of GNU compiling tools e.g. **cc**, **gcc**, **c++**, **g++** and **gdb**. whenever i compile  or debug a program using any of these tools, the following error msg is print:

Floating point exception (core dumped)

can anyone plz help and guide me how to resolve this? i am working on **linux_i386** build environment and cross-compiling for **linux_arm ** target platform.

---

### Post by LaRoza on 2008-01-22
What do you mean you copied it?

---

### Post by SandyKhan on 2008-01-22
i got them in a .tar.gz file. i extracted and copied them in /opt directory.

---

### Post by LaRoza on 2008-01-22
> **SandyKhan said:**
> i got them in a .tar.gz file. i extracted and copied them in /opt directory.

Can't you install them? There might be other steps in getting everything working.

```

sudo aptitude install build-essential

```

---

### Post by SandyKhan on 2008-01-22
i have already installed build-essential, and they are working fine. but, i am having the problem with cross-compiling tools which i have copied in /opt directory.

---

### Post by ynef on 2008-01-22
> **SandyKhan said:**
> i have already installed build-essential, and they are working fine. but, i am having the problem with cross-compiling tools which i have copied in /opt directory.

Just to be perfectly clear, does this happen when you try to execute your ARM-executable on your i386 operating system and hardware, or when you've moved it over to an ARM system?

---

### Post by SandyKhan on 2008-01-22
this happens in building/compiling. So, there are no executables yet. the build/compilation stops when a **.c** file is encountered and gcc is implicitly called.

---

### Post by ynef on 2008-01-22
> **SandyKhan said:**
> this happens in building/compiling. So, there are no executables yet. the build/compilation stops when a **.c** file is encountered and gcc is implicitly called.

Are you perfectly certain that the gcc version that gets called is the one you unpacked into /opt, or could it be the one you've got installed via build-essential? I know my questions sound stupid, but just covering the basics here. :-)

---

### Post by SandyKhan on 2008-01-22
yes, i'm pretty sure about that. bcoz i change directory to /opt/../bin and then call **gcc** specific to those tools through **./gcc**

---

### Post by tehet on 2008-01-22
You'll need dpkg-cross and some other stuff to get a working cross-compiling tool chain.
[http://people.debian.org/~debacle/cross/](http://people.debian.org/~debacle/cross/)

---

### Post by SandyKhan on 2008-01-22
actually, the tool chain i am using to cross-compile is provided by the vendor. So, i have to limit myself to the given tool chain. but, i am unable to cross-compile as the floating point exception is occuring everytime i try to compile.

---

