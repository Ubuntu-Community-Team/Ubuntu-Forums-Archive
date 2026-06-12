---
title: "Wine configuration questions"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by L a r r y on 2008-07-04
I am trying to make Wine work on Ubuntu 8.04, and am following these directions:  [https://help.ubuntu.com/community/Wine]("https://help.ubuntu.com/community/Wine")

After the initial install, I was advised to run winecfg in my Terminal.  There I get this mass of error messages before the configuration utility came up: 
-----
[COLOR="DarkRed"]preloader: Warning: failed to reserve range 00000000-60000000
Warning: the specified System directory L"C:\\windows\\system32" is not accessible.[/COLOR]
-----
:KS**and**:KS
-----
[COLOR="DarkRed"]err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report[/COLOR]
-----
These error messages were repeated a half-dozen times on the Terminal screen before the config utility opened up.  In the config utility, I am running the default Windows XP and the sound doesn't work.

Wine is in the Applications menu, and it has a working copy of Notepad and RegEdit, and Internet Explorer needs a Gecko engine installed before it displays anything.

What file do I need to look at to try to fix these errors?

---

### Post by whitethorn on 2008-07-04
Wine doesn't like pulse audio, I use 

pasuspender wine /../../foo.exe 

to stop pulse audio and to use alsa. It should give you sound back. As for the other erros I have no idea.

pasuspender also works great for other programs with problems working with pulse audio  like skype.

---

