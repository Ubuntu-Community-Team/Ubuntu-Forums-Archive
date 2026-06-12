---
title: "Problem to communicate with serial port"
date: 2021-02-08
forum: Programming Talk
---

### Post by tekaya05 on 2021-02-08
[COLOR=#cc7832]I am using ST32 connected to the computer with USB cable. this micro-controller is already programmed and should give me two values 
(it has worked on windows 10 I just replaced [COLOR=#6a8759]'/dev/ttyS1' with [COLOR=#6a8759]'COM1')[/COLOR][/COLOR].
the problem is that when i compile my program it doesn't show any Errors. I don't even know if I am communicating with the right port or not.

DO you have an Idea what can i do to solve this problem?  
 


import [/COLOR]serial
[COLOR=#cc7832]import [/COLOR]re
serport = [COLOR=#6a8759]'/dev/ttyS1'
[/COLOR]serbaudrate = [COLOR=#6897bb]9600
[/COLOR]ser = serial.Serial([COLOR=#aa4926]port [/COLOR]= serport[COLOR=#cc7832], [/COLOR][COLOR=#aa4926]baudrate [/COLOR]= serbaudrate[COLOR=#cc7832], [/COLOR][COLOR=#aa4926]bytesize[/COLOR]=serial.EIGHTBITS[COLOR=#cc7832], [/COLOR][COLOR=#aa4926]parity[/COLOR]=serial.PARITY_NONE[COLOR=#cc7832], [/COLOR][COLOR=#aa4926]timeout[/COLOR]=[COLOR=#6897bb]2[/COLOR])
[COLOR=#cc7832]try[/COLOR]:
    ser.isOpen()
[COLOR=#cc7832]except[/COLOR]:
    [COLOR=#8888c6]print[/COLOR]([COLOR=#6a8759]"Error"[/COLOR])
    [COLOR=#8888c6]exit[/COLOR]()

[COLOR=#cc7832]if [/COLOR]ser.isOpen():
    [COLOR=#cc7832]try[/COLOR]:
        [COLOR=#cc7832]while [/COLOR][COLOR=#6897bb]1[/COLOR]:
            [COLOR=#cc7832]if [/COLOR]ser.inWaiting() > [COLOR=#6897bb]0[/COLOR]:
                response = ser.readline()
                needles = re.match([COLOR=#6a8759]"(\d+);(\d+)"[/COLOR][COLOR=#cc7832], [/COLOR]response.decode([COLOR=#6a8759]"utf-8"[/COLOR]))
                [COLOR=#cc7832]if [/COLOR]needles:
                    [COLOR=#8888c6]print[/COLOR]([COLOR=#6a8759]"Got: {} {}"[/COLOR].format(needles[[COLOR=#6897bb]1[/COLOR]][COLOR=#cc7832], [/COLOR]needles[[COLOR=#6897bb]2[/COLOR]]))
                    [COLOR=#808080]#print("Got: {}".format(needles[2]))
[/COLOR][COLOR=#cc7832]else[/COLOR]:
                ser.write([COLOR=#a5c261]b"1"[/COLOR])
    [COLOR=#cc7832]except [/COLOR][COLOR=#8888c6]Exception [/COLOR][COLOR=#cc7832]as [/COLOR]e:
        [COLOR=#8888c6]print[/COLOR](e)

---

### Post by spjackson on 2021-02-08
Welcome to the forums.

I haven't done serial comms in Python, but I suspect you don't have read/write permission to the device. Typically, you would need to be in the group dialout. You could test for that:
```

ls -l /dev/ttyS*
id
cat /dev/null > /dev/ttyS1
cat /dev/ttyS1 > /dev/null

```
If you get "permission denied", then that will need dealing with.

You don't have the initializer inside a try/except scope.
```

try:
  ser.isOpen

```
looks a bit weird. This call isn't likely to raise an exception.

I read that isOpen is deprecated in favour of is_open.

---

### Post by norobro on 2021-02-08
Are you sure the device is on ttyS1?```
$ sudo dmesg | grep ttyS
[    0.970737] 00:03: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A
```

---

### Post by spjackson on 2021-02-08
[Posted in error.]

---

