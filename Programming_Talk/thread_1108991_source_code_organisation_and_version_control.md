---
title: "source code organisation and version control"
date: 2009-03-28
forum: Programming Talk
---

### Post by sujoy on 2009-03-28
How do you organise your projects?

Do you place the C source codes and the header files in src/ subdirectory, or use a separate dir for headers? Where should i keep the Makefile?

Please also mention your preference for other languages.

Version control as I have understood so far is for source codes only. However, does it work with other components like icons, images, embedded flash etc ?

---

### Post by stroyan on 2009-03-28
Organization depends on the size of the project.
If it is simple then all files go in one directory.
When it starts to get complicated then common functions are grouped into libraries.
In that case the files for each library are grouped in a subdirectory.
Internal header files can stay with the library code.
External header files for public interfaces go in a common headers directory.

Multiple large programs may have their code moved to separate subdirectories.
Code shared between programs should be in libraries.

One makefile per directory.
The root directory gets a makefile that invokes make in each subdirectory.
That allows changes to be made in small makefiles but a single make command to rebuild everything.

Many version control packages can handle binary files.
But they won't be able to show what is different between versions as they can with text files.
And the size of multiple binary revisions will grow much faster than text files.
Plan ahead for having enough room.

---

### Post by sujoy on 2009-03-28
thank you for clearing things up. :)

i tend to lose focus as the code size spans multiple files, and as such organising things up front seems to be the only logical way to keep things sane.

---

