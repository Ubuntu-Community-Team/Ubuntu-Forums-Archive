---
title: "Lirc capturing input from remote without batteries"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by lovinglinux on 2008-11-15
There is something wrong with lirc or my infrared receiver.

I was experiencing some issues with my remote when watching videos, like unresponsive buttons or the video forwarding by itself. I removed the batteries from my remote, but the issue persisted. So I decided to run the irw command and, for my surprise, lirc keeps translating inputs.

Is there a way to debug this and determine if it is a software bug or a problem with the receiver?

Here is the output of irw with the remote turned off (no batteries).

```

0000000000fe173f 00 Chan+Play PinnacleSysPCTVRemote
0000000000fe173f 00 Chan+Play PinnacleSysPCTVRemote
0000000000fe173f 00 Chan+Play PinnacleSysPCTVRemote
0000000000fe173f 00 Chan+Play PinnacleSysPCTVRemote
0000000000fe173f 00 Chan+Play PinnacleSysPCTVRemote
0000000000fe173f 00 Chan+Play PinnacleSysPCTVRemote
0000000000fe173f 00 Chan+Play PinnacleSysPCTVRemote
0000000000fe173f 00 Chan+Play PinnacleSysPCTVRemote
0000000000fe173f 00 Chan+Play PinnacleSysPCTVRemote
0000000000fe173f 00 Chan+Play PinnacleSysPCTVRemote
0000000000fe173f 00 Chan+Play PinnacleSysPCTVRemote
0000000000fe173f 00 Chan+Play PinnacleSysPCTVRemote
0000000000fe173f 00 Chan+Play PinnacleSysPCTVRemote
0000000000fe173f 00 Chan+Play PinnacleSysPCTVRemote
0000000000fe173f 00 Chan+Play PinnacleSysPCTVRemote
0000000000fe173f 00 Chan+Play PinnacleSysPCTVRemote
0000000000fe173f 00 Chan+Play PinnacleSysPCTVRemote
0000000000fe173f 00 Chan+Play PinnacleSysPCTVRemote
0000000000fe173f 00 Chan+Play PinnacleSysPCTVRemote
0000000000fe173f 00 Chan+Play PinnacleSysPCTVRemote
0000000000fe173f 00 Chan+Play PinnacleSysPCTVRemote
```

As you can see, is just a single button input that keeps showing up. I have removed the command for that particular button, but I would like to solve this.

There is nothing in the room that could emit infrared waves and there is no sunlight entering the room . 

Any ideas?

---

