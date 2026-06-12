---
title: "How do I remove lines that have more than a given number of characters?"
date: 2009-06-27
forum: Programming Talk
---

### Post by PryGuy on 2009-06-27
Good day everyone!
Well, I configure Squid and I have Access Control Lists to block bad sites. During start/restart Squid warns me this way:> 2009/06/27 21:16:29| WARNING: '.hardcor.spb.ru' is a subdomain of '.spb.ru'
2009/06/27 21:16:29| WARNING: because of this '.hardcor.spb.ru' is ignored to keep splay tree searching predictable
I can't manually correct it 'cause the warning list is too big. Yet I plan to schedule the blacklist download and parse it antomatically using sed or something.

I think I found a solution, One has to remove lines that have more than two dots in their names. The question is how do I do it? Thank you in advance!

---

### Post by soltanis on 2009-06-27
Which one do you want to do, remove lines with more than two dots in them or remove lines over a certain length?

Either can be accomplished by piping into an awk one-liner.
My lack of sufficient awk experience leads me to give you these perl one-liners, however;

Remove lines with more than two dots:

```

perl -ne 'print unless s/\././g > 2'

```

Remove lines with more than 80 chars:

```

perl -ne 'print unless length > 80'

```

---

### Post by PryGuy on 2009-06-27
> **soltanis said:**
> Which one do you want to do, remove lines with more than two dots in them or remove lines over a certain length?A first case. Thank you so much!!! But I stumbled upon another thing: what if domain is named '.someverybadpornsite.co.uk'? :(

---

### Post by soltanis on 2009-06-27
If you are trying to filter domains based on regular expression patterns, you can do that with perl too. If you want to filter the word porn out of a file, the following command

```

perl -ne 'print unless /porn/i' < file > new_file

```

Would filter all the lines with the word "porn" in them out, then write the results to new_file.

---

### Post by ghostdog74 on 2009-06-27
```

awk '
{ 
  f=0
  for(i=1;i<=NF;i++){
    o=$i
    b=gsub(/\./,"",o)    
    if (b>2){
        f=1
        break
    }
  }
}
!f && length <=80 ' file

```

---

### Post by soltanis on 2009-06-27
....and there's the awk.

---

### Post by PryGuy on 2009-06-28
Thanks, buddies!

---

