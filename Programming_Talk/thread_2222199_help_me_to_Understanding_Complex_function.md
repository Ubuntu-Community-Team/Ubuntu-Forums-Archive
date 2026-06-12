---
title: "help me to Understanding Complex function"
date: 2014-05-05
forum: Programming Talk
---

### Post by one_girl on 2014-05-05
[B]
I Found some Useful function to my homework
but I want to Understand it so I can do something like it
[/B]

```

void parse(char* line, char** argv)
{
    if (line != NULL)
    {
        char* arg = strtok(line, " \t\n");


        while (arg != NULL)
        {
            *argv++ = arg;
            arg = strtok(NULL, " \t\n");
        }
    }
    *argv = NULL;
}

```


```

void execute(char** argv)
{
    pid_t pid;
    int   status;


    if ((pid = fork()) < 0)
    {
        printf("*** ERROR: forking child process failed\n");
        exit(1);
    }
    else if (pid == 0)
    {
        if (execvp(*argv, argv) < 0)
        {
            printf("*** ERROR: exec failed\n");
            exit(1);
        }
    }
    else
    {
        while (wait(&status) != pid);
    }
}

```


```

void shell()
{
    int  exit = 0;
    char line[1024];


    while (!exit)
    {
        printf("shell~ ");


        if (fgets(line, sizeof(line), stdin) != NULL)
        {
            char* argv[64] = {NULL};


            parse(line, argv);


            if (argv[0] != NULL && strlen(argv[0]) == 4 && strncmp(argv[0], "exit", 4) == 0)
            {
                exit = 1;
            }
            else
            {
                execute(argv);
            }
        }
    }
}

```

---

### Post by ofnuts on 2014-05-05
What is the question?

---

### Post by mörgæs on 2014-05-05
The purpose of Ubuntuforums is not to make others do your homework. Thread closed.

Please also let your other threads dealing with homework rest.

---

