---
title: "Where do I get gstreamer.pc file from?"
date: 2012-04-06
forum: Packaging and Compiling Programs
---

### Post by mabo5184 on 2012-04-06
Hi,
I'm trying very hard to compile the latest Rhythmbox source code and I have been having some problems so I was looking for some advice.

During the ./configure phase I get complaints relating to packages missing. Usually the package is installed but the dev package is missing so I install that it I move onto the next missing package.

No package 'gstreamer-0.10' found
No package 'gstreamer-base-0.10' found
No package 'gstreamer-plugins-base-0.10' found
No package 'gstreamer-interfaces-0.10' found
No package 'gstreamer-pbutils-0.10' found


Now it is complaining the gstreamer pakages are missing, not so, they are installed, so I guess I need a dev package but I don't seem to be able to find any in the repo's ...

I assume this is probably a stupid question because I don't compile a lot of somewhere but I have run out of ideas. 

Does anyone have a suggestion ...

---

### Post by mc4man on 2012-04-06
libgstreamer0.10-dev

---

### Post by mabo5184 on 2012-04-06
I just discovered the dev packages are prefixed with lib, so the name is libgstreamer ...

I have now installed dev packages, errors have gone, almost ready to make ...

---

### Post by mabo5184 on 2012-04-06
Thanks

---

