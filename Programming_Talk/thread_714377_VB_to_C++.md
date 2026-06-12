---
title: "VB to C++"
date: 2008-03-03
forum: Programming Talk
---

### Post by dilbert92 on 2008-03-03
Hey all!

I need to write a program that sends data out the serial port.
BUT it needs to be in HEX form, so 'echo "Data" > /dev/ttyUSB0 is not an option.
I have VB script that will do what I want it to do. So I just need to convert this:

```

' Form load code
Private Sub Form_Load()
MSComm1.Settings = "9600,N,8,1" ' The TX-4-PC operates at 9600 baud
MSComm1.CommPort = 1             ' Change to the available comm port on your PC
MSComm1.PortOpen = True         ' Opens comm port
End Sub
' Used for the "pause"
Public Sub Pause(milli As Long)
Sleep (milli)
End Sub
                             TX-4-PC Serial RF Transmitter Interface
' Button 1 code. Sends synch byte of 170, a receiver address of "0", then turns OFF all outputs on
receiver.
Private Sub Command1_Click()
For I = 1 To 4 ' Loop 4 times
   MSComm1.Output = Chr$(170) & Chr$(0) & Chr$(0)
   Pause 250 ' Pause 250mS
Next I
End Sub
' Button 16 code. Sends synch byte of 170, a receiver address of "0", then turns ON output all outputs
on receiver.
Private Sub Command16_Click()
For I = 1 To 4 ' Loop 4 times
   MSComm1.Output = Chr$(170) & Chr$(0) & Chr$(15)
   Pause 250 ' Pause 250mS
Next I
End Sub

```

To C++, or any other language for that matter.


Any help would be greatly appreciated!

Thanks!

---

### Post by nanotube on 2008-03-03
python?
[http://pyserial.sourceforge.net/](http://pyserial.sourceforge.net/)

---

### Post by dilbert92 on 2008-03-04
Thanks for replying.

I got it, and I can send data i.e 
 ser.write("hello") 
to an Arduino with a LCD display. But how do I send "sync byte of 170"?? :confused:

Any help would be great! 
Thanks again!

---

### Post by nanotube on 2008-03-04
> **dilbert92 said:**
> Thanks for replying.

I got it, and I can send data i.e 
 ser.write("hello") 
to an Arduino with a LCD display. But how do I send "sync byte of 170"?? :confused:

Any help would be great! 
Thanks again!

well... if you tell me what exactly a "sync byte of 170" is, maybe i can help. what exactly does the thing expect? just a hex value 0x170? depending on what it needs and in what format, maybe the struct library may be of use: [http://docs.python.org/lib/module-struct.html](http://docs.python.org/lib/module-struct.html)

---

### Post by dilbert92 on 2008-03-05
I'm not really sure what a "sync byte of 170" is. :confused:
That's what I'm trying to figure out.
It's a Rentron TX-4-PC.
The website is: [http://www.rentron.com/remote_control/TX-4-PC.htm]("http://www.rentron.com/remote_control/TX-4-PC.htm")

I couldn't  attached the manual, It was too big. However, the HTML version  can be found here: [http://www.rentron.com/PC-Remote1.htm]("http://www.rentron.com/PC-Remote1.htm")

I have not got a chance to look a the link, but I will have a look at that the first chance I get!

Thanks again!

---

### Post by nanotube on 2008-03-05
aha, ok, from the manual:
The synchronization byte 170 consists of an even number of 1s' & 0s', or 10101010 in binary, and is is used to synchronize the transmitter with the PC serial port. 

because, 
```
>>> int('10101010', 2)
170

```
that alternating pattern of 1s and 0s translates to 170 in decimal. so all you need to do is write 
```
chr(170)
```
to the port to output that "synchronization byte 170".

or, if plain chr(170) doesn't work (think it should, though), maybe the following will: 
```
struct.pack('c',chr(170))
```

give that a try, see what happens. :)

---

