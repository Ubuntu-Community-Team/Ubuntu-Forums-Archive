---
title: "scanf() and infinite loops"
date: 2010-12-03
forum: Programming Talk
---

### Post by fasoulas on 2010-12-03
the default ```
scanf("%s");
``` only reads the string until the first whitespace.so after searching the web i found that i can read the whole string with the whitespaces if i replace it with ```
scanf("%[^\n]");
```

If i run the code below i have an infinite loop.
```

char str[256];
do{
  	printf("Enter your message : ");
	scanf("%[^\n]",str);
        somefunc(str);
}while(1);
```

i want to be able to read from standard input and send the string str to a function until i press ctrl + c.
How can i do this without having the infinite loops ?

---

### Post by worksofcraft on 2010-12-03
> **fasoulas said:**
> the default ```
scanf("%s");
``` only reads the string until the first whitespace.so after searching the web i found that i can read the whole string with the whitespaces if i replace it with ```
scanf("%[^\n]");
```

If i run the code below i have an infinite loop.
```

char str[256];
do{
  	printf("Enter your message : ");
	scanf("%[' ']",str);
        somefunc(str);
}while(1);
```

i want to be able to read from standard input and send the string str to a function until i press ctrl + c.
How can i do this without having the infinite loops ?

You should test the result of scanf for EOF to terminate your loop. Then when you pipe in files it will terminate when you get to end of input. It will also let you terminate with ctrl-D when using terminal input.

---

### Post by MadCow108 on 2010-12-03
why not use getline instead of scanf?

also when using:
scanf("%[^\n]");
you leave the newline in the stream which leads to an infinite loop when not discarding it.
so put a getchar() after it to remove it

I don't know what %[' '] is supposed to match. You only want spaces and quotes? kind of weird input.
anyhow also in that case you have to discard the non matching characters from the stream (e.g. a inverse scanf with ^) to avoid a infinite loop.

---

### Post by Arndt on 2010-12-03
> **fasoulas said:**
> the default ```
scanf("%s");
``` only reads the string until the first whitespace.so after searching the web i found that i can read the whole string with the whitespaces if i replace it with ```
scanf("%[^\n]");
```

If i run the code below i have an infinite loop.
```

char str[256];
do{
  	printf("Enter your message : ");
	scanf("%[' ']",str);
        somefunc(str);
}while(1);
```

i want to be able to read from standard input and send the string str to a function until i press ctrl + c.
How can i do this without having the infinite loops ?

I recommend against ever using 'scanf'. Read one line at a time with fgets, and use sscanf on each line (checking return values as you go, of course). Or assemble the total text piece by piece, if that's what you want.

---

### Post by fasoulas on 2010-12-03
> **MadCow108 said:**
> why not use getline instead of scanf?

also when using:
scanf("%[^\n]");
you leave the newline in the stream which leads to an infinite loop when not discarding it.
so put a getchar() after it to remove it

I don't know what %[' '] is supposed to match. You only want spaces and quotes? kind of weird input.
anyhow also in that case you have to discard the non matching characters from the stream (e.g. a inverse scanf with ^) to avoid a infinite loop.
i meant [^\n] you are right that was a mistake.

---

### Post by fasoulas on 2010-12-03
> **Arndt said:**
> I recommend against ever using 'scanf'. Read one line at a time with fgets, and use sscanf on each line (checking return values as you go, of course). Or assemble the total text piece by piece, if that's what you want.

i am not reading from a file but from the keyboard.
can i use fgets for keyboard(stdin) input?

---

### Post by MadCow108 on 2010-12-03
stdin, stdout and stderr are the names of the stream defined in stdio.h
fgets(str, N, stdin)
same all other FILE* functions like getline, ...

---

### Post by fasoulas on 2010-12-03
> **MadCow108 said:**
> stdin, stdout and stderr are the names of the stream defined in stdio.h
fgets(str, N, stdin)
same all other FILE* functions like getline, ...

is there a way to remove the \n character from the string ?

---

### Post by fasoulas on 2010-12-03
i thing i solved the infinite loop problem with 
```

scanf("%[^\n]",str);
getchar();	

```

but i don't know if is the best way to do it

---

### Post by Arndt on 2010-12-03
> **fasoulas said:**
> is there a way to remove the \n character from the string ?

Of course. You search for it, and if you found it, you replace it with '\0'. Since you know it will be at the end, you don't really need to use a search operation (strchr) but can get first the length of the string with strlen, and then look whether the last character is a newline. It may not be, for the last line in a file, or if the user signalled EOF.

---

