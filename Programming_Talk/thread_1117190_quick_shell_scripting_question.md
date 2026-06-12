---
title: "quick shell scripting question"
date: 2009-04-05
forum: Programming Talk
---

### Post by cmay on 2009-04-05
hi.
i read in one of my books that a shellscript should be for security reasons ended whit an - 
like example ```
#! /bin/bash - 
```  and i want to know if it is right and if so how about when you write python or perl scripts. should they be written as ```
#! /usr/bin/perl - 
``` or in python ```
#! /usr/bin/env python - 
```the book i refere to is classical shell scripting .
its a book from o.reily publising. 

thanks for any information on the subject.

---

### Post by jimi_hendrix on 2009-04-05
no, you would only do that for bash.  it just logs you in differently, for more info check man bash

---

### Post by cmay on 2009-04-05
thanks. 
i just wondered since i know you can pass options to perl like #! usr/bin/perl -w 
so it could be that you also had to do that for other kinds of shellscript languages but i never seen or heard of it before today when i started reading this book.

---

