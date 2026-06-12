---
title: "Open  a serial port"
date: 2007-12-17
forum: Packaging and Compiling Programs
---

### Post by dleroy on 2007-12-17
I am trying to compile "osp.c" is my version of "opening a serial port" code from the SERIAL PROGRAMMING GUIDE" lISTING 1 @ [http://www.easysw.com/~mike/serial/serial.html](http://www.easysw.com/~mike/serial/serial.html).
This is my file 'osp.c' listing :

* example code to open serial port                         */
  #include <stdio.h>   /* Standard input/output definitions */
    #include <string.h>  /* String function definitions */
    #include <unistd.h>  /* UNIX standard function definitions */
    #include <fcntl.h>   /* File control definitions */
    #include <errno.h>   /* Error number definitions */
    #include <termios.h> /* POSIX terminal control definitions */

    /*
     * 'open_port()' - Open serial port 1.
     *
     * Returns the file descriptor on success or -1 on error.
     */

    int
    open_port(void)
    {

      int fd; /* File descriptor for the port */


      fd = open("/dev/ttyS0", O_RDWR |O_NOCTTY | O_NDELAY);
      if (fd == -1)
     {
       /*
        * Could not open the port.
        */

        perror("open_port: Unable to open /dev/ttyS0 - ");
      }
      else
        fcntl(fd, F_SETFL, 0);

      return (fd);
    }

I am using version "Gusty"

This is the terminal display                                                                      comand line and    error
                                                                            
root@ub4:/home/leroy/src/rfid_c# gcc osp.c -o osp
/usr/lib/gcc/i486-linux-gnu/4.1.3/../../../../lib/crt1.o: In function `_start':
(.text +0x18): undefined reference to `main'
collect2: ld returned 1 exit status
If I use this commands I get these results 
root@ub4:/home/leroy/src/rfid_c# cpp osp.c  osp

Compiled Ok but don't run as user 

root@ub4:/home/leroy/src/rfid_c# ./osp
-su: ./osp: Permission denied
root@ub4:/home/leroy/src/rfid_c# sudo ./osp

Try to run with sudo gets this;

sudo: ./osp: command not found
root@ub4:/home/leroy/src/rfid_c#     

What am I doing wrong ??

All I want to do with this code is to change the "DTR" line on /dev/ttyS0 to a space "low"  to enable a peripheral device control line.

Thanks for any help you can give me.

don't know whats with the "smile: that should b "8"

---

### Post by yabbadabbadont on 2007-12-17
All C programs must have a main function.  It is the "main" entry point for the program.  Or did you just not show us all the code?  By the way, wrap your code with, wait for it.... code tags.  :D  It will look better.  You got the smiley instead of the eight because you didn't disable smileys in your post and an eight followed by a closing parend is a vaild smiley symbol on the forums.

---

### Post by dleroy on 2007-12-18
Added the required "int main()" stuff and it complied and executed OK.

Thanks for the assistance

one question: your comment "wrap you code in, wait for it... code tags" . What is that in reference too !!

Thanks again

---

### Post by yabbadabbadont on 2007-12-18
When you are editing your post on the forums, one of the buttons (the #) will wrap the selected text with special tags, so that the forum software will display the text using special formatting.  For example, here is some code wrapped with code tags:
```
static void
update_uptime(void)
        {
        gint    up_minutes;

        if (!uptime_enabled)
                return;

        /* Once every 10 seconds is default update period.
        */
        if (GK.ten_second_tick || _GK.up_minutes < 0)
                {
                uptime_seconds = (*read_uptime)();
                if (uptime_seconds > 0)
                        up_minutes = (gint) (uptime_seconds / 60);
                else
                        up_minutes = (gint)(time(0) - _GK.start_time + base_uptime) / 60;
                if (_GK.up_minutes != up_minutes)
                                draw_upminutes(up_minutes);
                _GK.up_minutes = up_minutes;
                }
        }

```
You will notice that it has used a monospace font and has preserved the indentation of the code.

---

