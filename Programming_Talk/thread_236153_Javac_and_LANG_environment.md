---
title: "Javac and LANG environment"
date: 2006-08-14
forum: Programming Talk
---

### Post by Tekkie on 2006-08-14
I have a strange problem, I check some Java files out of CVS over here, we created this files in Eclipse under Windows. I try to compile them on ubuntu to run some junit tests.

Before I used a RedHat system, and export LANG="en_US.iso885915" in the shellscript that starts the ANT build would work correcly and the files will compile.

If I copy over my files from RedHat to Ubuntu and run the same shellscript the LANG environment variable doesn't work and compile fails with "warning: unmappable character for encoding ASCII" on a loooot of files followed by the character garbage in the wrong character set.

Why dont other locales work in the shell for ubuntu? /usr/lib/locale/ also seems to be empty and when I try to install locale support using apt-get it tells me all files are already the latest version.

---

