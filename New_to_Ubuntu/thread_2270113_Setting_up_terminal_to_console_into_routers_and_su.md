---
title: "Setting up terminal to console into routers and such"
date: 2015-03-20
forum: New to Ubuntu
---

### Post by dup2 on 2015-03-20
Ok first off I am BRAND NEW to using Ubuntu. My background is more in networking and hardware related.  I have successfully installed Ubuntu 14.04 Gnome on my HP Probook6560b. I have everything up and running including being able to VPN into my companies network using Citrix Receiver. It has taken me a couple of days off and on to accomplish this.Let me say I should have done this years ago, this is really one of the best things I have ever received for free.
          I have figured out how to telnet and ssh from terminal mode . My big problem is I have to console into routers using a serial cable daily. I cannot for the life of me get this to work.I have been browsing the internet for two days off and on to find this info. I have found sites with info such as this **[http://www.coreboot.org/Serial_console#Enabling_Serial_Console](http://www.coreboot.org/Serial_console#Enabling_Serial_Console) ** but I am so green that I don't even know how to 
"create a file". this is the last piece of the puzzle that i need to really start using this and get away from the dreaded corporate windows 7 image my company uses. I really need a down to the key stroke solutions to get this up and running . 
          Before you guys say "learn the code ....don't fight it".... I will . I am very versed with Cisco language so I am capable and will learn the code with sites like this [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal) . Thank you in advance with any help you can give. I don't plan on being a one and done person around here.

---

### Post by steeldriver on 2015-03-20
Hello and welcome to the forums

I think that 'Serial Console' is not what you want - that's for configuring **your **system to look like a serial device

It sounds like you need to **connect to** a serial console device (Cisco router) - if so, you just need a client such as minicom (or putty, configured to use serial rather than TCP) which takes the place of the 'hyperterminal' client that you are probably using on Windows

See for example [http://www.cyberciti.biz/tips/connect-soekris-single-board-computer-using-minicom.html](http://www.cyberciti.biz/tips/connect-soekris-single-board-computer-using-minicom.html)

---

### Post by dup2 on 2015-03-20
Thanks for the reply steel driver. I have down loaded Putty but it will not connect it says "error unable to connect to serial port" . I found a work around by opening the terminal and typing -sudo putty . Putty opens and works great at that point.However I am unable to copy and paste anything except in that Putty session. Also  I am unable to copy a batch config from my documents and paste it into my putty session. I don't really care how I get this to work as most programs like Putty ,Tera-Term , secure CRT and such work about the same I just need to access a router and be able to copy a batch config into it.

---

### Post by dino99 on 2015-03-20
maybe i'm wrong, but usually the router can be set by 192.168.x.x from a browser

---

### Post by dup2 on 2015-03-20
> **9d9 said:**
> maybe i'm wrong, but usually the router can be set by 192.168.x.x from a browser


Yes you are correct but I need to be able to "Console" into them when they are fresh out of the box with a serial cable.

---

### Post by King of Heart 4711 on 2015-03-20
What type of serial port are you using? On board serial or a USB to Serial adapter.

If it is on board the device is at /dev/tty0 and USB adapter will be at /dev/ttyUSB0

use Minicom to connect: [https://help.ubuntu.com/community/Minicom](https://help.ubuntu.com/community/Minicom), try as root if a normal user will not allow a connection to the serial port. If it works with root but not your user account then you'll need a UDEV rule in place for the serial ports. I banged my head on this exact issue for about a month a while back.

---

### Post by steeldriver on 2015-03-20
instead of running the client (putty or minicom) as root (i.e. with sudo), it should be sufficient to add yourself to the 'dialout' group iirc

```

sudo gpasswd --add *username *dialout

```

where *username * is replaced by your actual username

---

### Post by dup2 on 2015-03-20
King of Heart. Thank you, I have just successfully consoled into my desk router. I truly love the simplicity of this operating system and its versatility. Now to look at some of the links at the bottom of the page to see if I can make some profiles . I have yet one more question . Is there a way to quit being ask my password every time I do anything in terminal mode ?

> **steeldriver said:**
> instead of running the client (putty or minicom) as root (i.e. with sudo), it should be sufficient to add yourself to the 'dialout' group iirc

```

sudo gpasswd --add *username *dialout

```

where *username * is replaced by your actual username


Ok I have been added to group dial out. Remember I am very green, so what does this enable me to do ?

Huh OO . Now it says

 Device /dev/ttyS0 is locked.

How do I remove myself from dialout ?

---

### Post by dup2 on 2015-03-20
> **dup2 said:**
> King of Heart. Thank you, I have just successfully consoled into my desk router. I truly love the simplicity of this operating system and its versatility. Now to look at some of the links at the bottom of the page to see if I can make some profiles . I have yet one more question . Is there a way to quit being ask my password every time I do anything in terminal mode ?




Ok I have been added to group dial out. Remember I am very green, so what does this enable me to do ?

Huh OO . Now it says

 Device /dev/ttyS0 is locked.

How do I remove myself from dialout ?



Ok I figured it out .

---

### Post by King of Heart 4711 on 2015-03-21
The best way that I have come up with is my udev rule for usb serial devices:

```
# serial
# this is the general rule that covers ttyUSB0 among others
KERNEL=="tty[A-Z]*[0-9]|pppox[0-9]*|ircomm[0-9]*|noz[0-9]*|rfcomm[0-9]*", GROUP="dialout"

# relax the permissions just for ttyUSB0
KERNEL=="ttyUSB0",              MODE="0666"
```

not a fan of adding my self to groups for one device, the above works perfectly for me.
the code works for the first USB Serial port, but ```
KERNEL=="ttyUSB0"
``` can be changed to whatever Serial port you are using

---

### Post by dup2 on 2015-03-23
Thanks all. I'm up and running at this point . Now I get to try and install Ubuntu 14.04 server on an old MAC Mini..

---

