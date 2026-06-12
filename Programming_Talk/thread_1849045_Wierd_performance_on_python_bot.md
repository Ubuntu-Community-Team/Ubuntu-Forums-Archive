---
title: "Wierd performance on python bot"
date: 2011-09-23
forum: Programming Talk
---

### Post by merlin371 on 2011-09-23
Hello guys I'm making a small irc bot but I'm having a wierd performance issue. 

If I spam on the chat, the first few lines the bot is very responsive, after that it starts taking data very slowly, and takes quite a long time to respond as well.

This is the source code
[https://github.com/mmarignoli/LtShinyBot](https://github.com/mmarignoli/LtShinyBot)

Thanks

---

### Post by johnl on 2011-09-24
Hi,

I noticed right away one major problem with your code.

```

  def run(self):
        print irc.recv(4096)
        irc.send ( 'NICK ' + botname + '\r\n' )
        irc.send ( 'USER lsb lsb lsb :LtShinyBot IRC BOT\r\n' )
        while True:
            data = irc.recv(4096)
            if data.find("PING") ...

```



Bear with me because this is long because I wanted to explain it correctly, but the solution is simple :)

You are using a TCP socket (which is correct).  TCP guarantees several things:
1. You will receive any data sent to you (it will not be lost)
2. It will be received correctly (there will not be any corruption)
3. It will be received in order

Note that it does **not** guarantee that data will be received in the chunks that it was sent.  TCP is a stream protocol,  meaning data is not stored as individual 'packets' like UDP.  It's all globbed together.  

When you call **irc.recv(x)**, you are telling your socket to return data, up to **x** bytes. This could be:

1. You could receive exactly 1 IRC event ('PRIVMSG foo bar :blah\r\n')
2 You could receive THREE events at once ('PRIVMSG ...\r\nJOIN ...\r\nQUIT ..\r\n')
3. You could receive some fraction of an event ('PRIVMSG foo bar :')


This is the reason that the IRC protocol, on top of TCP, has a delimiter at the end of each message, "\r\n".  This is so you can separate messages that may have been globbed together from eachother.


**The solution!**
You need to read just once event at once.  Since the end of message delimiter is the same as an end-of-line delimiter, there's a super easy to do this:

```
 
  # wherever you are initializing your socket:
  irc_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
  # this 'file' object now has a readline() method we can use
  irc_file = irc_socket.makefile("rb")

  def run(self):
        # no need to recv anything before you send PASS/NICK/USER
        irc_socket.send ( 'NICK ' + botname + '\r\n' )
        irc_socket.send ( 'USER lsb lsb lsb :LtShinyBot IRC BOT\r\n' )
        while True:
            # tada; just call readline() on your 'file' to get
            # exactly one whole IRC event
            data = irc_file.readline()

```

Hope this helps.  Additionally, instead of using **find()** to identify messages, you might want to take a look at [this stackoverflow question](http://stackoverflow.com/questions/930700/python-parsing-irc-messages) which will show you how to parse a message per the IRC format into the **command**, **sender** (optional) and **arguments**.

---

