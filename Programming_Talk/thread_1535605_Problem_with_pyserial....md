---
title: "Problem with pyserial..."
date: 2010-07-21
forum: Programming Talk
---

### Post by modmadmike on 2010-07-21
I wrote a program that pareses the serial input (to which a RFID reader is attached) for a string and executes a command upon finding the string; however, if the string is entered twice it runs the command twice even though there is a timeout. 

Here is the main program:
[PHP]#!/usr/bin/python
#############################################################
## Serial RFID authenticator by Mike Walker aka modmadmike ##
#############################################################
import time, serial, os

# Begin serial setup
ser = serial.Serial()
ser.baudrate = 2400
ser.port = '/dev/ttyS0'
# End serial setup


while True:
   ser.open()
   if len(ser.readline()) >= 10:
      code=str(ser.read(10)) #10 byte code
      if code == 'CODE-A' or code == 'CODE-B':
         print 'Code '+code+' is valid'
         os.system('sh /home/modmadmike/radr.sh') # Runs a script that types my password
         ser.flushInput() # !!!!!!!!!!!!THIS IS SUPPOSED TO CLEAR THE ENTIRE SERIAL BUFFER, BUT IT NEVER DOES!!!!!!!!
         code=''
         time.sleep(6) # Wait a few seconds for next authentication
      else:
         print 'Code '+code+' is invalid'
         ser.flushInput()
         ser.close()
         code=''[/PHP]

[This RFID reader]("http://www.parallax.com/tabid/768/ProductID/114/Default.aspx") attached like [so]("http://forums.parallax.com/forums/attach.aspx?a=12828") is what is connected to the serial port to send the codes. (They are only $10 at radioshack right now lol)

---

### Post by modmadmike on 2010-07-28
Sucks that nobody seems helpful!!!! I made a TEMPORARY fix by not daemonizing it (getting rid of the while loop) and adding a keyboard shortcut that runs the script. However, now I am unable to use the (single use) script if I'm not logged in because Ubuntu's keyboard shortcuts are only effective in an active gnome login (I can't even use it on the unlock screen :().

---

### Post by Can+~ on 2010-07-29
I haven't used the pyserial library, nor I have experience on this subject, but let's see anyway.

I would think that the buffer does get flushed, but it's still storing while on hold, and the next iteration grabs that. I guess an RFID reader isn't so clean, as it would try multiple times to get an accurate reading.

I would have it sleep a longer time after a successful input is found, flush it, and then listen again.

Also, you're opening the port on each iteration of the while loop, that may carry some consequences (or none).

---

