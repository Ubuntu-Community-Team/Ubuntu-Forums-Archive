---
title: "I need help with my USB to Serial Adapter"
date: 2006-03-03
forum: Programming Talk
---

### Post by rustyfx on 2006-03-03
Hello,

I have a robot that is controlled by a serial port.  The robot is working fine, but I need to move over to Linux so that I can have a real compute platform for controlling the robot.  (Cygwin on a PC was my previous platform.)

So, I puchased a notebook and a USB to serial adapter.  I have ubuntu linux installed.  Everything is working just fine (going through the /dev/ttyUSB0 interface) EXCEPT that my code doesn't receive the serial data from the robot.  The robot gets the data written by the code running on the linux machine, and it performs the requested commands, then it returns status.  However, somewhere between the USB to serial adapter and my code, the status byte doesn't get into my code.  Instead, my code just hangs on the read command to /dev/ttyUSB0.

I'm thinking that there must be a buffer somewhere in the usb to serial adapter - that it wants to be full before it sends a USB packet to the host system.  I'm hoping that I can change the behavior to send as soon as it gets anything (if my theory is anywhere close to correct).

Can anyone point me in a direction that could help me out?? - I'm feeling pretty stuck right now.  For example, I've been searching for the source code for the USB to serial driver - I can't find that on my machine.  A previous post said something about .../drivers/usb.  However, I don't see any source code in any directory matching that description.

Any information would be very much appreciated!!!

Thanks,
Robert

---

### Post by rustyfx on 2006-03-03
OK - here's one update.

In an effort to understand this further, I have my PC's serial port connected to the linux box through the USB to Serial adapter.

On the linux side, I enter the command:

cat /dev/ttyUSB0

Then, on the PC side, I send characters down the serial port using a terminal program.  After I type the cat command (and before I Cntl-C out of the command), the PC has the serial data echoed back.  Nothing is echoed back to the PC after I kill the cat command.

I can also:

cat a_text_file.txt > /dev/ttyUSB0 

on the linux side.  When I do this, the file contents show up on the PC side.

Can someone explain why "cat /dev/ttyUSB0" doesn't send received data to stdout - but instead back down /dev/ttyUSB0?????

I have yet to be able to have characters typed on the PC side to show up in a terminal or a program - but since the characters are echoed back to the PC, I have to assume that the linux driver is receiving that data.

Any thoughts are welcome.

Thanks,
Robert

---

### Post by toojays on 2006-03-03
The cat command is not bidirectional, so it makes sense that if wont show you what's being received when you send something.

If your serial data is text, you should install a terminal program (e.g. minicom) on your GNU box. If your serial data is binary (i.e. it uses non-printable text codes like \x000 \x001 etc), your best bet is to write a few functions in a scripting language, and use the languages REPL as your "terminal". I've used Python with the pyserial (python-serial in Synaptic IIRC) module for this in the past.

---

### Post by rustyfx on 2006-03-03
Thanks for your reply!

I expected that "cat /dev/ttyUSB0" would have taken data sent to the gnu box to be printed onto stdout.  However, it appears that something different happened instead - When I send a byte of data from my PC to the gnu box - the character is received - and then sent back to the PC.

PC   ---->  byte sent over serial   ---->   Gnu (executing cat command)

PC   <----  same byte returned    <----   Gnu

So, anything I type on the PC terminal is echoed back to the PC.  When I kill the cat command on the gnu side, the PC stops getting characters echoed back.

This echoing is the only evidence that I have that the gnu box is receiving the data at all.  I can't get the data through a read command in my code - and I can't get it to print to stdout with a cat command.

I'll install minicom and see what happens.

Thanks for the pointer to minicom.

Regards,
Robert

---

### Post by toojays on 2006-03-03
Yeah, I don't know why you get that behaviour with the echo.

---

### Post by rustyfx on 2006-03-04
Well, I've played around today, and I did find some new things out.

When I "cat /dev/ttyUSB0" on the linux box, and then I transmit characters to the linux box (with a terminal emulator on my PC) - nothing shows up UNTIL I hit return on the PC side.  What is very STRANGE is that the charaters are echoed back to the PC instantly.  But, data shows up on the stdout only when I send a return character.  Yuck!

OK - so, I changed the firmware in the robot to send a carriage return after each status byte.  I have software that I've written that controls the robot (this is running on the linux box) and it now receives the status byte - along with this extra carriage return.  Fine - I changed my software on the linux side to discard these carriage returns.

This is all fine - except: when the robot transmits a status byte - this byte is ECHOED BACK to the robot, even when I'm just running my software on the linux box (no cat command) - and I can tell you that my software is not echoing anything.  This echo has to be coming from the linux driver for the USB to Serial adapter.  This caused problems BECAUSE some of the possible status bytes can be actual commands to make the robot do things.  Thus - the robot was getting very confused, and the linux side and the robot side quickly lost synchronization.

So - I modified my status and command fields so that they could not overlap.  Double yuck.  And, the robot has been modified to discard any commands or data that looks like status.  But, with all of those changes, I now have a working linux/robot combo.

I cannot locate the source code for the Linux USB to Serial driver - can someone please tell me where this is????  I'm using Breezy - 5.10.

Thanks!!!
Robert

---

### Post by toojays on 2006-03-04
Really, using cat to send commands to your robot is not the right thing to do. Whatever weird behaviour the port is doing might be because it's not getting initialised properly. You're much better off using configuring minicom to do what you want, or using your own driver program which can set the proper serial port attributes.

Anyway, if you want to look at the driver to see what's going on, it's in the kernel source under drivers/usb/serial/. Different chips have different drivers; you'll need to find out what drivers you are using (by looking at the output of dmesg or lsmod) and take it from there.

---

