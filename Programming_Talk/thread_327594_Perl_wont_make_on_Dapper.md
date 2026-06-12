---
title: "Perl wont make on Dapper"
date: 2006-12-29
forum: Programming Talk
---

### Post by elf_sprog on 2006-12-29
Hi,

I just switched over to Ubuntu 6.0.6 from fedora 6. I did a server install, and when I enter perl -MCPAN -e shell Perl loads fine. When i type the o conf stuff at the perl prompt to delete old files that works too.

Then the trouble starts.

When I try to 

> install Bundle::CPAN 

Perl goes to the urls I listed in the set up, and downloads the files. But it will not Make!

Am i missing something here? I installed pmake, and make, and gcc, dunno if that is needed..

Has anyone else had this problem?

Any help mucho appreciated!

Ubuntu rocks!

---

### Post by elf_sprog on 2006-12-29
i have it making now, but it will not install Compress::ZLIB. 

Has anyone experianced this?

---

### Post by slavik on 2006-12-29
can't you install the packages for the modules?

---

### Post by elf_sprog on 2006-12-29
Probably, but im trying to get slash running, so I need a good solid perl working. I think ive found a workaround. :)

Thanks!

---

