---
title: "Python IRC bot question"
date: 2013-06-10
forum: Programming Talk
---

### Post by Oriden on 2013-06-10
Hello!
I'm currently attempting to build an IRC bot which accept commands with user input in Python.
However, I'm stuck at some point.

It works fine accepting commands without user input such as !hello (then the bot would reply: Hello World).

Now I'm trying to make it accept queries entered by an user.
For example, let's say I want to lookup the definition of a dog on the Urban Dictionary, I would use the API for that. So the command would be !urban dog. (!urban <query>). However I'm not able to make it accept a query, it just doesn't do anything and I believe i need help with this.

Thanks in advance.

---

### Post by Cheesehead on 2013-06-10
Is your problem with IRC, with Python, or with the Urban Dictionary API?

If it's Python, show us the code you have.
If it's the API, give us the link to the reference page.

---

### Post by Oriden on 2013-06-10
```
import socket
import string
import urllib2


host = "irc.rizon.net"
port = 6667
channel = "#help"
nick = "TestBot"
ident = "TestBot"
realname = "TestBot"


irc = socket.socket()
irc.connect( (host,port) )
irc.send('NICK ' + nick + '\r\n')
irc.send('USER ' + ident + ' ' + host + ' bla : ' + realname + '\r\n')
irc.send('JOIN '+ channel + '\r\n')
irc.send('PRIVMSG' + channel + ':test\r\n')




while 1:
   read = irc.recv(4096)
   if read.find ('PING') != -1:
      irc.send( ' PONG ' + read.split() [ 1 ] + '\r\n')
   print read
   if read.find('!hello') != -1:
       irc.send('PRIVMSG ' + channel + ' :Hello world!\r\n')




```
It doesn't have the Urban Dictionary API yet.
Here's a link to the API:
https://github.com/novel/py-urbandict

(or http://urbandictionary.com/define.php?term=)

---

### Post by ziekfiguur on 2013-06-10
Please post your code between CODE tags, that way the indentation stays right.

I don't see anything that checks for '!urban' in your code, you could do that the same way you check for '!hello', the query would then be at read[6:]

If you would like some examples, there has been a beginners programming challenge about IRC bots. See [this]("http://ubuntuforums.org/showthread.php?t=1793081") thread.

---

### Post by Oriden on 2013-06-10
Oh sorry for the tags, did this very quickly. I also explained in my previous post that I did not add the !urban part yet :)

I'll check that link tho, thanks!

---

### Post by Oriden on 2013-06-10
Thanks for the link, I've read it but it didn't really help me much.
Do you have anything else?

---

### Post by Cheesehead on 2013-06-10
Are you asking for ways to identify and slice (or reformat) input strings?
```
>>> a = "!hello"
>>> if a == "!hello":
...     print(True)
... 
True

>>> b = "!urban whatsup"
>>> if b.startswith("!urban"):   # str.startswith(input)
...     print(b[7:])             # string slice
... 
whatsup

```

---

### Post by Oriden on 2013-06-11
No, that's not what I'm looking for.
It basically just needs to accept user input, like !urban dog, the dog is a query made by the user. Something like raw_input() except now you type it with the command.

---

### Post by Bodsda on 2013-06-12
> **Oriden said:**
> No, that's not what I'm looking for.
It basically just needs to accept user input, like !urban dog, the dog is a query made by the user. Something like raw_input() except now you type it with the command.

You have some code that does nothing other than check and reply to a PING and to send a short message when you encounter !hello 
What you first need, as others have pointed out, is to identify when someone wants to query UD and to slice the query string out from their message. Then you need to implement a function to do the query and return the result, then you need to send that result to the channel.

What exactly are you having trouble with?

---

