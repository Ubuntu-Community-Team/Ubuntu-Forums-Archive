---
title: "POSIX character classes in regexps"
date: 2006-06-07
forum: Programming Talk
---

### Post by Arndt on 2006-06-07
I have an application where I need this regexp fragment to work:

\p{IsBasicLatin}

As far as I can tell, POSIX regexps should support this.

However, my test C program, which uses regcomp and regexec, does not recognize this as valid. It says "Invalid content of \{\}". It does recognize \p{L}, but I don't know whether that's equivalent, and I don't have full control of the form of the regexp anyway.

In various places I looked, there is talk about locales. Is there a particular locale I need to install to get this to work, and if so, which? Or does this simply not work in Debian?

By the way, I do have the library with regcomp and regexec, but the manual pages are missing. In what package can they be found?

My C program is so small, so I include it here:

```
#include <regex.h>
#include <stdlib.h>
#include <stdio.h>

int main(int argc, char **argv)
{
  char buf[80];
  char *exp = argv[1];
  regex_t exp_c;
  int s;

  if (argc != 2) {
    fprintf(stderr, "Usage: regexp pattern\n");
    exit(1);
  }

  s = regcomp(&exp_c, exp, REG_EXTENDED);

  if (s != 0) {
    regerror(s, &exp_c, buf, sizeof(buf));
    printf("error (%s)\n", buf);
    exit(1);
  }

  for (;;) {
    gets(buf);
    if (feof(stdin))
      break;
    s = regexec(&exp_c, buf, 0, NULL, 0);
    printf("s = %d\n", s);
  }

  return 0;

}

```

---

### Post by LordHunter317 on 2006-06-07
[QUOTE=Arndt]I have an application where I need this regexp fragment to work:

\p{IsBasicLatin}

As far as I can tell, POSIX regexps should support this.[/quote]POSIX regexs don't support \p at all.  If it's being supported on your platform, it's because GNU loves "embrace and extend" as much as MS.  I can ensure you that it's certainly not portable.

Switch to PCRE.

> By the way, I do have the library with regcomp and regexec, but the manual pages are missing. In what package can they be found?manpages-dev

---

### Post by Arndt on 2006-06-08
[QUOTE=LordHunter317]POSIX regexs don't support \p at all.  If it's being supported on your platform, it's because GNU loves "embrace and extend" as much as MS.  I can ensure you that it's certainly not portable.

Switch to PCRE.

manpages-dev[/QUOTE]

Thanks!

---

