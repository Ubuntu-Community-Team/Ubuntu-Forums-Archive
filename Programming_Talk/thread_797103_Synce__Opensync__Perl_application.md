---
title: "Synce / Opensync / Perl application"
date: 2008-05-17
forum: Programming Talk
---

### Post by cheat on 2008-05-17
Hello everyone,

I am currently developing some sort of front-end for the synce utilities in perl. The project was initiated because I grew frustrated with the device working fine and syncing manually, but failing using already existing tools such as raki, multisync, kitchensync and so on.

It is a tray icon that performs what all the other apps do, nothing fancy yet. However, I have been working for a few hours only.

I have two questions:

1. Is it worth releasing it to the public?
2. How do you manually remove an application from the device (there is no "unload.exe" in wm6) :confused:

Thanks.

---

### Post by VeeDubb on 2008-05-17
1. If it actually works any better than the stuff that's already out there, it is ABSOLUTELY worth releasing to the public.

2. To manually unintall a program on a pocket PC, there's a "Remove Programs" button in the "System" tab of the "Settings" menu.

---

### Post by cheat on 2008-05-19
Hi and thanks for the reply.

However, I'm not actually trying to find a method to remove the programs manually using the device but using my Linux box. To be more specific, in earlier versions of Windows Mobile there was a certain "unload.exe" file that performed this task.

I am fairly familiar with the old and new method of removing the installed applications. The problem is, the new method uses internal DLL calls on the device and there is no simple "run exe with program name as argument to remove".

Thus, removing an application remotely is no longer possible. I won't include a half-working feature in the application I'm building so that's why I wanted to know. Maybe someone knows. I'll also post on the XDA forums, maybe I'll be more successful.

In any event, none of the other applications out there detect my device even though ODCCM and VDCCM detect it. I can also browse it. The detection method in their case really bothers me.

Anyway, if the community wishes me to release it, I will. It's only an interface anyway...

Thanks.

---

