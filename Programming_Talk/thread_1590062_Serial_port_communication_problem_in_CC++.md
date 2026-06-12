---
title: "Serial port communication problem in C/C++"
date: 2010-10-07
forum: Programming Talk
---

### Post by GhostRider22 on 2010-10-07
Hello, 

I switched to linux 3 years ago, taught my self to program all over again, have set up servers, and i've ran into a large number of problems, nothing i could not solve without google, and this forum, untill now. 


Im communicating with an arduino micro controller over a usb, technically its a virtual serial port or something of that sort. 

For several months, i've had a php interface working just fine.  [http://67.165.90.222/index.php](http://67.165.90.222/index.php)

This always updates the temp on my thermostat, every attempt, every try. The refresh is limited in its speed because of limitations, but the transmit of the info always works. 

Now i've decided to setup a gui using glade, and gtk/gtkmm. I ran into some problems, so i decided to get a working terminal program first. 

It does not always send the data, sometimes it works, sometimes it doesnt. Seems some tempatures work better than others, but overall it appears to be random. I hope someone here can give me an idea why the PHP works perfectly fine, but the C++ does not. 

If you have any suggestions, outside the scope of my question, short of 2 c++ classes in college 7 years ago, im self taught, and may very well be making easy common mistakes. 

I thank you ahead of time. 


PHP
[PHP]<?php






$readtemp;
    require("php_serial.class.php");
    
    //Initialize the class1
    $serial = new phpSerial();
        
    //Specify the serial port to use
    $serial->deviceSet("/dev/ttyUSB0");
    
    //Set the serial port parameters.
    $serial->confBaudRate(1200); 
    $serial->confParity("none"); 
    $serial->confCharacterLength(8); //Character length 
    
    $serial->confStopBits(1); 
    $serial->confFlowControl("none");


    $serial->deviceOpen();

    $serial->sendMessage("U");
   
     $read = $serial->readPort();
     echo "Current temp is ";
     echo ord($read);
     echo "F";
    
    $serial->deviceClose();
    
  ?>  
    
    
    
    
    
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1">
<title>Control planel</title>
</head>
<body>



<form action="update.php"method="post"><select name="temp"><option value="B60:">60</option>
<option value="B61:">61</option>
<option value="B62:">62</option>
<option value="B63:">63</option>
<option value="B64:">64</option>
<option value="B65:">65</option>
<option value="B66:">66</option>
<option value="B67:">67</option>
<option value="B68:">68</option>
<option value="B69:">69</option>
<option value="B70:">70</option>
<option value="B71:">71</option>
<option value="B72:">72</option>
<option value="B73:">73</option>
<option value="B74:">74</option>
<option value="B75:">75</option>
<option value="B76:">76</option>
<option value="B77:">77</option>
<option value="B78:">78</option>
<option value="B79:">79</option>
<option value="B80:">80</option>
<option value="B81:">81</option>
<option value="B82:">82</option>
<option value="B83:">83</option>
<option value="B84:">84</option>
<option value="B85:">85</option>
<input type="submit" value="Update" /></form>



</body>
</html> 

[/PHP]C

[PHP]#include <iostream>
using namespace std;
#include <string.h> // string function definitions
#include <unistd.h> // UNIX standard function definitions
#include <fcntl.h> // File control definitions
#include <errno.h> // Error number definitions
#include <termios.h> // POSIX terminal control definitionss
#include <time.h>   // time calls
 char temp[6];
 char Xtemp[10];
//unsigned char tempX[8];


int main()
{



    int fd; // file description for the serial port
    
    fd = open("/dev/ttyUSB0", O_RDWR | O_NOCTTY | O_NDELAY);
    
    if(fd == -1) // if open is unsucessful
    {
        //perror("open_port: Unable to open /dev/ttyS0 - ");
        cout << "open_port: Unable to open /dev/ttyS0. \n";
    }
    else
    {
        fcntl(fd, F_SETFL, 0);
        cout << "port is open.\n";
    }
    struct termios port_settings;      // structure to store the port settings in

    cfsetispeed(&port_settings, B1200);    // set baud rates
    cfsetospeed(&port_settings, B1200);

    port_settings.c_cflag &= ~PARENB;    // set no parity, stop bits, data bits
    port_settings.c_cflag &= ~CSTOPB;
    port_settings.c_cflag &= ~CSIZE;
    port_settings.c_cflag |= CS8;
    
    tcsetattr(fd, TCSANOW, &port_settings);    // apply the settings to the port


    



    cout << "What is the desired tempature settings \n";
    cin >> temp;
    strcpy (Xtemp, "B");
        strcat (Xtemp, temp);
    strcat (Xtemp, ":");
    
    cout << Xtemp << "\n";
    write(fd, Xtemp, 6);  //Send data
    return 0;    
    

    }
    
    

    
    [/PHP]

---

### Post by dwhitney67 on 2010-10-07
If you are indeed interested in developing in C++, you should avoid the fixed-sized arrays, especially for handling user input.  Consider using the STL string class.

For example:
```

#include <string>

...

int main()
{
   std::string desiredTemp;

   std::cout << "Enter the desired temperature: ";
   std::cin  >> desiredTemp;

   std::string command = "B";
   command += desiredTemp + ":";

   write(fd, command.c_str(), command.size());
}

```

EDIT:

I cannot verify if the serial comm code is correct; I mean it looks fine.  Do you perhaps need to flush the port after you have written the command?

P.S.  And avoid global variables!

---

### Post by VernonA on 2010-10-07
IIRC the C code you've pasted is turning off the Stop bit, which I think you need. A common way to set-up ports is to read the current settings into the struct, then ensure the important ones are set the way you want them, then write it back. This helps prevent you accidentally changing some of the more esoteric default values.
Rgds
Vernon

---

### Post by GhostRider22 on 2010-10-08
> **VernonA said:**
> IIRC the C code you've pasted is turning off the Stop bit, which I think you need. A common way to set-up ports is to read the current settings into the struct, then ensure the important ones are set the way you want them, then write it back. This helps prevent you accidentally changing some of the more esoteric default values.
Rgds
Vernon


According to the references i could find that is sending 2 stop bits, I tried to switch it to send 1, and the problem did not change. 






> **dwhitney67 said:**
> If you are indeed interested in developing in C++, you should avoid the fixed-sized arrays, especially for handling user input. Consider using the STL string class.

For example:
```

#include <string>

...

int main()
{
   std::string desiredTemp;

   std::cout << "Enter the desired temperature: ";
   std::cin  >> desiredTemp;

   std::string command = "B";
   command += desiredTemp + ":";

   write(fd, command.c_str(), command.size());
}

```EDIT:

I cannot verify if the serial comm code is correct; I mean it looks fine. Do you perhaps need to flush the port after you have written the command?

P.S.  And avoid global variables!


Once i get this figured out, I will look into changing how i use the strings/arrays, thanks for the suggestion.

---

### Post by not_a_phd on 2010-10-11
I recently suffered from some seemingly random serial character drops under Ubuntu Linux. Turned out that XON/XOFF was enabled by default. The following settings cured this on the input side:

```

    // Do NOT: Map NL to CR, Ignor CR, Map CR to NL, or use XON/OFF ctl:
    options.c_iflag &= ~(INLCR | IGNCR | ICRNL | IXON | IXOFF | IXANY);

```

Don't know if this will help you or not. It was just one of those things...

---

### Post by tgalati4 on 2010-10-11
Serial communication is synchronous--precisely-timed bit stream that works well with a real serial port.  Using a USB converter (such as a PL2302) can cause problems because USB is asynchronous--hot pluggable, data resend, communication integrity checking, etc.  So depending on what you are trying to do, the slight hiccups in the USB stream can result in broken communication on the serial side.

Find an old computer with a real serial port and test your code.

---

### Post by GhostRider22 on 2010-10-15
> **not_a_phd said:**
> I recently suffered from some seemingly random serial character drops under Ubuntu Linux. Turned out that XON/XOFF was enabled by default. The following settings cured this on the input side:

```

    // Do NOT: Map NL to CR, Ignor CR, Map CR to NL, or use XON/OFF ctl:
    options.c_iflag &= ~(INLCR | IGNCR | ICRNL | IXON | IXOFF | IXANY);

```Don't know if this will help you or not. It was just one of those things...



that line does not work for me. says options not declared. I changed it to "port_settings" but no change.



> **tgalati4 said:**
> Serial communication is synchronous--precisely-timed bit stream that works well with a real serial port.  Using a USB converter (such as a PL2302) can cause problems because USB is asynchronous--hot pluggable, data resend, communication integrity checking, etc.  So depending on what you are trying to do, the slight hiccups in the USB stream can result in broken communication on the serial side.

Find an old computer with a real serial port and test your code.


I wish i had a serial port to verify the C code, but i do not. The PHP code on the same machine works perfectly.


Now i do have a question, that may be related to this problem. When I attach that function to a GUI using glade, the function/serial data is not ran/sent untill the program is closed. 

Do you need to close the port somehow in the code perhaps? Like i've done with the PHP code?



[COLOR=Black]**SOLVED**[/COLOR] 120 seconds after posting this. 

Well, this is what I get for taking example code from someone else, and not vetting it from the bottom up.

Orginal line in the code, honestly no idea what |= even means, but I did not notice it was different.

[PHP]port_settings.c_cflag |= CS8;[/PHP]Should be 

[PHP]port_settings.c_cflag &= CS8;[/PHP]Which actually sets it to 8 bits. 


So +1 to my lazyness = fail.

EPIC FACEPALM

---

### Post by dwhitney67 on 2010-10-15
> **GhostRider22 said:**
> ... honestly no idea what |= even means...

The |= is the short-hand notation of the following:
```

port_settings.c_cflag = port_settings.c_cflag | CS8;  

```
The | symbol denotes the OR operator.

Similarly, the &= is short-hand for:
```

port_settings.c_cflag = port_settings.c_cflag & CS8;

```
In this case, the & is the AND operator.

Anyhow, now you know why programmers prefer the short-hand notation; it involves a lot less typing.

---

### Post by VernonA on 2010-10-15
Glad to hear you're problem is fixed. However, I note there is a bit of luck going on here, since the old code looks right and you're new code looks wrong! The CS8 flag definitely needs to be ORed in, rather than ANDed, since you want to set a bit in an existing bitfield. If you do field = field & CS8 you are clearing all the bits to 0 (except possibly the CS8 bit itself if it is already set). A quick review of the meaning of the other flags (eg at [http://www.opengroup.org/onlinepubs/007908799/xsh/termios.h.html]("http://www.opengroup.org/onlinepubs/007908799/xsh/termios.h.html")) does suggest that most of them should actually be zero in your case, but that is pure luck. Perhaps the issue is that the C_SIZE flag should also be set rather than cleared (ie perhaps your code needs to be:
```

    port_settings.c_cflag &= ~PARENB;      // Clear parity-enable
    port_settings.c_cflag &= ~CSTOPB;      // Clear 2 stop bits
    port_settings.c_cflag |= CSIZE | CS8;  // Set 8 bit data

```
). I know serial comms can be tricky, so I'm only mentioning it so you know where to start if you need to make changes to it and nothing seems to work right!
Rgds
Vernon

---

### Post by GhostRider22 on 2010-10-22
> **VernonA said:**
> Glad to hear you're problem is fixed. However, I note there is a bit of luck going on here, since the old code looks right and you're new code looks wrong! The CS8 flag definitely needs to be ORed in, rather than ANDed, since you want to set a bit in an existing bitfield. If you do field = field & CS8 you are clearing all the bits to 0 (except possibly the CS8 bit itself if it is already set). A quick review of the meaning of the other flags (eg at [http://www.opengroup.org/onlinepubs/007908799/xsh/termios.h.html](http://www.opengroup.org/onlinepubs/007908799/xsh/termios.h.html)) does suggest that most of them should actually be zero in your case, but that is pure luck. Perhaps the issue is that the C_SIZE flag should also be set rather than cleared (ie perhaps your code needs to be:
```

    port_settings.c_cflag &= ~PARENB;      // Clear parity-enable
    port_settings.c_cflag &= ~CSTOPB;      // Clear 2 stop bits
    port_settings.c_cflag |= CSIZE | CS8;  // Set 8 bit data

```). I know serial comms can be tricky, so I'm only mentioning it so you know where to start if you need to make changes to it and nothing seems to work right!
Rgds
Vernon


I looked at that webpage, and another one for the libary, im lost as to how exactly the flags work. 

Using Or ( | )  does not work. It only works using &. 

Could someone here recommend something for me to read about how flags like this work? How they are actualy set and what does what? 

I'd like to know more about the mechanics of what is exactly happening. So i can follow it better when problems arise.

---

### Post by VernonA on 2010-10-25
There are many sites on the Web which will explain bit-wise arithmetic better than I could. However, I think you already know enough that you will understand this:
When two integers are OR-ed together, each of their bit locations is examined, and the matching bit in the result is set to 1 if either bit in the args is 1. If (and only if) both are 0, the result is 0. Eg in binary 100101 OR 110011 is 110111. The AND operation is similar, but uses the rule that the result bit is only set if both arg bits are set. Eg 100101 AND 110011 is 100001.
How does this apply here? Easy. To configure a port you need to send it lots of info. An efficient way to do this is to send an integer in which different bits each convey different settings. For example, to turn on parity checking, set bit 3. To enable h/w hand-shaking set bit 6. And so on (these numbers are just fictional examples). To make these settings easier to remember, they are given names using #define statements. Hence PARENB is defined to be 0b00000100 (ie bit 3 is set, so this value is 4 in decimal). To set the third bit you can now write:
```
    control_flags = control_flags | PARENB;

```since | means OR in C/C++. Note that if you wrote:
```
    control_flags = PARENB;

```you would still be setting the third bit but you would be clearing all the others too, which is not what you want at all.

As I mentioned in an earlier post, the best way to set up a port is to read the current settings, change the ones you care about, and write them back. This begs the question how do you clear a bit? The answer is fairly easy. If you consider the PARENB flag, to turn off parity checking you need to ensure this bit is 0. The normal way to do this is to invert the PARENB mask and AND it into the control_flags var. To do this, you first use the arithmetic NOT operation (so ~PARENB is 0b11111011) which generates a mask with a 0 in the position you want cleared. If you AND this into the register it will ensure the third bit is clear *without affecting any of the other bits*. Hence, to ensure parity checking is turned off you would write:
```
    control_flags = control_flags & ~PARENB;

```(And finally, note that C/C++ has a shorthand way of writing code of form "var = var op value" in which you can prepend the op onto the = and drop the repeat mention of the var. Thus i=i+1 can be written i += 1. Hence, you can write either:
```
    control_flags  = control_flags | PARENB;
or  control_flags |= PARENB;

```whichever makes you comfortable.)

Rgds
Vernon

---

### Post by GhostRider22 on 2010-10-25
I appreciate the response, and that all made sense. 

My only question, and maybe im missing something simple, looking at the library files for example [http://www.opengroup.org/onlinepubs/007908799/xsh/termios.h.html](http://www.opengroup.org/onlinepubs/007908799/xsh/termios.h.html)

How do you know which bit is supposed to be which settings?

EDIT

Nvm, i skipped your line explaining that they are defined the first read though.

---

