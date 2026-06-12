---
title: "Calling Scripts C++"
date: 2011-07-05
forum: Programming Talk
---

### Post by conradin on 2011-07-05
Hi all, 
based on a recent query which has piqued my interest, is there any way to
call a bash script from a C++ program besides using the system call?

I googled it and saw nothing useful....

---

### Post by in-dust-rial on 2011-07-05
cant you stream into devices directly?
is there a shell device?

just an idea.


maybe this helps - was too confusing to me xD
???
[http://www.digipedia.pl/man/doc/view/ost_TTYStream.3/](http://www.digipedia.pl/man/doc/view/ost_TTYStream.3/)
???

---

### Post by conradin on 2011-07-05
Yeah! I forgot about that! Im not sure how to implement it though. 
I'd love a tutorial if someone can find and easy one.

---

### Post by in-dust-rial on 2011-07-05
this was interesting...
[http://stackoverflow.com/questions/5072058/how-to-convert-bash-script-to-c-using-boostiostreams](http://stackoverflow.com/questions/5072058/how-to-convert-bash-script-to-c-using-boostiostreams)

basically you can just send it to /bin/bash.
hence you only need to find a tutorial that is verbous on how to send things to 'special' locations...

but when I started to search further 
...
I praised the SYSTEM command :P

---

