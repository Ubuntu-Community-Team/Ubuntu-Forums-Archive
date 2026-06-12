---
title: "how to access help when i am not online"
date: 2010-02-16
forum: Programming Talk
---

### Post by rejuvenate on 2010-02-16
while writing code in C many times i need the syntax or little details of the command as there in turbo C compiler (F1 is for help just keep cursor on the keyword) 
in ubuntu i am using gcc compiler and vim editor


also in shell do we have any option to bring the drop down option when i write half the command as it happens in many visual compiler..
thnx in advance

---

### Post by sharpdust on 2010-02-16
> **rejuvenate said:**
> while writing code in C many times i need the syntax or little details of the command as there in turbo C compiler (F1 is for help just keep cursor on the keyword) 
in ubuntu i am using gcc compiler and vim editor

If you press shift + k in vim, it will try to find the man page for that entry.

For example, 

```
#include <string>
```

Move your cursor over the word string and press shift+k and the man page for string(3) will open up.


> **rejuvenate said:**
> also in shell do we have any option to bring the drop down option when i write half the command as it happens in many visual compiler..
thnx in advance

The way you have worded this, I assume you are not talking about vim anymore. If so, then you can just start typing and then press tab to get a list of potential matches to what you're looking for.

Example:

% who [TAB]
who    whoami whois

---

### Post by Zugzwang on 2010-02-16
@OP: Install the "manpages-dev" package. Then you can do what you want on the terminal (for the standard functions in C), e.g. if you type "man get" in the terminal and hit <TAB> twice, you will get a list of possible man pages:
```

user@machine:~/Stuff$ man get
getafm               getbkgd              getconf              getent               getmaxx              getnonfreefonts      getopt               getstr               getty                getyx
getbegx              getbkgrnd            getcurx              getfacl              getmaxy              getnonfreefonts-sys  getparx              getsyx               get_wch
getbegy              getcchar             getcury              getfdprm             getmaxyx             getnstr              getpary              gettext              getwin
getbegyx             getch                geteltorito          getkeycodes          getmouse             getn_wstr            getparyx             gettextize           get_wstr 
```
Then, you can, for example, complete your request to "man getstr", hit enter and you'll see the documentation for the "getstr" function.

---

### Post by rejuvenate on 2010-02-17
thnx...that was a great help.....

---

### Post by rejuvenate on 2010-02-17
can we also access a sample code with that bcoz this is there in turbo c compiler in windows and should also be there in linux...
thnx in advance....

---

