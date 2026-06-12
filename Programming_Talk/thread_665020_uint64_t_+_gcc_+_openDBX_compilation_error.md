---
title: "uint64_t + gcc + openDBX compilation error"
date: 2008-01-11
forum: Programming Talk
---

### Post by Crapodino on 2008-01-11
Hi everybody. First, sorry for my english, i am argentinian.

I am trying to use a c library called openDBX that helps us talk to different RDBMS. Here is the link: [http://www.linuxnetworks.de/doc/index.php/OpenDBX](http://www.linuxnetworks.de/doc/index.php/OpenDBX)

I have already compiled and installed. Now, i am trying a simple c programe that uses it. The problem is that when i tried to compile this program, i have en compile error in a header i need to include of openDBX. 

Mi c program (Prueba.c) is this:

```
#include <stdio.h>
#include <stdlib.h>
#include <odbx.h>

int main(void) {
	puts("Hello World!!");
	return EXIT_SUCCESS;
}

```

The file odbx is the one i need to use. See that the problems occurs during compilation, even if i don't use it. This file (odbx.h) is in /usr/local/include. I undestand that this directory is standard so i don't need to pass any parametres to gcc. don't i ?

The error is this:

In file included from Prueba.c:3:
/usr/local/include/odbx.h:206: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘odbx_rows_affected’


If i open de odbx, the line 206 is like this:

uint64_t odbx_rows_affected( odbx_result_t* result );


The uint64_t is only used there. I think there is the problem. I see that odbx.h includes the stdint, in this way:
#ifdef HAVE_STDINT_H
#include <stdint.h>

Can i have a problem with this and the gcc ??? do you need some other information so that to help me ?

I am using gcc version 4.1.3 and ubuntu gutsy gibbon.

very thanks

mariano

---

### Post by hod139 on 2008-01-12
Are you sure you installed gcc correctly?
```

sudo apt-get install build-essential

```

This will install gcc and the standard libraries.

---

