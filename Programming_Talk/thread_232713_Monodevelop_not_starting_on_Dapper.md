---
title: "Monodevelop not starting on Dapper"
date: 2006-08-09
forum: Programming Talk
---

### Post by frenkel on 2006-08-09
Hi,

A few days ago I installed monodevelop. When trying to start it, I get this error:

> 
$ monodevelop

Unhandled Exception: System.Configuration.ConfigurationException: Cannot find /etc/mono/1.0/machine.config ()
in <0x000bb> System.Configuration.DefaultConfig:Init ()
in <0x0000d> System.Configuration.DefaultConfig:GetConfig (System.String sectionName)
in <0x0001a> System.Configuration.ConfigurationSettings:GetConfig (System.String sectionName)
in <0x0001f> MonoDevelop.Core.AddIns.AddInService:GetAddInDirectories (System.Boolean ignoreDefaultPath)
in <0x00024> MonoDevelop.Core.AddIns.AddInService:Initialize ()


That file is really missing. I filed a bug about it: [https://launchpad.net/distros/ubuntu/+source/monodevelop/+bug/55344](https://launchpad.net/distros/ubuntu/+source/monodevelop/+bug/55344), but nobody seems to have noticed.

I have even tried installing mono and mono-devel, but that didn't solve it.

Does anybody know with what package that config file comes?

Thanks in advance.

---

### Post by frenkel on 2006-08-09
Doesn't anybody know the answer?
Isn't anybody using monodevelop?
What's in your /etc/mono/1.0/machine.config?

---

### Post by gmclachl on 2006-08-09
machine.config is  (or appears to be) an XML file.

 It's included in the mono-common package

 George

---

### Post by frenkel on 2006-08-09
> **gmclachl said:**
> machine.config is  (or appears to be) an XML file.

 It's included in the mono-common package

 George

After installing mono-common I still don't have that file.

---

### Post by gmclachl on 2006-08-09
That's weird, if you open Synaptic and search for mono-common and view installed files it's listed under there.

---

### Post by frenkel on 2006-08-10
Weird..
I uninstalled monodevelop and mono-common, then installed mono-common and after that I installed monodevelop, and now the configs are just there.
Thanks!

---

