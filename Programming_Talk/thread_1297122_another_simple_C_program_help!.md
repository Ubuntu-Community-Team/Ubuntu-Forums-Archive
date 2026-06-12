---
title: "another simple C program help!"
date: 2009-10-21
forum: Programming Talk
---

### Post by mickmouse13 on 2009-10-21
I posted this before and got some help on one part of the code, i have added some stuff and it does not work much any more. The first part works, it asks Y/N to you being a zombie... and gives you the right answer but the second part always defaults to FAAAAAAAIL. idk any help? i have an idea it might be somethign to do with { } these. THANKS!

```
#include <stdio.h>

int main()
{
    char zombie;
    char run;
    printf ( "A man aproaches you. His face concield in the shadows.\n" );
    printf ( "'are you a zombie?'\n (y/n)\n" ); /*asks for y or n as answer*/
    scanf ( "%c", &zombie );
    if (zombie == 'y' ){
        printf( "You have obviously lost the game than.\n");/* its a zombie servival thing so you loose*/
    } else {
        printf ( "The man comes into the light; His face rotten and maggot filled he mumbles as the lumbers tword you,'you might wanna run than.' )press R to run)\n" ); /* the game beguins*/
        scanf ( "%c", &run );
        if (run == 'r' ){
        printf ( "you run just fast enough tio outrun him, ducking out in a room\n" );}/* never gives me a prompt or displays the "you run just fast..." message*/
    else {
    printf( "FAAAAAAAAIL\n" );/*skips streight to this... any ideas?*/
}
        
    
    }
    getchar();
    return 0;
} 
```

---

### Post by OpenGuard on 2009-10-21
```
if (this == that) {
    // true
} else {
    // false
} else {
    // maybe ?
}
```

This is what you have there ( and as far as I know, C doesn't know what "maybe" means ). What exactly you are trying to achieve ?

---

### Post by Tony Flury on 2009-10-21
the reason is almost certainly due to buffering of the standard input stream. Let me try to explain : 

when you type the "y" or "n" to the first question you actually type "y"<enter>

the "y" character is returned by the scanf call, and the enter character '\n' stays in the buffer.

so the next scanf call (where you expect an 'r'), the next character in the buffer is actually a '\n'- which is not the same as an 'r' - so you get the Fail message

if you only want a single character and ignore the rest you need to clear the buffer after the scanf calls - use

```

char ch;
while((ch = getc(stdin)) != EOF && ch != '\n')
{
continue;
}

```
This code snippet will clear everything in the buffer upto and including any '\n' character


An an aside - your indentation style (or lack of style :-) ) is making your code incredibly difficult to read.

---

### Post by Tony Flury on 2009-10-21
> **OpenGuard said:**
> ```
if (this == that) {
    // true
} else {
    // false
} else {
    // maybe ?
}
```

This is what you have there ( and as far as I know, C doesn't know what "maybe" means ). What exactly you are trying to achieve ?

I think what he actually has is 

```

if (zombie)
{

}
else
{ 
    if (run)
    {
    }
    else
    {
    }
}

```

but as i have pointed out his indentation style makes it difficult to work it out.

---

### Post by OpenGuard on 2009-10-21
> **Tony Flury said:**
> I think what he actually has is 

```

if (zombie)
{

}
else
{ 
    if (run)
    {
    }
    else
    {
    }
}

```but as i have pointed out his indentation style makes it difficult to work it out.

Eh, didn't saw the second, nested if.

@ OP - get an IDE with some kind of automatic code formating feature ..

---

### Post by mickmouse13 on 2009-10-21
I went with Tony Flury's fix. And no i dont have indention syle. i will work on this. Thanks all for your answers.

---

### Post by mickmouse13 on 2009-10-21
thanks for ther help

---

