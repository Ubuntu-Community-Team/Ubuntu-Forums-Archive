---
title: "Problems With SQLite"
date: 2012-11-30
forum: Programming Talk
---

### Post by MTariq on 2012-11-30
I am trying to compile a project that includes wxWidgets and SQLite3 on CodeBlocks.
Now the problem is on compilation C:B says

Undefined Reference to "sqlite3_open()"
...
and so on.
Google told me that I should add -lsqlite3 to the linker options in build options of project so I did and the resulting string was

`wx-config  sqlite3 --libs`

but now the linker is saying

cannot find -lwx_gtk2u_sqlite3-2.8

Please Help...

---

### Post by bouncingwilf on 2012-12-01
Sorry but not sure exactly what you require as your description is limited and I have no experience of using wxWidgets but:

It looks like you've failed to include the sqlite headers in your code i.e.

#include<sqlite3.h>

failing that; I would ensure that you use the -lsqlite3 flag when you compile.


Bouncingwilf

---

### Post by MTariq on 2012-12-01
Ahan!
Failing that would certainly result in:

Undefined/Undeclared function sqlite3_open();
or so on. But that is not the case. I have included sqlite3.h

What I think that this might be my mistake of supplying the wrong command line arguments   to the linker, Or I may not even have the sqlite3 lib installed at all. How can I check Whether I even have the library or not?
I have searched in /usr/lib/  for string sql but found nothing.

---

### Post by MTariq on 2012-12-01
Done :-)

I just tried the command 'wx-config --libs' on the terminal which returned this

-L/usr/lib/i386-linux-gnu -pthread -L/usr/lib/i386-linux-gnu -lwx_gtk2u_richtext-2.8 -lwx_gtk2u_aui-2.8 -lwx_gtk2u_xrc-2.8 -lwx_gtk2u_qa-2.8 -lwx_gtk2u_html-2.8 -lwx_gtk2u_adv-2.8 -lwx_gtk2u_core-2.8 -lwx_baseu_xml-2.8 -lwx_baseu_net-2.8 -lwx_baseu-2.8 

so I copied the whole text added '-lsqlite3' at the begining and paste it in linker options. After that all goes well.... :->
Thanks a lot.....

---

