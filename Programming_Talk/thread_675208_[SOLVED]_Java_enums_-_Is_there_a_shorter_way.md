---
title: "[SOLVED] Java enums - Is there a shorter way?"
date: 2008-01-22
forum: Programming Talk
---

### Post by mike_g on 2008-01-22
Hi I'm starting on what should be quite a large project in Java. I want to use enums for stuff like error codes. Heres my enum:
```
public enum ErrorCodes
{
    EXIT_SUCCESS, USER_DATA_FILE_NOT_FOUND;
}

```
The thing is the only way I seem to be able to return an enumerated integer from a function is like so:
```
return ErrorCodes.USER_DATA_FILE_NOT_FOUND.ordinal();
```
And I'm not even sure if thats right; it just compiles. Am I doing this right? and is there a shorter way to return an enum as an int?

---

### Post by stevescripts on 2008-01-22
mike_g

This may help: [http://java.sun.com/j2se/1.5.0/docs/guide/language/enums.html](http://java.sun.com/j2se/1.5.0/docs/guide/language/enums.html)

Personally, I haven't done much java development for several years now.

Steve

---

### Post by CptPicard on 2008-01-22
Is there a specific reason why you want to return an int, not the enum value itself? Seems to me you're taking an unneccessary additional step here.

---

### Post by mike_g on 2008-01-22
steve: cheers that explains the difference Java enums have compared with C++, which is what I was used to. Not so sure if I like the new and improved version, but maybe the reason will become apparent sometime.

CptPickard: Well originally I tried returning an enum type but mashed the compiler as it thought I was declaring an enum. I guess it would probably be best for me to work out how to return the buggers.

---

### Post by CptPicard on 2008-01-22
Just make the return type of the method "ErrorCodes" in this example...

---

### Post by mike_g on 2008-01-22
>_< Lol, I'm an idiot. Thanks.

---

