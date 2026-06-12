---
title: "Control Gui by command line - GTK, C"
date: 2006-08-04
forum: Programming Talk
---

### Post by zootreeves on 2006-08-04
Ok I have create a simple GTK interface for my program and when you click a button it opens a file open dialog box. What I want to do is have it so if I pass an option to it via the command line (e.g. myprog -d) then it will start with the dialog box open.

Is this possible? Could someone give me an example or just point me in the right direction. Thanks

---

### Post by dabear on 2006-08-04
I don't know very much C, but somthing like this might work:
```

#include <stdio.h>
#include <stdlib.h>

int main(int argc, char **argv)
{
    if(argc == 1 && argv[1] == '-d')
    {
        //trigger launch of dialog
    }
}

```
The clue here, is that the arguments form the command line will be given to the main function. argc is the amount of argumnts given, while argv is the arguments them selves. Good luck!

---

### Post by KaeseEs on 2006-08-04
> **dabear said:**
> I don't know very much C, but somthing like this might work:
```

#include <stdio.h>
#include <stdlib.h>

int main(int argc, char **argv)
{
    if(argc == 1 && argv[1] == '-d')
    {
        //trigger launch of dialog
    }
}

```
The clue here, is that the arguments form the command line will be given to the main function. argc is the amount of argumnts given, while argv is the arguments them selves. Good luck!


You're basically right, but there are a couple of minor issues, both with the 'if' statement in main().  'argc' counts the name under which the program is invoked as the first argument, thus calling your prog with no actual args yields an argc value of 1 - so, a program called with one argument will have a value of 2 for argc in main().  Also, argv[] is a string ( more accurately an array of chars ), so the == operator generally won't work on it - the workaround is to use strcmp(), which compares strings, and returns zero if the two arguments are identical.  Thus, we arrive at:

```

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int main(int argc, char **argv)
{
    if(argc == 2 && !(strcmp(argv[1], '-d')))
    {
        //trigger launch of dialog
    }
}

```

---

### Post by dabear on 2006-08-04
> **KaeseEs said:**
> *snip*
Yeah, thanks, I've never programmed in C, but figured out I could give it a try :p

zootreeves; go for python instead, prototyping will generally be much faster :)

---

