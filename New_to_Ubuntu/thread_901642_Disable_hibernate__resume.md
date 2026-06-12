---
title: "Disable hibernate / resume"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by maybeway36 on 2008-08-26
Is there a way to disable the resume feature in Kubuntu? When I boot up, my splash screen appears for a few seconds and then disappears. Booting without the "quiet" option, I see this happens right after the system tries to resume from the swap partition. I never use hibernate, but would like to have the splash screen stay up.

---

### Post by jbrown96 on 2008-08-26
I don't think there is a way to remove it. Try disabling it in /etc/default/acpi-support at line ~4

---

