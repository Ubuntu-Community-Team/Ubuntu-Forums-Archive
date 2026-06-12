---
title: "How send/receive binary values via rs232"
date: 2009-05-19
forum: Programming Talk
---

### Post by ritchie-w on 2009-05-19
Hi,

I just have the problem,that I try to write a data transmission
via rs232 of binary values (3964) between a to machines.

I do not get transmitted a 0x2 Value (STX), and a 0x0 (NUL) value.
(receiving and transmit).

I use the following termios setting, which should really raw mode:
> 
	term_attr.c_iflag &= ~(BRKINT | ICRNL | INPCK | ISTRIP | IXON | IUCLC | INLCR| IXANY );

	/* output modes - clear giving: no post processing such as NL to CR+NL */
	term_attr.c_oflag &= ~(OPOST|OLCUC|ONLCR|OCRNL|ONLRET|OFDEL);

	/* control modes - set 8 bit chars */
	term_attr.c_cflag |= ( CS8 ) ;

    /* local modes - clear giving: echoing off, canonical off (no erase with 
	backspace, ^U,...),  no extended functions, no signal chars (^Z,^C) */
	term_attr.c_lflag &= ~(ECHO | ECHOE | ICANON | IEXTEN | ISIG);

	term_attr.c_cflag |= CRTSCTS;					// using flow control via CTS/RTS


But i do not get these values transmitted ? Why

Thanks for any help 

Ritchie

---

### Post by UbuKunubi on 2009-05-19
Have you used a volt/multi meter to make sure that the signal is flowing?
Is the serial port enabled in both machines BIOS's?

Can you post the code used to send and receive the RS232?

Need more info to provide more help.
All the best,
Ubu

---

### Post by ritchie-w on 2009-05-20
I use the following code for init
> 
{ 
    if ((fd = open(TERM_DEVICE, O_RDWR | O_NOCTTY)) == -1) 
        { 
        perror("terminal: Can't open device " TERM_DEVICE); 
        return(1); 
        } 
    /* configurare RS232 */ 
    if (tcgetattr(fd, &term_attr) != 0) 
        { 
        perror("terminal: tcgetattr() failed"); 
        return(1); 
        } 
    /* save old flags */ 
    old_flags = term_attr.c_lflag; 
    cfsetispeed(&term_attr, TERM_SPEED); 
    cfsetospeed(&term_attr, TERM_SPEED); 
    cfmakeraw(&term_attr); 

    term_attr.c_cflag |= CRTSCTS;                    // using flow control via CTS/RTS 
                                                            
    if (tcsetattr(fd, TCSAFLUSH, &term_attr) != 0) 
        { 
        perror("terminal: tcsetattr() failed"); 
        return(1); 
        } 

    /* change standard input */ 
    if (tcgetattr(STDIN_FILENO, &term_attr) != 0) 
        { 
        perror("terminal: tcgetattr() failed"); 
        return(1); 
        } 

    if (tcsetattr(STDIN_FILENO, TCSAFLUSH, &term_attr) != 0) 
        perror("terminal: tcsetattr() failed"); 

    FD_SET(fd, &input_fdset);                          /* Select the first channel 1 */ 
    return 0; 
} 


Read() and write() is used for transfering data.

After I changed this termios to the first posted setting I received char like 0x10 (DLE).

But I still fighting with char 0x0 and 0x2.

Buffer chars are defined as unsigned char*. 

I will write a small test code (send/receive) this evening to see which chars are filtered by termios configuration.

Thanks for help.

Ritchie

---

### Post by UbuKunubi on 2009-05-20
What speed are you running this connection at?

In the past ive started low (300 baud), and then ramped it up to find the safe speed given the setup/distance involved.

IF some of the data values are escape characters you will need to double escape them at the transmit side, and then de-escape them on the recieve.

Hope im not trying to teach you how to suck eggs!

---

### Post by ritchie-w on 2009-05-20
Hi,

i am running with 9600Baud.
My testprogram is running well now. All chars will transmitted.

I tested the transmission with two program. One is only receiving, and the other is only writting.

Using standard function (write/read).

Now I have to test my original program, which is using send/receive and
acknowledgement of the transmission (DLE or NAK).

Will see if this works.

I tested the transmission directly in Kdevelop on both sides and it works.
with and without delay.

>Hope im not trying to teach you how to suck eggs! 
No problem. But it isn't my first data transmission i programmed.
But ubuntu / linux is quiet new for me in this manner. Even I am using 
a converter and I do not have a data analyser to test it :-(. 

Anyways thanks for support. 
I will report you the results of the final test. Yesterday i still 
lost chars, but i do not know where ?

Ritchie

---

### Post by ritchie-w on 2009-05-20
Hi,

the function is now working fine.
The main problem was almost the function 

	cfmakeraw(&term_attr);

It means, send/receive Data in raw,
but some char's like STX, DLE or maybe other as well
will come as 0 to the calling function read() back.

That was the reason for the "lost chars".

Thanks for help

Ritchie

---

