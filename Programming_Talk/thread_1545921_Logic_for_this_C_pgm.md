---
title: "Logic for this C pgm"
date: 2010-08-04
forum: Programming Talk
---

### Post by navaneethan on 2010-08-04
```
#include<stdio.h>

void main()
{
static char *s[]={"black","white","yellow","violet"};
char **ptr[]={s+3,s+2,s+1,s},***p;
p=ptr;
**++p;
printf("%s",*--*++p + 3);

}
```

Here I get the Output "**ck**"
I couldn't able to understand the logic here

1)**++ptr what does it?
2)what is going on in the printf....
3)please explain elaborately

---

### Post by dv3500ea on 2010-08-04
As far as I understand it, although I don't normally code in c:
```

static char **s={"black","white","yellow","violet"};
// s is a pointer to a pointer of characters so an array of strings
char ***ptr={s+3,s+2,s+1,s},***p;
// ptr and p are pointers to arrays of strings.
// s+3 = {"black","white","yellow",[SIZE="4"]"violet"[/SIZE]}
// s+2 = {"black","white",[SIZE="4"]"yellow","violet"[/SIZE]}
// s+1 = {"black",[SIZE="4"]"white","yellow","violet"[/SIZE]}
// s = {[SIZE="4"]"black","white","yellow","violet"[/SIZE]}
// (I think)
// therefore:
// ptr = {		
//    {"black","white","yellow",[SIZE="4"]"violet"[/SIZE]},
//    {"black","white",[SIZE="4"]"yellow","violet"[/SIZE]},
//    {"black",[SIZE="4"]"white","yellow","violet"[/SIZE]},
//    {[SIZE="4"]"black","white","yellow","violet"[/SIZE]}
//	}
p=ptr;
//p is just an alias to ptr
**++p;
//p is incremented
//p = {		
//    {"black","white","yellow",[SIZE="4"]"violet"[/SIZE]},
//    [b]{"black","white",[SIZE="4"]"yellow","violet"[/SIZE]},
//    {"black",[SIZE="4"]"white","yellow","violet"[/SIZE]},
//    {[SIZE="4"]"black","white","yellow","violet"[/SIZE]}[/b]
//	}

printf("%s",*--*++p + 3);
//p is incremented
//p = {		
//    {"black","white","yellow",[SIZE="4"]"violet"[/SIZE]},
//    {"black","white",[SIZE="4"]"yellow","violet"[/SIZE]},
//    [b]{"black",[SIZE="4"]"white","yellow","violet"[/SIZE]},
//    {[SIZE="4"]"black","white","yellow","violet"[/SIZE]}[/b]
//	}
//and dereferenced
//-> {"black",[SIZE="4"]"white","yellow","violet"[/SIZE]}
//and decremented
//-> {[SIZE="4"]"black","white","yellow","violet"[/SIZE]}
//and dereferenced
//-> [SIZE="4"]"black"[/SIZE]
//and 3 is added
//-> [SIZE="4"]"bla**ck**"[/SIZE]

//NOTE: Boldness and bigger font is used to show where the pointer is.
//{"black","white",[SIZE="4"]"yellow","violet"[/SIZE]} is effectively {"yellow","violet"}
//
//{		
//    {"black","white","yellow",[SIZE="4"]"violet"[/SIZE]},
//    [b]{"black","white",[SIZE="4"]"yellow","violet"[/SIZE]},
//    {"black",[SIZE="4"]"white","yellow","violet"[/SIZE]},
//    {[SIZE="4"]"black","white","yellow","violet"[/SIZE]}[/b]
//	} 
//is effectively:
//{
//    {"yellow","violet"},
//    {"white","yellow","violet"},
//    {"black", "white","yellow","violet"}
//}
//
//[SIZE="4"]"bla**ck**"[/SIZE] is effectively "ck"

```

Note I have replaced []s after an identifier with *s before because they mean the same thing (in c arrays == pointers).

I hope this is just example code because it is extremely confusing and you wouldn't want to use something like this in real life ;)

---

### Post by interval1066 on 2010-08-04
Wow... this cat (whomever wrote the code) really likes to de-reference his pointers. As you have probably already surmised from dv3500ea's post the guy is using really cryptic pointer math to simply de'ref array elements. Rather than use easier to understand array subscripts (char *poop[]) he's de-referencing the pointer to the array (**poop) and de-referencing a pointer to a pointer to the array (***poop) and so on. Really hard to follow all that jazz, as you pointed out. Its not illegal, obviously, I mean, they have whole contests (search "Obfuscated C Code") on who can write the most cryptic C code, but as an example, its really awful.

---

### Post by Bachstelze on 2010-08-04
It's probably (bad) homework.

---

### Post by trent.josephsen on 2010-08-04
> **dv3500ea said:**
> Note I have replaced []s after an identifier with *s before because they mean the same thing (in c arrays == pointers).
[*sigh*](http://c-faq.com/aryptr/aryptrequiv.html)

---

### Post by navaneethan on 2010-08-07
This is not mine homework because i just got the output and while i understand the reason for this output i got stuck thats why sharing here;-)
i am not a school boy to do homework ;-) as well as i am not the expert like you ;-) just to know the exact reason thas why i stepped here ;-) please mind it

---

### Post by SaintDanBert on 2010-08-07
> **navaneethan said:**
> 
...
1)**++ptr what does it?
2)what is going on in the printf....
3)please explain elaborately


Take a look at [http://www.codeproject.com/KB/cpp/complex_declarations.aspx](http://www.codeproject.com/KB/cpp/complex_declarations.aspx) to help you understand the **declarations**. It often helps me to draw boxes to represent memory locations and variable contents.

when you see **"buttercup"** with a C or C++ program, what you get is an array of characters -- one location for each -- PLUS, one extra byte appears on the end to hold a NUL-character '\x00'. From my example, you get:  |b|u|t|t|e|r|c|u|p|\x00|

Your declaration:  **char *s[]={...}** says that you want
[list]
[*] an array "[]" of unspecified size
[*] give the array the identifier "s"
[*] the array holds pointers "*" to character data "char"
[*] initialize the array "="
[*] with the contents "{ entry, entry, ..., entry }"
[*] determine the array size based on the number of entries
[/list]

Each of your entries is a null-terminated string, also known by the colloquial name, ** char star ** because of the "char *" in the declaration.

By the way, the following are identical in how the use memory:
[list]
[*] char *here[];   // an array of pointers to character data
[*] char **there;   // a pointer to, pointers to character data
[/list]

I hope this helps,
~~~ 0;-Dan

---

### Post by monraaf on 2010-08-07
> **navaneethan said:**
> This is not mine homework because i just got the output
You got the 'output' from what? This doesn't look like auto generated code to me. My guess is, you wrote the code yourself maybe a couple of weeks ago, maybe you got distracted. And you are now looking at your own code again, and are trying to figure out what you wrote in the first place ;).

---

### Post by jon zendatta on 2010-08-07
++ monraf are you a psychologist

---

### Post by jon zendatta on 2010-08-07
oh sorry monraaf i have trouble with words:KS

---

