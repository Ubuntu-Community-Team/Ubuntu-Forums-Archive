---
title: "CPP code syntax legality?"
date: 2010-04-02
forum: Programming Talk
---

### Post by OgreProgrammer on 2010-04-02
I am away from my compiler for a few days and I had an idea. I am wondering if this is problematic. Can the default come first? text is set by a mouse click, so its only possible to be one of those four types. 

```

switch(text) {
    default : type = REGION_ACTOR_FILLED;
    case "Normal" : type = SPRITE;
    case "Canvas"  : type = CANVAS;
    case "Wire Frame Region" : type = REGION_ACTOR;
}

```

Googling switch case doesnt seem to cover that.

---

### Post by dwhitney67 on 2010-04-02
The default can come first, but typically most programmers put it last.

As for your case values, switch() will not work with a string.  To do what you want, you will need to manually define the if/else blocks.

P.S.  In the future, should you use switch/case statements, don't forget the 'break' after each case.

---

### Post by ibuclaw on 2010-04-02
Some compiled languages support matching strings in case statements, C/C++ is not one of those languages - although I have seen some wild and wonderful ways to hack it on.

One notable except I've seen (from xchat)
```

switch (code) {
    case CHR('W','O','R','D'):
        /* do stuff */
        break;
}

```

Where CHR() is a macro that does some magic along the lines of:
```
return (a << 1) + (b << 2) + (c << 4) + (d << 8);
```



On a side note, you should really use break; else the statement will fall through and run the code beneath too. :)

---

### Post by OgreProgrammer on 2010-04-02
> **ibuclaw said:**
> Some compiled languages support matching strings in case statements, C/C++ is not one of those languages - although I have seen some wild and wonderful ways to hack it on.

One notable except I've seen (from xchat)
```

switch (code) {
    case CHR('W','O','R','D'):
        /* do stuff */
        break;
}

```Where CHR() is a macro that does some magic along the lines of:
```
return (a << 1) + (b << 2) + (c << 4) + (d << 8);
```

On a side note, you should really use break; else the statement will fall through and run the code beneath too. :)

Yeah, I took them out to simplify.

Thanks for help people.

---

