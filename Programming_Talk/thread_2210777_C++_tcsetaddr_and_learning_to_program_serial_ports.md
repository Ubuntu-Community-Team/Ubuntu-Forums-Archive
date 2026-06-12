---
title: "C++: tcsetaddr and learning to program serial ports"
date: 2014-03-12
forum: Programming Talk
---

### Post by thisisbasil on 2014-03-12
Hello all, I am not entirely sure whether this is a C++ question, an Ubuntu question, or both. At any rate, I posted this ([http://stackoverflow.com/questions/22307542/tcsetaddr-and-learning-to-program-serial-ports](http://stackoverflow.com/questions/22307542/tcsetaddr-and-learning-to-program-serial-ports)) over at stackoverflow; its not really getting any traction over there, so I thought maybe someone here might be able to answer. My issue is as follows:

          [B]I am trying to learn how to use serial ports using C/C++  (mostly C++) in xubuntu linux 12.10. I found a couple helpful tutorials  but, as is the case in all tutorials, the text is canned and doesn't  address a lot of the "gotchas". I am trying to do something simple: open  a serial port (sent in as a command-line parameter), get the initial  port settings and print them out, then initialize the port to new  settings.

  Here is what I have thus far:[/B]

  [HTML]#include <termios.h>
#include <iostream>
#include <string>
#include <cstdlib>
#include <unistd.h>
#include <fcntl.h>
#include <cstdio>
using namespace std;

int main(int count, char* parms[])
{
    if (count != 2)
        exit(1);

    //open port
    string fname = parms[1];
    cout << fname << ": ";
    int fd = open(fname.c_str(), O_RDWR | O_NOCTTY | O_NDELAY   );
    if (!fd)
    {
        cout << "error" << endl;
        exit(1);    
    }

    termios getPortSettings, setPortSettings;

    //get current port settings
    tcgetattr(fd,&setPortSettings);
    getPortSettings = setPortSettings;
    speed_t iBaud = cfgetispeed(&getPortSettings),
        oBaud = cfgetospeed(&getPortSettings);

    cout << "iBaud: " << iBaud << " oBaud: " << oBaud << endl;
    cout << "\nPress Enter to change port status";
    cin.get();

    //set baud rate 19200
    cfsetispeed(&setPortSettings,B19200);
    cfsetospeed(&setPortSettings,B19200);

    //set to no parity
    setPortSettings.c_cflag &= ~PARENB;

    //one stop bit
    setPortSettings.c_cflag &= ~CSTOPB;

    //clear out current word size
    setPortSettings.c_cflag &= ~CSIZE;

    //set 8 data bits
    setPortSettings.c_cflag |= CS8;     

    //apply settings
    int ret = tcsetattr(fd,TCSAFLUSH,&setPortSettings);
    if (ret < 0)
    {
        cout << "error ("<< ret <<") in applying settings!\n";
        exit(1);
    };

    tcgetattr(fd,&setPortSettings);
    iBaud = cfgetispeed(&getPortSettings);
    oBaud = cfgetospeed(&getPortSettings);

    cout << "iBaud: " << iBaud << " oBaud: " << oBaud << endl;

    //close port
    close(fd);
    return 0;
}[/HTML]  [B]When I test, I am testing out serial ports like /dev/ttyS0 though  /dev/ttyS31 (it really shouldn't matter which I choose here right?). I  am able to open just about every interface and get settings from them (I  want to find out how to extract other settings, its just the Baud rates  look like the low hanging fruits and I need to ease myself back into  the bitwise math needed to extract everything else).
  Basically, every time I make the call to tcgetattr(), it fails with  the generic -1 return code.  Eventually, I want to try hook two of my  computers up and send data between the two using a simple null modem  cable or usb cable (the code to do so would basically be the same, the  only difference is the device file right?), and this is just my first  step in doing so.[/B]

Any help that could be offered: whether I am making a mistake in my code, or with how I understand communication to serial ports to exist would be appreciated.

---

### Post by spjackson on 2014-03-12
I think your errors are likely to be with permissions. Unless you are sufficiently privileged, your open will fail. Your attempt at testing for this is wrong. Also, check errno when these low level calls fail, so that you can see what's going on.

> 
```

    int fd = open(fname.c_str(), O_RDWR | O_NOCTTY | O_NDELAY   );
    if (!fd)
    {
        cout << "error" << endl;
        exit(1);    
    }

```

As it stands, if open fails (returning a negative value), you skip that test and get "bad file descriptor" in the rest of your system calls. Try this:

```

#include <cerrno>
#include <string.h>

    int fd = open(fname.c_str(), O_RDWR | O_NOCTTY | O_NDELAY   );
    if (fd < 0)
    {
        cout << "error" << endl;
        cout << errno << " " << strerror(errno) << "\n";
        exit(1);    
    }

```

---

### Post by thisisbasil on 2014-03-12
Thank you for the quick reply.

I had tried sudo ./a.out <serial port> before, thinking that this might be the issue; unfortunately, it wasn't/isn't. 

Using cerrno, I was able to get a more specific error message: "5 Input/output error". I am doing some research now into how to alleviate this problem, but if you (or anyone else) can provide some insight, I am all ears.

As a side: is there any graceful way to determine if the user has sufficient privileges for such things. I suppose I could do a system call or something to determine the user, but that just seems like a horrid way to go about it.

---

### Post by steeldriver on 2014-03-12
Does

```

stty -aF /dev/ttyS0

```

work? AFAIK the default setup is for /dev/ttySx to be owned by root:dialout 

```

$ ls -l /dev/ttyS?
crw-rw---- 1 root dialout 4, 64 Feb 23 08:20 /dev/ttyS0
crw-rw---- 1 root dialout 4, 65 Feb 23 08:20 /dev/ttyS1
crw-rw---- 1 root dialout 4, 66 Feb 23 08:20 /dev/ttyS2
crw-rw---- 1 root dialout 4, 67 Feb 23 08:20 /dev/ttyS3
crw-rw---- 1 root dialout 4, 68 Feb 23 08:20 /dev/ttyS4
crw-rw---- 1 root dialout 4, 69 Feb 23 08:20 /dev/ttyS5
crw-rw---- 1 root dialout 4, 70 Feb 23 08:20 /dev/ttyS6
crw-rw---- 1 root dialout 4, 71 Feb 23 08:20 /dev/ttyS7
crw-rw---- 1 root dialout 4, 72 Feb 23 08:20 /dev/ttyS8
crw-rw---- 1 root dialout 4, 73 Feb 23 08:20 /dev/ttyS9

```

i.e. members of the 'dialout' group should be able to read/write to the devices (a holdover from the days of serial modems presumably)

```

$ id steeldriver
uid=1002(steeldriver) gid=1003(steeldriver) groups=1003(steeldriver),4(adm),**20(dialout)**,50(staff),124(sambashare)

```

However as you have already noted, that doesn't seem to be your issue here (if it doesn't work even with sudo)

---

### Post by thisisbasil on 2014-03-12
This is the output from stty:

[HTML]$ sudo stty -aF /dev/ttyS0
stty: /dev/ttyS0: Input/output error[/HTML]

Any ideas as to where to go from here?

---

### Post by steeldriver on 2014-03-12
What kind of machine is it? does it actually have serial ports? I'm pretty much at the limit of my knowledge here, but iirc it makes a difference what's actually 'there' e.g. if I do it on my bare 12.04 Server laptop:

```

$ sudo stty -aF /dev/ttyS0
stty: /dev/ttyS0: Input/output error

```

but if I dock the laptop into a base which actually has a physical RS232 port

```

$ sudo stty -aF /dev/ttyS0
speed 9600 baud; rows 0; columns 0; line = 0;
intr = ^C; quit = ^\; erase = ^?; kill = ^U; eof = ^D; eol = <undef>;
eol2 = <undef>; swtch = <undef>; start = ^Q; stop = ^S; susp = ^Z; rprnt = ^R;
werase = ^W; lnext = ^V; flush = ^O; min = 1; time = 0;
-parenb -parodd cs8 hupcl -cstopb cread clocal -crtscts
-ignbrk -brkint -ignpar -parmrk -inpck -istrip -inlcr -igncr icrnl ixon -ixoff
-iuclc -ixany -imaxbel -iutf8
opost -olcuc -ocrnl onlcr -onocr -onlret -ofill -ofdel nl0 cr0 tab0 bs0 vt0 ff0
isig icanon iexten echo echoe echok -echonl -noflsh -xcase -tostop -echoprt
echoctl echoke

```

---

### Post by thisisbasil on 2014-03-12
Good call, I am on a laptop myself.  Hypothetically speaking, what difference would it make if I were to attempt the same thing with a USB port as opposed to a COM port? If so, which device would I need to be working with here?

---

