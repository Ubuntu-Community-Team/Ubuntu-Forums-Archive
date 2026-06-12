---
title: "C PROGRAMMING HELP - #include?"
date: 2011-03-01
forum: Packaging and Compiling Programs
---

### Post by squareff255 on 2011-03-01
I'm trying to get the concept of #include so I'm trying to write a very simple program and I'm not sure what's going wrong...

I have a program called name.c that looks like this:


#include <stdio.h>

main()
{
  char name[25];

  printf("What is your name?\n");

  scanf("%s", name);

  printf("Your name is %s!\n", name);
}

Pretty simple. I have compiled it, run it, and it works just fine on it's own. Then I have a program I started called personal_info.c and it looks like this:

#include <stdio.h>

main() /*gets personal information from the user*/
{
#include "name.c"
}

NOW, name.c IS in the same directory as personal_info.c so that should be fine, right? I was hoping that when I compiled and ran personal_info.c it would basically just run name.c but it's giving me this:

mckenzie@film-box:~/Documents/compy/scripts$ gcc personal_info.c
In file included from personal_info.c:6:
name.c: In function ‘main’:
name.c:4: error: expected ‘;’ before ‘{’ token

Why would it want me to put a ';' before '{' in name.c?

---

### Post by SevenMachines on 2011-03-01
Its probably a good idea to start going through a basic tutorial or book to get used to these sort of things. In short, #include sort of tells the compiler (preprocessor) "take this file and put it here before compiling"
 its not running something or calling some other bit of code.  Theres some more to it than that but i think you probably need a good tutorial for a bit more information. and yes, compiler messages are not always the clearest :)

---

### Post by ibuclaw on 2011-03-01
I concur, C is not a language any odd fella can just pick up overnight, and from what I've seen, you've been taking a cowboy route of crashing through it as if it's as any other scripting language ;).

Best advice is sit back, take a deep breath, and have a look at a [starter guide]("http://www.cprogramming.com/tutorial.html#ctutorial") to get your feet wet first.

If you get through it and are totally freaked out by linked-lists; binary trees; memory management; bitwise operators; structs and unions; data sections; assembly; linkers; etc... well then at least you get something out of it either way. Even if you decided it's probably best to leave C alone as it's just not quite what you are looking for.

Regards
Iain

---

### Post by squareff255 on 2011-03-01
Thanks guys. I figured it out. I was reading SevenMachines reply and realized it doesn't call anything. It just inserts it, so I basically had the main() function of name.c inside of the main() function of personal_info.c. It works now. BUT you guys are right, I am rushing through C a bit quickly without really solidifying the concepts. :) I'll take it a bit slower.

---

