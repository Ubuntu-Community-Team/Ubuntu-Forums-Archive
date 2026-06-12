---
title: "[c++] Problem with memcpy"
date: 2007-01-29
forum: Programming Talk
---

### Post by jion on 2007-01-29
Hi!.

Before nothing, sorry my bad english.

I have a problem with a memcpy. I can't port a SDL game make in windows with mingw to linux with gcc. The error is not in SDL library, but in a function that use memcpy.
The game is a tetris, and the function that not work is the function in charge of remove full lines of  tetris.

This is the function:

**data** is an array of 20x10 Uint8 that it represents the board.

```

void tablero::borrarlineas()
{
    Uint8* ttemp = (Uint8*)&data;
    Uint8 i, j;

    memcpy(ttemp, data, sizeof(data));
    for(i=0; i < 20;i++)
        if(lines[i])
        {
            memcpy(ttemp+10, ttemp, sizeof(Uint8)*(10*i));
            lines[i] = false;
        }

}

```

This function work perfectly in windows, but in linux clear  completely the board :( . What is the problem?:S

---

### Post by goatflyer on 2007-01-29
According to 'man memcpy'...

> 
DESCRIPTION
       The  memcpy()  function  copies  n bytes from memory area src to memory
       area dest.  The memory areas should not overlap.  Use memmove(3) if the
       memory areas do overlap.



Reading your code, I see the memory areas definitely overlap.
The logic of your program seems to depend on which bytes are copied first:

Compare this:
```

void memcpy(char *dest, char *src, int cnt)
{
  while(cnt--)
    *dest++ = *src++;
}

```
...with this...
```

void memcpy(char *dest, char *src, int cnt)
{
  while(cnt--)
    dest[cnt] = src[cnt];
}

```

Both copy the block, but in different order.  ANSI C memcpy does not guarantee which direction the transfer happens.

---

### Post by Auria on 2007-01-29
Hi

what type is data? if it is a class, AFAiK it's a bad idea to use memcpy on it, copy constructors are AFAK a better way.

---

### Post by Lux Perpetua on 2007-01-29
> **goatflyer said:**
> According to 'man memcpy'...



Reading your code, I see the memory areas definitely overlap.
The logic of your program seems to depend on which bytes are copied first:

Compare this:
```

void memcpy(char *dest, char *src, int cnt)
{
  while(cnt--)
    *dest++ = *src++;
}

```
...with this...
```

void memcpy(char *dest, char *src, int cnt)
{
  while(cnt--)
    dest[cnt] = src[cnt];
}

```

Both copy the block, but in different order.  ANSI C memcpy does not guarantee which direction the transfer happens.
...and the solution would be to use **memmove** instead of memcpy.

---

### Post by jion on 2007-01-30
Thanks! memmove work fine!

---

