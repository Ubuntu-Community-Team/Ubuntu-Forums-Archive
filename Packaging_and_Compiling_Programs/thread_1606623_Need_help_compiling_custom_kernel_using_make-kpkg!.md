---
title: "Need help compiling custom kernel using make-kpkg!"
date: 2010-10-26
forum: Packaging and Compiling Programs
---

### Post by TehDooMCat on 2010-10-26
**EDIT:** The solution was to remove the .git folder from the source dir. It created the packages fine then. Although the kernel doesn't even boot :(

I'm doing a test to see how much power I can squeeze out of my Atom processor/ION chipset netbook by compiling a supposedly-optimized kernel for it. I've done this before on an old laptop mostly with success (although some drivers were missing), but I don't think I've ever managed to do it "the Debian way" - using make-kpkg.

I'm using zen-kernel (latest stable version from their git repo) and I've set it up to compile using the Intel C Compiler (rather than GCC) as that supposedly compiles programs optimized for the Intel processor they're on. Got the processor type/features in menuconfig set to 'Intel Atom' and I'm using the BFS scheduler... It compiles fine using ICC, which is p. cool, but the way Debian/Ubuntu packages it, it fails towards the end of making the kernel package with this error:
```
dpkg-gencontrol: error: package linux-image-2.6.35-zen2+ not in control info
```

Having done some googling, it's apparently the '+' at the end of the kernel name that dpkg doesn't like. However, I have no clue how to change 'zen2+' to just 'zen2'. I don't know whether that plus comes from the revision number, or --append-to-version, or what. Couldn't find anything in .config or menuconfig or by grepping through the source, that added zen2+ to the end of the version name...

I'm doing this on Ubuntu 10.10 and to the people experienced in compiling kernels for Ubuntu or Debian [+variants], could they explain to me what config files/program flags set the different parts of the kernel name? Or at least, how to prevent make-kpkg stalling at this error? :p

---

### Post by Noccy on 2011-03-26
The problem is in the "+" :)

You need to edit the scripts/setlocalversion (I think) file and find the part where it appends the +; it should be a string like "+" which you simply reduce to an empty string "".

After that it should compile okay.

- Chris

---

