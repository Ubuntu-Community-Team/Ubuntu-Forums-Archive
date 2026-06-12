---
title: "Super Easy Beginner's Programming Challenge"
date: 2009-06-21
forum: Programming Talk
---

### Post by jinksys on 2009-06-21
**Challenge:** Write a hexadecimal to decimal converter.

The user should be able to type in a hexadecimal number in 0x format, ie) 0xFF, and be shown the decimal equivalent.

Use whatever language you want.

Non-beginners, I know it is possible to accomplish this task in two lines of C, but this is for beginners so let's see if they can figure it out.  

Have fun and good luck!

---

### Post by Grissess on 2009-06-21
How about Python? Single line:

```
print int(raw_input('Enter hex number: '), 16)
```

---

### Post by MadCow108 on 2009-06-21
its a one liner in most languages.
e.g. c++:
cin >> hex >> number;

but doing it "by hand" is more interesting :)

---

### Post by Reiger on 2009-06-21
Any language that can work without the aid of whitespace will do this on one line if you want it to. Although this Haskell program will crash hard if it isn't fed an Integer.
```

[COLOR="White"]main = (=<<) (\i -> putStrLn $ show (read i :: Integer)) getLine[/COLOR]

```

---

### Post by jinksys on 2009-06-21
> **Reiger said:**
> Any language that can work without the aid of whitespace will do this on one line if you want it to. Although this Haskell program will crash hard if it isn't fed an Integer.
```

[COLOR="White"]main = (=<<) (\i -> putStrLn $ show (read i :: Integer)) getLine[/COLOR]

```

I can't read that. White text on a white background.

---

### Post by Reiger on 2009-06-21
That's because I didn't want to spoil it for others. :P 
You can read it by either selecting all the text, or just quoting me (but never posting that reply if you didn't intend to actually reply at all).

---

### Post by soltanis on 2009-06-21
For the two-lines of C solution, it will actually be two lines.

```

#include <stdio.h>
int main(int argc, char **argv) { long i; char *end; if (argc < 2) { fprintf(stderr, "you must supply at least 1 argument\n"); return 1; } i = strtol(argv[1], &end, 16); if (*end != '\0') { fprintf(stderr, "looks like you supplied something invalid in your argument\n"); } printf("%d\n", i); return 0; }

```

Boo mandatory newlines (damn C preprocessor).

---

### Post by jinksys on 2009-06-21
> **soltanis said:**
> For the two-lines of C solution, it will actually be two lines.

```

#include <stdio.h>
int main(int argc, char **argv) { long i; char *end; if (argc < 2) { fprintf(stderr, "you must supply at least 1 argument\n"); return 1; } i = strtol(argv[1], &end, 16); if (*end != '\0') { fprintf(stderr, "looks like you supplied something invalid in your argument\n"); } printf("%d\n", i); return 0; }

```

Boo mandatory newlines (damn C preprocessor).

I was actually just talking about the code that does the input/output, not the whole program.

---

### Post by ghostdog74 on 2009-06-21
Beginners just follow the [formula](http://www.webelfin.com/webelfindesign/hexdec.html)
```

awk 'BEGIN{
    #No lowercase. Do you own.
    printf "Enter hex number eg FFBA: "
    getline hex < "-"    
    #create hex table
    table["0"]=0
    table["1"]=1
    table["2"]=2
    table["3"]=3
    table["4"]=4
    table["5"]=5
    table["6"]=6
    table["7"]=7
    table["8"]=8
    table["9"]=9
    table["A"]=10
    table["B"]=11
    table["C"]=12
    table["D"]=13
    table["E"]=14
    table["F"]=15        
    j=0
    for (i=length(hex);i>0;i--){             
        total = total + table[substr(hex,i,1)] * (16 ^ j)
        j++        
    }
    print "hex: "hex," dec: "total
}'


```
NB: no lowercase. do your own.

---

### Post by soltanis on 2009-06-22
> **jinksys said:**
> I was actually just talking about the code that does the input/output, not the whole program.

Oh.

---

### Post by Mirge on 2009-06-22
> **soltanis said:**
> For the two-lines of C solution, it will actually be two lines.

```

#include <stdio.h>
int main(int argc, char **argv) { long i; char *end; if (argc < 2) { fprintf(stderr, "you must supply at least 1 argument\n"); return 1; } i = strtol(argv[1], &end, 16); if (*end != '\0') { fprintf(stderr, "looks like you supplied something invalid in your argument\n"); } printf("%d\n", i); return 0; }

```Boo mandatory newlines (damn C preprocessor).

The part that says: i = strtol(argv[1],** &end**, 16); 

Just wondering how that works? Haven't used it, but hafta ask anyway, would any issues arise from not allocating memory to the char* variable?

---

### Post by jinksys on 2009-06-23
> **Mirge said:**
> The part that says: i = strtol(argv[1],** &end**, 16); 

Just wondering how that works? Haven't used it, but hafta ask anyway, would any issues arise from not allocating memory to the char* variable?

strtol is defined as:

strtol(char *string, char **end, int base);

end points to a pointer that will be set to the character immediately following the long integer in the string.

This website has an example:
[http://www.thinkage.ca/english/gcos/expl/c/lib/strtol.html](http://www.thinkage.ca/english/gcos/expl/c/lib/strtol.html)

---

### Post by Mirge on 2009-06-23
thanks!

---

