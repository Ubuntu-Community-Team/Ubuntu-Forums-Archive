---
title: "Get Console output in C/C++"
date: 2005-05-03
forum: Programming Talk
---

### Post by Kimm on 2005-05-03
ok, perhaps this is a very silly question and everyone should know how to do it... but I happen not to :razz:

when I run an application in the console, lets say I run apt-get, It prints information on the screen, and if an error occures it tells me that, I can easily tell that an error occured from inside the application, like so:

```

int number = 0;

number = system("apt-get <something>");

```

and thats easy, but what if I wanted to know exactly what the problem was, if I was running apt-get and something unwanted happens, perhaps I want to know exactly what library was missing or perhaps if it is not in the repositores, how would I know that?

I mean, I want the app to be able to know, so that the app knows what to do

---

### Post by Xerampelinae on 2005-05-03
You probably have to look into pipes.  Read about the execp and dup functions... sorry I don't have time to go into detail.

---

### Post by Kimm on 2005-05-04
I'm having trubble finding information about those functions, perhaps someone could explain more closely?

---

### Post by toojays on 2005-05-04
What Xerampelinae is talking about, "pipes", is a way your program can hook into the actual text output of a program, not just its return code.

For your app, you could read the output from apt, and interpret any error messages.

Here's a simple example of using popen:```
/* there is no error checking, this is just an example */

#include <stdio.h>

int main()
{
  FILE * uname;
  char os[80];
  int lastchar;
  
  uname = popen("uname -o", "r");
  lastchar = fread(os, 1, 80, uname);
  os[lastchar] = '\0';
  printf("Your OS is %s", os);
  pclose(uname);
  return 0;
}
```

---

### Post by Kimm on 2005-05-04
yes, thank you, thats great ^^ now I just need to learn GTK+ or wxWidgets to complete my app, not to advanced GUi though so it should work just fine ^^

thank you!! :grin:

---

