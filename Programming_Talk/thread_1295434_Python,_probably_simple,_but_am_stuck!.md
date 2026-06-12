---
title: "Python, probably simple, but am stuck!"
date: 2009-10-19
forum: Programming Talk
---

### Post by dchurch24 on 2009-10-19
Hi all, I have a small piece of Python code that executes commands. For the most part it works fine, but no matter what I do I cannot make it execute a certain string:


echo -e "\xFF\x00\x00" > /dev/ttyUSB0

I've tried escaping everything that needs it, but I eventually came to the conclusion that I'd need to find another way, so I wrapped those commands up in shell scripts and passed that to the code. It didn't execute those commands either.

So, in desperation, I have simply said "if the command is this, then run this script"


```

 def run_command(self,cmd):
      if cmd=="plug_3_off":
        os.system("/home/dave/Automation/./plug_3_off.sh")
      if cmd=="plug_3_on":
        os.system("/home/dave/Automation/./plug_3_on.sh")
      else:
        os.system(cmd)

```

..however, for some reason the "if" statements are ignored and the os.system(cmd) is triggered and the error is "plug_3_off" not found.

So, seemingly the string compare is not working - can strings be compared this way in Python or is there a specific method?

---

### Post by Bachstelze on 2009-10-19
Normally, it should work. Can you tell us exactly how you run the script?

---

### Post by dchurch24 on 2009-10-19
Yep.

I have the following code in VB.Net:

(IPAddress, Port and Switch (the command being sent) are set when the class is instanced)

```


Public Sub Toggle()
        Dim tcpClient As New System.Net.Sockets.TcpClient()
        tcpClient.Connect(IPAddress, Port)
        Dim networkStream As NetworkStream = tcpClient.GetStream()
        If networkStream.CanWrite And networkStream.CanRead Then
            ' Do a simple write.
            Dim sendBytes As [Byte]() = Encoding.ASCII.GetBytes(Switch)
            networkStream.Write(sendBytes, 0, sendBytes.Length)
            ' Read the NetworkStream into a byte buffer.
            Dim bytes(tcpClient.ReceiveBufferSize) As Byte
            networkStream.Read(bytes, 0, CInt(tcpClient.ReceiveBufferSize))
            ' Output the data received from the host to the console.
            Dim returndata As String = Encoding.ASCII.GetString(bytes)
            'Console.WriteLine(("Host returned: " + returndata))
        Else
            If Not networkStream.CanRead Then
                Console.WriteLine("cannot not write data to this stream")
                tcpClient.Close()
            Else
                If Not networkStream.CanWrite Then
                    Console.WriteLine("cannot read data from this stream")
                    tcpClient.Close()
                End If
            End If
        End If
        ' pause so user can view the console output
        Console.ReadLine()
    End Sub


```

The Switch could be something like "./adu sk0" to switch the ADU unit I have plugged in. This works fine.

The echo -e "\xFF\x00\x00" > /dev/ttyUSB0 is for a USB relay that is plugged into another USB port. If I run the above command at the terminal, it works and the relay switch is activated. The same is true if I run the .sh script with that command in it.

If I use the VB code, it doesn't work, yet the code is triggered as after this step is complete is sends another command "mythosd" which tells all my myth clients that a switch has been triggered (it tells me if the kids get out of bed and turn their lights on for instance).  I have a try{}catch on the call for this class and there is no error, it sends the bytes, gets a callback and as far as the VB is concerned it has executed it's code fine and without errors.

The error must be in the Python listener.

The entire code is as such:

```

import SocketServer
import commands
import os

class EchoRequestHandler(SocketServer.BaseRequestHandler ):
    def setup(self):
        print self.client_address, 'connected!'
        self.request.send('hi ' + str(self.client_address) + '\n')

    def run_command(self,cmd):
      if cmd=="plug_3_off":
        os.system("/home/dave/Automation/./plug_3_off.sh")
      if cmd=="plug_3_on":
        os.system("/home/dave/Automation/./plug_3_on.sh")
      else:
        os.system(cmd)

    def handle(self):
        data = 'dummy'
        while data:
            data = self.request.recv(1024)
            self.request.send(data)
            if data.strip() == 'bye':
                return
            self.run_command(data.strip())

    def finish(self):
        print self.client_address, 'disconnected!'
        self.request.send('bye ' + str(self.client_address) + '\n')

    #server host is a tuple ('host', port)
server = SocketServer.ThreadingTCPServer(('', 50002), EchoRequestHandler)
server.serve_forever()


```

The script is simply the 'echo' command above, and as I say, runs fine if I start it with ./plug_3_on.sh - permissions are set correctly etc... so I'm not sure why this script isn't kicking it off.

Currently, I'm rewriting the VB code in C#(mono with SDL) so I can clear XP off that machine, although I had trouble getting the touchscreen drivers working last time I tried, hence I gave up and installed windows on it and wrote the client in VB.

---

### Post by Bachstelze on 2009-10-19
Maybe data is not what you expect. Add a print statement to your run_command() method:

```

    def run_command(self,cmd):
      print cmd
      if cmd=="plug_3_off":
        os.system("/home/dave/Automation/./plug_3_off.sh")
      if cmd=="plug_3_on":
        os.system("/home/dave/Automation/./plug_3_on.sh")
      else:
        os.system(cmd)

```

and see what gets written in your terminal.

---

### Post by dchurch24 on 2009-10-19
Hmmm.

Thanks, have done so.

The output is simply:

plug_3_on

...which is what I would expect.

Following that, I get:

sh: plug_3_on: not found

which implies that the string compare is failing, and it's falling through to the else: and trying to execute the command that it's received, in this case "plug_3_on".

If I actually send "plug_3_on.sh" then it seems to execute it, but the script doesn't fire. I even put "echo "working"" in the script, and that gets output to the screen, just the echo -e "\xFF\x00\x00" > /dev/ttyUSB0 doesn't do anything. Like I say, if I run the script at the terminal, the relay triggers so that line is working. If I simply type that line into the terminal, that too triggers the relay.

It's baffling!

The permissions on the scripts are set as such:

```

-rwxrwxrwx 1 root root   37 2009-10-19 19:12 plug_3_off.sh
-rwxrwxrwx 1 root root   37 2009-10-19 19:12 plug_3_on.sh

```

I have also run the listener .py as sudo but it makes no odds.

---

### Post by ve4cib on 2009-10-19
Is it possible that cmd has extra whitespace (trailing newlines, spaces, etc...)?  You might try replacing it with "cmd.strip()" in your if-statement and see if that helps.

---

### Post by Bachstelze on 2009-10-19
> **ve4cib said:**
> Is it possible that cmd has extra whitespace (trailing newlines, spaces, etc...)?  You might try replacing it with "cmd.strip()" in your if-statement and see if that helps.

It is already strip()'ed in the handle() method.

---

### Post by dchurch24 on 2009-10-19
Ha - I think we must have had the same thought at the same time.

I just added the .strip(), but alas, it's the same story.

It's also Trim() ed from the vb code as well.

EDIT: I thought it couldn't hurt.

---

### Post by dchurch24 on 2009-10-19
This is truly baffling me (these are the bugs I don't like - no errors, just not working ;-) )

What makes it more annoying is that I had this working, then this being the only bloody machine in the house not backed up ('tis now! - and all code is in my SVN as well; I've learned that lesson) it's HDD went last week. I had copied the scripts to another machine, but this was before the new relay was added. I remember having this trouble the last time I wrote it.

Is there another way to compare strings, such as  

String.Compare([string1],[string2])

---

### Post by dchurch24 on 2009-10-19
Ahhh - I need elif, no another if.

It seems as if the if statements were nested and were acting like a Switch(or select case).

However, now I don't get the "plug_3_off" not found error, but the relay is not switching. The script is executing as I put "echo "plug off"" etc... afer the relay switch line.

---

### Post by dchurch24 on 2009-10-19
Oh man, do I feel stupid. :P

After all that, I'd forgotten to put


#!/bin/bash

at the top of the scripts. Now the relay switches every time.

Thanks so much for you time guys, it's really appreciated!

---

### Post by benj1 on 2009-10-19
can you not do
```
open("/dev/ttyUSB0","w").write("\xFF\x00\x00")
```
instead of your os.system() calls ?

---

### Post by Can+~ on 2009-10-19
> **benj1 said:**
> can you not do
```
open("/dev/ttyUSB0","w").write("\xFF\x00\x00")
```
instead of your os.system() calls ?

I was thinking the exact same thing. In *nix, everything is a file, although I've never tried writing directly to a device on python (but I had in C).

---

### Post by benj1 on 2009-10-19
> **Can+~ said:**
> I was thinking the exact same thing. In *nix, everything is a file, although I've never tried writing directly to a device on python (but I had in C).

neither have i but the op is trying to run a shell script with

echo "\xFF\x00\x00" > /dev/ttyUSB0

in it, which is basically the same thing.

i suppose you could get fancy and do

```
print >>open("/dev/ttyUSB0","w"), "\xFF\x00\x00"
```
which is a closer analogue to the echo statement but a bit less readable

---

### Post by jpkotta on 2009-10-19
[http://pyserial.sourceforge.net/](http://pyserial.sourceforge.net/)
```
apt-get install python-serial
```

---

### Post by A_Fiachra on 2009-10-19
> **Bachstelze said:**
> Maybe data is not what you expect. Add a print statement to your run_command() method:

```

    def run_command(self,cmd):
      print cmd
      if cmd=="plug_3_off":
        os.system("/home/dave/Automation/./plug_3_off.sh")
      if cmd=="plug_3_on":
        os.system("/home/dave/Automation/./plug_3_on.sh")
      else:
        os.system(cmd)

```and see what gets written in your terminal.


I would try ...

```

    def run_command(self,cmd):
      print cmd
      if ( cmd=="plug_3_off" ) :
        return_value = os.system("/bin/sh /home/dave/Automation/plug_3_off.sh")
        print >>sys.stderr, "Got return value: %d" % ( return_value )
      if cmd=="plug_3_on":
         return_value = os.system("/bin/sh /home/dave/Automation/plug_3_on.sh")
        print >>sys.stderr, "Got return value: %d" % ( return_value )
       else:
        ## DO NOT RUN AN UNKNOWN COMMAND EVER!!!!!!!!!!!!
        return -1

```

---

### Post by dchurch24 on 2009-10-21
Wow!

I'm about to re-write the whole 'package' if you like - I have finally got my touchscreen working with CrunchBang, so I can retire the Windows box, and rewrite that, and with it, I will try to write directly to the device as you suggest.

That's much more elegant than shelling scripts all over the place.

Thanks all.

---

