---
title: "Help with python file transfer"
date: 2011-10-14
forum: Programming Talk
---

### Post by mushy365 on 2011-10-14
I have made a server and client to send files across my network, as im trying to learn python and sockets. It works fine and the server send the file and the client saves the file, the problem  is that the client stays in the recv loop even after the file is finished sending, ive tried lots of ways to get the client to realise that the download is finished and to break out of the loop but it does not work. 

The problem is with the recvfile function in cli.py can anyone help me get it to reconise the file has stopped sending

[B]filerec.py
[/B]```

#!/usr/bin/python
import os, glob, shutil
import sys
import socket
import time
import string
import ConfigParser

#functions
def sendfile(socket,path,name):
    confirm = socket.recv(1024)
    if(confirm == "_BEGIN_"):
      fullfile = path + name
      print "[Notice] sending file " + fullfile
      if os.path.exists(fullfile):
         #file exists we can transfer it.
         #open file in rb
         #loop through and send to socket
         f = file(fullfile,'rb')
         while 1:
            data = f.read(1024)
            if len(data) <= 0:
               break
            socket.send(data)
         socket.send(data)
         f.close()
         print "[Notice] finished sending file " + fullfile

    else:
      print "No confirmation recieved"

def list_files(path):
   os.chdir(path)
   ffiles = glob.glob("*.*")  
   return ffiles; 


def usage():
   print "usage: filerec.py [portnumber][base address to read from]"

#usage: filerec.py [portnumber][base address to read from]
#check argv 

if(len(sys.argv) > 2):
   #we have at least 3 args we can contunue
   port = int(sys.argv[1])
   path = sys.argv[2]
   
   if os.path.isdir(path):
      #path is valid
      print "Server listening - Serving files from " + path
      # now lets create a socket
      sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
      sock.bind(('', port))
      sock.listen(5)

      #loop to accept connections.
      
      while True:
         sdata = ""
         newSock, address = sock.accept()
         print "**Connection from ", address
         rcvdata = newSock.recv(1024)
         commands = rcvdata.split(' ')
         if(commands[0] == 'list'):
             print "[Request] List files ", address
             fil = list_files(path)
             for f in fil:
                sdata = sdata + f + "\n" 
             newSock.send(sdata)
         
         elif(commands[0] == 'get'):
             #remove first word
             filenam = " ".join(commands[1:])
             print "**Requested download of " + filenam
             if(os.path.exists(path + filenam)):
                newSock.send("_YESFILE_")
                sendfile(newSock,path,filenam)
                
             else:
                print "File does not exist" + path + filenam
                newSock.send("_NOFILE_")
         elif(commands[0] == 'quit'):
             newSock.close()
             sock.close()
             print "**Remote host terminated connection"
             break;
         
         else:
            print "**Invalid command " + rcvdata
            newSock.send("**Invalid command")

   else:
      print "Invalid path " + path
      exit()
        


else:
   usage()

```

[B]cli.py
[/B]```

#!/usr/bin/python
import os, glob, shutil
import sys
import socket
import time
import string
import ConfigParser

#usage cli.py localhost 9000
def recvfile(s, filename):
    
    #remove get
    cmds = filename.split(" ")
    fname = " ".join(cmds[1:])
    
    #create the file
    FILE = open(fname, "w+")
    FILE.close()
    s.send("_BEGIN_")
    print "Downloading file: " + fname
    rf = open(fname,'wb')
    while True:
       data = s.recv(1024)
       if(len(data)<= 0):
         break
       rf.write(data)
    rf.close()
    print "Finished Dowloading file:  " + fname

if(len(sys.argv) > 2):
   host = sys.argv[1]
   port = int(sys.argv[2])

   s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
   s.connect((host, port))
   
   while True:
      snd = raw_input("> ")
      cmds = snd.split(" ")
      if(cmds[0] == 'get'):
        #file dowload
       
        s.send(snd)
        data = s.recv(1024)
        if(data == '_NOFILE_'):
          print "File not found"
        elif (data == '_YESFILE_'):
          print "file found"
          recvfile(s, snd)

      else:  
        s.send(snd)
        data = s.recv(1024)
        print data
        #print "msg length: " + str(len(data))
        s.close()
        break

```

---

### Post by heyandy889 on 2011-10-14
Hey, man. Found a possible solution to your problem.

[http://docs.python.org/library/socket.html](http://docs.python.org/library/socket.html)
under socket.recv, says "The return value is a string representing the data received." So, may I suggest replacing

```

if(len(data)<= 0):
         break

```

with this

```

if(data==""):
         break

```


Also, "break" might not be working the way you want. Maybe change the loop structure from 

```

while True:
       data = s.recv(1024)
       if(len(data)<= 0):
         break
       rf.write(data)

```

to this

```

data="Let's start here!"
while data != "": #or however you do "not equals" in Python
       rf.write(data)
       data = s.recv(1024)

```

Then, you're using the While loop as it was intended by its creators. Shouldn't affect functionality, but it's easier to read and you can debug easier.

Good luck, pal!

---

### Post by mushy365 on 2011-10-14
Hey thanks for the tips. Even tho i got it working before i saw your reply with replacing
if(len(data)<= 0):
         break
with 
if(len(data)<= 1024):
         breakwhich is the length of data im trying to recieve, im still gonna try your idea. 

because sometimes after i dowload a file, when i go to download another i get an error because in the handshake before its sending over jibberish almost like something that was chched in the socket and it causes my program to error.

---

### Post by mushy365 on 2011-10-14
doing it this way gives an error
[B]UnboundLocalError: local variable 'data' referenced before assignment
[/B]
> data = "starting"
    while data != "":
       data = s.recv(1024)

---

### Post by mushy365 on 2011-10-14
ive been working with this for hours, and still cant get it to work perfectly, most files it runs fine.  some files it doesnt transfer all the files, after transfering one file, when i go to transfer another sometimes it errors on the

infoval = int(fsizeinfo[1]) bit, because it reads it as some kind of base 10 x blah blah blah. 

im wondering if there is some excess data in the socket after a file transfer that somehow messes this conversion up. 

i tried the changes suggested above, but they caused more problems so i had to revert back to what i had  - this is my most up to date version. Could someone use it to do a file transfer on thier system and help me work out some of the bugs. 

```
#!/usr/bin/python
import os, glob, shutil
import sys
import socket
import time
import string
import ConfigParser

#usage cli.py localhost 9000
def pct(num1,num2):
    return (float(num1)/num2)*100

def recvfile(s, filename):
    
    #remove get
    cmds = filename.split(" ")
    fname = " ".join(cmds[1:])
    
    #create the file
    FILE = open(fname, "w+")
    FILE.close()
    s.send("_BEGIN_")
    fsize = ""
    fsize = s.recv(1024)
    fsizeinfo = fsize.split('=')
    infotype = fsizeinfo[0]
    
    
    if(infotype == "_F_SIZ_"):
       infoval = int(fsizeinfo[1])
 
    print "Downloading file: " + fname + " [size " + str(infoval) + "]"
    rf = open(fname,'wb')
    transtotal = 0
    
    while True:
       data = s.recv(1024)
       transtotal = transtotal + len(data)
       if(len(data) < 1024):
         tot = pct(transtotal , infoval)
         tot = round(tot,2)
         sys.stdout.write (str(transtotal) + " / " + str(infoval) + "..." + str(tot) + "%\r\n")
         
         rf.write(data)
         print "last packet size:" + str(len(data))
         break
       tot = pct(transtotal, infoval)
       tot = round(tot,2)
       sys.stdout.write(str(transtotal) + " / " + str(infoval) + "..." + str(tot) + "%\r")
       rf.write(data)
    rf.close()
    print "Finished Dowloading file:  " + fname

if(len(sys.argv) > 2):
   host = sys.argv[1]
   port = int(sys.argv[2])

   s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
   s.connect((host, port))
   
   while True:
      snd = raw_input("> ")
      cmds = snd.split(" ")
      if(cmds[0] == 'get'):
        #file dowload
       
        s.send(snd)
        data = s.recv(1024)
        if(data == '_NOFILE_'):
          print "File not found"
          s.close()
          break
        elif (data == '_YESFILE_'):
          
          recvfile(s, snd)
          s.close()
          break

      else:  
        s.send(snd)
        data = s.recv(1024)
        print data
        #print "msg length: " + str(len(data))
        s.close()
        break
```


```
#!/usr/bin/python
import os, glob, shutil
import sys
import socket
import time
import string
import ConfigParser

#functions
def sendfile(socket,path,name):
    confirm = socket.recv(1024)
    if(confirm == "_BEGIN_"):
      #get file size
      siz = os.path.getsize(path + name)
      socket.send("_F_SIZ_=" + str(siz))
      
      fullfile = path + name
      print "[Notice] sending file " + fullfile
      if os.path.exists(fullfile):
         #file exists we can transfer it.
         #open file in rb
         #loop through and send to socket
         f = file(fullfile,'rb')
         
         while True:
            data = f.read(1024)
            if len(data) <= 0:
               socket.send(data)
               break
            socket.send(data)
         
         f.close()
         print "[Notice] finished sending file " + fullfile

    else:
      print "No confirmation recieved"

def list_files(path):
   os.chdir(path)
   ffiles = glob.glob("*.*")  
   return ffiles; 


def usage():
   print "usage: filerec.py [portnumber][base address to read from]"

#usage: filerec.py [portnumber][base address to read from]
#check argv 

if(len(sys.argv) > 2):
   #we have at least 3 args we can contunue
   port = int(sys.argv[1])
   path = sys.argv[2]
   
   if os.path.isdir(path):
      #path is valid
      print "Server listening - Serving files from " + path
      # now lets create a socket
      sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
      sock.bind(('', port))
      sock.listen(5)

      #loop to accept connections.
      
      while True:
         sdata = ""
         newSock, address = sock.accept()
         print "**Connection from ", address
      
         rcvdata = newSock.recv(1024)
         commands = rcvdata.split(' ')
         if(commands[0] == 'list'):
             print "[Request] List files ", address
             fil = list_files(path)
             for f in fil:
                sdata = sdata + f + "\n" 
             newSock.send(sdata)
         
         elif(commands[0] == 'get'):
             #remove first word
             filenam = " ".join(commands[1:])
             print "**Requested download of " + filenam
             if(os.path.exists(path + filenam)):
                newSock.send("_YESFILE_")
                sendfile(newSock,path,filenam)
                
             else:
                print "File does not exist" + path + filenam
                newSock.send("_NOFILE_")
         elif(commands[0] == 'quit'):
             newSock.close()
             sock.close()
             print "**Remote host terminated connection"
             break;
         
         else:
            print "**Invalid command " + rcvdata
            newSock.send("**Invalid command")

   else:
      print "Invalid path " + path
      exit()
        


else:
   usage()
```

---

### Post by ziekfiguur on 2011-10-15
EDIT: nevermind, didn't read the last post good enough

---

