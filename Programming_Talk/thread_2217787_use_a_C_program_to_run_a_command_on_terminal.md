---
title: "use a C program to run a command on terminal"
date: 2014-04-18
forum: Programming Talk
---

### Post by one_girl on 2014-04-18
I want to create a program in C language that would allow me to run a command in the terminal.and run a game and the code working the game correctlybut when the user want to run a command (shall)this error ShowsSegmentation fault (core dumped)why ????

---

### Post by tejashs on 2014-04-18
you can use gdb to step through your program and find out the problem.
Also its not good to call main() inside your program

---

### Post by one_girl on 2014-04-18
what you mean by (gdb)
I am new in Unix and in that program
and Last day of Submission is sooooon :confused:

---

### Post by ofnuts on 2014-04-19
GDB is a debugger. If you code in C this is a very useful tool that you should have learned to use. Otherwise putting printf() calls in your code to see the code paths and check the value is a good technique. Since you seem to go as far as printing the shell prompt the next suspect is your parse() function.

Edit: actually gets() returns without needing to enter an input... The explanation: when you get the choice number scanf() reads the digits and stops on the first non-digit character (the "\n"), leaving it in the buffer. So when gets() starts it reads that lingering EOL and doesn't wait for you input. Then your parse() function is called with an empty buffer.

PS: You should compile your code with a stricter warning level. You aren't even including the proper header files.

---

### Post by dwhitney67 on 2014-04-19
> **one_girl said:**
> what you mean by (gdb)
I am new in Unix and in that program
and Last day of Submission is sooooon :confused:

Obviously you are working on school work, but since it appears that you have made an effort, I suppose it is ok to offer hints and suggestions to you.

First of all, it would be helpful if you organized your program a little better.  In C (and in other languages), proper indentation of the code can make a HUGE difference between understanding the code and being successful in maintaining it (without introducing a bug).

Let's take your code, and for now, let's simplify it.  (Btw, always exercise the habit of writing a little bit of code, and then testing it.  Don't write a 1000 lines of code, and then begin testing.)
```

#include <stdio.h>

void displayMenu()
{
    printf("Welcome to CS408 Program . . .  \n");
    printf("We have 2 mode:\n\n");
    printf("1) Shell mode \n");
    printf("2) Game mode \n");
    printf("3) To close the program \n");
    printf("Enter the choice for mode: ");
}

void shell()
{
    printf("In shell mode...\n\n");
}

void game()
{
    printf("In game mode...\n\n");
}

int main()
{
    int exit = 0;

    while (!exit)
    {
        char line[32];
        int  choice;

        displayMenu();

        if (fgets(line, sizeof(line), stdin) != NULL)
        {
            if (sscanf(line, "%d", &choice) == 1)
            {
                switch (choice)
                {
                    case 1:
                        shell();
                        break;

                    case 2:
                        game();
                        break;

                    case 3:
                        exit = 1;
                        break;

                    default:
                        printf("\n**** Illegal choice; try again...\n\n");
                        break;
                }
            }
            else
            {
                printf("\n**** Illegal input; try again...\n\n");
            }
        }
        else
        {
            printf("\n**** Illegal input; try again...\n\n");
        }
    }

    printf("All done!\n");

    return 0;
}

```

As you can see from the code above, I've ripped out the *potentially* buggy code that you have written in x() -- which should more aptly be named shell(), and game().  The use of scanf() in the menu() function is a *poor* choice, but I'm not sure if your teacher has told you of this yet (for all I know, he/she is not that savvy of a programmer either).  Either way, it has been replaced with the use of fgets() and sscanf().

The reason for using fgets() -- and it will be apparent later -- is that when scanning input using scanf() for a particular type, say an int, the remaining newline character (which comes from pressing enter/return on your keyboard) is still in the standard-input buffer.

I've also opted to use a switch() in the code so as to manage the input choices a little better (should your teacher ask you to add more choices to the menu).  In summary, the code above should compile without issue, and should run just fine.

Now... onto the rest of the program.  Let's start off easy... with the game portion of it.  Replacing the incomplete game() function I presented earlier, with (most of) your code should yield the following:
```

...
#include <time.h>    /* for time() */
#include <stdlib.h>  /* for srand() */

#define GAME_LOWER_LIMIT 0
#define GAME_UPPER_LIMIT 100
...

void game()
{
    int  number;
    int  done = 0;
    char line[32];
    int  numGuesses = 0;

    srand(time(0));
    number = GAME_LOWER_LIMIT + rand() % (GAME_UPPER_LIMIT - GAME_LOWER_LIMIT + 1);

    while (!done)
    {
        printf("Guess a number between %d and %d: ", GAME_LOWER_LIMIT, GAME_UPPER_LIMIT);

        if (fgets(line, sizeof(line), stdin) != NULL)
        {
            int guess;

            if (sscanf(line, "%d", &guess) == 1)
            {
                if (number == guess)
                {
                    printf( "\nYou guessed correctly after %d times!\n\n", numGuesses);
                    done = 1;
                }
                else
                {
                    printf("Your guess was too %s.\nTry again: ", number < guess ? "high" : "low");
                    numGuesses++;
                }
            }
            else
            {
                printf("\nIllegal input; try again...\n\n");
            }
        }
        else
        {
            printf("\nIllegal input; try again...\n\n");
        }
    }
}
...

```
Again, note that I have replaced the direct use of scanf() with the fgets()/sscanf() combo.  This will allow for handling of erroneous input from the user.

Btw, note that I opted to define the macros (GAME_LOWER_LIMIT and GAME_UPPER_LIMIT) using all-cap lettering.  This follows the standard C convention, as should you when you develop C code.

Now... onto the shell() functionality.  Again I opted to use fgets() to ensure I processed user input as best as possible.
```

...
#include <string.h>    // for strncmp()
#include <unistd.h>    // for fork() and execvp()
#include <sys/wait.h>  // for wait()
...

void parse(char* line, char** argv)
{
    while (*line != '\0')
    {
        while (*line == ' ' || *line == '\t' || *line == '\n')
            *line++ = '\0';

        *argv++ = line;

        while (*line != '\0' && *line != ' ' && *line != '\t' && *line != '\n')
            line++;
    }
    *argv = '\0';
}

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

...

```

As you can see, the most pertinent changes to your code involved replacing bug-prone gets() and scanf() with the usage of fgets(), and when needed, sscanf().

The rest mainly involved cleaning up the formatting of the code to make it easier to read, and to introduce some additional error checking.  If you prefer to use the K&R style of coding, then go for it.  I personally prefer the GNU-style so that it makes the code easier to read and it makes it easier to match curly brackets.

P.S.  Did you develop the parse() function, or was this given to you by your teacher?  It is flawed (has a bug) and also does not check that there are fewer than 64 arguments associated with the command (e.g. "ls -l" has two args, the command and the option).

Here's a better parse() function, however it too does not check to see if there are fewer than 64 args:
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

---

### Post by one_girl on 2014-04-19
Thank you soooooooooooooooooooooooooooo much

For your helpppppppp


 :guitar:

---

### Post by one_girl on 2014-04-19
dwhitney67

could you please delete your Reply now
For security reason

and I want the Thread to be delete also

---

### Post by Iowan on 2014-04-19
> **one_girl said:**
> dwhitney67

could you please delete your Reply now
For security reason

and I want the Thread to be delete also
Why???
It might help someone else.
The only "Security" risk is that "your" answer is posted.

---

### Post by one_girl on 2014-04-19
ah ok

I told like that because u know 
this is problem for me If some one else in my class take the same code here
anyhow 
thank u allllllllllll so much 
^^

---

### Post by dwhitney67 on 2014-04-19
> **one_girl said:**
> ah ok

I told like that because u know 
this is problem for me If some one else in my class take the same code here
anyhow 
thank u allllllllllll so much 
^^

If you had not presented any code whatsoever in your OP, I would not have taken the time to help you with your class assignment.

The only reason why I did help you is because your code was mostly functional, with the exception of the usage of scanf() and gets().  I may have reorganized your original code a bit, but the gist of what I gave you came from your code.

You should take the time to understand why using scanf() to read in raw-input is a bad choice.  Similarly, you should understand why using gets() is frowned up.  Do some "Google" research on these topics and you will find plenty of commentary.

P.S.  You should also become familiar with 'gdb' (and possibly 'ddd', which is a GUI front-end to 'gdb').  This tool can help you debug your programs.  Typically to prep a program for debugging, you do something like this:
```

$ gcc -g MyProgram.c -o myprog

$ gdb ./mprog

# or

$ ddd ./myprog

```
From a beginner's stand-point, 'ddd' would probably be a better choice to use.  You will probably need to install it on your system, since it does not come with 'build-essential'.

---

### Post by one_girl on 2014-04-19
this is not class Assignment 
this is Part of the Operating System Project 
I now you take time and Effort to help me
and I know the low of that Website not allow to delete any Post Especially after it fixed 
&#1613;Sorry Forget that

I really appreciate your effort

OK, I will do as your Explain

:P

---

