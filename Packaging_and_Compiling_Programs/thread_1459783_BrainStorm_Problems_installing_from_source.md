---
title: "BrainStorm: Problems installing from source"
date: 2010-04-21
forum: Packaging and Compiling Programs
---

### Post by gandhioftherillo on 2010-04-21
I am trying to install software called BrainStorm from source

'./config' runs fine with no errors but when I run 'make' this is what I get:


```
make  all-recursive
make[1]: Entering directory `/usr/local/src/BrainStorm'
Making all in src
make[2]: Entering directory `/usr/local/src/BrainStorm/src'
gcc -DHAVE_CONFIG_H -I. -I..  -DPACKAGE_LOCALE_DIR=\""/usr/local//locale"\" -DPACKAGE_SRC_DIR=\""."\" -DPACKAGE_DATA_DIR=\""/usr/local/share"\" -D_REENTRANT -pthread -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libsoup-2.4 -I/usr/include/libxml2   -D_REENTRANT -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12    -Wall -g -g -O2 -MT gps-map.o -MD -MP -MF .deps/gps-map.Tpo -c -o gps-map.o gps-map.c
gps-map.c:108: error: field ‘units’ has incomplete type
gps-map.c: In function ‘initialize_gpsd’:
gps-map.c:154: warning: implicit declaration of function ‘gps_query’
gps-map.c: In function ‘gps_init’:
gps-map.c:696: error: ‘imperial’ undeclared (first use in this function)
gps-map.c:696: error: (Each undeclared identifier is reported only once
gps-map.c:696: error: for each function it appears in.)
make[2]: *** [gps-map.o] Error 1
make[2]: Leaving directory `/usr/local/src/BrainStorm/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/usr/local/src/BrainStorm'
make: *** [all] Error 2
```

My newbishness is keeping from getting passed this.
Any ideas as to what I am doing wrong?

Thanks in advance for the help!

---

### Post by gmargo on 2010-04-22
Please provide link to the source code.

---

### Post by SevenMachines on 2010-04-22
i'd think its less what your doing and maybe the Brainstorm source needing updated for a newer version of gpsd (though i could be wrong). as mentioned before if you have a source code link or a link to svn or something like that?

---

### Post by lykeion on 2010-04-22
I googled brainstorm and gps and found the link to download the sources:

[http://aircrafter.org/boggs/stormchasing/BrainStorm](http://aircrafter.org/boggs/stormchasing/BrainStorm)

I got a similar compile error:


gps-map.c:108: error: field &#8216;units&#8217; has incomplete type
gps-map.c: In function &#8216;gps_init&#8217;:
gps-map.c:696: error: &#8216;imperial&#8217; undeclared (first use in this function)
gps-map.c:696: error: (Each undeclared identifier is reported only once
gps-map.c:696: error: for each function it appears in.)

I suggest you contact the author for help (there's an email form on his homepage)

---

### Post by SevenMachines on 2010-04-22
a 'semi' working version (it looks and runs ok to my untrained eye :) ) can be got by adding
 enum unit {unspecified, imperial, nautical, metric};

to gps-map.c and commenting out the calls to gps_query. these options seem to no longer exist in libgps-dev. but, as [lykeion]("http://ubuntuforums.org/member.php?u=102981") says, the author will know how to fix it up properly

---

### Post by gandhioftherillo on 2010-04-22
Thanks everyone for the input! I sent the author an email yesterday and am awaiting a reply. In the meantime I'll try the 'enum unit {unspecified, imperial, nautical, metric};' workaround and see what happens.

Thanks again

---

### Post by SevenMachines on 2010-04-22
the enum stuff looks fairly harmless, but the gps_query stuff is for getting updates from gpsd by the look of it so commenting it out is going to remove that functionality if nothing else. seems to work after a fashion, cache update from openstreetmaps takes a living age though!

---

### Post by gandhioftherillo on 2010-04-24
> **SevenMachines said:**
> a 'semi' working version (it looks and runs ok to my untrained eye :) ) can be got by adding
 enum unit {unspecified, imperial, nautical, metric};

to gps-map.c and commenting out the calls to gps_query. these options seem to no longer exist in libgps-dev. but, as [lykeion]("http://ubuntuforums.org/member.php?u=102981") says, the author will know how to fix it up properly

Where exactly in gps-map.c should I put the
```
enum unit {unspecified, imperial, nautical, metric};
```
line?

---

### Post by gandhioftherillo on 2010-04-24
From what I can tell (I'll do some more testing before setting this as "Solved") gps_query has been changed to gps_send

It has successfully installed and compiled... I'm about to test it with my GPS and see what happens

Wish me luck!

---

