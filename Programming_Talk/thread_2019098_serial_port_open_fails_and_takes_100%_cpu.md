---
title: "serial port open fails and takes 100% cpu"
date: 2012-07-07
forum: Programming Talk
---

### Post by garland3 on 2012-07-07
I've downloaded the source code for obdgpslogger and compiled it on my 12.04 machine. 
[http://icculus.org/obdgpslogger/](http://icculus.org/obdgpslogger/)
[http://icculus.org/obdgpslogger/downloads/obdgpslogger-0.16.tar.gz](http://icculus.org/obdgpslogger/downloads/obdgpslogger-0.16.tar.gz)

Everything compiles fine, but when I run the obdgpslogger I have two problems when I run the program with this command

```
./obdgpslogger -s /dev/ttyUSB0 -b 9600 -a 5 -i temp,map,rpm,vss,throttlepos,sparkadv
```1. The program/computer doesn't communicate correctly witht the ELM chip. I keep on getting 'timeout' for all the calls to write to the serial and wait for a response. Looking at the source code shows that the program is not getting a response back from the chip when it sends a command to it.
While it is in the openserial() function this is the stdout.

```

Opening serial port /dev/ttyUSB0, this can take a while
Timeout!
Timeout!
Timeout!
Timeout!
Timeout!
Timeout!
Successfully connected to serial port. Will log obd data
Successfully connected to gpsd. Will log gps data
Timeout!
Couldn't get obd bytes for cmd 00
GPS acquisition complete
```But it isn't successfully connected to the serial port.

If I open putty and set it up with the correct settings than I can communicate with the chip manually.

Any ideas on why this isn't working?

2. While my computer is trying to communicate with the ELM chip, the obdgpslogger takes 100% of the cpu. 

Not sure where to start with this one to debug the problem. Any ideas??
Attached is the output of this command. 
```
$ cpufreq-info
```

---

### Post by alexfish on 2012-07-07
Hi

without chewing through the code

possible try libcssl , serialport , available at sourceforge

the version I use is "libcssl-0.9.4"

it has an interesting callback feature, worth reading

regards

alexfish

---

### Post by garland3 on 2012-07-07
I would really like to know why my computer is having problems rather than just switch libraries. 
Termios is a standard unix serial port controller.  

[http://en.wikibooks.org/wiki/Serial_Programming/termios](http://en.wikibooks.org/wiki/Serial_Programming/termios)

obdgpslogger is stable and works for many people, I'm just trying to understand why it isn't working for me. So I don't ultimately think it is a programming problem. 

Here is the problematic code, so that you don't have to dig through it. 

When a command is sent to the ELM chip it responds back and then gives a  '>' symbol to indicate that it is waiting for a new command. 

```

#include <termios.h>

int openserial(const char *portfilename, long baudrate, long baudrate_target) {
    struct termios options;
    int fd;

    fprintf(stderr,"Opening serial port %s, this can take a while\n", portfilename);
    fd = open(portfilename, O_RDWR | O_NOCTTY | O_NDELAY);
    // fd = open(portfilename, O_RDWR | O_NOCTTY);

    if(fd == -1) {
        perror(portfilename);
    } else {
        fcntl(fd, F_SETFL, 0);

        // Get the current options for the port
        tcgetattr(fd, &options);

        options.c_cflag |= (CLOCAL | CREAD);
        options.c_lflag &= !(ICANON | ECHO | ECHOE | ISIG);
        options.c_oflag &= !(OPOST);
        options.c_cc[VMIN] = 0;
        options.c_cc[VTIME] = 100;

        tcsetattr(fd, TCSANOW, &options);

        long current_baud = 9600;
        if(0 != modifybaud(fd, baudrate)) {
            fprintf(stderr, "Error modifying baudrate. Continuing, but may suffer issues\n");
        } else {
            if(baudrate != 0)
                current_baud = baudrate;
        }

        // Reset the device. Some software changes settings and then leaves it
        blindcmd(fd,"ATZ",1);

        // printf("Baudrate upgrader disabled\n");
        if(0 > upgradebaudrate(fd, baudrate_target, current_baud)) {
            fprintf(stderr, "Error upgrading baudrate. Continuing, but may suffer issues\n");
        }

        // Now some churn to get everything up and running.
        // Do a general cmd that all obd-devices support
        // Do this once in case we have a partially-written command somehow
        blindcmd(fd,"0100",1);
        // Disable command echo [elm327]
        blindcmd(fd,"ATE0",1);
        // Disable linefeeds [an extra byte of speed can't hurt]
        blindcmd(fd,"ATL0",1);
        // Don't insert spaces [readability is for ugly bags of mostly water]
        blindcmd(fd,"ATS0",1);
        // Then do it again to make sure the command really worked
        blindcmd(fd,"0100",1);

    }
    return fd;
}



// Blindly send a command and throw away all data to next prompt
/**
 \param cmd command to send
 \param no_response if we don't read to next prompt [ie, on exit]
 \param fd file descriptor
 */
void blindcmd(int fd, const char *cmd, int no_response) {
    char outstr[1024];
    snprintf(outstr, sizeof(outstr), "%s%s\0", cmd, OBDCMD_NEWLINE);
    appendseriallog(outstr, SERIAL_OUT);
    write(fd,outstr, strlen(outstr));
    if(0 != no_response) {
        sleep(1);
        readtonextprompt(fd);
    }
}



/// Throw away all data until the next prompt
void readtonextprompt(int fd) {
    char retbuf[4096]; // Buffer to store returned stuff
    readserialdata(fd, retbuf, sizeof(retbuf));
}


/// Collect data up to the next prompt
/** Reads up to the next '>'
   \param buf buffer to fill
   \param n size of buf
   \return number of bytes put in buf, or -1 on error
*/
int readserialdata(int fd, char *buf, int n) {
    char *bufptr = buf; // current position in buf

    struct timeval start,curr; // For timing out
    if(0 != gettimeofday(&start, NULL)) {
        perror("Couldn't gettimeofday");
        return -1;
    }
    memset((void *)buf, '\0', n);
    int retval = 0; // Value to return
    int nbytes; // Number of bytes read
    do {
        nbytes = read(fd, bufptr, buf+n-bufptr-1);
        if(-1 == nbytes && EAGAIN != errno) {
            perror("Error in readserialdata");
        }
        if(-1 != nbytes) {
            // printf("Read bytes '%s'\n", bufptr);
            retval += nbytes; // Increment bytecount
            bufptr += nbytes; // Move pointer forward
        }
        if(0 != gettimeofday(&curr, NULL)) {
            perror("Couldn't gettimeofday");
            return -1;
        }
        if(OBDCOMM_TIMEOUT < 1000000l*(curr.tv_sec - start.tv_sec) +
            (curr.tv_usec - start.tv_usec)) {
            printf("Timeout!\n");
            return -1;
        }
    } while (retval == 0 || bufptr[-1] != '>');

    appendseriallog(buf, SERIAL_IN);
    return retval;
}


```

---

### Post by xb12x on 2012-07-08
One thing I noticed was that you expect it to work on /dev/ttyUSB0, but you ran putty on /dev/ttyUSB1. 

And I think obdgpslogger is at 100% of cpu while waiting for the connection because it's stuck in a very tight loop of code until the connection happens. So it's probably normal for that program.

Run minicom
 $ sudo minicom -s

 Scroll down to "Serial port setup"
  Change the first line to /dev/ttyUSB0
  Change Bps/Par/Bits to the correct settings
  Disable Hardware Flow Control 
 Save setup as dfl (default)

See if the system recognizes your adapter
 $ dmesg | grep tty 
    You should see your adapter attached to ttyUSB0

See if /dev/ttyUSB0 exists
 $ ls -al /dev/ttyUSB*
    You should see /dev/ttyUSB0
 
Reboot your computer

See if the system still recognizes your adapter
 $ dmesg | grep tty 

See if /dev/ttyUSB0 exists
 $ ls -al /dev/ttyUSB*

Good luck.

---

### Post by garland3 on 2012-07-08
New information but still have a problem. 

Apparently ubuntu 12.04 and the FTDI chip USB-Serial converter are having problems.

What tipped me off was that when I was trying to communicate with the ELM chip using minicom, it would work if turned the hardware flow control off. 

[http://ubuntuforums.org/showthread.php?t=1717311](http://ubuntuforums.org/showthread.php?t=1717311)

So I modified the configuration of the serial port in the obdgpslogger code so that hardware control flow is off and software control flow is turned on.

```
// Get the current options for the port
        tcgetattr(fd, &options);

        
        options.c_cflag |= (CLOCAL | CREAD); // original
        options.c_cflag &= ~CRTSCTS; //hardware control off, anthon
        options.c_lflag &= !(ICANON | ECHO | ECHOE | ISIG); // original
        
        options.c_iflag |= (IXON | IXOFF | IXANY); // software flow control    ,anthon
        options.c_oflag &= !(OPOST);
        options.c_cc[VMIN] = 0;
        options.c_cc[VTIME] = 100;

        tcsetattr(fd, TCSANOW, &options);
```When I compile and run the program it successfully starts logging data but then quits after about 10 seconds. 

```
shari@shari-MX3414:~/obdgpslogger/bin$ sudo sh anthony_run.sh 
Opening serial port /dev/ttyUSB1, this can take a while
Successfully connected to serial port. Will log obd data
Successfully connected to gpsd. Will log gps data

/*RUNS FOR 10-15 seconds, and then .. */

Couldn't get obd bytes for cmd 20
Timeout!
Error reading from serial port
Received OBD_ERROR from serial read. Exiting

```where anthony_run.sh is
```

#! /bin/sh
# run as sudo. 

# log data. 
./obdgpslogger -s /dev/ttyUSB1 -b 9600 -i temp,map,rpm,vss,throttlepos,sparkadv
```Maybe a buffer is getting filled and then it fails?? at least it is partially working now. 

All the best!

Anthony

---

### Post by garland3 on 2012-07-08
> **xb12x said:**
> 
And I think obdgpslogger is at 100% of cpu while waiting for the connection because it's stuck in a very tight loop of code until the connection happens. So it's probably normal for that program.


Good catch. I'll put some usleep() in there to slow it down if it hasn't received any data from the serial recently. Thanks!

Now to solve the second problem. Why is it failing after a few seconds??

---

### Post by OM55 on 2012-07-08
Hi guys,

You may also want to know that there is a small bug in the default install of Ubuntu 12.04 - it neglects to include the users in the dialout group - which means there are no permissions to use the serial port. As a result user applications cannot access any serial port, whether a real serial port or a USB-Serial adapter.

You can reinstall the 'Users and Groups' by: 

```
sudo apt-get install gnome-system-tools
```

and then run at the command line: 

```
users-admin
```

Select 'Groups', find 'dialout' and check the checkboxes of all the relevant users.

You may need to logout and login so the change will take effect.

---

### Post by xb12x on 2012-07-08
What is being transferred, ASCII characters or raw 8-bit data? 

Software flow control (XON/XOFF) uses the high bit (bit-7) of each transferred byte. This works with ASCII characters as they are 7 bits. 

But if transferring raw 8-bit data then disable software flow control.

---

### Post by xb12x on 2012-07-08
> **OM55 said:**
> Hi guys,

You may also want to know that there is a small bug in the default install of Ubuntu 12.04 - it neglects to include the users in the dialout group - which means there are no permissions to use the serial port. As a result user applications cannot access any serial port, whether a real serial port or a USB-Serial adapter.

You can reinstall the 'Users and Groups' by: 

```
sudo apt-get install gnome-system-tools
```

and then run at the command line: 

```
users-admin
```

Select 'Groups', find 'dialout' and check the checkboxes of all the relevant users.

You may need to logout and login so the change will take effect.




I noticed that but I didn't know why. I thought it was something I did. I've been using sudo to get around it. 



Thanks!

---

### Post by garland3 on 2012-07-08
This is what I did.
```
sudo apt-get install gnome-system-tools
users-admin
```I was already added to the dial-out group, but I  saw a tty group. So I added myself to the tty group after goggling it to make sure I wasn't doing anything really dumb. 

Then in the code I got rid of the software control in the settings for the serial port. So this is my final configuration code. 

```

// Get the current options for the port
tcgetattr(fd, &options);
        
options.c_cflag |= (CLOCAL | CREAD); 
options.c_cflag &= ~CRTSCTS; //hardware control off
options.c_lflag &= !(ICANON | ECHO | ECHOE | ISIG);         
options.c_oflag &= !(OPOST);
options.c_cc[VMIN] = 0;
options.c_cc[VTIME] = 100;

tcsetattr(fd, TCSANOW, &options);
```Then I compiled it, went to my car at 2:30 am, and tried running my anthony_run.sh script without 'sudo', and it worked!!!

Then I ran
```
./obd2kml
```made the google earth file of my obd and gps data, and now I have  a cool representation of my cars performance!!

Thanks guys!

All the best, 

Anthony G

---

