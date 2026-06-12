---
title: "Creating .run packaged files"
date: 2007-04-09
forum: Programming Talk
---

### Post by jeznet on 2007-04-09
I would like to know how to create a packaged .run file, the one similar to nvidia installer. I know that it contains a header script that extracts the embedded tarball into /tmp and another script to install it. Lets say I have a .tgz file and a script installer, I would use *cat script.sh file.tgz > myinstaller.run*, how would I extract the .tgz file from itself? Or is there a professional way to do this?

-Jez

---

### Post by jeznet on 2007-04-24
I think I'm helping myself more than the community..:) 

Anyways theres a package called makeself. Just ***sudo apt-get install makeself*** 

Its a neat program..I packaged a game including its resources into a self-contained file that autoruns the program.

---

