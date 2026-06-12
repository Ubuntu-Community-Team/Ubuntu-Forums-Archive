---
title: "Perhaps someone might find it usefull..."
date: 2005-06-22
forum: Programming Talk
---

### Post by Kimm on 2005-06-22
I wrote this program to run a game of mine, I cant realy write bash scripts but I know C++ pretty well so I fugured I can write something in C++ that does this instead.

I usualy write more advanced programs but this is just a handy little thing I made.
Its a program that launches a program along with all the arguments that you give it, Its realy a very silly program but I supose someone else might have use for it, if not else I supose you can just examine the code and perhaps learn something from it (if your a beginner). If you want it to run a different executable you have to change the code though

This runns Jedi Knight: Jedi Academy through cedega (see arg variable)

```

#include <stdlib.h>
#include <string.h>

int main(int argc, char *argv[])
{
	char arg[200] = "cd /home/kimm/Program/JKA\ncedega jamp.exe ";
	int argi = argc - 1, temp;
			
	if(argi != 0)
	{
		for(temp = 0;temp <= argi; temp++)
		{
			strcat(arg, argv[temp]);
			strcat(arg, " ");
		}
	}
		
	system(arg);
	
return 0;
}

```

---

### Post by LordHunter317 on 2005-06-22
There are much better ways of doing this, generally.  Look into the exec() family of calls.

---

### Post by Kimm on 2005-06-22
I supose, I do know most of the acctual C++... but when it comes to what Library to use and what all the functions do, I usualy stand clueless.

I tried looking for exec() on C++ without any luck, perhaps you can provide me with a link?

---

### Post by LordHunter317 on 2005-06-22
[QUOTE=Kimm]I tried looking for exec() on C++ without any luck, perhaps you can provide me with a link?[/QUOTE]Run 'apropos exec' on your system and you should get a series of POSIX standard calls with names like 'execle' and 'execvp'.

---

### Post by jerome bettis on 2005-06-22
yeah you should use fork and execvp and wait for the child process to return.

---

### Post by jerome bettis on 2005-06-23
i had to do this sort of thing about 6 months ago.  i found the file and wasn't satisfied with the way i was doing things back then so i reworked it a little bit.  any criticism or suggestions to improve code quality and even new features is welcome.

```
// shell.cpp
// a _very_ simple unix shell. 
// supports arguments but not > < | & or anything fancy like that yet
// 
// 1. read command from user
// 2. tokenize command and arguments
// 3. fork off a process
// 4. exec the command
// 5. wait for it to return
// 6. repeat until exit

#include <iostream>
#include <unistd.h>
#include <sys/types.h>
#include <sys/wait.h>
#include <string>
#include <sstream>
#define SIZE 100
using namespace std;

// reads a command from cin and tokenizes it for the args.
// places these tokens in supplied array
// returns the number of tokens
int getCmd(char** cmd)  { 
    const char* prompt = "$ ";
    cout << prompt;
    string buff;
    getline(cin, buff);
    istringstream is(buff);
    int j = 0;
    is >> buff;                                 // get token
    while (is)  {                               // while stream is good
        cmd[j] = new char;
        strncpy(cmd[j++], buff.c_str(), SIZE);  // copy to array
        is >> buff;
    }
    return j;
}

inline void forkFailed()  {
    cerr << "fork failed.\n";
    exit(1);
}

inline void excevpFailed(const char* str)  {
    cerr << str << ": command not found.\n";
    exit(1);
}

int main(int argc, char** argv)  {
    char** cmd = new char*[SIZE];
    pid_t childId, waitId;
    int childStat;
    int cmdSize = getCmd(cmd);                  // read a command
    while (strncmp(cmd[0], "exit", SIZE))  {    // go until exit
        childStat = 0;
        if ((childId = fork()) == -1)  {        // fork off another process
            forkFailed();
        } else if (childId == 0)    {           // execute command
            execvp(cmd[0], cmd);                // if the child gets to
            excevpFailed(cmd[0]);               // this line, something's wrong
        } else if (childId == (pid_t)(-1))  {
            forkFailed();
        } else  {                               // wait for child to return
            waitId = wait(&childStat);
        }
        for (int i = 0; i < cmdSize; i++)  {
            cmd[i] = NULL;
        }
        cmdSize = getCmd(cmd);
    }
    return 0;
}

```

---

