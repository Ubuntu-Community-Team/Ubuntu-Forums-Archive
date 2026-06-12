---
title: "Make your own packages?"
date: 2005-11-04
forum: Packaging and Compiling Programs
---

### Post by ljr2600 on 2005-11-04
Is there any way to make your own packages for personal use with ubuntu? For example, I want to be able to use eclipse, however there isn't a package available for it. i could just install it, however, then I couldn't easily uninstall it later because its not managed by synaptic.

Also:
I assume that making packages out of software you want to install would be more appropriate because you can manage it with synaptic then, correct?

---

### Post by nenotnom on 2005-11-04
You can use checkinstall for this, it's in the repositories. 
(Is this the right forum to ask questions btw?)

---

### Post by Saiboogu on 2005-11-04
No, this isn't the spot for questions.. 

.. And yes, checkinstall is the perfect solution. If your package follows the usual configure / make / make install method, just replace make install with checkinstall. That bundles it all into a .deb and installs it with dpkg.

---

### Post by Kyral on 2005-11-04
1) Move to the Packaging and Compiling subforum in the Programming Forum.

2) If you even plan on actually like making this package public, don't use checkinstall. Read the Debian New Maintainers Guide on how to make a Debpack the real way. But for personal use, yah its fine :P

---

### Post by SpEcIeS on 2005-11-07
Check install works pretty good, but sometime I receive scrollkeeper issues. Not sure what that is about. :rolleyes:

---

