---
title: "Code snippet meaning?"
date: 2010-04-04
forum: Programming Talk
---

### Post by yasokrish on 2010-04-04
#include <stdlib.h>
#include <stdio.h>
#include <string.h>
int main(int argc, char **argv)
{
  char buf[40];
  FILE *badfile;
  badfile = fopen("./badfile", "w");

  *(long *) &buf[0] = bffffea2;    
   (long *) &buf[1] = some address ;    
  *
  *(long *) &buf[2] = some address ;    
  fwrite(buf, sizeof(buf), 1, badfile);
  fclose(badfile);
}

What does *(long *) &buf[0]=some address  mean?????

While compiling it gives error msg like  bffffea2  undeclared......... 
What type does *(long *) &buf[0] mean and what type it stores??
Am newbie to c programming.Do help.

Thanks,
Yasokrish

---

### Post by gmargo on 2010-04-04
You have to do your own homework.

---

### Post by nvteighen on 2010-04-04
Ugh... I don't get how this could work in a regular architecture even after the syntax is corrected. Why is there a hardcoded address? Who told you something will be stored there?

EDIT: Ok, the code is *that* awful that I misread it completely. Heck, the whole *(long *)&buf[0] is totally unnecessary!!

---

### Post by LKjell on 2010-04-04
Well char buf[40] means that you are allocating 40 bytes address which is continuous.

*(long*) &buf[0] means that at address buf[0] you are writing something that can hold 8 bytes. Assuming you are writing something else with *(long*) &buf[1] it means that buf[0] (one byte) will not change but the other 7 bytes if *(long*) &buf[0] will be overridden by the new write.

Basically when you invoke a *(long*) &buf[i] you write from buf[i:i+7]

---

### Post by lisati on 2010-04-04
Nothing much to add, beyond asking if bffffea2 meant to be a hard-coded address. The way it is coded at the moment, the compiler is likely to interpret it as the name of a variable, which would explain the error message about it being undefined.

A suggestion for future: use the [noparse]```
 and 
```[/noparse] tags around code snippets you post, it will help preserve the formatting. One way of inserting the proper [noparse][code][/noparse] tag(s) is to highlight the code snippiet and click on the "#" button [IMG]http://ubuntuforums.org/images/editor/code.gif[/IMG]

---

### Post by Cracauer on 2010-04-04
Folks.

The OP has been posting a stream of threads asking for help with programs that exploit security holes.

I think this has been going on long enough and you need to put your BS sensors a notch higher now.

Thank you.

Sorry but enough is enough.

---

### Post by CptPicard on 2010-04-04
Oh, I believe people's bs sensors are high up enough, but I also wouldn't be too concerned regarding the threat level posed by this particular h4x0r in training ;)

---

### Post by Cracauer on 2010-04-04
> **CptPicard said:**
> Oh, I believe people's bs sensors are high up enough, but I also wouldn't be too concerned regarding the threat level posed by this particular h4x0r in training ;)

Yeah but he also hacks up his maybe compiling code until it's not usable at all anymore for "help".

That would be fine if he wasn't starting as many threads as he does.

---

### Post by lisati on 2010-04-04
Concerns noted. I'm inclined to agree with CptPicard at the moment about the level of threat.

There's also the "report" feature if things seem to be getting out of hand.

---

### Post by yasokrish on 2010-04-05
Hi,
Sorry for inconvenience caused.Nothing intentional.Extremely sorry.Since am new to linux,i posted threads.No illegal intentions.

Thank You,
Yasokrish

---

