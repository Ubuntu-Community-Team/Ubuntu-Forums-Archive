---
title: "Log Serial Port Data to a Specified Logfile"
date: 2007-11-15
forum: Programming Talk
---

### Post by duuchung on 2007-11-15
I am not a programmer. I only know a little programming.  My inventor friend asks me to capture data in a file from a test board device connected to the serial port. He wants to use the captured data for further processing.

I found [http://ubuntuforums.org/showthread.php?t=432](http://ubuntuforums.org/showthread.php?t=432).

I installed Device-SerialPort-1.002 with a bit of hard work.

I read Bill Birthsiel's article, Controlling Modems with Win32::SerialPort.

I connected my friend's test board with the serial interface of my Linux ubuntu.

I played with example1.txt, example4.txt and example5.txt. I set the baud rate to 4800 in  example4.txt. I input ASCII numbers into the test board with example5.txt. I read the output of example5.txt in the LCD panel which displayed the numbers I had keyed into the test board.The test board device has been properly connected to my PC and there are signals passing.


I found Bruce Garlock's article, Log Serial Port Data to a Specified Logfile, from the internet.I added  Birthsiel's example5.txt with Garlock's logger.pl. The new file does not work. Nothing was sent to the log file. There is something missing. I need help. Can any guru please help me?

example4sve.pl
```

#!/usr/bin/perl -w

# cross-platform example4


#use strict;

use vars qw( $OS_win $ob $port );


BEGIN {

        $OS_win = ($^O eq "MSWin32") ? 1 : 0;

        if ($OS_win) {

            eval "use Win32::SerialPort";

	    die "$@\n" if ($@);

        }

        else {

            eval "use Device::SerialPort";

	    die "$@\n" if ($@);

        }

} # End BEGIN

$LOGDIR    = "/var/log";              # path to data file

$LOGFILE   = "serial.log";            # file name to output to


if ($OS_win) {

    $port = '/dev/ttyS0';

    $ob = Win32::SerialPort->new ($port);

}

else {

    $port = '/dev/ttyS0';

    $ob = Device::SerialPort->new ($port);

}

die "Can't open serial port $port: $^E\n" unless ($ob);



$ob->user_msg(1);	# misc. warnings

$ob->error_msg(1);	# hardware and data errors


$ob->baudrate(4800);

$ob->parity("none");

## $ob->parity_enable(1);   # for any parity except "none"

$ob->databits(8);

$ob->stopbits(1);

$ob->handshake('rts');


$ob->write_settings;


####new

#

# Send a string to the port

#

#

#$ob->write("AT");

$ob->write("ATE0X4\r"); 

sleep 1;



#

# open the logfile, and Port

#



open(LOG,">>${LOGDIR}/${LOGFILE}")

    ||die "can't open smdr file $LOGDIR/$LOGFILE for append:  $!\n";


open(DEV, "<$port") 

    || die "Cannot open $port: $_";


select(LOG), $| = 1;      # set nonbufferd mode


#

# Loop forver, logging data to the log file

#


while($_ = <DEV>){        # print input device to file

    print LOG $_;

}


undef $ob;
```




















I added  Birthsiel's example5.txt with Garlock's logger.pl. The new file does not work. Nothing was sent to the log file.

---

### Post by zero-9376 on 2007-11-15
you might want to look at a program called ttylog (in repos) which i believe can do what you want using normal bash redirection. i wrote a serial port logger for python as well but i dont know where that is atm, but it used the pyserial module from sourceforge (also in repos)

---

### Post by kunilkuda on 2007-11-16
I'm firmware developer for AVR MCU, and using ubuntu to host my utility.

My favourite script to log RS232/serial port is : [http://www.uni.aps.anl.gov/controls/docs/serialWatch.html](http://www.uni.aps.anl.gov/controls/docs/serialWatch.html) Using that script, I can log all the MCU's event (and time) to any log file (using redirection, of course).

Note that your board must use ASCII/text output, the script cannot capture binary data over serial port. Also, you need to install "expect" to run the script.

To log binary data over serial port, I think you should create your own program (but it's easy..don't worry about it). Read this link to do that : [http://tldp.org/HOWTO/Serial-Programming-HOWTO/index.html](http://tldp.org/HOWTO/Serial-Programming-HOWTO/index.html)

---

### Post by duuchung on 2007-11-16
I followed up all your advice.

I installed ttylog and am still figuring how to use it.

I installed expect and read the 2 leads. I updated what I could see fit for seialWatch.exp for my ttyS0.  It worked and displayed the 1st few lines.  However when I keyed in numbers in ASCII into the test board and they did not show up with the timestamp on the LCD panel as expected. Nothing went thru the serial interface as recognized by  seialWatch.exp.  I ran the example5.txt under the CPAN module Device::SerialPort seconds later, and the LCD panel showed the ASCII output from the test board.  

Something is still missing but so far so good I learned a lot. Thank you for your advice.

---

### Post by ahmatti on 2007-11-19
ttylog is very easy to use. If you want to log data with 9600 bps from /dev/ttyS0 you'd type 

```
ttylog -b 9600 -d /dev/ttyS0
```

To save output to file.txt

```
ttylog -b 9600 -d /dev/ttyS0 > file.txt 
```

You can also do the logging straight from shell using:

```
cat /dev/ttyS0 > file.txt
```

And use stty (see man stty) to change the settings of the serial port.

---

### Post by duuchung on 2007-11-22
Tks my fellow ubuntu comrades.

I tried "ttylog -b4800 -d /dev/ttyS0". The tty program was running. I keyed figures into the test board. Nothing appeared in the LCD pane.

I changed the flow control by "stty -F /dev/ttyS0 crtscts". I issued 
"stty -a
"
The following settings appeared:
```

"speed 4800 baud; rows 24; columns 69; line = 0;

intr = ^C; quit = ^\; erase = ^?; kill = ^U; eof = ^D; eol = M-^?;

eol2 = M-^?; swtch = M-^?; start = ^Q; stop = ^S; susp = ^Z;

rprnt = ^R; werase = ^W; lnext = ^V; flush = ^O; min = 1; time = 0;

-parenb -parodd cs8 hupcl -cstopb cread -clocal -crtscts

-ignbrk brkint -ignpar -parmrk -inpck -istrip -inlcr -igncr icrnl ixon

-ixoff -iuclc ixany imaxbel iutf8

opost -olcuc -ocrnl onlcr -onocr -onlret -ofill -ofdel nl0 cr0 tab0

bs0 vt0 ff0

isig icanon iexten echo echoe echok -echonl -noflsh -xcase -tostop

-echoprt echoctl echoke"

Nothing came forward to the LCD monitor. I switched back to example5.txt of Device-SerialPort. Data could be sent by the test board to the LCD.
The following settings appeared:
"B = 9600, D = 8, S = 1, P = none, H = rts"
```


Something is still missing. I am learning. Tks

---

### Post by duuchung on 2007-12-18
I finally solved the puzzle. The black box is less dark now. I modified the demo1.plx with all my knowledge accumulated from the payless, relentless and endless internet search. Input from the test board can be displayed on the LCD monitor and stored in a file.
My next step is to write a program to capture the input via the test board or keyboard with the choice by the user and store the chosen data in a file. I do not have a clue to do it at this stage. 

I attach the file below for people who are interested. Thank-you my Ubuntu friends.
```

#!/usr/bin/perl 
use lib './blib/lib','../blib/lib'; # can run from here or distribution base

######################### We start with some black magic to print on failure.

BEGIN { $| = 1; print "demo1.plx loaded "; }
END {print "not OK 1\n" unless $loaded;}
use Device::SerialPort 0.05;
$loaded = 1;
print "O Kay 1\n";

######################### End of black magic.

use strict;

my $PORT = "/dev/ttyS0";
my $pass;
my $fail;
my $in;
my $title1;
my $inputval;
my $title4;
my $title2;
my $title3;

# 2: Constructor and Basic Values

my $ob = Device::SerialPort->new ($PORT) || die "Can't open $PORT: $!";

$ob->baudrate(4800)	|| die "fail setting baudrate";
$ob->parity("none")	|| die "fail setting parity";
$ob->databits(8)	|| die "fail setting databits";
$ob->stopbits(1)	|| die "fail setting stopbits";
$ob->handshake("none")	|| die "fail setting handshake";

$ob->write_settings || die "no settings";

# 3: Prints Prompts to Port and Main Screen

$title1= "\r\n\r\n++++++++++++++++++++++++++++++++++++++++++\r\n";
$title2= "Simple Serial Terminal with echo to STDOUT\r\n\r\n";
$title3= "type CONTROL-Z on serial terminal to quit\r\n";
$title4="\r\n....Bye\r\n";

print $title1, $title2, $title3;

$ob->error_msg(1);		# use built-in error messages
$ob->user_msg(1);
$in = 1;
while ($in) {
    if (($inputval= $ob->input) ne "") {
	$inputval =~ s/\cM/\r\n/;
	#$ob->write($loc);
	print STDOUT $inputval;

open LOG, ">>test.log" || die "$!\n";
open(DEV, "<$PORT") 
    || die "Cannot open $PORT: $_";
select(LOG), $| = 1;      # set nonbufferd mode
#
print LOG $inputval;
}
    if ($inputval =~ /\cZ/) { $in--; }
    if ($ob->reset_error) { $in--;}
}
close(LOG);
print $title4;
sleep 1;
undef $ob;
```

---

### Post by duuchung on 2007-12-18
I finally solved the puzzle. The black box is less dark now. I modified the demo1.plx with all my knowledge accumulated from the payless, relentless and endless internet search. Input from the test board can be displayed on the LCD monitor and stored in a file.
My next step is to write a program to capture the input via the test board or keyboard with the choice by the user and store the chosen data in a file. I do not have a clue to do it at this stage. 

I attach the file below for people who are interested. Thank-you my Ubuntu friends.

regards 
duuchung

#!/usr/bin/perl 
use lib './blib/lib','../blib/lib'; # can run from here or distribution base

######################### We start with some black magic to print on failure.

BEGIN { $| = 1; print "demo1.plx loaded "; }
END {print "not OK 1\n" unless $loaded;}
use Device::SerialPort 0.05;
$loaded = 1;
print "O Kay 1\n";

######################### End of black magic.

use strict;

my $PORT = "/dev/ttyS0";
my $pass;
my $fail;
my $in;
my $title1;
my $inputval;
my $title4;
my $title2;
my $title3;

# 2: Constructor and Basic Values

my $ob = Device::SerialPort->new ($PORT) || die "Can't open $PORT: $!";

$ob->baudrate(4800)	|| die "fail setting baudrate";
$ob->parity("none")	|| die "fail setting parity";
$ob->databits(8)	|| die "fail setting databits";
$ob->stopbits(1)	|| die "fail setting stopbits";
$ob->handshake("none")	|| die "fail setting handshake";

$ob->write_settings || die "no settings";

# 3: Prints Prompts to Port and Main Screen

$title1= "\r\n\r\n++++++++++++++++++++++++++++++++++++++++++\r\n";
$title2= "Simple Serial Terminal with echo to STDOUT\r\n\r\n";
$title3= "type CONTROL-Z on serial terminal to quit\r\n";
$title4="\r\n....Bye\r\n";

print $title1, $title2, $title3;

$ob->error_msg(1);		# use built-in error messages
$ob->user_msg(1);
$in = 1;
while ($in) {
    if (($inputval= $ob->input) ne "") {
	$inputval =~ s/\cM/\r\n/;
	#$ob->write($loc);
	print STDOUT $inputval;

open LOG, ">>test.log" || die "$!\n";
open(DEV, "<$PORT") 
    || die "Cannot open $PORT: $_";
select(LOG), $| = 1;      # set nonbufferd mode
#
print LOG $inputval;
}
    if ($inputval =~ /\cZ/) { $in--; }
    if ($ob->reset_error) { $in--;}
}
close(LOG);
print $title4;
sleep 1;
undef $ob;

---

### Post by regomodo on 2008-02-26
sorry to necrobump this thread but i'm having a little issue with ttylog

For some reason i am only able to run ttylog as root through sudo. I thought there is possibly a ttylog group but it didn't work when i tried to add myself to it.
```

jon@debpc:~$ groups
jon tty dialout cdrom floppy audio video plugdev netdev scanner fuse vboxusers
```

What group do i have add myself to?

---

### Post by ryanhaigh on 2008-02-26
Have you checked the permissions on the device you are trying to access? If there is a special group that should tell you what it is.

---

### Post by regomodo on 2008-02-27
`

---

### Post by ryanhaigh on 2008-02-27
perhaps it uses a different output the plain stdout like the error output have a look at bash redirection that may help. im pretty sure when i did this i used the program tee to have the text in a file and on the screen but it was a while ago now

```
ttylog -d /dev/ttyUSB0 -b 9600 | tee log.txt
```

---

