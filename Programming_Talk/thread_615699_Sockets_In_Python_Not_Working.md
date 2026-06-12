---
title: "Sockets In Python Not Working"
date: 2007-11-17
forum: Programming Talk
---

### Post by Noodels on 2007-11-17
I've just started learning to use sockets in python and I've got a couple of programs which I am satisfied with apart from a small problem. The client only works on my computer. Here are the codes.

Server:
```
from socket import *
import pygame
from os import chdir
chdir('/home/noodels/prg/python/network/nudge/')
pygame.init()
alert = pygame.mixer.Sound('alert.wav')

mySocket = socket( AF_INET , SOCK_STREAM )
mySocket.bind( ( '' , 1992 ) )
while True:
 mySocket.listen( 1 )
 while True:
  channel , details = mySocket.accept()
  print "[SYSTEM]Message from" , details
  print channel.recv(100)
  alert.play()
  channel.send("Nudge successful.")
  channel.close()
```

Client:
```
from socket import *
host = 'localhost'
port = 1992

s = socket( AF_INET , SOCK_STREAM )
s.connect( (host , port) )
print "Enter something to send (or leave blank):"
message = raw_input()
if message == "":
 message = 'I am a fish.'
s.send(message)

print s.recv(100)
s.close()
```

I can run the server fine. And like that, the client can send a message to the server no problem. Of course, the client has to be on the same server as the computer. Replacing [host = 'localhost'] with [host = '127.0.0.1'] also works. But as soon as I put my ip address in there, when I try to run the program it stops, it doesn't complete the connection, it justs sits there with the _ thing just blinking as if it were mocking my novice attempts at networking. Is there something I need to do to the ip address first?

---

### Post by tyoc on 2007-11-17
haha, if you mean your public address, then that is a no no (it is a loopback connection), is like when you run your lighttpd or other server, and you can test it on "localhost" "home" or "127.0.0.1", but when you write your public address you cant.

In fact there is nothing wrong there, is a behaviour like that, your HW of connecting to internet doesnt do "loopback" you should buy another 1 if you really want to test it that way... or test it from other computer outside the local net... that is other computer with his own public IP address.

It is enought if you test it on localhost or 127.0.0.1 even with local LAN addressses and devices.


If you dont get it, try this:

in the browser write

> homesee what it display, then search for a site that give you your public email address and write your address in the navigation box, what you get??? ;)... not what you spect, isnt? ;).


It should work if you set up 2 computers in the same LAN with htheir own IP addresses...

---

### Post by chris.m.ball on 2007-11-17
The above poster was incorrect with their information.  If, for example, you are behind a router (like 99% of us are these days), simply do an "ifconfig" and grab your router-assigned IP which will probably be something like 192.168.1.2.  Put that into your client.py.  Start up your server and then your client and you should have zero problems connecting to yourself through your internal lan IP.

I actually took the time to create both of the files from your code, modify the audio string to point to a file I had locally on my system and everything worked just fine by using my internal lan IP.

If on the other hand you wish to use a truly external IP, you'll want to make sure that you're not blocking the inbound requests at the router or firewall level.  If you're not, then you should be able to use a completely external IP in your client.

:popcorn:

---

### Post by Smygis on 2007-11-17
Sorry if im a bit bitching now.

But omg, please read PEP8: 
[http://www.python.org/dev/peps/pep-0008/](http://www.python.org/dev/peps/pep-0008/)

---

### Post by tyoc on 2007-11-17
What I say is not wrong, perhaps the way I write it is wrong.


Testing a server within local LAN would only work for internal addresses, like home, 127.0.0.1 localhost, or other LAN addresses 192.168.1.2, 192.168.1.3, etc.

What you can't do is write the external public IP address and hope your machine answer the request... why?


PUBLIC_IP -> router <- PC1(192.168.1.2), PC2(192.168.1.3), ..., PCN(192.168.1.N)

Say me, if you write your external IP address inside the LAN section, which machine it is? none of them ;)... you need to do port forwarding in the case of servers to the specific LAN (internal) address. And even IIRC when you do port forwarding you will still be unable to connect to your public IP address within the LAN  (because3 your router need to support this feature).

like I say before, for test is enough if you 

>  It is enough if you test it on localhost or 127.0.0.1 even with local LAN addresses and devices.with the last I mean other machines in the LAN connecting to your local address.


> If on the other hand you wish to use a truly external IP, you'll want to make sure that you're not blocking the inbound requests at the router or firewall level. If you're not, then you should be able to use a completely external IP in your client.Only for e more rough, IIRC that will only work if you are behind a bridge not behind a router. For router  you will need to open the port and fordward it to the correct internal address.

I can try to explain what I know about this "issue" or "loopback thingy"... but I have give a hint with the "loopback thingy", but not in this moment.

---

### Post by Noodels on 2007-11-17
Okay, I've tried sending the client file to a friend to run the program. For him it didn't work, I expected as much what with a firewall. Is there a way to make the firewall let the program through or something?

---

### Post by red_Marvin on 2007-11-17
Yes, as tyoc said, you need to set up port forwarding on the router.

---

### Post by Noodels on 2007-11-18
I am now trying to run the program linked up to my ip address from another computer in the same network, internet is definitely working, the port is correct. Yet still, my computer wont respond to the connection my other computer is trying to make. Is there a firewall on my computer or something?

---

### Post by Noodels on 2007-11-19
I've looked thoroughly for any kind of security on my computer, I'm completely at a loss, why doesn't my computer accept other computers to connect up to ports I host?

---

### Post by tyoc on 2007-11-19
have your search what is port forward?, one of the results great source of knowledge this: [http://portforward.com/](http://portforward.com/)

there somewhere is also explained in some place why when you are testing a server from your local LAN you can connect to it, and sometimes if portforward done correctly people outside of the LAN network can do it to... but IIRC when that work and you introduce your public IP withihn the LAN you will not able to do it.

---

