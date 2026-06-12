---
title: "Help with connecting usb/serial device with program in terminal"
date: 2016-08-07
forum: New to Ubuntu
---

### Post by dnezl on 2016-08-07
Hi!

I'm running Ubuntu 16.04 LTS and my skills in ubuntu are rather limited, my google works tho. 

I need help with connecting to my usb-device and reading the data stored on it using a program called GpsDump, downloaded here [http://www.gpsdump.no/](http://www.gpsdump.no/).
I have found two previous posted issues mentioning the program but not a solution to my problem [here]("https://ubuntuforums.org/showthread.php?t=2124077&highlight=gpsdump") and [here]("https://ubuntuforums.org/showthread.php?t=1403398&highlight=gpsdump").

After downloading the program I run it in terminal 

```
$ ./gpsdump.0.12
GpsDumpLinux 0.12 commands:


-h   Display this text


-gc  GPS = Brauniger/Flytec family (not IQ Basic or Flytec 6015)
-gdg GPS = Digifly Graviter
-gg  GPS = Garmin (most models)
-giq GPS = IQ Basic
-gm  GPS = MLR protocols
-gx  GPS = XCTrainer (MXP2004 protocol at 57600 bauds)
-gy  GPS = Flymaster


-c"N"      Serial port N. Translates into /dev/ttyS"N"
-ca"name"  USB COM port. Translates into /dev/ttyACM"name"
-cu"name"  USB-to-serial port. Translates into /dev/ttyUSB"name"


-l"File"  Download a track and save it in a file. Extensions .kml and .igc
          are supported. If the extension is not recognized, both file types
          are generated. For the Brauniger/Flytec models the raw IGC data
          from the GPS is saved. If no name is given gpsdump will make one
          from the time stamp of the first position.


-f"N"     Select a specific flight (Brauniger/Flytec/Flymaster).
          If N=0 a flightlist is displayed.


-w"File"  Download waypoints and save them in a file. Extensions .gpx, .wpt
          (Ozi format) and .kml are supported. If the extension is not recognized
          all file types are generated. If no name is given gpsdump will make one
          from the current time. Supported GPS: Garmin, Brauniger/Flytec and Flymaster.


-r"File"  Read waypoints from a file and upload them to the GPS. Supported file
          formats: Ozi and GpsDump/$FormatGEO. Supported GPS: Garmin,
          Brauniger/Flytec and Flymaster.


--gap "Time"  Set gap (in integer minutes) between consecutive track points for
              detecting multiple tracks. If set to zero a single track is assumed.
              If not set, a single track is assumed, unless divided by the GPS (e.g. Garmin).
              A list is printed for the user to select from (comma separated input).


-x"File" Convert .igc to .kml


--noana   Skip speed analysis.
--scroll  Progress lines to terminal include crlf.

```
Figured out what port my device is mapped to and tried something I found somewhere else on the forum giving me this:
```
$ dmesg | grep tty
[    0.000000] console [tty0] enabled
[76042.701468] usb 2-1.1: pl2303 converter now attached to ttyUSB0

$ lsusb
Bus 002 Device 004: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port

$ ls -l /dev/bus/usb/002/004
crw-rw-r-- 1 root root 189, 131 aug.   7 18:16 /dev/bus/usb/002/004

```


I figure as my device is a IQ Basic and it should be on USB0 I tried to following commands unsuccessfully.
```

$ ./gpsdump.0.12 -giq -cu0 -f0
No GPS command found

$ ./gpsdump.0.12 -giq -cu0 -lFlight
Could not open COM port /dev/ttyUSB0

```

So, any ideas what I need to do to dump that flight-file onto my computer? I've tried running the commands in sudo but that didn't help. As you can tell there should be several "flights" or tracks on the device and I would like to view the list of flights before downloading the specific one I want and saving it to a file. I don't know if I am using the wrong command lines or if there is a problem with the connection to the device like driver issues. I know the device works fine when running GpsDump in Windows 8.

---

### Post by HermanAB on 2016-08-08
To access usb serial ports, make yourself a member of the dialout group.

To see which device the serial thingy shows up as, do:
$ ls /dev/tty*

(it may not be the save device every time)

You may need to set the serial port speed with stty:
$ stty -F /dev/ttyUSB0 9600

---

### Post by dnezl on 2016-08-08
> **HermanAB said:**
> To access usb serial ports, make yourself a member of the dialout group.

To see which device the serial thingy shows up as, do:
$ ls /dev/tty*

(it may not be the save device every time)

You may need to set the serial port speed with stty:
$ stty -F /dev/ttyUSB0 9600

Thanks for the reply Herman! I've tried what you mentioned and I think it was a matter of my user not being in the dialout group and me not running the program correctly. Added what I did below if people are interested.
The device comes up as this:
```

$ls /dev/tty*
/dev/ttyUSB0
```

I added my user to the group dialout.
```

$ [COLOR=#111111][FONT=Consolas]sudo adduser "username" dialout[/FONT][/COLOR]
```
I ran your command for setting the baud to 9600 but I didn't get any immediate feedback for the command being accepted so I did this to confirm:
```

$ stty -F /dev/ttyUSB0 -a
speed 9600 baud; rows 0; columns 0; line = 0;
intr = ^C; quit = ^\; erase = ^?; kill = ^U; eof = ^D; eol = <undef>; eol2 = <undef>; swtch = <undef>;
start = ^Q; stop = ^S; susp = ^Z; rprnt = ^R; werase = ^W; lnext = ^V; discard = ^O; min = 1; time = 0;
-parenb -parodd -cmspar cs8 hupcl -cstopb cread clocal -crtscts
-ignbrk -brkint -ignpar -parmrk -inpck -istrip -inlcr -igncr icrnl ixon -ixoff -iuclc -ixany -imaxbel
-iutf8
opost -olcuc -ocrnl onlcr -onocr -onlret -ofill -ofdel nl0 cr0 tab0 bs0 vt0 ff0
isig icanon iexten echo echoe echok -echonl -noflsh -xcase -tostop -echoprt echoctl echoke -flusho
-extproc

```

I had a suspicion that the gpsdump wouldn't give me feedback in the terminal for the settings being set so I tried this first and I was correct:
```

$ ./gpsdump.0.12 -lFlight1
No GPS type specified
```
So I specified my gps type with the same as before:
```

$ ./gpsdump.0.12 -giq
No GPS command found
$ ./gpsdump.0.12 -giq -cu0
No GPS command found
$ ./gpsdump.0.12 -giq -cu0 -lFlight1
Product: IQ-BASIC, SW 1.3.07, S/N 6584
Track list:
     0; 16.07.24; 15:20:28;        2; 0
     1; 16.07.24; 13:08:37;        2; 0
     2; 16.07.23; 11:59:32;        2; 0
     3; 16.07.18; 17:28:58;        2; 0
     4; 16.07.18; 16:36:31;        2; 0
     5; 16.07.18; 15:54:42;        2; 0
     6; 16.07.15; 16:33:16;        2; 0
     7; 16.07.15; 16:01:24;        2; 0
     8; 16.07.15; 15:26:12;        2; 0
     9; 16.06.14; 17:03:06;        2; 0
    10; 16.06.13; 19:45:22;        2; 0
    11; 16.06.12; 17:40:23;        2; 0
    12; 16.06.11; 17:35:13;        2; 0
    13; 16.06.11; 16:55:03;        2; 0
    14; 16.06.11; 13:50:38;        2; 0
    15; 16.06.06; 13:10:54;        2; 0
    16; 16.06.05; 17:56:14;        2; 0
    17; 16.05.11; 18:59:32;        2; 0
    18; 16.05.11; 14:26:19;        2; 0
    19; 16.05.11; 14:19:08;        2; 0
    20; 16.05.11; 14:05:44;        2; 0
    21; 16.05.11; 12:39:37;        2; 0
    22; 16.05.09; 16:55:39;        2; 0
    23; 16.05.09; 12:51:56;        2; 0
    24; 16.04.20; 17:56:08;        2; 0
    25; 16.04.16; 14:31:06;        2; 0
    26; 16.04.16; 12:23:30;        2; 0
    27; 16.04.13; 12:00:45;        2; 0
    28; 16.04.12; 12:37:37;        2; 0
    29; 16.04.11; 15:07:27;        2; 0
    30; 16.04.11; 11:00:04;        2; 0
    31; 16.04.10; 13:08:38;        2; 0
    32; 16.04.10; 10:56:44;        2; 0
    33; 16.04.06; 16:34:16;        2; 0
    34; 16.04.06; 15:00:33;        2; 0
    35; 16.04.04; 15:20:43;        2; 0
    36; 16.04.03; 10:34:33;        2; 0
    37; 16.04.02; 12:22:10;        2; 0
    38; 16.04.01; 10:31:29;        2; 0
    39; 16.03.31; 10:25:44;        2; 0
    40; 16.03.30; 12:32:41;        2; 0
    41; 16.03.30; 11:23:07;        2; 0
    42; 16.03.29; 12:34:58;        2; 0
    43; 16.03.28; 12:19:00;        2; 0
    44; 16.03.28; 08:56:10;        2; 0
    45; 16.03.27; 10:35:49;        2; 0
    46; 16.03.23; 15:29:28;        2; 0
    47; 16.02.14; 15:30:37;        2; 0
    48; 16.02.14; 13:35:38;        2; 0
    49; 16.02.09; 13:40:12;        2; 0
 Done
Select: 
```


Great success! :D The list corresponds to the flights done with the gps. Continued below; selecting a flight saved the flight in the folder of the GpsDump in both .kml and .igc formats.
```

Select: 0
Match in flight list for flight 0
Bytes: 30116
Computing statistics
Finding greatest out-and-return (gap = 800m)
Finding greatest triangles (gap = 800m)
File Flight1.kml written, NO signature
File Flight1.igc written
```

I added this, stolen from another thread, not sure if I need it tho.
```
sudoedit /etc/udev/rules.d/50-myusb.rules
Save this text:
KERNEL=="ttyUSB[0-9]*",MODE="0666"
KERNEL=="ttyACM[0-9]*",MODE="0666"
```

---

### Post by dnezl on 2016-08-08
Now if only a mod could tag this thread with GpsDump.

---

### Post by dnezl on 2016-12-01
Tried again on a new computer with 64bit CPU. Couldn't open the gpsdump at all and recieveing the error message "No such file or directory".

Did this and now it works!

```
sudo apt-get install libc6:i386 libncurses5:i386 libstdc++6:i386
apt-get update
```

However, I couldn't get access to read/write to the port so this remedied that:

```
sudo usermod -a -g dialout <username>
```

Logget out and in again and tried again.

---

