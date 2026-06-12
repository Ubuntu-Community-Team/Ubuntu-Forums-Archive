---
title: "Help with Qdevelop and the serial port"
date: 2008-09-19
forum: Programming Talk
---

### Post by grüner pfirsich on 2008-09-19
hi

I'm new using linux because of a project in the school.. anyway, the project must use a serial port to send and receive data.

I work with Qdevelop (and also learning how to use it) but first I check the programs using the bash.. the point is, I managed to send data using the RS 232. The code is easy because I dont know yet how to deal with details and it works but when I try to program a function using the pushbutton in Qdevelop to send the data (using the write command) it does not work.

I mean, it compiles and everything but it doesnt send anything


Here is the code I use:

#include <stdio.h>   
#include <string.h>  
#include <unistd.h>  
#include <fcntl.h>   
#include <errno.h>   
#include <termios.h> 

    int main(void)
    {
      int fd, n; 

      fd = open("/dev/ttyUSB0", O_RDWR | O_NOCTTY | O_NDELAY);
      n=write(fd, "SEND", 4);
      if (n<0)
      {
	fputs("failed! \n", stderr);
      }	
      return (fd);
      close(fd);
}
	

Does any one have an idea what's wrong?

---

### Post by dwhitney67 on 2008-09-19
It could be that you do not have privileges to open that port (/dev/ttyUSB0).

From the description of your application in the OP, I would say that fundamentally, the bigger issue you are facing is not so much with getting the port to function, but the lack of following the MVC (Model-Viewer-Controller) paradigm.

A GUI (IMHO) should not be communicating directly to a port; it should instead be communicating with another process (that you develop) that opens and controls comm to the port.

---

