---
title: "Problem about chat client server's system!"
date: 2008-10-31
forum: Programming Talk
---

### Post by starving_wages on 2008-10-31
I have a exercise about system of chat client&server,namely

>  Desig and programming one system of client-server to implememt functions which communicate message as string of characters by TCP socket. System consist of chat client and chat server.Having three messages are exchanged between client and server, namely:
 &#61607;Connection setup: When a user enter one command line
remote-chat <IP address server>:<port address> <IP address called client>:<port address>, a TCP connection will be create, client send “connection setup” message, consist of :
      o	Message descriptor field: is a 32 bit integer. It is set to 0 with “connection setup”message,
       oAddress field: 6 bytes long, consist of IP address of called client (4 bytes)  and port address of called client (2 bytes).
When server receive “connection setup”message , it will create a TCP connection to called client with IP address and port address of client in “connection setup” message.
    &#61607;	Data exchange: Used to exchange data betweens client and server. It consist of :
      o	Message descriptor field: is a 32 bit integer, is set to 1 with this data exchange
      o	Length of data field: is a integer describers length of text message.
      o	Data field: consist of text message is used to exchange.
When server receive data from client, chat server have to move to another client, used to data exchage message, too.
&#61607;	Connection teardown: when user press Ctrl+C, connection teardown will be sent before program of client close. Connection teardown only consist of one field: 
      o	message descriptor field: is a 32 bit integer, is set to 2 with this connection teardown.
When server receives this message, chat server will send to corresponding client. And then client will drop TCP connection  with server and close program.
	

I am a new baby.Who master can help you!hic hic! Actually, i don't know thoroughly that my teacher asked!
Thanks you in advance!

---

### Post by loell on 2008-10-31
a homework isn't  warmly welcomed here, in any case if you want to do it python, you'd be better using python twisted framework.

---

### Post by starving_wages on 2008-10-31
I know that. I only hope anyone help me several direction to solve this exercise!! 
Normally, chat client must be an object which make a request to server. But this exercise, chat server will make a TCP socket to called client after command line(remote-chat<ip addr>....) is entered at request client !!

---

