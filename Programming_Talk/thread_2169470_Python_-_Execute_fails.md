---
title: "Python - Execute fails"
date: 2013-08-22
forum: Programming Talk
---

### Post by Random20210831 on 2013-08-22
I made this script:
```
#!/usr/bin/env python
# -*- coding:utf-8 -*-


#
# The most stupid IRC bot
#


import socket
import time
import feedparser


# Config
# ------


server  = "irc.freenode.net" # Server
channel = "#botwar" # Channel
botnick = "XDroid" # Bot's name


# Stupid setup functions
# ----------------------


# Send message to the channel


def sendmsg(chan, msg):
  ircsock.send("PRIVMSG "+ chan +" :"+ msg +"\n")


# Join the channel


def joinchan(chan):
  ircsock.send("JOIN "+ chan +"\n")


# Connect to server
# -----------------


ircsock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
ircsock.connect((server, 6667))
ircsock.send("USER "+ botnick +" "+ botnick +" "+ botnick +" :$\n")
ircsock.send("NICK "+ botnick +"\n")
joinchan(channel)


# Stupid functions
# ----------------


while 1:
  ircmsg = ircsock.recv(2048)
  ircmsg = ircmsg.strip("\n\r")
  print(ircmsg)


  if ircmsg.find("+hello") != -1: 
    ircsock.send("PRIVMSG "+ channel +" :Hello guys!\n")


  if ircmsg.find("+verge") != -1:
    url="http://www.theverge.com/rss/index.xml"
    feed = feedparser.parse(url)
    for i in range(1,6):
      news=feed["items"][i].link
      ircsock.send("PRIVMSG "+ channel +" :The Verge ~ " + news +"\n")


  if ircmsg.find("+place") != -1:
    ircsock.send("PRIVMSG "+ channel +" :I don't know\n")


  if ircmsg.find("+time") != -1:
    ircsock.send("PRIVMSG "+ channel +" :It's " + time.ctime() + "\n")


  if ircmsg.find("+tux") != -1:
    ircsock.send("PRIVMSG "+ channel + " :    .--.\n")
    ircsock.send("PRIVMSG "+ channel + " :   |o_o |\n")
    ircsock.send("PRIVMSG "+ channel + " :   |:_/ |\n")
    ircsock.send("PRIVMSG "+ channel + " :  //   \ \ \n")
    ircsock.send("PRIVMSG "+ channel + " : (|     | )\n")
    ircsock.send("PRIVMSG "+ channel + " :/'\_   _/`\ \n")
    ircsock.send("PRIVMSG "+ channel + " :\___)=(___/\n")


  if ircmsg.find("PING :") != -1:
    ircsock.send("PONG :pingis\n")


  # ------------------
  # *quit doesn't work
  # ------------------


  # Reconnect the bot


  if ircmsg.find("+rcn") != -1:
    try:
        ircsock.quit()
    except:
        pass


    ircsock.send("PRIVMSG "+ channel + " /quit")
    ircsock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    ircsock.connect((server, 6667))
    ircsock.send("USER "+ botnick +" "+ botnick +" "+ botnick +" :XDroid\n")
    ircsock.send("NICK "+ botnick +"\n")
    joinchan(channel)

```

And I tried to run it with **./XDroid.py** (that's name of file, it also has execute permission), but it shows this error:
```
: No such file or directory
```
How to fix it?

---

### Post by trent.josephsen on 2013-08-22
What happens when you run it with "python XDroid.py"?

---

### Post by Random20210831 on 2013-08-22
It works. But when run another script (for example blablabla.py with ./blablabla.py) it runs well, without error.

---

### Post by Cheesemill on 2013-08-22
Is the script in your home folder or on another drive?

Can you post the output of the following from the script directory please.

```
pwd
ls -lh XDroid.py
mount
```

---

### Post by spjackson on 2013-08-22
> **ZDroid said:**
> 
And I tried to run it with **./XDroid.py** (that's name of file, it also has execute permission), but it shows this error:
```
: No such file or directory
```
How to fix it?
I suspect DOS line endings. While python does not care, it does matter for the hashbang first line.

---

### Post by Random20210831 on 2013-08-22
> **spjackson said:**
> I suspect DOS line endings. While python does not care, it does matter for the hashbang first line.
Here is no DOS line endings.

@Cheesemill You think that I want to develop script and run it from another drive?
```
$ ls -lh XDroid.py
-rwxrwxr-x 1 zlatan zlatan 2,5K avg 22 14:26 XDroid.py
```

---

### Post by Cheesemill on 2013-08-22
I was just wondering if you are trying to run the script from an external USB device as by default these are mounted with the noexec option, meaning you cannot run files from them even if they do have the execute bit set correctly.

Which directory is your script in?

---

### Post by ofnuts on 2013-08-22
> **ZDroid said:**
> I
And I tried to run it with **./XDroid.py** (that's name of file, it also has execute permission), but it shows this error:
```
: No such file or directory
```
How to fix it?
The full bash answer isn't "*[FONT=courier new]: No such file or directory[/FONT]*" but "*[FONT=courier new]bash: **somefile**: No such file or directory[/FONT]*"

So what is the full bash answer? because so far we have to take your word that you really entered "./XDroid.py" without any typo.

---

### Post by spjackson on 2013-08-22
> **ZDroid said:**
> Here is no DOS line endings.

That's a pity. DOS line endings produce exactly the symptom you describe on my machine.
```

$ ./foo.py
: No such file or directory
$ python ./foo.py
Hello
$ od -c foo.py
0000000   #   !   /   u   s   r   /   b   i   n   /   e   n   v       p
0000020   y   t   h   o   n  \r  \n  \r  \n   p   r   i   n   t       "
0000040   H   e   l   l   o   "  \r  \n

```
Sorry I wasn't able to help.

---

### Post by Random20210831 on 2013-08-22
@Cheesemill In **~/dev/git/XDroid**.
@ofnuts This is just for you.
[ATTACH=CONFIG]245589[/ATTACH]
@spjackson It's right.
```

od -c XDroid.py
0000000   #   !   /   u   s   r   /   b   i   n   /   e   n   v       p
0000020   y   t   h   o   n  \r  \n   #       -   *   -       c   o   d
0000040   i   n   g   :   u   t   f   -   8       -   *   -  \r  \n  \r
0000060  \n   #  \r  \n   #       T   h   e       m   o   s   t       s
0000100   t   u   p   i   d       I   R   C       b   o   t  \r  \n   #
0000120  \r  \n  \r  \n   i   m   p   o   r   t       s   o   c   k   e
0000140   t  \r  \n   i   m   p   o   r   t       t   i   m   e  \r  \n
0000160   i   m   p   o   r   t       f   e   e   d   p   a   r   s   e
0000200   r  \r  \n  \r  \n   #       C   o   n   f   i   g  \r  \n   #
0000220       -   -   -   -   -   -  \r  \n  \r  \n   s   e   r   v   e
0000240   r           =       "   i   r   c   .   f   r   e   e   n   o
0000260   d   e   .   n   e   t   "       #       S   e   r   v   e   r
0000300  \r  \n   c   h   a   n   n   e   l       =       "   #   z   d
0000320   r   o   i   d   "       #       C   h   a   n   n   e   l  \r
0000340  \n   b   o   t   n   i   c   k       =       "   X   D   r   o
0000360   i   d   "       #       B   o   t   '   s       n   a   m   e
0000400  \r  \n  \r  \n   #       S   t   u   p   i   d       s   e   t
0000420   u   p       f   u   n   c   t   i   o   n   s  \r  \n   #    
0000440   -   -   -   -   -   -   -   -   -   -   -   -   -   -   -   -
0000460   -   -   -   -   -   -  \r  \n  \r  \n   #       S   e   n   d
0000500       m   e   s   s   a   g   e       t   o       t   h   e    
0000520   c   h   a   n   n   e   l  \r  \n  \r  \n   d   e   f       s
0000540   e   n   d   m   s   g   (   c   h   a   n   ,       m   s   g
0000560   )   :  \r  \n           i   r   c   s   o   c   k   .   s   e
0000600   n   d   (   "   P   R   I   V   M   S   G       "   +       c
0000620   h   a   n       +   "       :   "   +       m   s   g       +
0000640   "   \   n   "   )  \r  \n  \r  \n   #       J   o   i   n    
0000660   t   h   e       c   h   a   n   n   e   l  \r  \n  \r  \n   d
0000700   e   f       j   o   i   n   c   h   a   n   (   c   h   a   n
0000720   )   :  \r  \n           i   r   c   s   o   c   k   .   s   e
0000740   n   d   (   "   J   O   I   N       "   +       c   h   a   n
0000760       +   "   \   n   "   )  \r  \n  \r  \n   #       C   o   n
0001000   n   e   c   t       t   o       s   e   r   v   e   r  \r  \n
0001020   #       -   -   -   -   -   -   -   -   -   -   -   -   -   -
0001040   -   -   -  \r  \n  \r  \n   i   r   c   s   o   c   k       =
0001060       s   o   c   k   e   t   .   s   o   c   k   e   t   (   s
0001100   o   c   k   e   t   .   A   F   _   I   N   E   T   ,       s
0001120   o   c   k   e   t   .   S   O   C   K   _   S   T   R   E   A
0001140   M   )  \r  \n   i   r   c   s   o   c   k   .   c   o   n   n
0001160   e   c   t   (   (   s   e   r   v   e   r   ,       6   6   6
0001200   7   )   )  \r  \n   i   r   c   s   o   c   k   .   s   e   n
0001220   d   (   "   U   S   E   R       "   +       b   o   t   n   i
0001240   c   k       +   "       "   +       b   o   t   n   i   c   k
0001260       +   "       "   +       b   o   t   n   i   c   k       +
0001300   "       :   $   \   n   "   )  \r  \n   i   r   c   s   o   c
0001320   k   .   s   e   n   d   (   "   N   I   C   K       "   +    
0001340   b   o   t   n   i   c   k       +   "   \   n   "   )  \r  \n
0001360   j   o   i   n   c   h   a   n   (   c   h   a   n   n   e   l
0001400   )  \r  \n  \r  \n   #       S   t   u   p   i   d       f   u
0001420   n   c   t   i   o   n   s  \r  \n   #       -   -   -   -   -
0001440   -   -   -   -   -   -   -   -   -   -   -  \r  \n  \r  \n   w
0001460   h   i   l   e       1   :  \r  \n           i   r   c   m   s
0001500   g       =       i   r   c   s   o   c   k   .   r   e   c   v
0001520   (   2   0   4   8   )  \r  \n           i   r   c   m   s   g
0001540       =       i   r   c   m   s   g   .   s   t   r   i   p   (
0001560   "   \   n   \   r   "   )  \r  \n           p   r   i   n   t
0001600   (   i   r   c   m   s   g   )  \r  \n  \r  \n           i   f
0001620       i   r   c   m   s   g   .   f   i   n   d   (   "   +   h
0001640   e   l   l   o   "   )       !   =       -   1   :      \r  \n
0001660                   i   r   c   s   o   c   k   .   s   e   n   d
0001700   (   "   P   R   I   V   M   S   G       "   +       c   h   a
0001720   n   n   e   l       +   "       :   H   e   l   l   o       g
0001740   u   y   s   !   \   n   "   )  \r  \n  \r  \n           i   f
0001760       i   r   c   m   s   g   .   f   i   n   d   (   "   +   v
0002000   e   r   g   e   "   )       !   =       -   1   :  \r  \n    
0002020               u   r   l   =   "   h   t   t   p   :   /   /   w
0002040   w   w   .   t   h   e   v   e   r   g   e   .   c   o   m   /
0002060   r   s   s   /   i   n   d   e   x   .   x   m   l   "  \r  \n
0002100                   f   e   e   d       =       f   e   e   d   p
0002120   a   r   s   e   r   .   p   a   r   s   e   (   u   r   l   )
0002140  \r  \n                   f   o   r       i       i   n       r
0002160   a   n   g   e   (   1   ,   6   )   :  \r  \n                
0002200           n   e   w   s   =   f   e   e   d   [   "   i   t   e
0002220   m   s   "   ]   [   i   ]   .   l   i   n   k  \r  \n        
0002240                   i   r   c   s   o   c   k   .   s   e   n   d
0002260   (   "   P   R   I   V   M   S   G       "   +       c   h   a
0002300   n   n   e   l       +   "       :   T   h   e       V   e   r
0002320   g   e       ~       "       +       n   e   w   s       +   "
0002340   \   n   "   )  \r  \n  \r  \n           i   f       i   r   c
0002360   m   s   g   .   f   i   n   d   (   "   +   p   l   a   c   e
0002400   "   )       !   =       -   1   :  \r  \n                   i
0002420   r   c   s   o   c   k   .   s   e   n   d   (   "   P   R   I
0002440   V   M   S   G       "   +       c   h   a   n   n   e   l    
0002460   +   "       :   I       d   o   n   '   t       k   n   o   w
0002500   \   n   "   )  \r  \n  \r  \n           i   f       i   r   c
0002520   m   s   g   .   f   i   n   d   (   "   +   t   i   m   e   "
0002540   )       !   =       -   1   :  \r  \n                   i   r
0002560   c   s   o   c   k   .   s   e   n   d   (   "   P   R   I   V
0002600   M   S   G       "   +       c   h   a   n   n   e   l       +
0002620   "       :   I   t   '   s       "       +       t   i   m   e
0002640   .   c   t   i   m   e   (   )       +       "   \   n   "   )
0002660  \r  \n  \r  \n           i   f       i   r   c   m   s   g   .
0002700   f   i   n   d   (   "   +   t   u   x   "   )       !   =    
0002720   -   1   :  \r  \n                   i   r   c   s   o   c   k
0002740   .   s   e   n   d   (   "   P   R   I   V   M   S   G       "
0002760   +       c   h   a   n   n   e   l       +       "       :    
0003000               .   -   -   .   \   n   "   )  \r  \n            
0003020       i   r   c   s   o   c   k   .   s   e   n   d   (   "   P
0003040   R   I   V   M   S   G       "   +       c   h   a   n   n   e
0003060   l       +       "       :               |   o   _   o       |
0003100   \   n   "   )  \r  \n                   i   r   c   s   o   c
0003120   k   .   s   e   n   d   (   "   P   R   I   V   M   S   G    
0003140   "   +       c   h   a   n   n   e   l       +       "       :
0003160               |   :   _   /       |   \   n   "   )  \r  \n    
0003200               i   r   c   s   o   c   k   .   s   e   n   d   (
0003220   "   P   R   I   V   M   S   G       "   +       c   h   a   n
0003240   n   e   l       +       "       :           /   /            
0003260   \       \       \   n   "   )  \r  \n                   i   r
0003300   c   s   o   c   k   .   s   e   n   d   (   "   P   R   I   V
0003320   M   S   G       "   +       c   h   a   n   n   e   l       +
0003340       "       :       (   |                       |       )   \
0003360   n   "   )  \r  \n                   i   r   c   s   o   c   k
0003400   .   s   e   n   d   (   "   P   R   I   V   M   S   G       "
0003420   +       c   h   a   n   n   e   l       +       "       :   /
0003440   '   \   _               _   /   `   \       \   n   "   )  \r
0003460  \n                   i   r   c   s   o   c   k   .   s   e   n
0003500   d   (   "   P   R   I   V   M   S   G       "   +       c   h
0003520   a   n   n   e   l       +       "       :   \   _   _   _   )
0003540   =   (   _   _   _   /   \   n   "   )  \r  \n  \r  \n        
0003560   i   f       i   r   c   m   s   g   .   f   i   n   d   (   "
0003600   P   I   N   G       :   "   )       !   =       -   1   :  \r
0003620  \n                   i   r   c   s   o   c   k   .   s   e   n
0003640   d   (   "   P   O   N   G       :   p   i   n   g   i   s   \
0003660   n   "   )  \r  \n  \r  \n           #       -   -   -   -   -
0003700   -   -   -   -   -   -   -   -   -   -   -   -   -  \r  \n    
0003720       #       *   q   u   i   t       d   o   e   s   n   '   t
0003740       w   o   r   k  \r  \n           #       -   -   -   -   -
0003760   -   -   -   -   -   -   -   -   -   -   -   -   -  \r  \n  \r
0004000  \n           #       R   e   c   o   n   n   e   c   t       t
0004020   h   e       b   o   t  \r  \n  \r  \n           i   f       i
0004040   r   c   m   s   g   .   f   i   n   d   (   "   +   r   c   n
0004060   "   )       !   =       -   1   :  \r  \n                   t
0004100   r   y   :  \r  \n                                   i   r   c
0004120   s   o   c   k   .   q   u   i   t   (   )  \r  \n            
0004140       e   x   c   e   p   t   :  \r  \n                        
0004160           p   a   s   s  \r  \n  \r  \n                   i   r
0004200   c   s   o   c   k   .   s   e   n   d   (   "   P   R   I   V
0004220   M   S   G       "   +       c   h   a   n   n   e   l       +
0004240       "       /   q   u   i   t   "   )  \r  \n                
0004260   i   r   c   s   o   c   k       =       s   o   c   k   e   t
0004300   .   s   o   c   k   e   t   (   s   o   c   k   e   t   .   A
0004320   F   _   I   N   E   T   ,       s   o   c   k   e   t   .   S
0004340   O   C   K   _   S   T   R   E   A   M   )  \r  \n            
0004360       i   r   c   s   o   c   k   .   c   o   n   n   e   c   t
0004400   (   (   s   e   r   v   e   r   ,       6   6   6   7   )   )
0004420  \r  \n                   i   r   c   s   o   c   k   .   s   e
0004440   n   d   (   "   U   S   E   R       "   +       b   o   t   n
0004460   i   c   k       +   "       "   +       b   o   t   n   i   c
0004500   k       +   "       "   +       b   o   t   n   i   c   k    
0004520   +   "       :   X   D   r   o   i   d   \   n   "   )  \r  \n
0004540                   i   r   c   s   o   c   k   .   s   e   n   d
0004560   (   "   N   I   C   K       "   +       b   o   t   n   i   c
0004600   k       +   "   \   n   "   )  \r  \n                   j   o
0004620   i   n   c   h   a   n   (   c   h   a   n   n   e   l   )
0004637

```

---

### Post by Vaphell on 2013-08-22
```
sed -i 's/\r$//' XDroid.py
```

---

### Post by Random20210831 on 2013-08-22
Vaphell, you are king.

---

### Post by spjackson on 2013-08-22
> **ZDroid said:**
> 
@spjackson It's right.
```

od -c XDroid.py
0000000   #   !   /   u   s   r   /   b   i   n   /   e   n   v       p
0000020   y   t   h   o   n  \r  \n   #       -   *   -       c   o   d
0000040   i   n   g   :   u   t   f   -   8       -   *   -  \r  \n  \r

```
I'm confused. I suggested to you that the problem might be DOS line endings. You asserted that your script did not have DOS line endings, then you posted this to show that it does have DOS line endings. What do you mean by "It's right?"

---

### Post by Random20210831 on 2013-08-22
I used your od -c as you suggested and saw that I'm wrong and you right (I had DOS line endings).

---

