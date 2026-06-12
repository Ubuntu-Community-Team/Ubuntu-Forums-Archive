---
title: "open shell script on button click"
date: 2005-06-25
forum: Programming Talk
---

### Post by mtron on 2005-06-25
Hi! I started to learn some very basic programming and need some help please. i am working with anjuta to create a gui with some buttons.

When a button is clicked i want to run a shell script, that preforms some tasks.

I created the gui with glade, and added the "Clicked" Signal to the button, then i need to attach the actual funcion to the button and that's where i dunno what to do.

in the file "src/callbacks.c" 

is the line 
```
on_button1_clicked            (GtkButton       *button,
                                        gpointer         user_data)
{

}
```

so can someone tell me what to add that it opens a local script in a new terminal?

Thanks!

---

### Post by buffbikedude on 2005-06-26
1. Install the manpages-dev package.

2. Pull up the man page for "fork", that will show you how to start anther process. Also look at the "exec" man pages ("execv" is one).

Here is roughly what you'd write if you wanted to run "/home/user/bin/burnit" with the argument "pics":

```
#include <unistd.h>
#include <sys/types.h>
#include <sys/wait.h>

on_button1_clicked            (GtkButton       *button,
                                        gpointer         user_data)
{
    int status;
    if (fork() == 0) {
        execl("/home/user/bin/burnit", "pics");
    }
    wait(&status);
}
```

The control will return to the GUI after the script has been run.

---

### Post by buffbikedude on 2005-06-26
Actually, there's a much simpler way. This essentially does the same thing as what I wrote above. You can see more on "system" by typing "man system".

```
#include <stdlib.h>

on_button1_clicked            (GtkButton       *button,
                                        gpointer         user_data)
{
    system("/home/user/bin/burnit pics");
}
```

---

### Post by mtron on 2005-06-27
Perfect. Thanks a lot! 

one more question:

i want to attach a terminal in the gui (like in emelfm) to see the error when a script fails.

But i could not figure out which selector to use. Is it enough to use a scrolled window in the gui, and then attach a function to it that will display a terminal?

cheers

---

