---
title: "parse output of shell command in c++"
date: 2006-10-26
forum: Programming Talk
---

### Post by Lotharster on 2006-10-26
I'd like my c++ program to execute a shell command and then evaluate the results, like e. g.

execute "ls" and save the results in an variable. The system() command does not work since it echoes the results of the command to stdout.

Any ideas?

Regards,
Lotharster

---

### Post by duff on 2006-10-26
popen gives you a FILE * of the stdout.

---

### Post by IYY on 2006-10-27
In case you need more detail, here is a common example:

Where whichDir is a string containing the directory on which to call ls, sendme is a string into which the full command gets written, and result is the result string.

```
sprintf (sendme,"ls %s",whichDir);
fp = popen (sendme,"r");
fscanf (fp,"%s",result);
```

---

### Post by amo-ej1 on 2006-10-27
or you can have it write output to a named pipe and read from that pipe

---

### Post by tzulberti on 2006-10-27
Another way is to use system(command), for example: system("ls -a")

---

### Post by daller on 2008-02-03
> **IYY said:**
> In case you need more detail, here is a common example:

Where whichDir is a string containing the directory on which to call ls, sendme is a string into which the full command gets written, and result is the result string.

```
sprintf (sendme,"ls %s",whichDir);
fp = popen (sendme,"r");
fscanf (fp,"%s",result);
```

How do you define these variables? (I'm a C++ n00b)

---

### Post by a9bejo on 2008-02-03
This is C, but I guess it will serve as an example for popen:

[php]
#include "stdio.h"

int main(){
    FILE* fp;
    char result [1000];
    fp = popen("ls -al .","r");
    fread(result,1,sizeof(result),fp);
    fclose (fp);
    printf("%s",result);
    return 0;
}
[/php]

---

### Post by eolo999 on 2008-08-01
Should close a stream (file) opened with popen() with:

pclose(fp);

just a little thing, i know...

---

### Post by ghostdog74 on 2008-08-01
why do this when you can just do it in C++? See [here.](http://www.gnu.org/software/libc/manual/html_node/File-System-Interface.html#File-System-Interface)

---

### Post by lisati on 2008-08-01
> **ghostdog74 said:**
> why do this when you can just do it in C++? See [here.]("http://www.gnu.org/software/libc/manual/html_node/File-System-Interface.html#File-System-Interface")

I was a bit baffled at first, but "click click"........

I think the popen() option is an interesting one as it has application beyond just scanning a directory for files.

---

### Post by dwhitney67 on 2008-08-01
Beware that when using popen() you have no idea how much data is coming back at your application.  Rather than use a fixed-sized buffer on the stack to store the return data, it would be wiser to use a buffer allocated on from the heap.  If the buffer turns out to be too small, then you can allocate more memory.

Here's an example (in C):
[PHP]#include <stdio.h>
#include <stdlib.h>

int main()
{
  FILE *pfd = popen( "ls -R ~/", "r" );

  const size_t BUFSZ = 1024;
  char *buf = malloc( BUFSZ );
  size_t bufPos = 0;

  while (1)
  {
    bufPos += fread( buf+bufPos, 1, BUFSZ, pfd );

    if ( !feof(pfd) )
    {
      // more data available
      buf = realloc( buf, bufPos + BUFSZ );
    }
    else
    {
      break;
    }
  }
  pclose( pfd );

  printf( "buf =\n%s\n", buf );

  free( buf );

  return 0;
}[/PHP]
Feel free to choose a smaller or larger BUFSZ if you wish.

---

### Post by dwhitney67 on 2008-08-01
For those who prefer C++, here's something thrown together without too much thought given to the design or class/method names:
[PHP]#include <iostream>
#include <string>
#include <vector>
#include <algorithm>
#include <stdexcept>

#include <cstdio>
#include <cstdlib>


class ExecCommand
{
  public:
    ExecCommand( const std::string &cmd )
    {
      FILE *pfd = popen( cmd.c_str(), "r" );

      if ( pfd == 0 )
      {
        throw std::runtime_error( "Command or process could not be executed." );
      }

      while ( !feof(pfd) )
      {
        char buf[ 1024 ] = {0};

        if ( fgets(buf, sizeof(buf), pfd) > 0 )
        {
          m_results.push_back( std::string(buf) );
        }
      }
      pclose( pfd );
    }

    const std::vector<std::string>& getResults() const
    {
      return m_results;
    }

    friend std::ostream & operator<<( std::ostream &os, const ExecCommand &exec )
    {
      std::for_each( exec.m_results.begin(), exec.m_results.end(), ExecCommand::Displayer(os) );
      return os;
    }

  private:
    class Displayer
    {
      public:
        Displayer( std::ostream &os ) : m_os(os) {}

        void operator()( const std::string &str )
        {
          m_os << str;
        }

      private:
        std::ostream &m_os;
    };

    std::vector<std::string> m_results;
};


void displayString( const std::string &str )
{
  std::cout << str;
}


int main( int argc, char **argv )
{
  try
  {
    std::string cmd;

    for ( int i = 1; i < argc; ++i )
    {
      cmd += argv[i];
      cmd += " ";
    }

    // execute the cmd and store results
    //
    ExecCommand exec( cmd );

    // display the results
    //
    std::cout << exec << std::endl;

    // alternate way to get the results
    //
    // const std::vector<std::string> &results = exec.getResults();
    // std::for_each( results.begin(), results.end(), displayString );
  }
  catch ( std::exception &ex )
  {
    std::cerr << "Error: " << ex.what() << std::endl;
  }

  return 0;
}[/PHP]

---

### Post by ghostdog74 on 2008-08-02
one should try to write portable code. the program will fail if compiled in other platforms that doesn't have ls. Use the C libraries as far as possible.

---

### Post by dwhitney67 on 2008-08-02
Funny enough, the code works on both my Ubuntu and Fedora systems.  It's portable enough for me.  If you are referring that it should be portable to Windoze, then I think you missed the point of the assignment.

It wasn't just to list the contents of a directory (well yes, that's what the OP wanted), but the OP also stated that the popen() could be used for other purposes.  So I obliged to provide some code that can be used to capture the output of system commands... LINUX SYSTEM COMMANDS... in C and C++.  If you have a better way, then by all means implement it!

---

### Post by ghostdog74 on 2008-08-02
> **dwhitney67 said:**
> Funny enough, the code works on both my Ubuntu and Fedora systems. 
That's because "ls" is available in *nix systems.

>  If you are referring that it should be portable to Windoze, 
yes i am. There should be a way (makefile?) to compile the program using "dir" instead of "ls" in a windows environment if OP insist on using system calls. But why do that?
> 
then I think you missed the point of the assignment.

the OP did indicate he wants to list directory entries in C++ and I have shown better way using C libraries, so what point have i missed ?:)

> 
It wasn't just to list the contents of a directory (well yes, that's what the OP wanted), but the OP also stated that the popen() could be used for other purposes. 
did OP state that? 


> 
 If you have a better way, then by all means implement it!
see post #9

lastly, this is a very old thread., so i will just stop here.

---

### Post by dribeas on 2008-08-02
> **lisati said:**
> I was a bit baffled at first, but "click click"........

I think the popen() option is an interesting one as it has application beyond just scanning a directory for files.

You can use pipes (either named or unnamed) and redirect input/output from commands with dup2 system call. This will be more powerfull than popen() as it allows you to establish a two way communication with the program: you could use bc (or any other calculator) as a math backend for your application by redirecting input and ouput of bc to pipes and interacting through them. Or you could, as someone asked a couple of days ago, use mplayer controlled by your software. Just think of any interactive application that you might want to control.


   David

---

### Post by dwhitney67 on 2008-08-02
> **ghostdog74 said:**
> That's because "ls" is available in *nix systems.


yes i am. There should be a way (makefile?) to compile the program using "dir" instead of "ls" in a windows environment if OP insist on using system calls. But why do that?

the OP did indicate he wants to list directory entries in C++ and I have shown better way using C libraries, so what point have i missed ?:)


did OP state that? 



see post #9

lastly, this is a very old thread., so i will just stop here.
You're correct; my apologies... the OP was not the one that stated popen() could be used for other purposes; it was someone else.

If all one wants to do it examine the directory structure, then yes, using opendir() and readdir() are probably the best solutions.  However, if I want to run a different command, say the an 'ifconfig eth0', then the popen() solution provides a nifty way to get the output of that command directly into a C/C++ application.

Anyhow, don't think that 'ls' is the only command supported by the code I wrote earlier.  Run the application (perhaps only on a Linux platform) for other one-way commands.  In the C++ example, you can enter a command on the command-line.  For instance:
```
$ g++ exec_cmd.cpp -o exec_cmd
$ exec_cmd "ifconfig eth0"
```

---

### Post by dwhitney67 on 2008-08-02
> **dribeas said:**
> You can use pipes (either named or unnamed) and redirect input/output from commands with dup2 system call. This will be more powerfull than popen() as it allows you to establish a two way communication with the program: you could use bc (or any other calculator) as a math backend for your application by redirecting input and ouput of bc to pipes and interacting through them. Or you could, as someone asked a couple of days ago, use mplayer controlled by your software. Just think of any interactive application that you might want to control.


   David
Can you please provide a snippet of code (or a complete application) that employs the use of dup2(), so that one could say, interface with 'bc'?

---

### Post by ghostdog74 on 2008-08-02
> **dwhitney67 said:**
>  However, if I want to run a different command, say the an 'ifconfig eth0', then the popen() solution provides a nifty way to get the output of that command directly into a C/C++ application.
[/CODE]
using C++ networking libraries to get IP/mac address should be the way to go. The only reason why i think i need popen() is I really have no choice. Furthermore, I would just write a simple script to execute ifconfig, than to write a C++ program to call it.

---

### Post by dwhitney67 on 2008-08-02
> **ghostdog74 said:**
> using C++ networking libraries to get IP/mac address should be the way to go. The only reason why i think i need popen() is I really have no choice. Furthermore, I would just write a simple script to execute ifconfig, than to write a C++ program to call it.
Yes, using a library, whether in C or C++, would be the way to go.  Care to tell me if this library exists?  If it does, I am not aware of it.

What is the point of writing a script to call ifconfig, if you can use the system() library call?  The issue at hand is not how to run a system command from a C/C++ application, but how to get the output back into the C/C++ application so that it can be used.  The system() call only returns whether the command was issued or not; not whether it succeeded or failed, much less the output of the command.  Fundamentally, I think you are missing the bigger picture.

P.S.  I'm done with this thread unless you have something new to offer.

---

### Post by ghostdog74 on 2008-08-02
> **dwhitney67 said:**
> Yes, using a library, whether in C or C++, would be the way to go.  Care to tell me if this library exists?  If it does, I am not aware of it.

If you know Perl, you should have known CPAN. I am sure with C++, there will be such a depository somewhere that contains C++ networking libraries. I am not an expert in C++. [Just a](http://www.laurentconstantin.com/en/netw/netwib/)random search. Even libraries like net.h , inet.h , sockets.h , libc can be used. Whether or not we are able to find and use these libraries, my main point is to look for them first, instead of jumping straight to calling system commands. 
PS. I am also done.

---

