---
title: "Repack a game in a .deb-package to a snap, problems with audio."
date: 2017-01-02
forum: Packaging and Compiling Programs
---

### Post by renfors on 2017-01-02
I'm trying to repack a game in a .deb-package to a snap.
All files that are shown when running "ldd" are included in the snap.


When i run it from the installed snap, i get this and the sound doesnt work: 
AL lib: (WW) alc_initconfig: Failed to initialize backend "pulse"
AL lib: (WW) alc_initconfig: Failed to initialize backend "alsa"


Also, in the beginning, i get "Segmentation fault (core dumped)" but the game still runs.

---

