---
title: "how to kill a fork()"
date: 2008-01-23
forum: Programming Talk
---

### Post by Elisei on 2008-01-23
hi everybody:

i am a bit stuck writing a small C program. basically i fork of a process
to execute a user submitted command that is executed by execvp().
but if the command that is submitted  runs forever, like "ping localhost" there is no way to stop it without stopping the actual program that calls execvp().
i am trying to figure out how to call kil(pid, SIGUSR1); so the prog recognises that it came from stdin while something like "ping localhost" is running & outputting to the screen.

it is confusing but i can post the code ...

---

### Post by dwhitney67 on 2008-01-23
If I understand your query correctly, you want to be able to fork a child process, use an exec-style call to replace the child-process with another, and provide the parent the capability to kill the child-process at will.

Here's one example:
[PHP]#include <unistd.h>
#include <sys/types.h>
#include <signal.h>
#include <stdio.h>

int main()
{
  pid_t childPID = fork();

  if ( childPID == -1 )
  {
    printf( "failed to fork child\n" );
    _exit( 1 );
  }
  else if ( childPID == 0 )
  {
    char *args[] = { "ping", "localhost", 0 };

    execv( "/bin/ping", args );
  }

  while ( 1 )
  {
    printf( "Enter 'q' to kill child process...\n" );
    char c = getchar();

    if ( c == 'q' )
    {
      kill( childPID, SIGKILL );
      break;
    }

    sleep( 1 );
  }

  return 0;
}[/PHP]

P.S.  Alternatively, in lieu of using kill(), you could opt to use the "-c" option with ping to limit the number of pings issued.

---

