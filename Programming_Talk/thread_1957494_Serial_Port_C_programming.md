---
title: "Serial Port C programming"
date: 2012-04-12
forum: Programming Talk
---

### Post by Z.K. on 2012-04-12
I was wondering if anyone could help me get a start on serial port programming.  I have no idea where to start actually and examples would be great.  I have looked all over the Internet but did not find anything useful.  I would prefer to do this in C or C++, but I might have to use python with I can't figure out how to do this in C.  I do have a C and C++ programming background, but not with Linux.  I did find a serial port library someone had written, but I could not get it to work.


I got the rs232.c and rs232.h files from [http://www.teuniz.net/RS-232/]("http://www.teuniz.net/RS-232/").  It is supposed to work for Linux and Windows.  The port seems to open fine as I don't get any errors, but nothing comes back.  I am using a PIC based USB serial device.  When I send ```
~ver~
``` I should get back > VER:1.31, but all I get is a series of received 0 bytes.

In a terminal it works fine.

:confused:

This is the code I used:
```

#include <iostream>
#include "rs232.h"

using namespace std;

int main()
{
    cout << "Hello world!" << endl;
    unsigned char data[8] = "~ver~\0";
    unsigned char buf[4095];
    int n = 0;

    cout << data << endl;


    if(OpenComport(16, 115200) == 0)
    {
        cout << "Comport Opened" << endl;

        for(int j=0;j< '\0' ;j++)
            SendByte(16, data[j]);

        while(1)
        {
            n = PollComport(16, buf, 4095);

            if(n > 0)
            {
              buf[n] = '\0';   // always put a "null" at the end 
                               //of a string! 

                  for(int i=0; i < n; i++)
                  {
                        if(buf[i] < 32)  // replace unreadable 
                                         // control-codes by dots
                        {
                          buf[i] = '.';
                        }
                  }
            }

              cout << "received " << n << " bytes: " << (char *)buf 
                                                          <<   endl;
        }



        CloseComport(16);
    }
    else
        cout << "Error opening Comport" << endl;

//cout << "received " << 4 << " bytes: " << 'k' << endl;

    return 0;
}

```

---

### Post by alexfish on 2012-04-12
don't see any thing in the *.c or the *.h which relates to the fd / how the ttys* is going to get configured

can have a look here then compare one to another

[http://www.comptechdoc.org/os/linux/programming/c/linux_pgcserial.html](http://www.comptechdoc.org/os/linux/programming/c/linux_pgcserial.html)

is there a reason for this to be done with c ,, next best alternative is to use tclsh

here is a simple tclsh serial port .. compare it whith the c test program
 so can test in tcl then can write similar in c



 ```
 if { [catch {set serial [open "/dev/ttyS1" RDWR]} fid] } {
           puts  "\n/dev/ttyS1: $fid \n"
        return
    } else {

    fconfigure $serial -mode "115200,n,8,1"
    fconfigure $serial -blocking 0 -buffering full -ttycontrol {RTS 0 DTR 1}
    after 500
#    set data [fconfigure $serial -ttystatus] can test the status lines here
#    puts "$tty : Status : $data"
        puts $serial "Hello world!"
        after 100
        flush $serial
        after 100
        set data [read $serial]
        puts $data
       close $serial
} 
```

---

### Post by Z.K. on 2012-04-12
> **alexfish said:**
> don't see any thing in the *.c or the *.h which relates to the fd / how the ttys* is going to get configured

can have a look here then compare one to another

[http://www.comptechdoc.org/os/linux/programming/c/linux_pgcserial.html](http://www.comptechdoc.org/os/linux/programming/c/linux_pgcserial.html)

is there a reason for this to be done with c ,, next best alternative is to use tclsh

here is a simple tclsh serial port .. compare it whith the c test program
 so can test in tcl then can write similar in c





Yes, I noticed that also so I started over and I have something now that kind of works.  It seems to open the serial port okay, but what it returns is just garbage.  Perhaps it is how I am trying to do the read.

new code:
```

#include <stdio.h> /* Standard input/output definitions */
#include <string.h> /* String function definitions */
#include <unistd.h> /* UNIX standard function definitions */
#include <fcntl.h> /* File control definitions */
#include <errno.h> /* Error number definitions */
#include <termios.h> /* POSIX terminal control definitions */




//Initialize serial port
int initport(int fd)
{
    int portstatus = 0;

    struct termios options;
    // Get the current options for the port...
    tcgetattr(fd, &options);
    // Set the baud rates to 115200...
    cfsetispeed(&options, B115200);
    cfsetospeed(&options, B115200);
    // Enable the receiver and set local mode...
    options.c_cflag |= (CLOCAL | CREAD);

    options.c_cflag &= ~PARENB;
    options.c_cflag &= ~CSTOPB;
    options.c_cflag &= ~CSIZE;
    options.c_cflag |= CS8;
    //options.c_cflag |= SerialDataBitsInterp(8);           /* CS8 - Selects 8 data bits */
    options.c_cflag &= ~CRTSCTS;                            // disable hardware flow control
    options.c_iflag &= ~(IXON | IXOFF | IXANY);           // disable XON XOFF (for transmit and receive)
    //options.c_cflag |= CRTSCTS;                     /* enable hardware flow control */


    options.c_cc[VMIN] = 0;     //min carachters to be read
    options.c_cc[VTIME] = 0;    //Time to wait for data (tenths of seconds)


    // Set the new options for the port...
    //tcsetattr(fd, TCSANOW, &options);


    //Set the new options for the port...
    tcflush(fd, TCIFLUSH);
    if (tcsetattr(fd, TCSANOW, &options)==-1)
    {
        perror("On tcsetattr:");
        portstatus = -1;
    }
    else
        portstatus = 1;


    return portstatus;
}


/*
* 'open_port()' - Open serial port 1.
*
* Returns the file descriptor on success or -1 on error.
*/
int open_port(void)
{
    int fd; /* File descriptor for the port */
    fd = open("/dev/ttyUSB0", O_RDWR | O_NOCTTY | O_NDELAY);

    if (fd == -1)
    {
        /*
        * Could not open the port.
        */
        perror("open_port: Unable to open /dev/ttyUSB0 --- \n");
    }
    else
        fcntl(fd, F_SETFL, 0);

    return (fd);
}

int main(void)
{

    int serial_fd = open_port();

    if(serial_fd == -1)
        printf("Error opening serial port /dev/ttyUSB0 \n");
    else
    {
        printf("Serial Port /dev/ttyUSB0 is now open \n");

        if(initport(serial_fd) == -1)
        {
            printf("Error Initializing port");
            close(serial_fd);
            return 0;
        }

        sleep(.5);
        //usleep(500000);
        //printf("size of data being sent = %ld", sizeof("~ver~\n\r"));

        int n = write(serial_fd, "~ver~\n\r", 8);

        if (n < 0)
            fputs("write() of 8 bytes failed!\n", stderr);
        else
        {
            printf("Successfully wrote 8 bytes\n");

            
            //sleep(1);
            char buffer[32];


                int n = read(serial_fd, buffer, sizeof(buffer));
                //sleep(1);
                if (n < 0)
                    fputs("read failed!\n", stderr);
                else
                {
                    printf("Successfully read from serial port -- %s\n", buffer);
                    
                }


        }

        sleep(.5);
        //usleep(500000);

        printf("\n\nNow closing Serial Port /dev/ttyUSB0 \n\n");

        close(serial_fd);
    }


    return 0;
}


```

---

### Post by alexfish on 2012-04-13
can help if post results of garbage

then readers will know what you mean

what is the baud rate of the the device your connecting to ?

also does the program exit from the reading cycle or does it hang

---

### Post by vanangamudi on 2012-04-13
well here is C code... i tried compiling it... compile with no problem.. I'm using Ubuntu 10.10

[Serial Port Manipulation in C]("http://yengal-marumugam.blogspot.com/2011/07/serial-port-manipulation-in-c-linux.html")

hope it helps ;D

---

### Post by Z.K. on 2012-04-13
> **vanangamudi said:**
> well here is C code... i tried compiling it... compile with no problem.. I'm using Ubuntu 10.10

[Serial Port Manipulation in C]("http://yengal-marumugam.blogspot.com/2011/07/serial-port-manipulation-in-c-linux.html")

hope it helps ;D

Thanks, but your code does not read anything back which is what I am having trouble with.  I was not having trouble with the writing.  Still, thanks for the link.

):P

---

### Post by Z.K. on 2012-04-13
> **alexfish said:**
> can help if post results of garbage

then readers will know what you mean

what is the baud rate of the the device your connecting to ?

also does the program exit from the reading cycle or does it hang

Well, I am sure how to explain garbage other than weird characters.  I have attached an image file.

---

### Post by alexfish on 2012-04-13
noticed:

you sending
```
"~ver~\n\r"
```
have you tried  IE: "<string>\r" ... "~ver~\r"

---

### Post by Z.K. on 2012-04-13
> **alexfish said:**
> noticed:

you sending
```
"~ver~\n\r"
```
have you tried  IE: "<string>\r" ... "~ver~\r"

Yes, I did.  I also noticed that though n=8 during write operation, n=0 after all read operations.

---

### Post by alexfish on 2012-04-14
only thing can think of when reading the buff need to decide what type of data, if string then char

eg 

read(char *buffer, int len)

if need to use stream 

EG:

```
struct PIC_STREAM;

typedef
    struct {
        int (*open)(struct PIC_STREAM *stream, const char *path, int mode, void *data);
        int (*close)(struct PIC_STREAM *stream);
        int (*read)(struct PIC_STREAM *stream, char *buffer, int len);
        int (*getchar)(struct PIC_STREAM *stream, char *buffer);
        int (*write)(struct PIC_STREAM *stream, char *buffer, int len);
        int (*seek)(struct PIC_STREAM *stream, int64_t pos, int whence);
        int (*tell)(struct PIC_STREAM *stream, int64_t *pos);
        int (*flush)(struct PIC_STREAM *stream);
        int (*eof)(struct PIC_STREAM *stream);
        int (*lof)(struct PIC_STREAM *stream, int64_t *len);
        int (*handle)(struct PIC_STREAM *stream);
        }
```best tip pointer can give here, look in the Gambas sourse files EG: CSerialPort.c

also a bit of wel known tcl script
```
#!/bin/sh
# the next line restarts using tclsh \
exec tclsh "$0" "$@"
 # simple serial port example to send Command to Device and
 # wait for Reply response in a fixed amount of time.  At the
 # bottom is a simple loop to do this 20x to check serial
 # handler reliability...
 #
 # Works well on Tcl 8.0 and up on Unix (Solaris/NT), poorly on
 # the tclsh included with Tcl 8.1.1 on NT, but pretty well on
 # the wish included with same.
 #
 # NOTE may need to set comPort appropriately for your
 # platform.  Must have a Device configured to respond
 #
 switch $tcl_platform(os) {
     {Linux}            {set comPort /dev/tty*}
     {SunOS}            {set comPort /dev/cua/a}
     {Windows NT}       {set comPort COM2:}
     default            {error "Must configure comPort"}
 }
 set waitSecs 2
 set nTries   20

 #
 # A cheap version of expect.
 #
 # Set up a event-driven I/O reader on the channel, output the
 # string, and wait some number of seconds for the result.
 #
 # @param fd
 #        a channel opened in non-blocking mode for I/O
 #        with buffering turned off.
 #
 # @param outstr
 #        a string to send to the output channel -- note: end-
 #        of-line characters must be included in this string,
 #        if desired.
 #
 # @param regexp
 #        regular expression to match in the incoming data.
 #
 # @param seconds
 #        number of seconds to wait for above match
 #
 # @throws error
 #        if eof is detected on the channel while waiting
 #
 # @returns int
 #        1 if a match is found, 0 otherwise.
 #
 proc send_expect {fd outstr regexp seconds} {
     global send_exp

     # make sure global vars are initialized properly
     set send_exp($fd.matched)        0
     if {![info exists send_exp($fd.buffer)]} {
         set send_exp($fd.buffer) {}
     }

     # set up our Read handler before outputting the string.
     if {![info exists send_exp($fd.setReader)]} {
         fileevent $fd readable 
[list private_send_exp_reader \
                 $fd $regexp]
         set send_exp($fd.setReader) 1
     }

     # output the string to send
     puts -nonewline $fd $outstr
     flush $fd

     # set up a timer so that we wait a limited amt of seconds
     set afterId [after [expr {$seconds*1000}] \
             
[list set send_exp($fd.matched) 0]]
     vwait send_exp($fd.matched)
     set matched $send_exp($fd.matched)
     unset send_exp($fd.matched)
     catch 
[list after cancel $afterId]

     # If we got an eof, then throw an error
     if {$matched < 0} {
         error "Channel EOF while waiting for data"
         return 0
     }
     return $matched
 }

 #
 # PRIVATE channel read event handler for send_expect.  Should
 # not be called by user.
 #
 proc private_send_exp_reader {fd regexp} {
     global send_exp

     if {[eof $fd]} {
         close $fd
         set send_exp($fd.matched) -1
         return
     }
     append send_exp($fd.buffer) [read $fd]
     if {[regexp $regexp $send_exp($fd.buffer)]} {
         set send_exp($fd.matched) 1
     }
 }

 #
 # Return the current contents of the send_expect buffer
 #
 # @param fd
 #        channel identifier that was used with send_expect
 #
 # @returns string
 #        the current contents of the buffer for the channel
 #
 proc send_exp_getbuf {fd} {
     global send_exp
     return $send_exp($fd.buffer)
 }

 #
 # Reset the send_expect buffer, returning its contents
 #
 # @param fd
 #        channel identifier that was used with send_expect
 #
 # @returns string
 #        the current contents of the buffer for the channel
 #
 proc send_exp_resetbuf {fd} {
     global send_exp

     set buf $send_exp($fd.buffer)
     set send_exp($fd.buffer) {}
     return $buf
 }

 #
 # Close out a send_expect session, closing I/O event handler
 #
 # @param fd
 #        channel identifier that was used with send_expect
 #
 # @returns
 #        the channel identifier passed as the fd parameter
 #
 proc send_exp_end {fd} {
     global send_exp

     fileevent $fd readable {}
     foreach v [array names send_exp $fd.*] {
         catch 
[list unset send_exp($v)]
     }
     return $fd
 }

 ##
 ## MAIN
 ##
 set Command [lindex $argv 0]
 set Reply [lindex $argv 1]
 set fd [open $comPort RDWR]
## can set the fd bits here Feel free to experiment
 fconfigure $fd -blocking 0 -buffering none \
         -mode 9600,n,8,1 -translation binary -eofchar {}

 # Loop nTries times, sending Command to device and expecting Reply.
 set nMatches 0
 for {set i 0} {$i < $nTries} {incr i} {
     if {[send_expect $fd "$Command\r" "$Reply" $waitSecs]} {
         incr nMatches
         regsub -all "\r" [send_exp_getbuf $fd] {\r} buf
         regsub -all "\n" $buf {\n} buf
         puts "GOT MATCH: <$buf>"
     } else {
         puts "NO MATCH IN $waitSecs SECONDS"
     }
     send_exp_resetbuf $fd
 }
 send_exp_end $fd
 close $fd
 puts "Matched $nMatches/$nTries\
         ([expr 100.0*$nMatches/$nTries]%)"

# command ./test-serial <Command> <expected Reply>
```

---

### Post by alexfish on 2012-04-15
Can also try this route

using cssl

can be downloaded from 

[http://sourceforge.net/projects/cssl/](http://sourceforge.net/projects/cssl/)

to make a lib.so

gcc -o libcssl.so cssl.c -shared -D_GNU_SOURCE -fPIC

for other Read the Readme

if using cssl.h example:

```
#include <stdio.h>
#include <unistd.h>

#include "cssl.h"


/* if it is time to finish */
static int finished=0;


/* example callback, it gets its id, buffer, and buffer length */
static void callback(int id,
         uint8_t *buf,
         int length)
{
int i;
//    printf("Test\n");
for(i=0;i<length;i++) {

//    switch (buf[i]) {

//    case 0x04: /* Ctrl-D */
//     finished=1;
//     return;

//    case '\r': /* replace \r with \n */
//     buf[i]='\n';

//    }

    putchar(buf[i]);
}

fflush(stdout);
}


int main()
{
cssl_t *serial;

cssl_start();

serial=cssl_open("/dev/ttyUSB0",callback,0,
         9600,8,0,1);

if (!serial) {
    printf("%s\n",cssl_geterrormsg());
    return -1;
}

//cssl_putstring(serial,"Type some data, ^D finishes.");

while (!finished)
    pause();

printf("\n^D - we exit\n");

cssl_close(serial);
cssl_stop();

return 0;
}
```

to find what is in a lib.so try these commands
nm -D libcssl.so

nm --dynamic libcssl.so

---

### Post by Teuniz on 2012-05-26
Example code that demonstrates how to use the library to receive characters and print them to the screen:
(compile with the command: gcc main.c rs232.c -Wall -o2 -o test)

```

/**************************************************

file: main.c
purpose: simple demo that receives characters from
the serial port and print them on the screen

**************************************************/

#include <stdlib.h>
#include <stdio.h>

#ifdef _WIN32
#include <Windows.h>
#else
#include <unistd.h>
#endif

#include "rs232.h"



int main()
{
  int i, n,
      cport_nr=0,        /* /dev/ttyS0 (COM1 on windows) */
      bdrate=9600;       /* 9600 baud */

  unsigned char buf[4096];


  if(OpenComport(cport_nr, bdrate))
  {
    printf("Can not open comport\n");

    return(0);
  }

  while(1)
  {
    n = PollComport(cport_nr, buf, 4095);

    if(n > 0)
    {
      buf[n] = 0;   /* always put a "null" at the end of a string! */

      for(i=0; i < n; i++)
      {
        if(buf[i] < 32)  /* replace unreadable control-codes by dots */
        {
          buf[i] = '.';
        }
      }

      printf("received %i bytes: %s\n", n, (char *)buf);
    }

#ifdef _WIN32
    Sleep(100);  /* it's ugly to use a sleeptimer, in a real program, change the while-loop into a (interrupt) timerroutine */
#else
    usleep(100000);  /* sleep for 100 milliSeconds */
#endif
  }

  return(0);
}

```

---

