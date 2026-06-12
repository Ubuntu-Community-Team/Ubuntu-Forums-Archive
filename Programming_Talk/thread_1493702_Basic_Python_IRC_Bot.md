---
title: "Basic Python IRC Bot"
date: 2010-05-26
forum: Programming Talk
---

### Post by paddy.melon on 2010-05-26
OK, so I want to create a full IRC bot in python (more for the fun so don't try to convince me to use supybot or something)
ALA tutorial at shellium.org, here: [http://wiki.shellium.org/w/Writing_an_IRC_bot_in_Python](http://wiki.shellium.org/w/Writing_an_IRC_bot_in_Python)

I have a base for the bot. Works, tested, good. However, to get further, how do I pass off 'commands' in the bot
eg>

hello example

returns:
hello example!

by running hello(example) as the function. Effectively, how can I figure out where the parts I seek with ircmsg.find and thus, extract the rest of the line to parse to functions?

Thanks so much for all help!

---

### Post by simeon87 on 2010-05-26
Based on what I see in the tutorial, I'm guessing ircmsg is just a string. If so, in that tutorial they're looking for a substring and then calling the function hello. To find the parts of the string that you're looking for, you need to parse the string yourself. For example, you can split the string by spaces and then take the needed parts and give them as arguments to functions:

```

>>> msg = "hello world"
>>> splits = msg.split(' ')
>>> splits[0]
'hello'
>>> splits[1]
'world'
>>> 
```

So if splits[0] is 'hello', then you can call the function hello(splits[1]). But keep in mind that this is a very basic way of parsing as it's not guaranteed that the user will type in the correct number of arguments. You should actually check that before calling any functions.

---

### Post by chevloschelios on 2010-05-26
***CHECK THIS OUT!***

```
import socket
 
network = 'irc.snm.co.nz'
port = 6667
irc = socket.socket ( socket.AF_INET, socket.SOCK_STREAM )
irc.connect ( ( network, port ) )
print irc.recv ( 4096 )
irc.send ( 'NICK botty\r\n' )
irc.send ( 'USER botty botty botty :Python IRC\r\n' )
irc.send ( 'JOIN #paul\r\n' )
irc.send ( 'PRIVMSG #Paul :Hello World.\r\n' )
while True:
   data = irc.recv ( 4096 )
   if data.find ( 'PING' ) != -1:
      irc.send ( 'PONG ' + data.split() [ 1 ] + '\r\n' )
   if data.find ( '!botty quit' ) != -1:
      irc.send ( 'PRIVMSG #paul :Fine, if you don't want me\r\n' )
      irc.send ( 'QUIT\r\n' )
   if data.find ( 'hi botty' ) != -1:
      irc.send ( 'PRIVMSG #paul :I already said hi...\r\n' )
   if data.find ( 'hello botty' ) != -1:
      irc.send ( 'PRIVMSG #paul :I already said hi...\r\n' )
   if data.find ( 'KICK' ) != -1:
      irc.send ( 'JOIN #paul\r\n' )
   if data.find ( 'cheese' ) != -1:
      irc.send ( 'PRIVMSG #paul :WHERE!!!!!!\r\n' )
   if data.find ( 'slaps botty' ) != -1:
      irc.send ( 'PRIVMSG #paul :This is the Trout Protection Agency. Please put the Trout Down and walk away with your hands in the air.\r\n' )
   print data
```

---

### Post by paddy.melon on 2010-05-27
Sweet!

Thanks so much guys! I really appreciate it. Should get my bot going...

---

### Post by hughr2005 on 2012-04-07
I've been looking for something like this for ages and I just got it working. It's the best (simplest and most comprehendible) bot script I've seen in ages, and in my 'native' language, python :D Thank you so much chevloschelios

---

