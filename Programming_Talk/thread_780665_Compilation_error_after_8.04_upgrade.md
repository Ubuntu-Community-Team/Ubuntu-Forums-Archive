---
title: "Compilation error after 8.04 upgrade"
date: 2008-05-03
forum: Programming Talk
---

### Post by andymadonna on 2008-05-03
Hi everybody,

I'm somewhat new to C++. I just upgraded to Ubuntu 8.04 from 7.10 and now I am getting this weird compilation error. I am guessing a newer version of g++ is included in 8.04 that looks for this error? It compiled when I had 7.04

I have been using this c library in c++ code and has worked fine until now

```
utils.c: In function ‘char* basename(const char*)’:
utils.c:108: error: declaration of ‘char* basename(const char*)’ throws different exceptions
utils.h:159: error: from previous declaration ‘char* basename(const char*) throw ()’
```

Here is the declaration in utils.h:

```
extern char* basename( const char* pathname );
```

and heres the function in utils.c:

```
char* basename( const char* pathname )
{
  char* base, * last_slash;

  last_slash = strrchr( pathname, '/' );
  if( ! last_slash )
    {
      base = (char*) calloc( strlen( pathname ) + 1, sizeof( char ) );
      strcpy( base, pathname );
    }
  else
    {
      base = (char*) calloc( strlen( last_slash++ ), sizeof( char ) );
      strcpy( base, last_slash );
    }

  return base;
}
```

Can anyone can help me understand what this error means and what I need to do?

Thank you

---

### Post by andymadonna on 2008-05-03
Apparently there is a similar function called basename in UNIX system's, maybe that includes linux. I just renamed my function to ubasename() and there is no error.

---

