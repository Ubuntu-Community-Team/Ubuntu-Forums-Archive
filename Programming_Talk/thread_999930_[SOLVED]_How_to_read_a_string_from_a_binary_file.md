---
title: "[SOLVED] How to read a string from a binary file?"
date: 2008-12-02
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-12-02
How? I always get some garbage instead of any characters.

I write the string like this:
```

char string[200] = "hello";
fwrite( &string, sizeof(char), 200, savefile );

```

And I read it like this:
```

char string[200];
fread(&string, sizeof(char), 200, fp);

```

Result when reading: &#65533;&#65533;&#65533;

What's the problem? Probably very simple and noob thing I forgot.

---

### Post by geirha on 2008-12-02
Pass string to fread/fwrite with &string[0] or just string (which is equivalent). You are passing address-of address-of the first char in the array.

---

### Post by crazyfuturamanoob on 2008-12-03
> **geirha said:**
> Pass string to fread/fwrite with &string[0] or just string (which is equivalent). You are passing address-of address-of the first char in the array.

Doesn't work, I tried both "&string[0]" and "string". Could you post me an example?

Edit: The string I was trying to write/read wasn't valid, when I print it, I get those question marks.

Edit2: What does fread return if can't read anything? Like if it reaches EOF? And what normally when it succeeds reading something?

---

### Post by geirha on 2008-12-03
```

#include <stdio.h>
#include <string.h>

int main(void)
{
    FILE *f;
    char outstr[200]= "Hello\n";
    char instr[200]= "";

    f= fopen("/tmp/foo.dat", "w");
    fwrite(outstr, sizeof(char), strlen(outstr), f);
    fclose(f);

    f= fopen("/tmp/foo.dat", "r");
    fread(instr, sizeof(char), 199, f);
    fclose(f);

    printf(outstr);
    printf(instr);

    return 0;
}

```

---

