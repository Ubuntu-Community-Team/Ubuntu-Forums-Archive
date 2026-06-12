---
title: "Can't start other process from &quot;gnome-terminal&quot;, started by &quot;execv&quot;."
date: 2011-12-03
forum: Programming Talk
---

### Post by lemik on 2011-12-03
Hello, i tried to start other process from "gnome-terminal" as it's written in "help":
gnome-terminal -e "other_program".
From terminal, manually, it works well - starts new window with "gnome-terminal" in it and executes the "other_program" in this new window.
Then I tried to start it from code:

.............
pid_t child_pid;
char* pArgv [] = {"-e", "other_program", NULL};
................
child_pid = fork();
if ( 0 == child_pid )
{
    execvp ( "gnome-terminal", pArgv );
}
...........
After execution this line I have new open window for "gnome-terminal", but "other_program" did not executed.
I tried different versions of the "exec" functions, but without success.
What I do wrong? How can I start new terminal window and execute some program in it from C-code?
Than you in advance.

---

### Post by Arndt on 2011-12-03
> **lemik said:**
> Hello, i tried to start other process from "gnome-terminal" as it's written in "help":
gnome-terminal -e "other_program".
From terminal, manually, it works well - starts new window with "gnome-terminal" in it and executes the "other_program" in this new window.
Then I tried to start it from code:

.............
pid_t child_pid;
char* pArgv [] = {"-e", "other_program", NULL};
................
child_pid = fork();
if ( 0 == child_pid )
{
    execvp ( "gnome-terminal", pArgv );
}
...........
After execution this line I have new open window for "gnome-terminal", but "other_program" did not executed.
I tried different versions of the "exec" functions, but without success.
What I do wrong? How can I start new terminal window and execute some program in it from C-code?
Than you in advance.

The first (zeroth) element in argv is supposed to be the name of the program. Try with

```
char* pArgv [] = {"gnome-terminal", "-e", "other_program", NULL};
```

---

### Post by lemik on 2011-12-03
**Thanks a lot! It works!!!**=D>

---

### Post by lemik on 2012-01-06
Now I tried to set title to new-oped window by option: "--title=MyTitle"
.............
pid_t child_pid;
char* pArgv [] = {"-e", "other_program", "--title=MyTitle", NULL};
................
child_pid = fork();
if ( 0 == child_pid )
{
execvp ( "gnome-terminal", pArgv );
}
...........

and new title is not set :confused:

How can I open new terminal window with my title?
Thank you in advance.

---

### Post by ofnuts on 2012-01-06
> **lemik said:**
> Now I tried to set title to new-oped window by option: "--title=MyTitle"
.............
pid_t child_pid;
char* pArgv [] = {"-e", "other_program", "--title=MyTitle", NULL};
................
child_pid = fork();
if ( 0 == child_pid )
{
execvp ( "gnome-terminal", pArgv );
}
...........

and new title is not set :confused:

How can I open new terminal window with my title?
Thank you in advance.
```

char* pArgv [] = {"-e", "other_program", "--title", "MyTitle", NULL};

```
(likely)

---

### Post by lemik on 2012-01-06
Does not work: I get a message:
"Failed to parse arguments: Unknown option --titleMyTitle".

Sorry, I forgot "," after  "--title".

It was: char* pArgv [] = {"-e", "other_program", "--title" "MyTitle", NULL}; 

But any way: 

char* pArgv [] = {"-e", "other_program", "--title", "MyTitle", NULL}; 

does not display new title.

---

### Post by lemik on 2012-01-06
Actually, for a half of second I can see the new title, but it instantly changes to directory, that I start process from.

---

