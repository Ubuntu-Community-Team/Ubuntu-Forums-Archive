---
title: "gsettings and/or gconf"
date: 2011-01-20
forum: Packaging and Compiling Programs
---

### Post by tonemgub on 2011-01-20
Hello.
I have been writing an application for a few months and have used gconf for my first release. I know that maverick is using dconf and gsettings and that gnome recommends migrating to gsettings. The problem is that I want my application to run on both, maverick and lucid. Is there a seamless way (for the user) to use gsettings in lucid (something I, as a developer could do)? If possible, I would like to avoid having to code something like that:
```
#ifdef HAS_GSETTINGS
  g_settings_get...()
#else
  g_conf_get...()
#endif
```
Thank you for your help.

---

