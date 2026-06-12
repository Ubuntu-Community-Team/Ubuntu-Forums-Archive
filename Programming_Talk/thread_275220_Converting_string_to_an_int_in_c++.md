---
title: "Converting string to an int in c++"
date: 2006-10-11
forum: Programming Talk
---

### Post by thenetduck on 2006-10-11
Hi, 
  I can seem to get this done. The code, 
 
```

int store;
store = string.atoi("555"); 

```

Will work just fine, however when I do something like this, it will not work. Gives me an error saying that Error: cannot convert std::string to 'const char* for argument 1' to 'int atoi(const char*)'

```

string thing = "555";
int store;
store = atoi(thing);


```


Any help is wanted and useful thanks,

 The Net Duck

---

### Post by amo-ej1 on 2006-10-11
atoi is a C function (see man atoi)

```

ATOI(3)                    Linux Programmer’s Manual                   ATOI(3)

NAME
       atoi, atol, atoll, atoq - convert a string to an integer

SYNOPSIS
       #include <stdlib.h>

       int atoi(const char *nptr);
       long atol(const char *nptr);
       long long atoll(const char *nptr);
       long long atoq(const char *nptr);

```

So you're passing a std::string as a const char *. Both are obviously not the same. But it is very easy to get a char * out of a std::string. 

So
```

string foo = "123";
int i = atoi(foo.c_str());

```
will do the trick. 

(The advised way to do this in C++ is to pull this through a stringstream. This is explained in [http://www.ubuntuforums.org/showthread.php?t=271738&highlight=stringstream](http://www.ubuntuforums.org/showthread.php?t=271738&highlight=stringstream)
)

---

### Post by thenetduck on 2006-10-11
Wow this was very helpful, thank you so much : ) 

 The Net Duck

---

### Post by soilland on 2008-03-20
Thank you very much! this helped me too :)

---

