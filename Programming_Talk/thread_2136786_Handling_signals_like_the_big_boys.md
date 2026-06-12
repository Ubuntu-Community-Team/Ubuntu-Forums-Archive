---
title: "Handling signals like the big boys"
date: 2013-04-18
forum: Programming Talk
---

### Post by tkks on 2013-04-18
Hi All,

I am still trying to write a custom shell and I want to handle SIGINT and SIGTSTP, so I assigned them handlers:

```

signal(SIGINT, sigint_handler);
signal(SIGTSTP, sigtstp_handler);

```

The problem is that I get the user input with fgets() :

```

fgets(lineSize, MAX_LINE_SIZE, stdin);

```

When waiting for the user input if I press CTRL+z or CTRL+c the handlers will not be invoked until I press ENTER.

And when I am waiting on a running a command like so:

```

pID=fork();
if(pID ==-1){
    printf("error...");
    return;
} else if(pID == 0) {
    execvp(args[0], args);
    printf("error...");
    return;
} else {
    wpID=wait(&status);
    if(wpID == -1){
        printf("error...");
    }
    return;
}

```

 And I press CTRL+z or CTRL+c the handlers are not invoked at all and the program gets stuck.

Anybody has an idea what the problem might be?

Thanks a lot

---

