---
title: "Execute code upon recieving ctrl-c"
date: 2006-08-02
forum: Programming Talk
---

### Post by Randomskk on 2006-08-02
Hey
In my C++ program, ideally I want to be able to execute one line of code when the program recives a ctrl-c from the terminal (or a kill <procname>), to erase the lock file I create when the program starts.
I realise lock files are not the most elegant way to do things, but it serves the purpose here well enough.

So, then - how can I have a line of code executed when the C++ application gets a ctrl-c?

Thanks

---

### Post by ylixir on 2006-08-03
#include <signal.h>
....
void callback_function(int bleh){...}
....
main()
  signal(SIGINT, callback_function);
...

something like that.  man signal might be appropriate, as it's been a while, but i think that will get you started at least.

---

### Post by Randomskk on 2006-08-03
Thanks!
That works perfectly.

---

### Post by ylixir on 2006-08-05
glad to hear it.

---

