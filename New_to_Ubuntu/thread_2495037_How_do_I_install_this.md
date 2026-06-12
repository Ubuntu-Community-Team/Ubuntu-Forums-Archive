---
title: "How do I install this?"
date: 2024-02-05
forum: New to Ubuntu
---

### Post by shadowmartyr on 2024-02-05
Hi, already installed Okular but I don't understand how to add Cairo backend from here:
[https://github.com/jonathanffon/poppler-lcd-patch](https://github.com/jonathanffon/poppler-lcd-patch)

---

### Post by Holger_Gehrke on 2024-02-05
Quite simple: you "git clone" the repository, change into the generated directory (should be 'poppler-lcd-patch'), and run the 'gen.sh' script. This will download the current source code for libpoppler, patch it and try to compile it. This will probably fail because of missing tools or dependencies, so be prepared to repeat that step multiple times, each time installing the dependency or tool it complained about. Once compilation succeeds, you will have a private copy of libpoppler. Now call gen.sh again but with the parameter 'inject'. The script will patch the .desktop files of programs known to use poppler to use that private copy instead of the one provided by Ubuntu.

Holger

---

