---
title: "Problem compiling. stdio and cstdio not included"
date: 2010-01-06
forum: Packaging and Compiling Programs
---

### Post by dreamspy on 2010-01-06
Hi

I was trying to compile libtorrent (this version: [libtorrent-0.12.4.tar.gz]("http://libtorrent.rakshasa.no/downloads/libtorrent-0.12.4.tar.gz")) and I got this error:

'snprintf' was not declared in this scope

So I added #include "stdio.h" to a couple of .cc files which fixed that. 

I also got this error in one .cc file:

'sscanf' is not a member of 'std'

which I fixed by adding #include <cstdio> to the file.

But I'm wondering what the problem might be?  I suspected that the problem would reoccur, and it did when I was trying to compile rtorrent. 

I tried to compile the same pacakges on a fresh install of Ubuntu 9.10, and didn't get any errors.

The computer I was compiling this on was an upgraded Ubuntu 9.10 (recently upgraded from 9.04). And if I remember correctly then in the upgrade process it said that it was going to remove some obsolete packages, and if I remember correctly then one of that packages was gcc (cant remember the version).  I checked in synaptic though and gcc 4:4.4.1 was installed.

So anyone have a clue what's going on here and how to fix it? 

regards
Frímann

---

### Post by SevenMachines on 2010-01-06
gcc 4.4 cleaned up some headers. this breaks code that included headers indirectly through other ones, now they have to be specified directly. fixing it wont cause problems on older gcc versions though so.

things you might see are,
```
error: 'sscanf' was not declared in this scope
error: 'EOF' was not declared in this scope
error: '::fseek' has not been declared
```this means <cstdio> is missing in the file

---

### Post by dreamspy on 2010-01-06
Ahh so this is then only a problem with cstdio?  

I don't mind adding a few #include lines when I compile. I just thought something was wrong here.

---

### Post by dreamspy on 2010-01-06
btw is there any possibility of including the #include <cstdio> in the whole project withouth having to edit 10-20 .cc files?

Probably not though... anyone?

---

### Post by SevenMachines on 2010-01-06
as i mentioned, some headers that used to be drawn in indirectly now arent in gcc 4.4. programs should really include everything they use directly but it can easily be missed until something they rely on changes. 
you might also see errors in changing to gcc 4.4 such as (from memory so might not be exactly right!)
uint32_t doesnt declare a type - missing #include <stdint.h>
i think i saw some with something like memcpy and/or memset too, which was a missing <cstring> include

---

### Post by SevenMachines on 2010-01-06
> **dreamspy said:**
> btw is there any possibility of including the #include <cstdio> in the whole project withouth having to edit 10-20 .cc files?

Probably not though... anyone?
i'd say #include in the file you use it in, if you rely indirectly on one of your included files including some other header then you can end up with problems such as the one you describe

---

### Post by dreamspy on 2010-01-06
Yeah of course one should do that if your writing the code yourself. I'm just thinking about when I'm compiling programs from source I get from the internet.

---

### Post by LKjell on 2010-01-06
> **dreamspy said:**
> Yeah of course one should do that if your writing the code yourself. I'm just thinking about when I'm compiling programs from source I get from the internet.

Then you fix it and send it upstream :)

---

### Post by dreamspy on 2010-01-06
Well that's not such a bad idea :)

---

