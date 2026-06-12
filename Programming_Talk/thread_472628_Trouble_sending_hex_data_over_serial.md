---
title: "Trouble sending hex data over serial"
date: 2007-06-13
forum: Programming Talk
---

### Post by renzokuken on 2007-06-13
hi,

further to this thread (which i now understand) i am having trouble actually figuring out how to send the hex data, more specifically how to write it in the code.

firstly for a little background on the data, see the attachment for an excert of the manual.

now i need to send THAT data over the serial to my equipment.

the code reads

```

Sub Main

        RS232BaudRate(6)       [color=green] 'set baud rate to 9600[/color]    
	RS232DataBits(4)        [color=green]'set data bits to 8[/color]    
	RS232Parity(0)          [color=green]'set parity to none[/color]    
	RS232StopBits(0)        [color=green]'set stopbits to 1 (0=1 bit, 1=1.5 bits, 2=2 bits)[/color]    
	RS232Port(0)           [color=green] 'set port to comport 1[/color]    
	RS232Init              [color=green] 'open com port[/color]    
	[color=red]RS232Send("0x00, 0x01, 0x00, 0x00, 0x00, 0x00")[/color]            [color=green] 'send data (as hex ??!!??)[/color]    

End Sub


```

all the commands above are function/keywords built into the Shell i am using (based on Sax Basic) I know it works up to the RS232Init function because an led on my equipment flashes when data is received, even if its wrong data.

heres a little info on the RS232Send Function

**Sub RS232Send(SendStr As String)**
**Keyword : **   RS232Send
**Definition : ** Sends the string out to the defined serial port
**Parameters : ** SendStr (the string to be sent to the serial port)
**Return Value : ** None
**Example : ** Send a message :-
   RS232Parity(RS232_ComPort1)
   RS232Init
   RS232Send("hello world!"+VBCRLF)
**Syntax : ** RS232Send(<string>)


so how do i enter the hex code as a string? thanks..........

---

### Post by Stephen Howard on 2007-06-13
Early development might be easier if you use some terminal software instead of jumping straight to code  - try cutecom (in the repositories)

---

### Post by renzokuken on 2007-06-13
Hi Stephen (again >_<)

im in XP at the mo at work.

i have software in VB6, VB.NET and C that all work fine, i just cant figure out how to "format" the hex data in the ADL shell RS232Send command. do i use "s ...... 0x or &H in front of the bytes?......thats my only problem, figuring out how to write the 6 bytes i need to send

---

### Post by nerdzero on 2007-06-13
renzokuken,

This is a guess again, but I imagine the string you are sending is actually sending ASCII codes of the characters.  Each character is one byte (maybe 2 if Sax works in unicode).  If you want to send hex try this...

```
RS232Send( Chr(&H00) & Chr(&H01) & Chr(&H00) & Chr(&H00) & Chr(&H00) & Chr(&H00) )
```

The Chr function returns the ASCII character for the given number which in this case is represented in hex format (&H).  The & symbol by itself joins multiple strings together to form a single string (you can use the + character as well but & is "better" VB syntax).  For example, instead of

```
RS232Send( "TEST" )
```

you could probably send

```
RS232Send( Chr(&H54) & Chr(&H45) & Chr(&H53) & Chr(&H54)  )
```

or in decimal format instead of hex

```
RS232Send( Chr(84) & Chr(69) & Chr(83) & Chr(84)  )
```

and get the same result.

Make sense?  Check out asciitable.com if you don't know where I'm getting these numbers from.

---

### Post by renzokuken on 2007-06-13
thanks nerdzero.

i did actually try

RS232Send(Chr(00) + Chr(01) + Chr(00) ........etc)

obviously with no luck......but looks like i was just missing the **&H**

i'll have a go and see what happens back at work tomorrow.....

thanks guys.

---

### Post by nerdzero on 2007-06-13
Actually anything 0 through 9 is the same in decimal and hex so if Chr(00) didn't work, neither will Chr(&H00) :(

Can you connect a scope to your serial port to see what's coming out of it?  Also, do you need to send a stop bit or anything?

---

### Post by Stephen Howard on 2007-06-13
Can't help you with the RS232Send command, but the function specification looks straight forward and I'd have expected that building up a string using chr concatenation would have worked.

If you're not having any luck, then I recommend that you download a serial port monitor (there are plenty of public domain ones for windows - at least 10yrs ago there were!) and then use it to snoop the port while using "Zaber's demo software" referred to in the manual.

Are you setting up the port based on the specification for the device?  If not, and you're guessing, perhaps  also mess around with the settings and stretch the stop bits to 2 - the device might be a bit slow.

---

### Post by renzokuken on 2007-06-14
they specify in the manual

9600 baud rate (value = 6)
8 bata bits (value = 4)
no parity
no handshaking
1 stop bit

which is what i'm using.......

if i send

**RS232("hello world")** the orange LED flashes (which according to the manual signifies data transfer),

whereas if i send **RS232Send( Chr(&H00) & Chr(&H01) & Chr(&H00) & Chr(&H00) & Chr(&H00) & Chr(&H00) )** then i dont get a flash on the LED.

i dont understand why it would receive crap like "hello world" but not my actual hex string

should i put a pause between the RS232Init and the Send command?

EDIT: ok, so i initialised the device only, then ran a single line command from the shell to send a unit renumber command which resulted in an LED flash.........then i sent another manual command to move both units a certain distance, and although it didnt move, i finally got a flash on the LED, so it is definately receiving the commands (may have to implement a pause function to create a few second delay between the initialisation and the send command)

---

### Post by Stephen Howard on 2007-06-14
Pause shouldn't matter as the initialisation is happening at your end and should be immediate.  That said, it can't hurt.

I know it doesn't really make sense, but maybe the send command expects a CR/LF to mark the end of the string?  surely not, but that said, the example appends VBCRLF to the end of the "Hello world" example...  Presumably VBCRLF is a constant??

Is RS232Send a VB command?  I briefly browsed and couldn't find any likely references to it.

---

### Post by Stephen Howard on 2007-06-14
PS:  are there any other RS232xxxx commands?  Maybe there's one that sends bytes??

---

### Post by renzokuken on 2007-06-14
im not sure what VBCRLF is.

as for RS232Send, it is a command buit into the ADL shell (ADL shell is based on SAX Basic) so i guess its written in  some form of Basic probably using the **mscomm** library ( which by the way, is available in ADL so maybe that is the way to go) but i cant find the Source code for the command.

i got all the info on the RS232 commands from [www.chemistry.nmsu.edu/studntres/chem435/Manuals/Cary_100/Cary_100_ADL/](www.chemistry.nmsu.edu/studntres/chem435/Manuals/Cary_100/Cary_100_ADL/)

EDIT, appears the link isnt working at the mo

---

### Post by renzokuken on 2007-06-14
I DONE IT !!!!!!!!

its a cheat way of doing it i guess but heres how i did it

the stage came with some demo software, one of which is a CLI program written in C.

i dropped the exe into the system32 folder then just use ADL's sendkeys function to control the stage, not perfect i guess but it works......which is good enough for me

```

Sub Main 
    
        X = Shell("ZaberCDemoWin32") 'open and use zabers c demo to move stage
       
        Wait 3
	SendKeys "com1"
	Wait 1
	SendKeys "~"                 'press enter
	Wait 3
        SendKeys " "                 'press space
	Wait 1
	SendKeys "0"                 'unit number (0=all, 1=1, 2=2 etc)
	SendKeys "~"
	Wait 1
	SendKeys "1"                 'command number - see zaber manual for list
	SendKeys "~"
	Wait 1
	SendKeys "0"                 'data, in this case microsteps to move
	SendKeys "~"
	
	
End Sub
```

still gonna phone the company who wrote adl though and find out how to do it the way we were trying to (with RS232Send)

---

### Post by nerdzero on 2007-06-14
vbCrLf is a visual basic constant for Carriage Return and Line Feed characters concatenated together.  Are you running this shell inside XP?  Try changing your process priority in the Task Manager to Realtime if so.

---

### Post by nerdzero on 2007-06-14
Well if SendKeys will do what you need then congrats! :D

---

### Post by Stephen Howard on 2007-06-14
cool!

---

### Post by renzokuken on 2007-06-18
just a little update for you both

i managed to avoid the sendkeys. i figured out how to reference libraries and used the mscommlib to do the serial stuff from within ADL.

this is my code so far.....and hopefully problem solved

```

Dim OldHandShake As Integer
Dim OldSettings As String
Dim OldMode As Integer
Dim OldInputLen As Integer
Dim myCom As Object



Sub PortOpen
 
        
        Set myCom = CreateObject("MSCommLib.MSComm")
        
        With myCom
          
          .CommPort = 1
          .PortOpen = True
          'save current port settings
          OldHandShake = .Handshaking
          OldSettings = .Settings
          OldMode = .InputMode
          OldInputLen = .InputLen
          'set the new settings
          .Handshaking = comNone
          .Settings = "9600,N,8,1"
          .InputMode = comInputModeText
          .InputLen = 1
          .RThreshold = 1
          lprint("Opening com port......")
          Wait 1
          lprint("Done.")
          lprint("Renumbering units......")
          .Output = Chr$(0) + Chr$(2) + Chr$(0) + Chr$(0) + Chr$(0) + Chr$(0)   ' renumber all units
          lprint("Done.")
        End With
     
End Sub

Sub Home
         With myCom
         .Output = Chr$(0) + Chr$(1) + Chr$(0) + Chr$(0) + Chr$(0) + Chr$(0)
         End With
End Sub

Sub OneOne

        With myCom
        .Output = Chr$(2) + Chr$(20) + Chr$(137) + Chr$(78) + Chr$(2) + Chr$(0)
        End With
        
End Sub

Sub PortClose
        With myCom
        .PortOpen = False
        End With
End Sub

Sub Main
	PortOpen
	Wait 3
	Home
	Wait 7
	OneOne
	Wait 7
	PortClose

End Sub

```

---

