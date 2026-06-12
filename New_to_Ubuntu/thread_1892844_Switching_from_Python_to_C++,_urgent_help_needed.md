---
title: "Switching from Python to C++, urgent help needed"
date: 2011-12-08
forum: New to Ubuntu
---

### Post by AlexTolic on 2011-12-08
This is one of those things that drive me crazy. I have done everything i have read and still cannot compile and run this program. What is wrong?

#include <stdio.h>

int main()
{
printf("Hello, world\n);
return 0;
}

It keeps return a list of invalid syntax

---

### Post by nmaster on 2011-12-08
> **AlexTolic said:**
> 
It keeps return a list of invalid syntax

you need to close the quotation marks. right?
```
#include <stdio.h>

int main()
{
printf("Hello, world\n[COLOR="Red"]"[/COLOR]);
return 0;
}
```

---

### Post by ksprasad on 2011-12-08
> 
printf("Hello, world\n);

 
Missed the ending double quote i guess.

---

### Post by AlexTolic on 2011-12-08
Thank you for that, slipped right past me :D
however...

ex.c: In function &#8216;main&#8217;:
ex.c:5:1: error: stray &#8216;\&#8217; in program
ex.c:5:23: error: expected &#8216;)&#8217; before &#8216;n&#8217;

???

Also thank you guys for responding so quickly. This is an excellent forum.

---

### Post by nmaster on 2011-12-08
> **AlexTolic said:**
> 
Also thank you guys for responding so quickly. This is an excellent forum.
 that's why this community is awesome:)

mind posting the new code? i have a feeling you have another typo...

---

### Post by AlexTolic on 2011-12-08
> **nmaster said:**
> that's why this community is awesome:)

:] glad i finally joined 

and this is the new code, nothings really changed except including the ending quote


#include <stdio.h>

int main()
{
printf("Hello World!"\n);
return 0;
}

---

### Post by nmaster on 2011-12-08
> **nmaster said:**
> you need to close the quotation marks. right?
```
#include <stdio.h>

int main()
{
printf("Hello, world\n[COLOR="Red"]"[/COLOR]);
return 0;
}
```

you need to put the quote *after* the '\n'.  see my post from before.

---

### Post by AlexTolic on 2011-12-08
ex.c:12:5: error: redefinition of &#8216;main&#8217;
ex.c:3:5: note: previous definition of &#8216;main&#8217; was here
ex.c: In function &#8216;main&#8217;:
ex.c:14:1: error: stray &#8216;\&#8217; in program
ex.c:14:23: error: expected &#8216;)&#8217; before &#8216;n&#8217;

Fixed that again and i feel so stupid for letting that slip so many times :[ but still im not grasping this problem at all

---

### Post by nmaster on 2011-12-08
> **AlexTolic said:**
> ex.c:12:5: error: redefinition of ‘main’
ex.c:3:5: note: previous definition of ‘main’ was here
ex.c: In function ‘main’:
ex.c:14:1: error: stray ‘\’ in program
ex.c:14:23: error: expected ‘)’ before ‘n’

Fixed that again and i feel so stupid for letting that slip so many times :[ but still im not grasping this problem at all

is it really that different from python?  just slow down a little and go character by character.  copy the code i gave you (verbatim).  does that work?

---

### Post by AlexTolic on 2011-12-08
Thank you for the help I got it to compile and rune. I was just rushing it and getting frustrated because i didnt really understand anything. Thank you for putting up with me :D haha

---

### Post by nmaster on 2011-12-08
haha, well i think we've all been there.  just so ya know, you're actually doing a "hello world" for C rather than C++. you're probably using gcc and just didn't notice.

```

// C++ Hello World
#include <iostream>
using namespace std;

int main ()
{
  cout << "Hello World!";
  return 0;
}

```

EDIT: if you're problem has been resolved, be sure to mark the thread as "SOLVED".

---

### Post by AlexTolic on 2011-12-08
Wow, that was the biggest thing i needed to hear haha i was using gcc. Thank you so much for the help again :D

---

