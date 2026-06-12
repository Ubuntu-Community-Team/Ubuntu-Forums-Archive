---
title: "How to wrap a GUI around a commandline program?"
date: 2010-02-08
forum: Programming Talk
---

### Post by resander on 2010-02-08
The commandline program CCC accepts commands from its stdin and generates results on its stdout. The source code is not available for CCC, only the binary.

The GUI program GGG uses its stdin and stdout for input and output communication with CCC. GGG stdin connects to the output of CCC and GGG stdout connects to CCC stdin like pipes. GGG starts CCC. The source has to be written for GGG. 

GGG catches GUI events which are translated to to CCC input commands that are sent on GGG stdout and GGG stdin data goes to GUI widgets.

I am not sure how to make this 'crossed-cable' type of connection between GGG and CCC. 

Here is an incomplete starter main for GGG:

```

int main ( int argc , char * argv[] )
   {
   pid = fork ( ) ;
   if ( pid == 0 ) // child process
      {
      execl ( "CCC" , ... ) ; // starts process for comandline CCC
      }
   else if ( pid != -1 )  // the gui process
      {
      init_GUI() ;
      // what goes in here for the crossed-cable stuff?
      }
   return 0 ;
   }

```

Is the main above a reasonable approach? or are there better ways?

---

