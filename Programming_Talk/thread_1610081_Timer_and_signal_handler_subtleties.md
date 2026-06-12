---
title: "Timer and signal handler subtleties"
date: 2010-10-31
forum: Programming Talk
---

### Post by erupter on 2010-10-31
I've been experimenting with timers.
Trying to grasp them.
I'm am able to create a virtual timer that works, but in the prospective of running my class in an autonomous thread, i would rather use a real timer.
But changing the type makes my program to exit printing "Alarm clock".

Also i tried to execute a private function of the class from within the signal handler, but the compiler says
"/home/erupter/Documents/working/digi_maxstream_24019_modem.cpp:26: error: invalid use of member ‘external_modem::fd’ in static member function
/home/erupter/Documents/working/digi_maxstream_24019_modem.cpp:191: error: from this location"

main.cpp ```

#include </home/erupter/Documents/working/digi_maxstream_24019_modem.cpp>
#include <stdlib.h>
#include <time.h>

int main (void) {
  int i,j,k;
  j=0;
  k=0;
  printf ("Initializing modem\n");
  
  for (i=0;i<100;i++){
    printf("Attempt %d\n",i+1);
    external_modem* ext_modem=new external_modem;

    if (ext_modem->initialised)
    {
      printf("Modem found on port %s\n",ext_modem->modem_com_port);
      j++;

    }
    else
    {
      printf("Modem not found\n");
      k++;
    }
    delete ext_modem;
  }
  printf("average hits %d/%d\n",j,k);

  return 0;
}
```digi_maxstream_24019_modem.cpp```

#include <assert.h>
#include <errno.h>
#include <fcntl.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <sys/dir.h>
#include <sys/param.h>
#include <sys/signal.h>
#include <sys/time.h>
#include <sys/types.h>
#include <termios.h>
#include <unistd.h>

#ifndef TRUE
  #define TRUE 1
#endif
#ifndef FALSE
  #define FALSE 0
#endif

class external_modem
{
  private:   
    char pathname[MAXPATHLEN];
    int fd;
    speed_t BAUDRATE;
    struct sigaction sa;
    struct itimerval timer;

  
  public:
    bool initialised;
    char bitrate[8];
    char modem_com_port[MAXPATHLEN];
  
  private:
    int initport(int fd)
    {
      struct termios options;
      tcgetattr(fd, &options);
      cfsetispeed(&options, BAUDRATE);
      cfsetospeed(&options, BAUDRATE);
      options.c_cflag |= (CLOCAL | CREAD);
      options.c_cflag &= ~PARENB;
      options.c_cflag &= ~CSTOPB;
      options.c_cflag &= ~CSIZE;
      options.c_cflag |= CS8;
      tcsetattr(fd, TCSANOW, &options);
      return 1;
    };
    
    
    int writeport(int fd, char *chars)
    {
      int len = strlen(chars);
      int n = write(fd, chars, strlen(chars));
      if (n < 0) {
          return 0;
      }
      return 1;
    };
    
    
    int readport(int fd, char *result)
    {
      int iIn = read(fd, result, 254);
      result[iIn-1] = 0x00;
      if (iIn < 0) 
              return 0;
                
      return 1;
    };

    static int file_select (const struct direct *entry)
    {
      if ((strcmp(entry->d_name, ".") == 0) || (strcmp(entry->d_name, "..") == 0))
    return (FALSE);
      if ( (strncmp(entry->d_name,"ttyS",4) == 0) || (strncmp(entry->d_name,"ttyUSB",6) == 0))
    return (TRUE);
      else
    return(FALSE);
    };



    int find_modem (char *return_str)
    {
      int count,i,j;
      struct direct **files;
      char portstring[13];
      strcpy(pathname,"/dev/");
      count =  scandir(pathname, &files, file_select, alphasort);
      if (count <= 0)
      {
    return -1;
      }

      for (i=1;i<count+1;i++)
      {
    strcpy(portstring,"");
    strcpy(portstring,"/dev/");
    if (strncmp(files[i-1]->d_name,"ttyS",4) == 0)
      strncat(portstring,files[i-1]->d_name,5);
    if (strncmp(files[i-1]->d_name,"ttyUSB",6) == 0)
    {
      strncat(portstring,files[i-1]->d_name,7);
    }
    if ((fd = open(portstring, O_RDWR | O_NOCTTY | O_NDELAY)) != -1)
    {
      fcntl(fd, F_SETFL, FNDELAY); // don't block serial read
      initport(fd);
      
      char sCmdStr[MAXPATHLEN]={"+++"};
      char sCmdRes[MAXPATHLEN]={"\0"};
      usleep(500000);
      if (writeport(fd,sCmdStr))
      {
        
        
        usleep(1000000);
        if (readport(fd,sCmdRes)) {
          
          if(strcmp(sCmdRes,"OK") == 0){
        strcpy(sCmdStr,"ATHV\r");
        usleep(90000);
        if (writeport(fd,sCmdStr)){
          usleep(90000);
          if(readport(fd,sCmdRes)) {
            int vid;
            vid=atoi(sCmdRes);
            if (vid == 611) {
              strcpy(modem_com_port,files[i-1]->d_name);
              printf("DiGi xStream 24-019 found on %s.\n",modem_com_port);
              strcpy(sCmdStr,"ATCN\r");
              usleep(90000);
              writeport(fd,sCmdStr);
              break;
            }
            
          }
        }
          }
        }
      }
      else
        close(fd);      
    }

    close(fd);
    if (i==count)
    {
      return 1;
    }
      }
      strcpy(return_str,modem_com_port);
      return 0;
    };
    
    static void timer_handler (int signum)
    {
      static int count = 0;
      count++;
      if (!(count % 100))
    printf("ok\n");
      writeport(fd,"test");
    };
    
    void timer_setup (int usec)
    {
   
    memset (&sa, 0, sizeof (sa));
    sa.sa_handler = &timer_handler;
    sigaction (SIGVTALRM, &sa, NULL);

   
    timer.it_value.tv_sec = 0;
    timer.it_value.tv_usec = usec;
   
    timer.it_interval.tv_sec = 0;
    timer.it_interval.tv_usec = usec;
    
    setitimer (ITIMER_REAL, &timer, NULL);

    };
    


  public:

    external_modem(void)
    {
      
      initialised=FALSE;
      BAUDRATE=B19200;
      strcpy(bitrate,"19200");
      strcpy(pathname,"/dev/");
      if (!find_modem (modem_com_port)) {
    initialised=TRUE;
    timer_setup(10000);

      }

    };
    
    external_modem(int command)
    {
      int pause;
      initialised=FALSE;
      strcpy(pathname,"/dev/");
      switch (command)
      {
    case 4800:
      BAUDRATE=B4800;
      strcpy(bitrate,"4800");
      pause=40000;
      break;
    case 9600:
      BAUDRATE=B9600;
      strcpy(bitrate,"9600");
      pause=20000;
      break;
    case 19200:
      BAUDRATE=B19200;
      strcpy(bitrate,"19200");
      pause=10000;
      break;
    case 38400:
      BAUDRATE=B38400;
      strcpy(bitrate,"38400");
      pause=5000;
      break;
    case 57600:
      BAUDRATE=B57600;
      strcpy(bitrate,"57600");
      pause=2500;
      break;
    case 115200:
      BAUDRATE=B115200;
      strcpy(bitrate,"115200");
      pause=1000;
      break;
    default:
      BAUDRATE=B19200;
      strcpy(bitrate,"19200");
      pause=10000;
      break;
      }
      if (!find_modem (modem_com_port))
      {
    initialised=TRUE;
    timer_setup(pause);
    
      }
      
    };
    
    ~external_modem(void)
    {
      if (initialised)
    close (fd);
      
      
    };
    
    int set_speed(int command)
    {
      switch (command)
      {
    case 4800:
      BAUDRATE=B4800;
      strcpy(bitrate,"4800");
      break;
    case 9600:
      BAUDRATE=B9600;
      strcpy(bitrate,"9600");
      break;
    case 19200:
      BAUDRATE=B19200;
      strcpy(bitrate,"19200");
      break;
    case 38400:
      BAUDRATE=B38400;
      strcpy(bitrate,"38400");
      break;
    case 57600:
      BAUDRATE=B57600;
      strcpy(bitrate,"57600");
      break;
    case 115200:
      BAUDRATE=B115200;
      strcpy(bitrate,"115200");
      break;
    default:
      BAUDRATE=B19200;
      strcpy(bitrate,"19200");
      break;
      }
      initport(fd);
      
    };
    
    int initialize (void)
    {
      initport(fd);
            
    };
  
};






```

---

### Post by dwhitney67 on 2010-10-31
First of all, nip the practice of specifying a relative path to an include file.  Use the -I GCC compiler option to specify the path(s) to where your header files reside.  Oh, and don't include .cpp files; only .h files.
```

/* BAD PRACTICE */
#include </home/erupter/Documents/working/digi_maxstream_24019_modem.cpp>

```

Second, try to avoid mixing C and C++.

Third, when posting code, take out all of the commented out (ie non-relevant) code from your posting.  It is distracting, and oftentimes would lead to the compiler to generate an error if it were included.

In the timer_setup(), fix the comments that related to 250ms.  That is incorrect; it should be something relevant to the parameter passed in, which by the variable name chosen, appears to be in units of microseconds (not milliseconds).

Now, as for your question, you cannot access your class object instance from the signal handler's function because it is, and must be, declared as static.  The function will not have any idea of the class instance.

There are two ways around the problem, for which I will discuss one approach here... use a semaphore, and set (or increment) it each time the timer expires.  This semaphore will need to be declared static.  Then somewhere in a "main-loop", you will need to examine the value of this semaphore; when it is at a certain value, then do something (eg. write).  Don't forget to clear the semaphore (or decrement it) after performing the operation.

P.S.  Read about what a semaphore is [here]("http://en.wikipedia.org/wiki/Semaphore_%28programming%29").


P.S.  If you application will only ever handle one MODEM, then there are alternatives to the approach above.  Hint:  Singleton pattern.

---

### Post by erupter on 2010-10-31
> **dwhitney67 said:**
> First of all, nip the practice of specifying a relative path to an include file.  Use the -I GCC compiler option to specify the path(s) to where your header files reside.  Oh, and don't include .cpp files; only .h files.

Well... right now i'm including it like this, but i would like it to become a standalone library. So it should be compiled by itself. That's why i'm using a main to call it.

> **dwhitney67 said:**
>  Second, try to avoid mixing C and C++.
Next to impossible as i never studied c++, only c.
I wouldn't even know what is strictly c in the code above and subsequently what would need to be changed.
I'm trying to learn but i don't expect to never make errors.
And besides i don't have noone to point out my errors in real time so...

> **dwhitney67 said:**
> 
There are two ways around the problem, for which I will discuss one approach here... use a semaphore, and set (or increment) it each time the timer expires.  This semaphore will need to be declared static.  Then somewhere in a "main-loop", you will need to examine the value of this semaphore; when it is at a certain value, then do something (eg. write).  Don't forget to clear the semaphore (or decrement it) after performing the operation.

P.S.  Read about what a semaphore is [here]("http://en.wikipedia.org/wiki/Semaphore_%28programming%29").


P.S.  If you application will only ever handle one MODEM, then there are alternatives to the approach above.  Hint:  Singleton pattern.

My application will eventually do LOTS of things, having to communicate with an external modem is just one of many things.
That's why i'd like the modem class to be independent, that way i can link to the appropriate class for each modem, and have it poll the modem by itself outside of my application and eventually generate a custom signal of "data available".

And why does it quit if i change ITIMER_VIRTUAL to ITIMER_REAL?

---

### Post by Arndt on 2010-10-31
> **erupter said:**
> 

Next to impossible as i never studied c++, only c.
I wouldn't even know what is strictly c in the code above and subsequently what would need to be changed.


I probably misunderstand what you mean, but your code is C++, so it surely is C++ you should study.

> **erupter said:**
> 
And why does it quit if i change ITIMER_VIRTUAL to ITIMER_REAL?

The manual page for 'setitimer' says this:

```
       ITIMER_REAL    decrements in real time, and delivers SIGALRM upon expi&#8208;
                      ration.

       ITIMER_VIRTUAL decrements only  when  the  process  is  executing,  and
                      delivers SIGVTALRM upon expiration.
```

So, when you change the type, you should also catch a different signal.

---

### Post by erupter on 2010-10-31
> **Arndt said:**
> I probably misunderstand what you mean, but your code is C++, so it surely is C++ you should study.

Please point me to something that is explicitly wrong in c++.

---

### Post by dwhitney67 on 2010-10-31
> **erupter said:**
> Please point me to something that is explicitly wrong in c++.

Nothing is explicitly wrong, but you could consider using the C++ library to your advantage rather than dwelling on using C-style functions such as strcmp(), strcpy(), printf(), etc.

I've attached a tarball with your code revamped.  It still needs some TLC, but it is in a better shape than what you have presented.

P.S. #1:  You never did indicate what you needed your timer to do, so in the version I have attached, the signal handler is doing squat.

P.S. #2:  "My application will eventually do LOTS of things..." is not a steadfast requirement.  Avoid making a "kitchen sink" out of your application.

---

### Post by erupter on 2010-10-31
> **dwhitney67 said:**
> 
P.S. #2:  "My application will eventually do LOTS of things..." is not a steadfast requirement.  Avoid making a "kitchen sink" out of your application.

My "application" will eventually be the controller (as in "[control system](http://en.wikipedia.org/wiki/Control_system)") of an autonomous robot. Will have to process all sorts of data and determine actions.
Communicating with the environment is but one of many tasks, and not a particularly high priority one.
I'll now have a look at your code.

---

### Post by erupter on 2010-10-31
Ok I'm beginning to understand.
It's much easier this way, but i did not know all the strings manipulation possibilities available.
this way you also taught me how to build a library, and that will be very useful.
Right now I'm fighting with it because it refuses to work.

1st of all the correct return string is "OK\r", otherwise the confront fails.
But nevertheless, looking at what happens with DDD, it totally jumps that part of the code and fails modem detection.
Anyway this is just a thingie in the code, the important part is how you wrote it.
I'll take inspiration so to speak :popcorn:

---

### Post by dwhitney67 on 2010-10-31
There also may be an issue with how I implemented readPort().  A better, yet still incomplete, approach is as follows:
```

// In the header file...

bool readPort(char* data, const size_t numBytes);


// and in the implementation file...

bool
DigiModem::readPort(char* data, const size_t numBytes)
{
   return read(fd, data, numBytes) > 0;
}

```
Note that I changed the method signature (ie return value), and also modified the return statement in the method.


P.S.  "Incomplete" means that the method does not check for anomalies.  If you set up the port to be non-blocking, and attempt a read when no data is present, a -1 is returned.  This is NOT an error... it is just an indicator that there is no data.  Always check errno; if no data is present, errno will be equal to EWOULDBLOCK.

---

### Post by erupter on 2010-11-03
> **dwhitney67 said:**
> There also may be an issue with how I implemented 
[...]


I've been doing my homework, and have re-writed my program a bit.
I'm trying to put some functions in a separate library.
For this purpose i created an h and cpp files and a makefile.
If i use the makefile alone, the library gets made.
But using the first makefile does not link to the second library, instead it produces a new library with static links inside.
I suppose it's something inside the makefile, but i've not been able to understand.

I'm unable to determine if i'm doing thigs right as the Make output is unclear wether it's linking or not.

Also i get a warning about a function declared but never defined, but the definition is clearly in the cpp. 
And a thing is not clear to me:
if i link to an external library and then modify a function inside the library, rebuilding it.
Why do i have to rebuild the main?
I expected a behaviour similar to that of DLLs under Windows.
Could you help me?

My actual source is below.
Thank you.

---

### Post by dwhitney67 on 2010-11-03
In your library, fix the following:

DigiModem.cpp:
```

bool DigiModem::readPort(std::string *result)
{
  char mystr[MAXPATHLEN] = {0};
  ...
}

```

ServiceFunctions.h (no need for 'static'):
```

int FileSelect(const dirent* entry);

```

ServiceFunctions.cpp (again, no need for 'static'):
```

int FileSelect(const dirent* entry)

```

P.S.  Why are you arbitrarily choosing MAXPATHLEN to be the size of the buffer?  The buffer will not contain a file-path, will it?

P.S #2 Whether in C or C++, if you have a "free-floating" function that you do not want external modules to reference, then you use the static keyword to qualify the function.  But bear in mind that a static function declaration should never appear in a header file!

---

### Post by erupter on 2010-11-03
> **dwhitney67 said:**
> P.S.  Why are you arbitrarily choosing MAXPATHLEN to be the size of the buffer?  The buffer will not contain a file-path, will it?

P.S #2 Whether in C or C++, if you have a "free-floating" function that you do not want external modules to reference, then you use the static keyword to qualify the function.  But bear in mind that a static function declaration should never appear in a header file!

PS #1 : That was just lazyness.
PS #2 : mmm... mumble mumble...

Using "static" means that, even if I load that module/library/class, it would not show as a member of the object? But would be available internally.
But this would be the purpose of private/public.
Private methods can't be referenced externally, but then I fail to understand the purpose of static.
Anyway I'll look it up on the net.

Changing topics: did you make the Makefile manually or did you use some program or interface?
I'm reading around about how Makefiles are made but i still haven't encountered any article describing something like yours.
Is there a way to print the actual commands that the script generates?

---

### Post by dwhitney67 on 2010-11-03
> **erupter said:**
> 
Using "static" means that, even if I load that module/library/class, it would not show as a member of the object? But would be available internally.
But this would be the purpose of private/public.
Private methods can't be referenced externally, but then I fail to understand the purpose of static.
Anyway I'll look it up on the net.

The functions that I asked you to correct are not part of a class; they are, as I call it, "free-floating" functions, that can be accessed by any module, within the library or the application.  If you wish to prevent other modules from accessing a particular function, then you declare it as static within the module where it is _implemented_.  Is this clear?  If so, hopefully the notion that one would not "advertise" said function in a header file is also clear.

> **erupter said:**
> 
Changing topics: did you make the Makefile manually or did you use some program or interface?
I'm reading around about how Makefiles are made but i still haven't encountered any article describing something like yours.
Is there a way to print the actual commands that the script generates?
I wrote the Makefile manually.  If you wish to see the actual commands, remove the @ symbols from where CXX is used (should be two places).


P.S.  In the context of a C++ class (and come to think of it, in Java too), the static keyword is used to denote methods and member data that are available regardless of whether a class object is instantiated or not.  All instantiations share the same static members/functions.  You can guard against access using the protected/private attributes.

---

