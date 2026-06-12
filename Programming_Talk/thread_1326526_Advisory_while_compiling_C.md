---
title: "Advisory while compiling C"
date: 2009-11-14
forum: Programming Talk
---

### Post by PostChache on 2009-11-14
I have just started learning C and whenever I compile a program it gives me a bunch of advice on it. It runs fine though, also when my friend compiles the same program it doesn't tell him anything. 

This is what it's telling me:
```

/home/cha-che/Documentos/Studies/Working_On/C_Primer_Plus/Exercise/Chapter_4/5.c: En la función ‘main’:
/home/cha-che/Documentos/Studies/Working_On/C_Primer_Plus/Exercise/Chapter_4/5.c:13: aviso: anchura de campo debe ser de tipo ‘int’, pero el argumento 2 es de tipo ‘size_t’
/home/cha-che/Documentos/Studies/Working_On/C_Primer_Plus/Exercise/Chapter_4/5.c:13: aviso: el formato ‘%*d’ espera el tipo ‘int’, pero el argumento 3 es de tipo ‘size_t’
/home/cha-che/Documentos/Studies/Working_On/C_Primer_Plus/Exercise/Chapter_4/5.c:13: aviso: anchura de campo debe ser de tipo ‘int’, pero el argumento 4 es de tipo ‘size_t’
/home/cha-che/Documentos/Studies/Working_On/C_Primer_Plus/Exercise/Chapter_4/5.c:13: aviso: el formato ‘%*d’ espera el tipo ‘int’, pero el argumento 5 es de tipo ‘size_t’
/home/cha-che/Documentos/Studies/Working_On/C_Primer_Plus/Exercise/Chapter_4/5.c:15: aviso: anchura de campo debe ser de tipo ‘int’, pero el argumento 2 es de tipo ‘size_t’
/home/cha-che/Documentos/Studies/Working_On/C_Primer_Plus/Exercise/Chapter_4/5.c:15: aviso: el formato ‘%*d’ espera el tipo ‘int’, pero el argumento 3 es de tipo ‘size_t’
/home/cha-che/Documentos/Studies/Working_On/C_Primer_Plus/Exercise/Chapter_4/5.c:15: aviso: anchura de campo debe ser de tipo ‘int’, pero el argumento 4 es de tipo ‘size_t’
/home/cha-che/Documentos/Studies/Working_On/C_Primer_Plus/Exercise/Chapter_4/5.c:15: aviso: el formato ‘%*d’ espera el tipo ‘int’, pero el argumento 5 es de tipo ‘size_t’

```

And this is my code:
```

#include <stdio.h>
#include <string.h>

int main(void)
{
    char firstname[25], lastname[25];

    printf("Please enter your first name\n");
    scanf("%s", firstname);
    printf("Please enter your last name\n");
    scanf("%s", lastname);
    printf("%s %s\n", firstname, lastname);
    printf("%*d %*d\n", strlen(firstname), strlen(firstname), strlen(lastname), strlen(lastname));
    printf("%s %s\n", firstname, lastname);
    printf("%*d %*d\n", -strlen(firstname), strlen(firstname), -strlen(lastname), strlen(lastname));
    
    return 0;
}

```

I'm really just curious on why it will compile correctly for my friend but not me. The only difference between our systems is that he uses 9.10 and I use 9.04

---

### Post by Arndt on 2009-11-14
> **PostChache said:**
> I have just started learning C and whenever I compile a program it gives me a bunch of advice on it. It runs fine though, also when my friend compiles the same program it doesn't tell him anything. 

This is what it's telling me:
```

/home/cha-che/Documentos/Studies/Working_On/C_Primer_Plus/Exercise/Chapter_4/5.c: En la función ‘main’:
/home/cha-che/Documentos/Studies/Working_On/C_Primer_Plus/Exercise/Chapter_4/5.c:13: aviso: anchura de campo debe ser de tipo ‘int’, pero el argumento 2 es de tipo ‘size_t’
/home/cha-che/Documentos/Studies/Working_On/C_Primer_Plus/Exercise/Chapter_4/5.c:13: aviso: el formato ‘%*d’ espera el tipo ‘int’, pero el argumento 3 es de tipo ‘size_t’
/home/cha-che/Documentos/Studies/Working_On/C_Primer_Plus/Exercise/Chapter_4/5.c:13: aviso: anchura de campo debe ser de tipo ‘int’, pero el argumento 4 es de tipo ‘size_t’
/home/cha-che/Documentos/Studies/Working_On/C_Primer_Plus/Exercise/Chapter_4/5.c:13: aviso: el formato ‘%*d’ espera el tipo ‘int’, pero el argumento 5 es de tipo ‘size_t’
/home/cha-che/Documentos/Studies/Working_On/C_Primer_Plus/Exercise/Chapter_4/5.c:15: aviso: anchura de campo debe ser de tipo ‘int’, pero el argumento 2 es de tipo ‘size_t’
/home/cha-che/Documentos/Studies/Working_On/C_Primer_Plus/Exercise/Chapter_4/5.c:15: aviso: el formato ‘%*d’ espera el tipo ‘int’, pero el argumento 3 es de tipo ‘size_t’
/home/cha-che/Documentos/Studies/Working_On/C_Primer_Plus/Exercise/Chapter_4/5.c:15: aviso: anchura de campo debe ser de tipo ‘int’, pero el argumento 4 es de tipo ‘size_t’
/home/cha-che/Documentos/Studies/Working_On/C_Primer_Plus/Exercise/Chapter_4/5.c:15: aviso: el formato ‘%*d’ espera el tipo ‘int’, pero el argumento 5 es de tipo ‘size_t’

```

And this is my code:
```

#include <stdio.h>
#include <string.h>

int main(void)
{
    char firstname[25], lastname[25];

    printf("Please enter your first name\n");
    scanf("%s", firstname);
    printf("Please enter your last name\n");
    scanf("%s", lastname);
    printf("%s %s\n", firstname, lastname);
    printf("%*d %*d\n", strlen(firstname), strlen(firstname), strlen(lastname), strlen(lastname));
    printf("%s %s\n", firstname, lastname);
    printf("%*d %*d\n", -strlen(firstname), strlen(firstname), -strlen(lastname), strlen(lastname));
    
    return 0;
}

```

I'm really just curious on why it will compile correctly for my friend but not me. The only difference between our systems is that he uses 9.10 and I use 9.04

Do you use exactly the same compiler options? Maybe they chose to make some warnings less visible in 9.10. You can see the version of gcc by doing "gcc -v". I have 4.3.3, in 9.04.

"Aviso" in Spanish seems to be what is called "warning" in English, by the way. You can turn on most warnings (it's a good idea) by compiling with -Wall.

---

### Post by PostChache on 2009-11-14
> **Arndt said:**
> Do you use exactly the same compiler options? Maybe they chose to make some warnings less visible in 9.10. You can see the version of gcc by doing "gcc -v". I have 4.3.3, in 9.04.

"Aviso" in Spanish seems to be what is called "warning" in English, by the way. You can turn on most warnings (it's a good idea) by compiling with -Wall.

I have 4.3.3 and so does my friend as well, what is -wall I'm not familair with these things so sorry about the questions xD
Also my friend is using 9.04 as well, I thought he was using 9.10 but he isn't.

---

### Post by GeneralZod on 2009-11-14
Flick through some of the comments here:

[http://bytes.com/topic/c/answers/221867-portable-way-printf-size_t-instance#post903390](http://bytes.com/topic/c/answers/221867-portable-way-printf-size_t-instance#post903390)

It seems that

[http://bytes.com/topic/c/answers/221867-portable-way-printf-size_t-instance#post903390](http://bytes.com/topic/c/answers/221867-portable-way-printf-size_t-instance#post903390)

is the most broadly portable way of getting rid of the warnings.

Are you and your friend both using 32 or 64-bit, BTW?

---

### Post by PostChache on 2009-11-14
> **GeneralZod said:**
> Flick through some of the comments here:

[http://bytes.com/topic/c/answers/221867-portable-way-printf-size_t-instance#post903390](http://bytes.com/topic/c/answers/221867-portable-way-printf-size_t-instance#post903390)

It seems that

[http://bytes.com/topic/c/answers/221867-portable-way-printf-size_t-instance#post903390](http://bytes.com/topic/c/answers/221867-portable-way-printf-size_t-instance#post903390)

is the most broadly portable way of getting rid of the warnings.

Are you and your friend both using 32 or 64-bit, BTW?
I use 64 bit he uses 32 bit

---

### Post by Arndt on 2009-11-14
> **PostChache said:**
> I use 64 bit he uses 32 bit

I think that explains it. int and size_t are the same size on one of your machines, but not on the other. You can check what sizeof(int) and sizeof(size_t) are, respectively. It's of course recommended not to depend on them to be the same.

In your format directive, it's probably better to use %l than %d.

---

### Post by movieman on 2009-11-14
> **PostChache said:**
> I use 64 bit he uses 32 bit

My guess is that strlen returns a size_t, which is probably a long rather than an int in 64-bit.

---

