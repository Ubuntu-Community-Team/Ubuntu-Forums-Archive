---
title: "Packaging a Firefox extension as deb?"
date: 2009-07-19
forum: Packaging and Compiling Programs
---

### Post by lovinglinux on 2009-07-19
Is there a tutorial on how to package a Firefox extension as deb?

I want to distribute my extensions as deb to satisfy some dependencies instead of forcing the user to manually run additional installation commands.

I also have a question regarding permissions. My extensions relies on shell scripts to perform most actions, but it seems when I install the extension on a new profile the scripts looses their executable status. Is this normal? How can I avoid forcing the user to run a chmod command after installing the extension?

---

### Post by nhandler on 2009-07-21
> **lovinglinux said:**
> Is there a tutorial on how to package a Firefox extension as deb?

Yes. The Mozilla Team has some excellent [documentation]("https://wiki.ubuntu.com/MozillaTeam/Extensions/Packaging") on the wiki about how to package Firefox extensions.

---

### Post by lovinglinux on 2009-07-21
> **nhandler said:**
> Yes. The Mozilla Team has some excellent [documentation]("https://wiki.ubuntu.com/MozillaTeam/Extensions/Packaging") on the wiki about how to package Firefox extensions.

Thank you very much.

---

