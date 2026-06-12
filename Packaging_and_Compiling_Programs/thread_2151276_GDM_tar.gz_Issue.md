---
title: "GDM tar.gz Issue"
date: 2013-06-04
forum: Packaging and Compiling Programs
---

### Post by CosmicFlux on 2013-06-04
Hi,

I'm trying to package a new desktop environment I've been working on. The environment uses MDM as login manager, because GDM no longer supports adding new themes. I'm in the process of writing the bash script that will automate the installation, but I'm running into an issue with the MDM setup manager. The script updates the compressed theme archive with a new set of files but when I gunzip to write to the archive and then re-compress MDM no longer recognises that it's a gzipped file.

Nothing has changed with the archive or with any of the existing files, there are just new ones being appended. I even tried unzipping and re-compressing without making any changes and MDM manager does the same thing - it flashes an error stating the file isn't recognized as a valid theme archive. It does this regardless of whether I use the GUI or CLI to zip/unzip the archive.

Anyone got any ideas? I'm so close to making this new desktop distributable!

[Login Screenshot]("http://img203.imageshack.us/img203/929/screenshotgreen.png")

Cosmic

---

### Post by oldos2er on 2013-06-04
Moved to Packaging & Compiling Programs.

---

