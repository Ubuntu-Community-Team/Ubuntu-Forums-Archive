---
title: "How Can I make a POSIX/C regex non-greedy?"
date: 2012-03-07
forum: Programming Talk
---

### Post by ItecKid on 2012-03-07
So I have a code where I am trying to extract a part of a url, the part between the http:// and the first /.  Like this:

```


#include <stdio.h>
#include <stdlib.h>
#include <sys/types.h>
#include <string.h>
#include <regex.h>

int main (int argc, char **argv)
{
        regex_t regex;
        int reti;
        char msgbuf[100];
        size_t nmatch = 2;
        regmatch_t pmatch[2];

        /* Match everything between http:// and
         * the first / */
        reti = regcomp (&regex, "http://\\([^/]*\\)/", 0);
        if (reti) {
                fprintf (stderr, "Failed to compile regular expression");
                exit (EXIT_FAILURE);
        }
        reti = regexec (&regex, argv[1], nmatch, pmatch, 0);

        char *match = strndup(argv[1]+pmatch[1].rm_so, pmatch[1].rm_eo);

        printf ("%s\n", match);

        return 0;
}

```

Assume the argv[1] is something like [http://www.google.com/stuff](http://www.google.com/stuff).  I am trying to match only the [www.google.com](www.google.com) part.  Even with the [^/] in there, it still matches everything.  (i.e, [www.google.com/stuff](www.google.com/stuff))  I appreciate any help anyone can provide.

---

### Post by Arndt on 2012-03-08
> **ItecKid said:**
> So I have a code where I am trying to extract a part of a url, the part between the http:// and the first /.  Like this:

```


#include <stdio.h>
#include <stdlib.h>
#include <sys/types.h>
#include <string.h>
#include <regex.h>

int main (int argc, char **argv)
{
        regex_t regex;
        int reti;
        char msgbuf[100];
        size_t nmatch = 2;
        regmatch_t pmatch[2];

        /* Match everything between http:// and
         * the first / */
        reti = regcomp (&regex, "http://\\([^/]*\\)/", 0);
        if (reti) {
                fprintf (stderr, "Failed to compile regular expression");
                exit (EXIT_FAILURE);
        }
        reti = regexec (&regex, argv[1], nmatch, pmatch, 0);

        char *match = strndup(argv[1]+pmatch[1].rm_so, pmatch[1].rm_eo);

        printf ("%s\n", match);

        return 0;
}

```

Assume the argv[1] is something like [http://www.google.com/stuff](http://www.google.com/stuff).  I am trying to match only the [www.google.com](www.google.com) part.  Even with the [^/] in there, it still matches everything.  (i.e, [www.google.com/stuff](www.google.com/stuff))  I appreciate any help anyone can provide.

"so" and "eo" sound like they could mean "start offset" and "end offset". You use "so" that way, but you use "eo" as if it was a count.

---

### Post by ve4cib on 2012-03-08
Have you tried using "?" to make the selection lazy?

```

reti = regcomp (&regex, "http://\\([^/]*?\\)/", 0);

```

I've never worked with regexes in C, but in other languages that works.

---

### Post by ItecKid on 2012-03-08
> **ve4cib said:**
> Have you tried using "?" to make the selection lazy?

```

reti = regcomp (&regex, "http://\\([^/]*?\\)/", 0);

```

I've never worked with regexes in C, but in other languages that works.

Yeah, the ? only works for Perl-based regexp, not for POSIX...

---

