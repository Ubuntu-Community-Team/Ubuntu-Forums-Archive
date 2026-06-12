---
title: "how to clear 'stdin' and 'stdout' buffers?"
date: 2011-09-15
forum: Programming Talk
---

### Post by avee137 on 2011-09-15
Hello,

i have tried using rewind() and fflush() for clearing the stdin buffer in my code but its not giving the desired result? is there any other way to do that.

Thanks.

---

### Post by dwhitney67 on 2011-09-15
You can look at this post to get some ideas on how to flush stdin: [http://ubuntuforums.org/showpost.php?p=11252133&postcount=7](http://ubuntuforums.org/showpost.php?p=11252133&postcount=7)

The only thing missing however is to check for an EOF condition (say for instance, the user inputs ctrl-d).

---

### Post by nvteighen on 2011-09-15
Oh my goodness... Why don't people use the search engine... neither read the forums' first page, where a similar thread is already going on?

---

### Post by karlson on 2011-09-15
> **nvteighen said:**
> Oh my goodness... Why don't people use the search engine... neither read the forums' first page, where a similar thread is already going on?

'cuz asking a question in an anonymous forum is much easier psychologically then solving a problem yourself.  Responsibility for the solution isn't yours in this case.

---

