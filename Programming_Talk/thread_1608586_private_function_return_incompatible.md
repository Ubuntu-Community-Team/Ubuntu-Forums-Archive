---
title: "private function return incompatible"
date: 2010-10-29
forum: Programming Talk
---

### Post by erupter on 2010-10-29
I'm developing a class to interface an RF modem.
```

#include <errno.h>
#include <fcntl.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <sys/dir.h>
#include <sys/param.h>
#include <sys/signal.h>
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
    char modem_com_port[MAXPATHLEN];
    int fd;
    speed_t BAUDRATE;
  
  public:
    bool initialised;
    char bitrate[8];
  
  public:
    external_modem(void);
    external_modem(int command);
    ~external_modem(void);
    int set_speed(char *command);
    int initialize (void);
  
  private:
    int initport(int fd);
    int writeport(int fd, char *chars);
    int readport(int fd, char *result);
    int file_select (const struct direct *entry);
    int find_modem (char *return_str);
  
};

external_modem::external_modem(void )
{
  BAUDRATE=B19200;
  strcpy(bitrate,"19200");
  strcpy(pathname,"/dev/");

};

external_modem::external_modem(int command)
{
  strcpy(pathname,"/dev/");
  switch (command)
  {
    case 1200:
      BAUDRATE=B1200;
      strcpy(bitrate,"1200");
      break;
    case 1800:
      BAUDRATE=B1800;
      strcpy(bitrate,"1800");
      break;
    case 2400:
      BAUDRATE=B2400;
      strcpy(bitrate,"2400");
      break;
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
};

external_modem::~external_modem(void )
{

};

int external_modem::initport(int fd)
{
  struct termios options;
  // Get the current options for the port...
  tcgetattr(fd, &options);
  // Set the baud rates to 19200...
  cfsetispeed(&options, BAUDRATE);
  cfsetospeed(&options, BAUDRATE);
  // Enable the receiver and set local mode...
  options.c_cflag |= (CLOCAL | CREAD);

  options.c_cflag &= ~PARENB;
  options.c_cflag &= ~CSTOPB;
  options.c_cflag &= ~CSIZE;
  options.c_cflag |= CS8;

  // Set the new options for the port...
  tcsetattr(fd, TCSANOW, &options);
  return 1;
};

int external_modem::writeport(int fd, char *chars)
{
  int len = strlen(chars);
  //chars[len] = 0x0d; // stick a <CR> after the command
  //chars[len+1] = 0x00; // terminate the string properly
  int n = write(fd, chars, strlen(chars));
  if (n < 0) {
//         fputs("write failed!\n", stderr);
      return 0;
  }
  return 1;
};

int external_modem::readport(int fd, char *result)
{
  int iIn = read(fd, result, 254);
  result[iIn-1] = 0x00;
  if (iIn < 0) {
//         if (errno == EAGAIN) {
//             printf("SERIAL EAGAIN ERROR\n");
          return 0;
//         } else {
//             printf("SERIAL read error %d %s\n", errno, strerror(errno));
//             return 0;
//         }
  }                    
  return 1;
};

int external_modem::file_select (const struct direct *entry)
{
// char *ptr;
if ((strcmp(entry->d_name, ".") == 0) || (strcmp(entry->d_name, "..") == 0))
  return (FALSE);
//   ptr = strrchr(entry->d_name, '.');
//   if ((ptr != NULL) && ((strcmp(ptr, ".c") == 0) || (strcmp(ptr, ".h") == 0)  || (strcmp(ptr, ".o") == 0) ))
if ( (strncmp(entry->d_name,"ttyS",4) == 0) || (strncmp(entry->d_name,"ttyUSB",6) == 0))
  return (TRUE);
else
  return(FALSE);
};

int external_modem::find_modem (char *return_str)
{
  int count,i,j;
  struct direct **files;
  char portstring[13];

//       strcpy(portstring,"");
//     strcpy(portstring,"/dev/");
  strcpy(pathname,"/dev/");
  count =  scandir(pathname, &files, file_select, alphasort);
  if (count <= 0)
  {
    return -1;
  }
  
  
//   printf("COM ports = %d\n",count);
  for (i=1;i<count+1;i++)
  {
    strcpy(portstring,"");
    strcpy(portstring,"/dev/");
    if (strncmp(files[i-1]->d_name,"ttyS",4) == 0)
      strncat(portstring,files[i-1]->d_name,5);
    if (strncmp(files[i-1]->d_name,"ttyUSB",6) == 0)
    {
      strncat(portstring,files[i-1]->d_name,7);
//       strncat(portstring,files[i-1]->d_name[7],1);
    }
    if ((fd = open(portstring, O_RDWR | O_NOCTTY | O_NDELAY)) != -1)
    {
      fcntl(fd, F_SETFL,0);
      initport(fd);
      
      char sCmdStr[MAXPATHLEN]={"+++"};
      char sCmdRes[MAXPATHLEN]={"\0"};
      usleep(500000);
      if (writeport(fd,sCmdStr))
      {
    fcntl(fd, F_SETFL, FNDELAY); // don't block serial read
    usleep(1000000);
    if (readport(fd,sCmdRes)) {
      if(strcmp(sCmdRes,"OK") == 0){
        strcpy(sCmdStr,"ATHV\r");
        usleep(70000);
        if (writeport(fd,sCmdStr)){
          usleep(70000);
          if(readport(fd,sCmdRes)) {
        int vid;
        vid=atoi(sCmdRes);
        if (vid == 611) {
          strcpy(modem_com_port,files[i-1]->d_name);
          printf("DiGi xStream 24-019 found on %s.\n",modem_com_port);
          strcpy(sCmdStr,"ATCN\r");
          usleep(70000);
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
//       printf("No modem found.\n");
    }
  }
  strcpy(return_str,modem_com_port);
  return 0;
};

```I admit it's my fist strict c++ code, I'm fluent with ansi c and visual basic.net.
Compiling this gives me
```

external_modem.cpp: In member function ‘int external_modem::find_modem(char*)’:
external_modem.cpp:54: error: argument of type ‘int (external_modem::)(const dirent*)’ does not match ‘int (*)(const dirent*)’

```Which I am unable to correct as i don't understand completely why it ends up being a different type.
And even if, seen externally, it were a different type, since i'm calling it from inside the class it should not have a problem of scope or "privacy".
Why is this happening?

---

### Post by GeneralZod on 2010-10-29
It would have been helpful if you had marked the line where the error occurred :)

Assuming it is this one:

```

count =  scandir(pathname, &files, file_select, alphasort);

```

it is because file_select is a non-static member function of external_modem, and as such is not an ordinary function (it only "makes sense" when associated with an instance of external_modem) like the kind scandir is expecting.  The fact that it is private should be a non-issue.

Declaring file_select as static should do the trick.

Edit:

Incidentally, I'm not sure if you're practicing C++ here, but this is distinctly un-C++-ish code: lots of C-style strings and string manipulations; returning 1 and 0 instead of bools; etc.

Edit2:

VVV

Ok, fair enough :)

---

### Post by erupter on 2010-10-29
That solved it, thanks.

> **GeneralZod said:**
> Incidentally, I'm not sure if you're practicing C++ here, but this is distinctly un-C++-ish code: lots of C-style strings and string manipulations; returning 1 and 0 instead of bools; etc.

Yes I know.
First of all because, as i said, I've not been trained to c++.
Secondly because this is an adaptation of a working program coded in c.
So i just copied over the functions trying to adapt the declarations :P
No will of really re-writing it again.
But it will eventually get done while improving the functionality.
Right now this all just comes from a serial port test dummy program, but have to evolve in a real modem control class.
So i'm just at the beginning :popcorn:

---

