---
title: "Problem Using Uppercase Only Terminal"
date: 2011-12-12
forum: New to Ubuntu
---

### Post by Ronny Svedman on 2011-12-12
I am in pretty much the same situation, only I have a Tektronix 4006-1 storage tube vector graphics terminal.

This one is even dumber when it comes to text than a tty because ti doesn't even backspace.. :/

BUT I would still like to be able to login from it and telnet to the PDP-11 emulator at the computer club at university, for the nice feeling of it, and for playing with tek graphics. (which I can admittedly do with xterm in tek emulation mode, but real iron is nicer). I have got as far as the original poster, I can login to an account with all-caps password, but despite the port (/dev/ttyUSB0 in my case) says it has iuclc, olcuc and xcase set, no case conversion appears to take place. 

Do I need to go to another OS (bsd, maybe) to get that old functionality? Does anyone know if it has been removed from the terminal drivers in the linux kernel? 

Ultrix, for example (dec unix for vax computers based on bsd 4.4), does set these options when you login with an all caps username, and from there on you can type capital letters by prefixing a backslash to them. 

Agetty in ubuntu 11.04 (i386 32bit), says in the manpage that -U on the commandline will turn on case conversions , and actually does set these options (iuclc, olcuc and xcase), but they have no apparent effect. Could it be that modern day bash ignores or resets this flag, or should conversion take place before bash gets the input? 

Please feel free to move this question away from beginner talk to something more appropriate if you can.

---

### Post by oldos2er on 2011-12-12
Post moved to its own thread.

---

### Post by Cato2 on 2011-12-13
I don't know the answer but you could edit your ~/.bash_profile from another terminal to include "stty -a" so you can see what is set, or directly set "stty iuclc" etc in the profile.

This may well be a kernel bug in the tty driver - see [http://www.mail-archive.com/bug-coreutils@gnu.org/msg19381.html](http://www.mail-archive.com/bug-coreutils@gnu.org/msg19381.html)

See also this thread, where it seems that "stty iexten iuclc" may help, though you may also need a password without alphabetic characters: [http://lists.gnu.org/archive/html/bug-coreutils/2010-02/msg00019.html](http://lists.gnu.org/archive/html/bug-coreutils/2010-02/msg00019.html)

Probably best to post in another forum here.

---

### Post by Ronny Svedman on 2011-12-22
After digging som emore, it turns out, the XCASE flag is not implemented in modern linux. together with iextend, iuclc  and olcuc does work, but there is no mechanism for prefixing uppercase characters, which means in modern linux a singlecase terminal is vritually unusable. I created a user with all caps name and all caps password, and made a uppercase named script that turns on iuclc and olcuc and iextend, and that lets me login and run simple commands, but there is no way to input shifted characters. also, xon/xoff flow control does not work even though stty ixon and ixoff are both in effect. I am usin /bin/sh for shell, since bash's prompt handling makes a mess of the display; the tek is too simple even for that.

iextend turns on non-posix options, and posix dropped uppercase support, so, man termios says:

 IEXTEN Enable implementation-defined input processing.  This  flag,  as
              well  as ICANON must be enabled for the special characters EOL2,
              LNEXT, REPRINT, WERASE to be interpreted, and for the IUCLC flag
              to be effective.


[FONT=Fixedsys]this is the output of stty -a as run from the tektronix:

speed 4800 baud; rows 35; columns 72; line = 0;
intr = ^C; quit = ^\; erase = ^?; kill = ^U; eof = ^D; eol = <undef>;
eol2 = <undef>; swtch = <undef>; start = ^Q; stop = ^S; susp = ^Z; rprnt = ^R;
werase = ^W; lnext = ^V; flush = ^O; min = 1; time = 0;
-parenb -parodd cs8 hupcl -cstopb cread clocal -crtscts
-ignbrk -brkint -ignpar -parmrk -inpck -istrip -inlcr -igncr icrnl ixon ixoff
iuclc -ixany -imaxbel -iutf8
opost olcuc -ocrnl onlcr -onocr -onlret -ofill -ofdel nl0 cr0 tab0 bs0 vt0 ff0
isig icanon iexten echo echoe echok -echonl -noflsh xcase -tostop -echoprt
echoctl echoke



Note that stty -a reports xcase to be in effect, and man stty says:

 * [-]xcase
              with icanon, escape with `\' for uppercase characters



BUT, man termios says:

.. XCASE  (not in POSIX; not supported under Linux) If ICANON is also set,
              terminal  is  uppercase  only.  Input is converted to lowercase,
              except for characters preceded by \.  On output, uppercase char&#8208;
              acters  are preceded by \ and lowercase characters are converted
              to  uppercase.   [requires  _BSD_SOURCE   or   _SVID_SOURCE   or
              _XOPEN_SOURCE]


so , it seems stty is blatantly lying to me.



that xon/xoff doesnt work anymore despite stty saying so (it did back in 2006 or so), is very confusing to me, and annoying since the tek doesn't scroll but has to erase the entire display, and i really really need a pause in output every 35 lines. Also the tek loses characters without working flowcontrol above 2400 bps.

also i suppose (but haven't tested yet) that his effectively will make it impossible to use my visual 550 (vt100 emulating early raster graphics terminal) or my vt102 even if I would get them from the cellar :(  

I wonder if it makes a difference that I'm using a USB-serial dongle rather than an oldfashioned com port? (there is none on my sony vaio..) 

lsusb reports:

Bus 005 Device 002: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port
 
which is supposed to be supported, and does work, showing up as /dev/ttyUSB0, apart from these problems I mention above. It will not do 110 or 150 baud but 300 and up is fine. 

anything else I could look for? maybe someone knows if a kernel compile with the right options (what is bsdsource, mentioned is the termios manpage?) might help me ?




[/FONT]

---

### Post by Cato2 on 2011-12-23
Looks like you are into the realm of kernel fixes...

You might like to try FreeBSD as that will have a more traditional Unix terminal driver - however that may not support your hardware so well as this is a laptop.  PC-BSD is a distribution of FreeBSD that is quite easy to install - see [http://en.wikipedia.org/wiki/PC-BSD](http://en.wikipedia.org/wiki/PC-BSD) - seems to include a live DVD: [http://harrykar.blogspot.com/2010/06/pc-bsd.html](http://harrykar.blogspot.com/2010/06/pc-bsd.html)

---

### Post by Ronny Svedman on 2011-12-27
I have a spare P4 /2.4 that has built in oldfashioned comports, and a gig of ram. I suppose it would be a nice BSD box, but there's no room on my desk for more screens.. hm. I could ssh into it ofcourse (or have the serial as console...). I am tempted to try that now. But removing xonf/xoff can not be ok even for ubuntu, because it will break kermit/zmodem etc over telnet/ssh as well as make life hard for people with oldfashioned modems. Can anyone confirm xon/xoff is really not working anymore, and if that is documented anywhere?  Dropping support for one-case terminals is ofcourse reasonable, but it should have been documented more obviously somehow. Dropping support for serial terminals altogether is IMHO a bad idea, and Xon/xoff working in the standard shell environment is really needed for many of them.

---

### Post by Ronny Svedman on 2012-07-07
I found out the problem with xon/xoff is actually that my USB-to-serial dongle has 1 K buffers built in. 1K of data is quite a few seconds at 2400 baud. When the terminal is on a motherboard serial port in my desktop system running 12.04/amd64, xon/xoff works as expected.(the 16550 standard port has 16 bytes buffer)

  The XCASE option to stty does not work on normal hardware either so that seems to be gone for good.

---

