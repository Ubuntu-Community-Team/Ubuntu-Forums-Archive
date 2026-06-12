---
title: "How hard would this be?"
date: 2008-09-23
forum: Programming Talk
---

### Post by Chondro_Biak on 2008-09-23
I have a program that was of course designed to run on Windows.

The programs function is as follows:
Monitor the status of your Herpstat product online.
Receive Scheduled Emails or VTEXT messages with status information.
Receive Emergency Email and VTEXT alerts.
Update the Herpstat’s firmware when code changes have been made.

The general idea is that you have a thermostat hooked up to a cage. And if you connect the thermostat to the computer you can monitor the temps etc. I would REALLY like to be able to do that with Ubuntu. I have not been able to get the program to work under Wine. 

How hard would it be to have the program rewrote to work under Ubuntu? 

Below is a link to the download website. Under "Herpstat Uploader Software"

I have been using Linux for about 5 years now, but I have never done programing. 

Any ideas? Suggestions? Difficulty level? lol

thanks
Chondro

---

### Post by skullmunky on 2008-09-25
Oh, that's cool.  btw your link was not included in the post but I looked it up.  It might be very hard or very easy - it depends on how hard it is to get access to the protocol the device uses.

Possibility 1: it has a proprietary USB driver.  then, this is hard, and is a job for god-level kernel hackers, because you would need to reverse engineer the driver based on analysing the USB data traffic.  well maybe just a wizard-level kernel hacker.  but tough nonetheless.

Possibility 2: the USB cable is really just a serial->usb emulation, such that the win32 herpstat software sees it as COM3 or similar.  then this is a little easier, because you can use standard serial port programming.

But, you still need to know the communication protocol the device uses.

I'd suggest contacting the manufacturer and asking if there is an SDK or protocol information available that you could use to write a program on linux to use your herpstat.  They might just say no but it's worth a try.  

I don't mean that you would necessarily go and write the program, :) but if they'll give you info then bring it back here ...

---

### Post by skullmunky on 2008-09-25
Another approach that would be easier if Spyder Robotics isn't helpful:

Get another thermometer that has a serial connection and an open protocol.  Then a simple python script will be able to monitor it and send you email alerts.

googling "thermometer serial port" found me this:

[http://www.spiderplant.com/hlt/index.html](http://www.spiderplant.com/hlt/index.html)

I don't know if that'd work for your application but there are certainly many others.

Another cheap, easy and fun approach would be to get an arduino and an electronic thermometer chip and build a device yourself:

[http://boundingbox.homelinux.net/blog/?p=39](http://boundingbox.homelinux.net/blog/?p=39)

---

### Post by Chondro_Biak on 2008-09-26
Thanks very much for the replies. 

I have contacted the manufacturer and he would love for it to be compatible to work with Linux. 

I have looked a little into this and it is a bit over my head. I don't know how to get this going with Linux. 

The thermostat uses option 2
"Possibility 2: the USB cable is really just a serial->usb emulation, such that the win32 herpstat software sees it as COM3 or similar. then this is a little easier, because you can use standard serial port programming."

But i still have no idea how to do that either.

---

### Post by skullmunky on 2008-09-28
That's great news!  Ok, next ask the manufacturer if they would be willing to make available the Serial Protocol that the device uses.

The protocol might be very simple - for example, the device maybe just sends a number every second, or every minute, or whatever, over the cable.

Or it might be a little more complicated, where the program sends a request for the current temp and the device sends it back.  Perhaps the protocol uses the letter "t" to ask for current temperature, the letter "r" to reset the device, "f" to ask for fahrenheit, "c" for celsius, etc.  so a conversation between the computer and device might look like this:

computer: "f"
computer: "t"
device: "76"
computer: "t"
device: "76.2"
computer: "t"
device: "75.9"
etc.


anyhoo, if they'll tell you what the protocol is, it probably would not be hard to write a program to do this.

---

### Post by Chondro_Biak on 2008-09-29
I sent them an email. 

Is the protocol going to be a program or a list?

I really appreciate your help. I have been messing with this for about a year now. I was just about to give up.

---

### Post by Chondro_Biak on 2008-09-29
Do you think it is possible to get this program to work "as is"? 

The product is designed to grab the data from the thermostat and put it on your computer. From there you can view it from anywhere by using your cell phone text messaging or view it using the internet. It will also receive and implement updates then received.

The manufacture is concerned that this might be taking a step backwards.

He told me his application was written in Visual Basic 6. Don't know if that helps at all?

Thoughts? Suggestions?

---

### Post by Chondro_Biak on 2008-09-29
A little more info:

the adapter is a USB to serial using a FTDI chip. There is linux support for that chip and their website is:

 [http://ftdichip.com/FTDrivers.htm](http://ftdichip.com/FTDrivers.htm)

The model of chip is FT232R.  The serial settings used are:  9600baud, no parity,8,1

Using VCP. I notice this driver is already pre-installed.

---

### Post by Zugzwang on 2008-09-30
> **Chondro_Biak said:**
> The manufacture is concerned that this might be taking a step backwards.

He told me his application was written in Visual Basic 6. Don't know if that helps at all?


In what sense would this be a step backwards? If you can get hold of a copy of the source code, then you might be able to replicate its behaviour (since it looks as if you can simply "talk" to some serial device).

---

### Post by Chondro_Biak on 2008-09-30
The manufacturer just doesn't want to loose anything from the windows version. 

It would be ideal if this program would just work under WINE.

I downloaded the software on a windows machine last night and played with it. I reviewed all of the files that are extracted off the CD and verified that they were all in place on my Ubuntu machine and some were missing, so I copied them over to their correct locations. (mainly system32 files)

When I install this and run it with WINE it does see the internet connection, however it does not see the COM ports. I think if that path could be made available to the program it would probably work as designed.

---

### Post by Zugzwang on 2008-09-30
> **Chondro_Biak said:**
> The manufacturer just doesn't want to loose anything from the windows version. 


What would the manufacturer lose from the windows version by given you information on the protocol? I don't get the point.

For Wine emulation, try to see where at which position in the /dev/ sub-system the USB device is mounted. Perhaps it works by plugging it in and then invoking "dmesg" from the command line. Then you might want to configure WINE in order to create a COM-mapping to there. 

I must admit that this is just an idea, it might or might not work.

---

### Post by Chondro_Biak on 2008-09-30
I hate sounding like an idiot, but I need to ask. 

"For Wine emulation, try to see where at which position in the /dev/ sub-system the USB device is mounted. Perhaps it works by plugging it in and then invoking "dmesg" from the command line. Then you might want to configure WINE in order to create a COM-mapping to there."

How do I do that? I am sure it is like 2 steps. But I am still learning the terminal.

---

### Post by Zugzwang on 2008-09-30
Ok, so step-by-step: 

[LIST]
[*]Start up a terminal (Applications->System tools->Konsole) here.
[*]Plug in your USB device
[*]type "dmesg" and hit enter. The last few line should ideally talk about some USB device plugged in. Copy&paste it here.
[/LIST]

---

### Post by Chondro_Biak on 2008-09-30
I am doing this remotely through a plink, so bear with me. lol

I am 90% sure I have it plugged it right now (I'm not at home). I also have a digital camera that is plugged in. 

Here is what I get:
[95626.012473] sd 10:0:0:0: [sdc] 2015232 512-byte hardware sectors (1032 MB)
[95626.013222] sd 10:0:0:0: [sdc] Write Protect is off
[95626.013225] sd 10:0:0:0: [sdc] Mode Sense: 03 00 00 00
[95626.013227] sd 10:0:0:0: [sdc] Assuming drive cache: write through
[95626.015845] sd 10:0:0:0: [sdc] 2015232 512-byte hardware sectors (1032 MB)
[95626.016468] sd 10:0:0:0: [sdc] Write Protect is off
[95626.016470] sd 10:0:0:0: [sdc] Mode Sense: 03 00 00 00
[95626.016472] sd 10:0:0:0: [sdc] Assuming drive cache: write through
[95626.016475]  sdc: unknown partition table
[95626.018754] sd 10:0:0:0: [sdc] Attached SCSI removable disk
[95626.018788] sd 10:0:0:0: Attached scsi generic sg3 type 0
[95635.471377] usb 2-2: USB disconnect, address 4
[99022.726505] usb 5-1: new full speed USB device using uhci_hcd and address 4
[99022.933331] usb 5-1: configuration #1 chosen from 1 choice
[99022.937697] ftdi_sio 5-1:1.0: FTDI USB Serial Device converter detected
[99022.937718] /build/buildd/linux-2.6.24/drivers/usb/serial/ftdi_sio.c: Detecte
d FT232RL
[99022.937794] usb 5-1: FTDI USB Serial Device converter now attached to ttyUSB0

[130821.529567] hub 5-0:1.0: port 1 disabled by hub (EMI?), re-enabling...
[130821.529573] usb 5-1: USB disconnect, address 4
[130821.529821] ftdi_sio ttyUSB0: FTDI USB Serial Device converter now disconnec
ted from ttyUSB0
[130821.529831] ftdi_sio 5-1:1.0: device disconnected
[130821.641417] usb 5-1: new full speed USB device using uhci_hcd and address 5
[130821.847733] usb 5-1: configuration #1 chosen from 1 choice
[130821.850667] ftdi_sio 5-1:1.0: FTDI USB Serial Device converter detected
[130821.850687] /build/buildd/linux-2.6.24/drivers/usb/serial/ftdi_sio.c: Detect
ed FT232RL
[130821.850749] usb 5-1: FTDI USB Serial Device converter now attached to ttyUSB
0
[142793.549362] console-kit-dae[20210]: segfault at 00000000 eip b7e57677 esp bf
ceaf54 error 4
&#8592;]0;shiloh@chondro: ~shiloh@chondro:~$

---

### Post by Kadrus on 2008-09-30
Sheesh!
Post between the code tags :p

---

### Post by Zugzwang on 2008-09-30
OP, please shorten the post #14 a little bit (the last 10-20 lines suffice). ;-) The important line seems to be this one:
```

[130821.850749] usb 5-1: FTDI USB Serial Device converter now attached to ttyUSB

```
If I interpret it correctly, then there should be some file (or virtual file) ttyUSB somewhere in your file system, possibly at /dev/ttyUSB. Verify this, please.

Then, read [here]("http://www.winehq.org/docs/en/wineusr-guide.html#AEN407") to get some information on how to add this as a COM-port to WINE. Don't have Wine installed here, so I can't help you on this little detail.

---

### Post by Chondro_Biak on 2008-09-30
I will need to do this from home I think. 

I will take a look when I get home, about 5 hours. 

I really appreciate the help. There is no way I could have got this going without your guys help.

I will check it out when I get home and post back.

---

### Post by Shiloh Hawkesworth on 2008-09-30
It's me Chondro_Biak

I have a different home account.

Under /dev I have one called ttyUSB0, which is what the above says, but the 0 got put on the line below.
I have verified that this is in fact the devise by unplugging all other USB devises.

When the program in question is running it refers to the ports as "comm", not sure if that is going to make a difference or not. I see in the link you posted it refers to the comm is com. Is that going to make a difference?

" Serial and parallel port configuration is very similar to drive configuration - simply create a symbolic link in ~/.wine/dosdevices with the name of the device. Windows serial ports follow a naming convention of the word "com" followed by a number, such as com1, com2, etc. Similarly, parallel ports use "lpt" followed by a number, such as lpt1. You should link these directly to the corresponding Unix devices, such as /dev/ttyS0 and /dev/lp0. For example, to configure one serial port and one parallel port, run the following commands:

          ln -s /dev/ttyS0 com1
          ln -s /dev/lp0 lpt1    "

I am not really understanding how this is done. How do I create a symbolic link?

---

### Post by asdfoo on 2008-09-30
> **Shiloh Hawkesworth said:**
> It's me Chondro_Biak

I have a different home account.

Under /dev I have one called ttyUSB0, which is what the above says, but the 0 got put on the line below.
I have verified that this is in fact the devise by unplugging all other USB devises.

When the program in question is running it refers to the ports as "comm", not sure if that is going to make a difference or not. I see in the link you posted it refers to the comm is com. Is that going to make a difference?

" Serial and parallel port configuration is very similar to drive configuration - simply create a symbolic link in ~/.wine/dosdevices with the name of the device. Windows serial ports follow a naming convention of the word "com" followed by a number, such as com1, com2, etc. Similarly, parallel ports use "lpt" followed by a number, such as lpt1. You should link these directly to the corresponding Unix devices, such as /dev/ttyS0 and /dev/lp0. For example, to configure one serial port and one parallel port, run the following commands:

          ln -s /dev/ttyS0 com1
          ln -s /dev/lp0 lpt1    "

I am not really understanding how this is done. How do I create a symbolic link?

The examples above create symbolic links.  Read the ln man page if you want to read how it works.

---

### Post by Shiloh Hawkesworth on 2008-09-30
OK. I created the symbolic link and the program runs the same.

What can I try next?

Perhaps running the file from the terminal? Would that help give a visual?

---

### Post by Shiloh Hawkesworth on 2008-09-30
When I run in the terminal this is what i get:

fixme:ole:OleLoadPictureEx (0xaaf064,77884,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32fae8), partially implemented.
fixme:ole:OleLoadPictureEx (0xaba69c,902,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f7a8), partially implemented.
fixme:ole:OLEPictureImpl_SaveAsFile (0x15d6d8)->(0x172f70, 0, (nil)), hacked stub.
fixme:comm:set_queue_size insize 1024 outsize 512 unimplemented stub
fixme:comm:set_queue_size insize 1024 outsize 512 unimplemented stub
err:comm:get_baud_rate tcgetattr error 'Input/output error'
err:comm:set_baud_rate tcgetattr error 'Input/output error'
fixme:comm:set_queue_size insize 1024 outsize 512 unimplemented stub
err:comm:get_baud_rate tcgetattr error 'Input/output error'
err:comm:set_baud_rate tcgetattr error 'Input/output error'
fixme:comm:set_queue_size insize 1024 outsize 512 unimplemented stub
err:comm:get_baud_rate tcgetattr error 'Input/output error'
err:comm:set_baud_rate tcgetattr error 'Input/output error'
fixme:comm:set_queue_size insize 1024 outsize 512 unimplemented stub
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:comm:set_queue_size insize 1024 outsize 512 unimplemented stub

---

### Post by skullmunky on 2008-09-30
If running it under Wine won't work, I'm still interested in whipping up something in Python to do the same thing.  I use the FTDI usb->serial chip all the time from linux for other microcontroller projects.  I think it'd be pretty easy ... of course I'd have to know exactly what the original program does, but if it basically just lets you set thresholds and then send alerts by email or SMS that really should be pretty easy.

The protocol will be a list.  having the source code for the original program is always the best case, but the communication protocol for the device is plenty of info to go on.

Regarding the manufacturer's questions, those are sort of legit because we're talking about porting their software, sort of.  If this was something they were going to distribute or support, that would be particularly important.  But here I think it's just important that the solution suit this particular user's needs.

---

### Post by Zugzwang on 2008-10-01
> **Shiloh Hawkesworth said:**
> OK. I created the symbolic link and the program runs the same.

What can I try next?

Perhaps running the file from the terminal? Would that help give a visual?

Did you create the symbolic links to /dev/ttyUSB0? ("ln -s /dev/ttyUSB0 com1")

The software will have some dialog box somewhere for choosing the port to be used. Change it to COM1.

---

### Post by Shiloh Hawkesworth on 2008-10-01
> **Zugzwang said:**
> Did you create the symbolic links to /dev/ttyUSB0? ("ln -s /dev/ttyUSB0 com1")

The software will have some dialog box somewhere for choosing the port to be used. Change it to COM1.

Yes I created the symbolic link. 

I also selected com1 as the port and still no change.

How easy will it be to proceed if the manufacturer does not give up the info we need?

---

### Post by Chondro_Biak on 2008-10-01
"I think it's just important that the solution suit this particular user's needs."
I agree...



[http://www.la-sorciere.de/Wine-HOWTO/configsystem.html](http://www.la-sorciere.de/Wine-HOWTO/configsystem.html)

under the:
Example 5-2. Common Sections in Wine configuration File 
section

How can I make sure my:
[serialports]
Com1=/dev/ttyS0

is actually Com1=/dev/ttyUSB0

?

What would the terminal line be to check that? 

When I type in "ln -s /dev/ttyUSB0 com1" I get:
&#8592;]0;shiloh@chondro: ~shiloh@chondro:~$ ln -s /dev/ttyUSB0 com1
ln: creating symbolic link `com1': File exists

[http://www.la-sorciere.de/Wine-HOWTO/ch-serial.html#SERIALPORT](http://www.la-sorciere.de/Wine-HOWTO/ch-serial.html#SERIALPORT)

In that section is states:
To access a serial port with Wine applications, the serial port must be set up in win.ini and Wine configuration file properly

Is setting up that symbolic link updating both the win.ini and Wine configuration file?

---

### Post by Zugzwang on 2008-10-01
> **Chondro_Biak said:**
> 
under the:
Example 5-2. Common Sections in Wine configuration File 
section

How can I make sure my:
[serialports]
Com1=/dev/ttyS0

is actually Com1=/dev/ttyUSB0
?

...by changing that configuration file using your favourite editor (for example, gedit)

> **Chondro_Biak said:**
> 
When I type in "ln -s /dev/ttyUSB0 com1" I get:
&#8592;]0;shiloh@chondro: ~shiloh@chondro:~$ ln -s /dev/ttyUSB0 com1
ln: creating symbolic link `com1': File exists

Then delete the old link beforehand: "rm com1"

> **Chondro_Biak said:**
> 
Is setting up that symbolic link updating both the win.ini and Wine configuration file?
No, it does neither. However, the HOWTO you refer to is from 2003, it might be outdated. I don't know.

---

### Post by Chondro_Biak on 2008-10-01
So to check the wineconf I will type in gedit wineconf ? on the terminal?


Wouldn't I want to type in:

ln -s /dev/usb/ttyUSB0 ~/.wine/dosdevices/com1

I was just thinking about the line. Because we are setting up a WINE symbolic link, shouldn't it be wrote like this?

---

### Post by Shiloh Hawkesworth on 2008-10-01
Any ideas on this line?

err:comm:set_baud_rate tcgetattr error 'Input/output error'

I am very open to any suggestions

---

### Post by Chondro_Biak on 2008-10-02
*bump*

---

### Post by pp. on 2008-10-02
Perhaps your queries would meet with more success if you posted them in the WINE forum.

---

### Post by Chondro_Biak on 2008-10-02
I have a link this this on the WINE page... :)

---

