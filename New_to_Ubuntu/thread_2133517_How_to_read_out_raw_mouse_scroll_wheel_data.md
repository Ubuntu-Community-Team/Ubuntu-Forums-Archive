---
title: "How to read out raw mouse scroll wheel data?"
date: 2013-04-08
forum: New to Ubuntu
---

### Post by kramer65 on 2013-04-08
For a home robotics project I need to read out the raw mouse scroll wheel data. Using the help of [this answer on Stackoverflow]("http://stackoverflow.com/a/12286738/1650012") I did manage to read out all the other information (mouse movements and button clicks) using the following python code:
```
import struct
file = open( "/dev/input/mice", "rb" )

def getMouseEvent():
  buf = file.read(3)
  button = ord( buf[0] )
  bLeft = button & 0x1
  bMiddle = ( button & 0x4 ) > 0
  bRight = ( button & 0x2 ) > 0
  x,y = struct.unpack( "bb", buf[1:] )
  print ("L:%d, M: %d, R: %d, x: %d, y: %d\n" % (bLeft,bMiddle,bRight, x, y) )

while True:
  getMouseEvent()
file.close()
```

Unfortunately, the scroll wheel is not in this information. I now understand I somehow have to switch the "mode" of the mouse to something other than PS/2, since that "only supports 3 bytes" where I apparently need a fourth one. But here I'm a bit lost..

Does anybody know how I can get the raw scroll wheel information (possibly by switching the mouse mode)? All tips are welcome!

---

