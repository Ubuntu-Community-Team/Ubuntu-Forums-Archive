---
title: "[SOLVED] Checking whether a process runs or not - C++"
date: 2008-08-25
forum: Programming Talk
---

### Post by Amazona aestiva on 2008-08-25
Hi!

I need to check if an other process or application runs or not.

I mean something like:
bool IsThisRuns(string)

Thanks in advance

---

### Post by dwhitney67 on 2008-08-25
C++ is not a scripting language where you can easily obtain system runtime information.

Consider using something like the following to execute your command and get the results:
[PHP]#include <string>
#include <iostream>
#include <cstdio>


bool isProcessRunning( std::string processName )
{
  bool processRunning = false;

  std::string cmd( "/sbin/pidof " + processName );

  FILE *pfd = popen( cmd.c_str(), "r" );

  if ( pfd > 0 )
  {
    while ( !feof(pfd) )
    {
      char buf[ 1024 ] = {0};

      if ( fgets(buf, sizeof(buf), pfd) > 0 )
      {
        std::string result( buf );

        if ( result != "\n" )
        {
          processRunning = true;
        }
      }
    }
    pclose( pfd );
  }

  return processRunning;
}

int main( int argc, char **argv )
{
  if ( argc < 2 )
  {
    std::cout << "Usage: " << argv[0] << " <process-name>" << std::endl;
    return 1;
  }

  std::cout << "Process " << argv[1] << " is running: "
            << (isProcessRunning( argv[1] ) ? "true" : "false")
            << std::endl;

  return 0;
}[/PHP]

---

### Post by Amazona aestiva on 2008-08-25
Thanks dwhitney67! That works perfectly!:)

---

