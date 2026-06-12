---
title: "Mono and missing metadata"
date: 2008-09-09
forum: Programming Talk
---

### Post by Xir on 2008-09-09
Hi. I'm new to Mono development and am having a devilishly hard time compiling some WinForms code. Whenever I run gmcs -pkg:dotnet test.cs I get a fatal error back stating:

error CS0006: cannot find metadata file `cscompmgd.dll'

Does anyone have any idea what could be causing that? I have uninstalled and reinstalled all my mono packages to no avail and I'm pulling my hair out. If I can't get this fixed I'll have to return to doing my development on a Windows box, and I'd really prefer not to have to. Thanks!

edit: Oh, I should mention I'm running 8.04LTS and installed the latest version of Mono out of the Ubuntu repositories.

---

### Post by A'Key on 2008-10-30
Hi, Xir
I encountered the same problem. I copied cscompmgd.dll, and some other files from the directory, with an installed windows: windisk/windows/assambly/gac/cscompmgd/... in the directory /usr/lib/mono/2.0 After that gmcs-pkg: dotnet test.cs - worked without a problem.
I have installed: kubuntu 8.04, mono-1.9.2, libgdiplus, libmono-dev, WindowsXP,. Net framework 1.1.

Sorry, if not quite clear written. I do not know English very well.

---

### Post by directhex on 2008-10-30
libmono-cscompmgd7.0-cil - Mono cscompmgd library
libmono-cscompmgd8.0-cil - Mono cscompmgd library

---

