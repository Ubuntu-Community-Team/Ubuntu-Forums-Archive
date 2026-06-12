---
title: "Snort - failed to load snort_dynamicrules"
date: 2012-09-18
forum: New to Ubuntu
---

### Post by termvrl on 2012-09-18
Hi All,
Good Day!

i have installed snort 2.9.3.1 on Ubuntu 12.04 64bit. 
i follow this guide: [http://www.snort.org/assets/158/snortinstallguide293.pdf](http://www.snort.org/assets/158/snortinstallguide293.pdf)

my problem is i failed to load snort_dynamicrules
ERROR: Failed to load /usr/local/snort/lib/snort_dynamicrules/imap.so: /usr/local/snort/lib/snort_dynamicrules/imap.so: wrong ELF class: ELFCLASS32
Fatal Error, Quitting..

i'm googled, and this error may occur because of compatible issue on dynamicrules (32bit version) and OS (64bit). 

i need help to solve this. 
Thank you!

---

### Post by termvrl on 2012-09-19
Hi All.

after i read more, i found that the cause of the error is on the type of rules im using.
because of im using a 64bit of ubuntu 12.04, i need to have dynamicrules for 64bit too. so in the snort.conf, i point the rules to the the 64bit rules, which is locate at */so_rules/precompiled/Ubuntu-10-4/x86-64/2.9.3.1 [ at * whrere you extract the rules file ]. =D

its took me two days to figure it out. lol

---

