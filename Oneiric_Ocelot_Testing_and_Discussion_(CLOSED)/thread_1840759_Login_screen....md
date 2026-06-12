---
title: "Login screen..."
date: 2011-09-08
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by sir.sargento on 2011-09-08
Hello. Anybody have any ideas to help me fix my login screen? Mine is still the old style and is aligned to the center. I have tried reinstalling the lightdm and unity-greeter package via synaptic but still the old login screen. Any ideas would be great.

Thanks,
Tony

---

### Post by Framli on 2011-09-08
It seems like you are still using GDM.

"sudo dpkg-reconfigure lightdm" should let you choose between using lightdm and gdm.

---

### Post by sir.sargento on 2011-09-08
> **Framli said:**
> It seems like you are still using GDM.

"sudo dpkg-reconfigure lightdm" should let you choose between using lightdm and gdm.

You were right I was still using GDM. However when selecting lightdm the following errors are output:

dpkg-maintscript-helper: warning: environment variable DPKG_MAINTSCRIPT_NAME missing
dpkg-maintscript-helper: warning: environment variable DPKG_MAINTSCRIPT_PACKAGE missing

Know how to fix that? Or will it even cause a problem?

Thanks again,
Tony

---

### Post by Framli on 2011-09-08
I have the same warnings after selecting Lightdm, but it works fine. If the command hasn't enabled the Oneiric login screen, try
"sudo /usr/lib/lightdm/lightdm-set-defaults --greeter=unity-greeter"

---

