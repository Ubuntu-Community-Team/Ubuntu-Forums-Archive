---
title: "[SOLVED] [python] Socket recovery problem"
date: 2008-06-27
forum: Programming Talk
---

### Post by -grubby on 2008-06-27
I'm redesigning my irc bot, anyways, I'm having [s]slight[/s] major problems with him. Some vars and stuff are in other files, but I don't really think they're needed here. If you need them, just ask and I'll post them. So, here's my file:

[php]
import socket
import string

from commands import *
from config import *
from constants import *
from dictionary import *
from volumes import *

# Connection
c.connect((host, port))
# Recovers anything the network sends
rec = c.recv(8192)

# Send bot user info and nick
c.send("NICK %s \n" % (nick))
c.send("USER %s %s bla : %s \n" % (ident, host, realname))
    
if bpass != "" :
    pass # Identify
for i in channels :
    #pass # Join i
    c.send("JOIN %s \n" % (i))

# Breaking up what is sent to it
complete = rec[1:].split(":", 1)
info     = complete[0].split(" ")
msgpart  = complete[1]
sender   = info[0].split("!")
cmd      = msgpart[1:].strip()

# Pouring the broken bits into finer grains of sand
sndr = sender[0]
chnl = info[2]

cl   = cmd.split(" ") # Splitting commands

def send(msg) : # Used to send "msg" to chnl
    c.send("PRIVMSG %s :%s" % (chnl, msg))
    
act = act() # Initializing the command manager

if msgpart[0] == prefix :
    if cmd == "hi" :
        act.hi()

# If it finds text directed at it
if (msgpart.find("hi "+nick)!=-1) :
    send("hi! %s!" % sndr)
    
##### FIX LINE #####
while True :
    print rec
    record = file("raw", "a"); record.write(rec); record.close()
[/php]

I'm pretty sure the problem is with the while True statement, however it was working fine last time. I was thinking of possibly putting the whole thing after connection in a while True statement, but I'm no sure if that would work. The "FIX LINE" comment is where I'm pretty sure something is going wrong.

---

### Post by -grubby on 2008-06-28
I've fixed it by moving everything from the vars under "for i in channels" to "    send("hi! %s!" % sndr)" In a def and parsing it using function(rec)

---

