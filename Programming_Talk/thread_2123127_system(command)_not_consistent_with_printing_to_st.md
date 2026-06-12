---
title: "system(command) not consistent with printing to stdout"
date: 2013-03-07
forum: Programming Talk
---

### Post by IAMTubby on 2013-03-07
Hello,
I wrote a program which does something like
```

while(i<100)
{
 printf(some_message_indicating_what_system_command_I'mdoing);
 system(some system command);
 printf("\n");
}

```
When I do ./a.out > log.txt, I find that all my printf's are at the bottom of the file, and all the system command outputs are at the top of the file. **I would like to have them in sequential order so that I can know which system command is called when comparing outputs.**

Please advise.
Thanks.

PS : Consider I'm printing the ls output of dir1, dir2, etc, upto dir100 in a loop. As of now, I get an output something like(see below). So this doesn't tell me which dir contains which files.

-----------------------------------
file.txt
hello.txt
..
..
upto dir100 contents



printing dir1 contents
printing dir2 contents
printing dir3 contents
printing dir100 contents
-----------------------------------

---

### Post by r-senior on 2013-03-07
It's probably because the buffer for stdout is not flushed until you send the '\n'. Try putting '\n' at the end of the first printf.

---

### Post by IAMTubby on 2013-03-07
> **r-senior said:**
> It's probably because the buffer for stdout is not flushed until you send the '\n'. Try putting '\n' at the end of the first printf.
r-senior, thanks for the reply. But I have taken care of that. That used to be one of my frequent mistakes, but not anymore.
I also tried putting a sleep, but doesn't work.

At the moment, my code looks something like(below), within a while loop.
```

printf("command == [%s]\n",command);
    system(command);
    printf("\n");

```

---

### Post by dwhitney67 on 2013-03-07
Try this ordering of statements in your loop:
```

printf(...);
system(...);
fflush(stdout);    // this is key!

```

Here's an example:
```

#include <stdlib.h>
#include <stdio.h>

int main()
{
    const char* dirs[] = { "/etc",  "/usr/bin",  "/usr/sbin" };

    for (size_t i = 0; i < sizeof(dirs) / sizeof(const char*); ++i)
    {
        char cmd[1024];
        snprintf(cmd, sizeof(cmd), "ls %s", dirs[i]);

        printf("Listing the files within %s...\n",  dirs[i]);
        system(cmd);
        fflush(stdout);
        printf("\n\n");
    }

    return 0;
}

```

---

### Post by IAMTubby on 2013-03-07
> **dwhitney67 said:**
> 
fflush(stdout);    // this is key!

wow sir, that works :)

EDIT:I'm trying to "mark thread as solved". where do I do that ? need a couple of days to get acquainted with the new layout which is great :)

---

### Post by r-senior on 2013-03-07
You can't. It's currently broken with the upgrade. The workaround is to edit the title of the thread and prefix with [SOLVED].

---

### Post by IAMTubby on 2013-03-07
> **r-senior said:**
> You can't. It's currently broken with the upgrade. The workaround is to edit the title of the thread and prefix with [SOLVED].
Alright, I'll wait for it then. 
A small suggestion :  can we change the background color for posts from gray back to white ? Otherwise the site's great.

---

### Post by dwhitney67 on 2013-03-07
> **IAMTubby said:**
> Otherwise the site's great.
On the contrary... too much space is allocated for displaying one's avatar and forum metrics above each post.  I fail to see what was wrong with the previous version.

---

### Post by r-senior on 2013-03-07
+1 

I need to get a cooling fan for my mouse wheel.

---

### Post by ofnuts on 2013-03-07
The real problem is that the buffering of stdout varies with the type of the actual output. By default, if the output is a tty (ie, no redirection), stdout is line-buffered, and a "\n" in the stream forces a flush. Otherwise, it is block-buffered and you get output only when the buffer (usually 4K) is full, or when the stdout is closed or when the program exits...

There are functions to control buffering, so, instead of fflush()'ing left and right, you can use setlinebuf(stdin) at the beginning of the program and keep the rest of the code unchanged. See "man setvbuf" for the gory details.

---

### Post by IAMTubby on 2013-03-07
> **dwhitney67 said:**
> On the contrary... too much space is allocated for displaying one's avatar and forum metrics above each post.  I fail to see what was wrong with the previous version.
true. Also, it's not easy to make out where 1 post finishes and the next starts, we could give like a better border to show the division. I'll try mailing a few suggestions to the admin. (dwhitney67, I'm sorry, I'm not aware if you are one of them :) ). But since change is the only constant, I guess this is inevitable every now and then :)

> **r-senior said:**
> 
I need to get a cooling fan for my mouse wheel.
haha :D. yup, too much scrolling required.

---

### Post by trent.josephsen on 2013-03-08
> **ofnuts said:**
> The real problem is that the buffering of stdout varies with the type of the actual output. By default, if the output is a tty (ie, no redirection), stdout is line-buffered, and a "\n" in the stream forces a flush. Otherwise, it is block-buffered and you get output only when the buffer (usually 4K) is full, or when the stdout is closed or when the program exits...

Well, you learn something new every day. I guess I knew that already, but I never thought about how it would interact with system(). Thanks.

---

