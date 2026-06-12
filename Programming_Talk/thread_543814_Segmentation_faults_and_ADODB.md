---
title: "Segmentation faults and ADODB"
date: 2007-09-05
forum: Programming Talk
---

### Post by UnfetteredDreaming on 2007-09-05
When using ADODB  to manipulate my postgresql database I'm getting a segmentation fault whenever my php script disconnects from the database. I used this same code in Gentoo and it worked, but in Ubuntu its been rather problematic. Has anyone else encountered this type of problem, and if so what did you do to remedy the situation.

Thanks in advance,
Matt

---

### Post by UnfetteredDreaming on 2007-09-05
I also tried directly connecting to the database through standard php libraries and I get the same error

my code I used to try this was

$DB = pg_connect("host=localhost dbname=testdb user=dbuser password=dbpass");

I still get a segmentation fault when the file ends.

has there been any fix to this?

---

### Post by simmerz on 2008-09-21
I still get this error message with Hardy Heron. Any news on it?

---

