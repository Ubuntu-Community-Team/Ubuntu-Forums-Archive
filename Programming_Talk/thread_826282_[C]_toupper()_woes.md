---
title: "[C] toupper() woes"
date: 2008-06-11
forum: Programming Talk
---

### Post by spadewarrior on 2008-06-11
I've been having trouble with this function. Instead of converting the following string 'hello' to 'HELLO', I get garbage.

Code:

[PHP]#include <stdio.h>
#include <string.h>
#include <ctype.h>



int main(void)
{
	char str[] = "hello";
	char str2[10];
	int n = 0;
	int count = 0;
	count = strlen(str);
	
	for(n=0; n<count; n++)
	
	{
		str2[n] = toupper(str[n]);
		n++;
	}
	
	printf("%s\n", str2);
	
	return 0;
	
}
[/PHP]

the output is normally something like:

```
H&#65533;L&#65533;h&#65533;
```

Does anybody get 'HELLO'? Is it my machine or something in the code?

---

### Post by lisati on 2008-06-11
I'm a bit rusty with my "C" coding, but it looks like you have a redundant "n++" in your code.

Try this:
> 
#include <stdio.h> 
#include <string.h> 
#include <ctype.h> 



int main(void) 
{ 
    char str[] = "hello"; 
    char str2[10]; 
    int n = 0; 
    int count = 0; 
    count = strlen(str); 
     
    for(n=0; n<count; n++) 
     
    { 
        str2[n] = toupper(str[n]); 
    } 
     
    printf("%s\n", str2); 
     
    return 0; 
     
}  



[COLOR=#000000][COLOR=#007700][/COLOR][/COLOR]

---

### Post by Jessehk on 2008-06-11
You're incrementing "n" twice: once in the "header" of the **for** loop and once within its body.

EDIT: This might be a nicer solution:
```

#include <stdio.h>
#include <ctype.h>

/* This snippet uses C99 code */

/* Convert a string to uppercase.
 * destructively modifies the given string.
 */
char *upcase( char *str ) {
    for ( char *iter = str; *iter != '\0'; iter++ )
        *iter = toupper( *iter );

    return str;
}

int main( void ) {
    char str[] = "hi there. I like apples!!";

    printf( "%s\n", upcase( str ) );
    return 0;
}

```

---

### Post by Joeb454 on 2008-06-11
> **Jessehk said:**
> You're incrementing "n" twice: once in the "header" of the **for** loop and once within its body.

I've just noticed that too :p I can see this could cause some issues

**EDIT:** I've just compiled the revised code from lisati - which works fine :)

Now all you need to do is to get the string input from the user ;)

---

### Post by spadewarrior on 2008-06-11
D'oh.

Thanks.

---

