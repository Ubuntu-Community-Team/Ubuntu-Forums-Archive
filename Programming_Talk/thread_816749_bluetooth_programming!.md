---
title: "bluetooth programming!"
date: 2008-06-03
forum: Programming Talk
---

### Post by pontifex3 on 2008-06-03
hi, im trying to do a very simple bluetooth program (i think), all i want it to do is to broadcast the name so any cellphone when searching for devices will find it, after its found, i would like any cellphone to be able to send small messages (im guessing writing a note and sending it would be the best), and my computer to receive them and save them, but i've managed nothing so far, i've only tried with python using pybluez, with which i failed miserably using this code:
```

import bluetooth

class rfcomm_server:
  def __init__(self,port):
    self.port=port
    self.create_server()
  def create_server(self):
    self.server_socket=bluetooth.BluetoothSocket(Bluetooth.RFCOMM)
    self.server_socket.bind(("",self.port))
    self.start_server()
  def start_server(self):
    while True:
      self.server_socket.listen(3)
      uuid = "1e0ca4ea-299d-4335-93eb-27fcfe7fa848"
      bluetooth.advertise_service( self.server_socket, "Mypc", uuid )
      self.client_socket,address=server_socket.accept()
      message= self.client_socket.recv(2048)
      if message is not None:
        print "received", message

if '__name__'=='__main__':
server=rfcomm_server(20)

```

when this failed, i tried working with lightblue and used:
```

import lightblue
s = lightblue.socket()
s.bind(("", 0)) 
s.listen(1)
lightblue.advertise("MyPc", s, lightblue.RFCOMM)
conn, addr = s.accept()
print "Connected by", addr  
conn.recv(1024)
conn.close()
s.close()

```

this one also failed, when i use the cellphones' "find device" thing, it wont even find the MyPc device (with neither of the codes), i have tried with different cellphones from sony ericcson and motorola. my bluetooth sure is working, since when i run kbluetooth, cellphones find my computer, and im able to send pictures and any kind of stuff from my phone to the computer. any help in /C++, python, Java, perl, or something that wont be too complicated to learn/ will be greatly appreciated! thanks a lot

p.s, even though kbluetooth works, its not good enough since i want the messages received to be automatically displayed on a projector and other stuff which would imply having to tweak the kbluetooth source a bit, and i think that might take much longer

pss. the code is not mine, i got it from api examples and a tutorial, but i understand it well enough, i didnt just download it and run it, aah except for the uuid! isnt the uuid supposed to be determined in the chipset or something? i could find any so i just used the one that the tut indicated and it didnt crash

thanks in advance =D

---

