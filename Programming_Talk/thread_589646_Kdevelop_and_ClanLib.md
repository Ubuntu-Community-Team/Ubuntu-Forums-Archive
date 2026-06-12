---
title: "Kdevelop and ClanLib"
date: 2007-10-24
forum: Programming Talk
---

### Post by phx_one on 2007-10-24
Hi to all.
I have a problem with clanlib in Kdevelop. I've installed Clanlib from official repository. all the packages are installed. clanlib headers are in usr/include, and libs are in usr/lib. all applications, which use clanlib libraries (for example, clanbomber), work properly. 
I created simple ClanLib application project in Kdevelop (using it's template). but when I run configure, it returns error:

checking ClanLib/application.h usability... yes
checking ClanLib/application.h presence... yes
checking for ClanLib/application.h... yes
checking for main in -lclanApp... no
configure: error: Couldn't find Clanlib libraries
*** Exited with status: 1 ***

but there are *.so files in /usr/lib, here is part of ls of this directory:

libclanApp.so  (this is link to libclanApp.so.2)
libclanApp.so.0.6.3 (this is .so file)
libclanApp.so.2  (this is link to libclanApp.so.0.6.3)

as I remember, /usr/lib is standard directory for libs, so it's not necessary to configure ld.
so, could you give me some advice, how can I solve this problem? thank you.

---

