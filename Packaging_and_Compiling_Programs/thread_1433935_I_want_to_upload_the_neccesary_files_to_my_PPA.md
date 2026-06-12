---
title: "I want to upload the neccesary files to my PPA"
date: 2010-03-19
forum: Packaging and Compiling Programs
---

### Post by Paradox Uncreated on 2010-03-19
Could someone describe the neccesary commands. I'm in the source dir, where I usually compile with make.

---

### Post by SevenMachines on 2010-03-23
try looking over [https://help.launchpad.net/Packaging/PPA/Uploading](https://help.launchpad.net/Packaging/PPA/Uploading) and see if that helps.
The actual file to upload will be the one that ends in 
_source.changes which is created when you have run debuild -S on your package. you'll need to make sure the key you sign the package with is added to your launchpad account too (if i remember right!)

---

### Post by Paradox Uncreated on 2010-03-23
You know, I am just going to skip the PPA, it is such a small app, and compiling is just fine. If anyone else wants to make a package though, it's @ [www.sourceforge.com/projects/pxu](www.sourceforge.com/projects/pxu). 

It's a limiter, and some other plugins. Probably interesting to musicians and audio-engineers.

Peace Be With You.

---

### Post by Paradox Uncreated on 2010-04-05
You know, I can do a package, but I don't want to read through obscure documentation in order to do it.

Just give me the basics, minimal scripts, to install one file. (meaning the scripts in the packages, and packaing with AR itself.)

Filestructure of the .deb is an AR archive.

And inside it is another archives.
For instance, what do I need, to install filex, without any additional happenings?

Compress file into data archive.. update the info file, etcetc? And package with AR? And so forth. 

Is there any documentation from this fundamental perspective somewhere?

---

### Post by Compintuit on 2010-04-06
I haven't found how to create one by hand. The two-archive structure is so the checksums can be in one for the other. The command to make a package is checkinstall. That's probably exactly what you want.

---

### Post by Paradox Uncreated on 2010-04-06
Do you need checksums at all?

This seems like a nice tool, when you deal with an obscure or complex Makefile, however I want to know the basics first.

---

