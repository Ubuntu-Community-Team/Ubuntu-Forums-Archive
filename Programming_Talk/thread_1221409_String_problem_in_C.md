---
title: "String problem in C"
date: 2009-07-23
forum: Programming Talk
---

### Post by dellwood on 2009-07-23
Hi, 

In my SDL app (the problem isn't with SDL), I have a function similar to the following:

```

void func( char string[10] ) {
     if( string == "fixed" ) {
          //do something
     }
     if( string == "resizeable" ) {
          //do something else
     }
     else {
          //give an error
     }
}

int main() {

     func( "resizeable");
}

```

But I'm getting the error from the else statement.  I haven't been using C that long, so I'm somewhat lost on how to correctly code this.  I couldn't find documentation that shows something similar (where a string is being checked via an if statement).  

All help is greatly appreciated :).

-Josh

---

### Post by Finalfantasykid on 2009-07-23
I'm not 100% sure, but I don't think you can compare a char* using a ==.  You might be better off using the strncmp function.

EDIT:  Also that second if statement should probably be an else if

---

### Post by Can+~ on 2009-07-23
Plain ol' C has no "==" operator for "strings", use [strncmp]("http://www.cplusplus.com/reference/clibrary/cstring/strncmp/").

And you should expect a [FONT="Courier New"][COLOR=#00AAFF]const char[/COLOR]* mystr[/FONT] as argument (I added the const for safety, if you plan on changing the reference (unlikely), then remove it).

---

### Post by Finalfantasykid on 2009-07-23
> **Can+~ said:**
> Plain ol' C has no "==" operator for "strings", use [strcmp]("http://www.cplusplus.com/reference/clibrary/cstring/strcmp/").

strcmp is the cause of many security holes, and it would be wise to use strncmp instead.

---

### Post by Can+~ on 2009-07-23
> **Finalfantasykid said:**
> strcmp is the cause of many security holes, and it would be wise to use strncmp instead.

I stand corrected.

All the strn___ are safer than their brothers.

Luckily, I rarely use C string functions.

---

### Post by Habbit on 2009-07-23
Actually, what would be the security hole in strcmp? It only reads until it finds a null character in either string. I understand the security considerations in the str__ functions that _write_ to a buffer, but here... I'm a bit dumbfounded. Could you illustrate me, O grand masters of the pointer?

---

### Post by Finalfantasykid on 2009-07-23
Actually I don't know all the details, I have only taken a sincle c programming course in university, but I was always told to use strn*** instead of str***.  We would loose marks if we did not do this, since it is good practice to use the more secure strn since you can garuntee that it will never exceed x number of characters, whereas with str it is possible(for a person with malicious intentions) to overwite the string buffer and cause some harm in one way or another.

EDIT:   According to this [http://www.informit.com/guides/content.aspx?g=cplusplus&seqNum=202](http://www.informit.com/guides/content.aspx?g=cplusplus&seqNum=202) , it is possible that a string will not have a null terminator, and a buffer overflow could occur.

---

### Post by dellwood on 2009-07-23
So I've (attempted) to implement the strncmp function, but I'm coming up with more problems:

```

char *scrn_attribs_p;
        scrn_attribs_p = (char *)&scrn_attribs;

        char *fixed_p;
        char fixed[5] = "fixed";
        fixed_p = (char *)&fixed;

        char *resizeable_p;
        char resizeable[10] = "resizeable";
        resizeable_p = (char *)&resizeable;

        int fixed_i, resizeable_i;

        fixed_i = int strncmp( const char *scrn_attribs_p, const *fixed_p, size_t  count );
        resizeable_i = int strncpm( constchar *scrn_attribs_p, const *fixed_p, size_t count);

        if( fixed_i == 0 ) {
                screen = SDL_SetVideoMode( win_width, win_height, win_depth, SWSURFACE );
        }
        if( resizeable_i == 0 ) {
                screen = SDL_SetVideoMode( win_width, win_height, win_depth, SWSURFACE | SDL_RESIZEABLE );
        }

```

It is giving me errors on the two strncmp lines, where it says, "expected expression before ‘int’." They are ints (according to the documentation) and they return integer values, so why is spitting out errors?

Thanks :).

-Josh

---

### Post by Habbit on 2009-07-23
> **Finalfantasykid said:**
> whereas with str it is possible(for a person with malicious intentions) to **overwrite the string buffer** and cause some harm in one way or another.

Yeah, that is what I know too, but strcmp does not write, only reads. Where's the security hole there? I think strncmp is just used to match with part of a string.

EDIT: even in the case you mention, strcmp will stop reading _somewhere_ because there will be some 0 in the memory... the worst harm would be "comparing" a buffer of, say, several gigabytes of non-nulls with itself. In particular, the attacker needs to control _both_ params to strcmp or the loop will end as soon as the shorter string ends.

---

### Post by Finalfantasykid on 2009-07-23
```
fixed_i = int strncmp( const char *scrn_attribs_p, const *fixed_p, size_t  count );
```I'll see if I can get this to work...

```

int count = 255;
fixed_i = strncmp(scrn_attribs_p, fixed_p, count);

```That should make it work I think.  I don't think you actually need the const, but if what I put there does not work, you could add the const at the initial variable declaration at the beginning of your func() function.  Of course you will have to do this for both functions.

---

### Post by Can+~ on 2009-07-23
> **Habbit said:**
> Where's the security hole there?.

I think what Finalfantasykid meant was more like a "potential crash" and not a security hole.

---

### Post by soltanis on 2009-07-23
Uh okay so to interject -- strcmp stops comparing strings when it reaches the end of one of the strings, and it determines when this happens according to a null terminator. If neither string has a null terminator, this can be problematic (the function will keep searching through whatever other crap is in memory until it hits a '\0') and may cause the function to stray out of your address space/crash badly. As for security holes, probably not, since strcmp does not actually do any memory copying (but you should probably always use strncpy, not strcpy).

Anyway, when strcmp(s1, s2) equals zero, the strings are equal:

```


if (strcmp(string, "hello, world") == 0) {

} else if (!strcmp(string, "goodbye, cruel world!")) {
// that also works ^
}


```

It means something if its > 0 or < 0 but I'm not really sure and I've never found this function useful for those purposes anyway.

In the other code you posted, you should not have the "int" before the "strcmp". The identifier "int" is only used for declarations, not assignments.

---

### Post by Darkhack on 2009-07-24
Usually, str_ functions are insecure and should be avoided for their strn_ counterparts.  However in the case of strcmp, it doesn't matter nearly as much.  The concern with strcmp is that it could allow an attack to retrieve information if the string passed in is not null terminated.  In my opinion, the real security flaw is that you didn't null terminate the input, not that you used strcmp.

---

### Post by dellwood on 2009-07-24
soltanis' way worked somewhat, though I decided to be on the safe side and go with FFK's strncmp method:

```

char *scrn_attribs_p;
        scrn_attribs_p = (char *)&scrn_attribs;

        char *fixed_p;
        char fixed[5] = "fixed";
        fixed_p = (char *)&fixed;

        char *resizeable_p;
        char resizeable[10] = "resizeable";
        resizeable_p = (char *)&resizeable;

        int fixed_i, resizeable_i, count;

        count = 255;

        fixed_i = strncmp(scrn_attribs_p, fixed_p, count);
        resizeable_i = strncmp(scrn_attribs_p, fixed_p, count);

        if( fixed_i == 0 ) {
                screen = SDL_SetVideoMode( win_width, win_height, win_depth, SDL_HWSURFACE );
        }
        else if ( resizeable_i == 0 ) {
                screen = SDL_SetVideoMode( win_width, win_height, win_depth, SDL_HWSURFACE | SDL_RESIZEABLE /*EDIT*/ );
        }
        else {
                printf( "Failed to set screen %s.\n", SDL_GetError() );
        }

        if( screen = NULL) {
                printf("Screen set to NULL\n");
        }


```

Which compiles, but doesn't do what is expected when passed the argument "fixed", it give the "failed to set screen" error followed by a segmentation fault ("zsh: segmentation fault ./Main") :(.  The odd thing is when I added the NULL check, that doesn't show, so I guess it is setting the screen to something (screen is an extern {SDL_Surface* screen} )?

-Josh :)

---

### Post by MadCow108 on 2009-07-24
char fixed[5] = "fixed";
leaves no room for the null character so it is no terminated string.
Exactly the problem which is discussed here.

your count is also far to big to handle the null termiantion problem that occurs. So strncmp tries to compare the (probably null terminated) string scrn_attrib with 255 chars in "fixed" which are just garbage it finds in memory after the fifth character.
Lesson: Always null terminate your strings if you plan to use functions relying on that (as strcmp strlen etc)

delare your string without the 5:
char fixed[] = "fixed";
then the compiler figures out the correct size and null terminates it.
or define a maximum size and use that as the maximum in the strn___ functions.
This is better for strings of unknown size, because strlen again relies on null-termination.

and you don't need those copies of the char pointers for strncmp as char arrays are just pointers.

```

#define MAX_STRING 255

...

char scrn_attribs[MAX_STRING] = "fixed";
char fixed[MAX_STRING] = "fixed";
char resizeable[MAX_STRING] = "resizeable";
int fixed_i, resizeable_i;
fixed_i = strncmp(scrn_attribs, fixed,MAX_STRING);
resizeable_i = strncmp(scrn_attribs, fixed,MAX_STRING);

```

---

### Post by dellwood on 2009-07-24
Thanks, I used the fixed[] = "fixed" method as I was wary of using defines in the library where the function was housed ( _INIT_(char scrn_attribs[MAX_LENGTH]){} ). But it works, so thanks for the help :).

-Josh

---

