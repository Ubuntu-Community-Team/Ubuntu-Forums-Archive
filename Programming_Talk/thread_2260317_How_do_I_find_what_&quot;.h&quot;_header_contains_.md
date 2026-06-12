---
title: "How do I find what &quot;.h&quot; header contains what functions I need, please?"
date: 2015-01-10
forum: Programming Talk
---

### Post by macbreak on 2015-01-10
[SIZE=3]First off, **HAPPY NEW YEAR TO YOU ALL, AND MAY GOD BLESS YOU RICHLY IN 2015 AND ETERNALLY!** [/SIZE]:D

Okay. I have learnt that I am better off learning C/C++ on a clunky, 12 year old laptop with an intentional lack of internet access (not this PC), due to the constant temptation of being distracted by all things internet. To be concise, what I need to know, is how does one find out what ".h" header file one needs to include to provide specific functionality? Is there some easy command you can type to tell you what include is needed? As an example - last night I needed "usleep", but I could not recall which header it was that furnished me with this functionality, and had to Google it. What I am basically saying is that I need to FORCE myself to read "man" pages and learn things from typing commands, rather than relying on the mighty Google (which is like standing in a room full of 10,000 people, asking a question, and receiving 10,000 differing "answers").

I thank you, anticipating a clever and concise solution... hopefully :)

Cheerio.

---

### Post by steeldriver on 2015-01-10
You could try the online man pages

```

$ man usleep

USLEEP(3)                 Linux Programmer's Manual                 USLEEP(3)

NAME
       usleep - suspend execution for microsecond intervals

SYNOPSIS
[COLOR=#0000ff][B]       #include <unistd.h>
[/B][/COLOR]
       int usleep(useconds_t usec);

   Feature Test Macro Requirements for glibc (see feature_test_macros(7)):

```

In cases of ambiguity (for example where there's a user command of the same name) you can specify the particular manual section that covers programming i.e. instead of

```

$ man printf

PRINTF(1)                       User Commands                       PRINTF(1)

NAME
       printf - format and print data

SYNOPSIS
       printf FORMAT [ARGUMENT]...
       printf OPTION

DESCRIPTION
       Print ARGUMENT(s) according to FORMAT, or execute according to OPTION:

```
do
```

$ man [COLOR=#0000ff]**3**[/COLOR] printf

PRINTF(3)                 Linux Programmer's Manual                 PRINTF(3)

NAME
       printf,  fprintf,  sprintf,  snprintf,  vprintf,  vfprintf,  vsprintf,
       vsnprintf - formatted output conversion

SYNOPSIS
[COLOR=#0000ff][B]       #include <stdio.h>
[/B][/COLOR]
       int printf(const char *format, ...);
       int fprintf(FILE *stream, const char *format, ...);

```

---

### Post by macbreak on 2015-01-10
> **steeldriver said:**
> You could try the online man pages

```

$ man usleep

USLEEP(3)                 Linux Programmer's Manual                 USLEEP(3)

NAME
       usleep - suspend execution for microsecond intervals

SYNOPSIS
[COLOR=#0000ff][B]       #include <unistd.h>
[/B][/COLOR]
       int usleep(useconds_t usec);

   Feature Test Macro Requirements for glibc (see feature_test_macros(7)):

```

In cases of ambiguity (for example where there's a user command of the same name) you can specify the particular manual section that covers programming i.e. instead of

```

$ man printf

PRINTF(1)                       User Commands                       PRINTF(1)

NAME
       printf - format and print data

SYNOPSIS
       printf FORMAT [ARGUMENT]...
       printf OPTION

DESCRIPTION
       Print ARGUMENT(s) according to FORMAT, or execute according to OPTION:

```
do
```

$ man [COLOR=#0000ff]**3**[/COLOR] printf

PRINTF(3)                 Linux Programmer's Manual                 PRINTF(3)

NAME
       printf,  fprintf,  sprintf,  snprintf,  vprintf,  vfprintf,  vsprintf,
       vsnprintf - formatted output conversion

SYNOPSIS
[COLOR=#0000ff][B]       #include <stdio.h>
[/B][/COLOR]
       int printf(const char *format, ...);
       int fprintf(FILE *stream, const char *format, ...);

```


Perfect! Just what I wanted, thank you. I am well versed with man pages; I'd thought of trying "man <command>" but I thought that the man pages were reserved for system software etc, and not for coding and headers. Much, much appreciated - thank you. Take care, God bless you.

---

