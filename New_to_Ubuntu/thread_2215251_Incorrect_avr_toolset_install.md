---
title: "Incorrect avr toolset install"
date: 2014-04-05
forum: New to Ubuntu
---

### Post by imbatronics on 2014-04-05
Greetings all

I am trying to use the serial functionality of my Arduino Mega2560. I am also very new to Linux thats why I'm in beginner section! First time poster ):P

Recently installed ubuntu 12.04 alongside windows 7 to avoid additional hardware when coding in C on Arduino.

For what i was trying to do, I was told to install the following tools: avr-gcc, avr-libc, avrdude. This was fine, I could handle even though I was not used to the linux installation protocol. My problem arose when I was trying to compile my main.c using **gcc main.c -o MateDealer** such that I could run the code from terminal/test it on the Arduino.

$ **make all**  //worked fine, no errors
$ **make program** //worked fine, no errors
[FONT=arial]hex file was generated and uploaded to the Arduino (I assume, since Tx and Rx lights were going crazy, no errors, avrdude seemed happy)

So, I tried to compile:[/FONT]
**gcc main.c -o MateDealer**

I get 
[B]main.c:16:20: fatal error: avr/io.h: No such file or directory
compilation terminated.[/B]

At this stage I had no idea what was going on, so I tried to copy/paste the io.h file from where it was sitting to where it should be
First I needed to see where the includes needed to be so I ran
**avr-gcc -print-file-name=include**


which gave me
**/usr/lib/gcc/avr/4.5.3/include**


then I used
 **cp /usr/lib/avr/include/avr/io.h /usr/lib/gcc/avr/4.5.3/include**


which gave me
**cp: cannot create regular file `/usr/lib/gcc/avr/4.5.3/include/io.h': Permission denied**

[FONT=arial]So, I tried to work around this by changing the **#include <avr/io.h>** in main.c to **[FONT=arial]#include "io.h"[/FONT]** and copying (using terminal command cp) io.h to the folder in which main.c is sitting.[/FONT]
[FONT=arial]Then, when I ran **gcc main.c -o MateDealer **[FONT=arial]in terminal I got a _different_ err[/FONT][/FONT][FONT=arial]or compared to the above error[/FONT][FONT=arial][FONT=arial]
**main.c:16:20: fatal error: avr/io.h: No such file or directory**** .**
Instead, another "sub header file" _which is included in io.h_ is also missing. I also need to include about 5 more header files e.g avr/xxx.h and I assume each of them include their own "sub header files".

My conclusion is that the compile found io.h, but I can't do this manually for each missing header file as it will take ages. I believe I have installed either avr-gcc, avr-libc, or avrdude (not sure which one) in the wrong location! While trying to fix this I stumbled upon [http://www.nongnu.org/avr-libc/user-manual/install_tools.html#install_avr_binutils](http://www.nongnu.org/avr-libc/user-manual/install_tools.html#install_avr_binutils) which gave me the idea of incorrect install path. I also got errors after the [/FONT][/FONT]**$ make**[FONT=arial][FONT=arial] command (see link above) when trying to install binutils.[/FONT][/FONT]

[FONT=arial]How can I:

a) determine which of the 3 mentioned tools (if not all) I have installed in the incorrect place/directory/path?
b) reinstall the misplaced tool in the correct location?

Appologies for the long post, I just wanted to make sure I am being clear as I often get lost trying to read other forum threads. Thank you in advance for your help![/FONT]

---

