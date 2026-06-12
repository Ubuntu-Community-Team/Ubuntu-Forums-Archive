---
title: "Beginners Programming Challenge #21"
date: 2011-06-28
forum: Programming Talk
---

### Post by Queue29 on 2011-06-28
**Beginners Programming Challenge #21**

**The Challenge**
To create an automated [RFC-2812]("http://www.kvirc.de/docu/doc_rfc2812.html") client... more commonly known as an [IRC Bot]("http://en.wikipedia.org/wiki/Irc_bot"). 


**Overview**
This challenge will be an exercise primarily in client-server communications and reading a standards document. Using the protocal defined in RFC 2812 your objective will be to create a client (a bot) that responds to messages sent out by the server. For example, you could create a simple bot that greets people as they enter a channel, or a complicated bot that generates somewhat-coherent phrases using markov chains and machine learning. Whether simple or complicated, all IRC bots need to be able to connect to a server, set a nick, and join a channel. For non-passworded servers, this is as simple as sending a NICK immediately followed by a JOIN once a connection to a server has been opened. 

For the purposes of this contest, have your bot hang out on the **#ufpc** channel on the **chat.freenode.net** server. You should see either me (Queue29) or my bot (cbot) once you connect (and maybe a few other challengers as well). 

**Howdoidoit**
Intermediate and Advanced programmers: don't read this, read RFC 2812. It contains everything you need to know. This section is for beginners who maybe have never opened a connection or even heard of Internet Chat Relay. Instead of having you guys scour the 'net for old sample code that conforms to the old standard, I am including a working template that demonstrates the fundamentals of the protocal:

```

# original source: http://www.osix.net/modules/article/?id=780
# (updated to the new standard)

import sys
import socket
import string
import time

HOST='chat.freenode.net'
PORT=6667
NICK='reallysimplebot'
IDENT='Nobody'
RNAME='Your Name'
CHANNEL='#ufpc'

s = socket.socket()
s.connect((HOST, PORT))
s.send('NICK ' + NICK + '\r\n')
s.send('USER ' + IDENT + ' 0 * :' + RNAME + '\r\n')

while True:
    line = s.recv(1024)
    print ">> " + line
    if 'MOTD command' in line:
        print '<< sending join...'
        s.send('JOIN ' + CHANNEL + '\r\n')
    elif 'JOIN' in line:
        print '<< sending welcome...'
        s.send('PRIVMSG ' + CHANNEL + ' :Welcome!\r\n')
    elif 'PING' in line:
        print'<< sending pong...'
        s.send('PONG ' + CHANNEL + '\r\n')

```


So what's going on? First up, we open a connection to the server using plain sockets. You can think of the HOST as the url of the server, in our case it will be chat.freenode.irc . The port is the port number- for non SSL, pick one of 6665, 6666, 6667, 8000, 8001, 8002. Then we create the connection (super easy in python!). The first two messages we send to the server are very important. As designated in RFC 2812 section 3.1, the first two messages to be sent to the server should be 'NICK <params>' followed by 'USER <params>' unless there is a password, in which case 'PASS <password>' goes first. The server/channel we are using is not password protected. Now this is important, and many of you are going to be confused by this: all messages sent to the server must end in Windows style carriage returns: '\r\n' instead of the usual '\n' . It's a part of the standard, and your bot really won't work if you forget to do that! 

You should note that all messages contain 1, 2, or 3 parts, delimted (awkardly, in my opinion) by space characters and : characters. Section 2.3.1 covers this in detail, but you can get away with reading the format examples in the document under each command's explanation. For example, in the NICK section, you are given the examples:
```

**NICK Wiz **               ; Introducing new nick "Wiz" if session is
                           still unregistered, or user changing his
                           nickname to "Wiz"
**:WiZ!jto@tolsun.oulu.fi NICK Kilroy**
                           ; Server telling that WiZ changed his
                           nickname to Kilroy.

```

So now that the bot is connected to the server, we need to join an actual channel. First, we should wait until the server stops spamming us with messages. A good indication of this is when the server sends a message like: *:holmes.freenode.net 376 ezbot :End of /MOTD command. * In my example bot, when the variable line contains "MOTD command", it sends a JOIN command. The join command will ultimately look like "JOIN #ufpc \r\n" . 

Lastly in my example bot is a mechanism for letting the server know the bot is still alive. Every once in a while, the server will send a PING message (section 3.7.2) and you must send a PONG message in response. If you don't, the server will disconnect you. 

**Extra credit**
- Have your bot connect using SSL: chat.freenode.net SSL ports include 6697, 7000, and 7070.
- Be creative! There are many things you can get a bot to do, so make yours do useful and interesting things to 
- Have your bot send messages in [COLOR="Red"]C[/COLOR][COLOR="SeaGreen"]O[/COLOR][COLOR="Purple"]L[/COLOR][COLOR="Blue"]O[/COLOR][COLOR="Green"]R[/COLOR]

**Help**
First, try to read and understand RFC 2812. That really is one of the goals of this challenge. But of course you can always find help here, or on #ufpc! You can also check out the source code for cbot [here]("https://github.com/shoenig/CoffeeBot"). 

**Judging** 
Judging will be based mostly on good design: This project is great because there is _tons_ of room for modularizing your code. Giant python scripts with no classes and functions make me sad. You don't want me to be sad, do you? Usefulness and Creativity will also be factors. There are numerous 'sample' bots that kind of work but don't really do much. You should make your bot stand out by doing purposeful things like.. replying with weather reports, detecting floods, keeping track of karma, and whatever else you can think of. 


Have fun! Judging will commence in a few weeks, or when the entries stop coming in.

---

### Post by cprofitt on 2011-06-29
interesting challenge; ensure that the testing of the bots is done in private channels.

---

### Post by JupiterV2 on 2011-06-29
Certainly an interesting challenge but I wonder if beyond the scope of "beginners?" It will require knowledge of sockets, the protocol and lexical analysis...something beyond simple learning techniques. I guess we'll see when people submit their code. =)

---

### Post by schauerlich on 2011-06-29
Hmm... I think I'll be trying this in Clojure. Eventually. :)

---

### Post by cgroza on 2011-06-29
This is my first try, it says Welcome and goodbye to people. Planning to improve it.
EDIT: separated the bot from the actions.
```

import sys
import socket
import string
import time

def parsemsg(s):
    """Breaks a message from an IRC server into its prefix, command, and arguments.
    """
    prefix = ''
    trailing = []
    if not s:
       raise IRCBadMessage("Empty line.")
    if s[0] == ':':
        prefix, s = s[1:].split(' ', 1)
    if s.find(' :') != -1:
        s, trailing = s.split(' :', 1)
        args = s.split()
        args.append(trailing)
    else:
        args = s.split()
    command = args.pop(0)
    return prefix, command, args

class Logger(object):
    def __init__(self, log_file = "/home/cgroza/irc_log.txt"):
        self.log_file = log_file
        self.log = open(self.log_file, "a")

    def Write(self, s):
        self.log.write(s)
        self.log.flush()

    def Close(self):
        self.log.close()

class IrcActions(object):
    def __init__(self, bot ,sock, channel = "#ufpc", host = "chat.freenode.net", nick_name = "stupid_bot",
            ident = "Stupid Bot", rname = "Botty Bot" ):
        self.bot = bot
        self.channel = channel
        self.host = host
        self.nick_name = nick_name
        self.ident = ident
        self.rname = rname
        self.sock = sock
        self.logger = Logger()

    def _BadArgs(self, args):
        self.SendMessage("Bad number of arguments, try the 'help' command.", self.GetNickName(args))
        return

    def OnInsult(self, args):
        if len(args) < 3:
            self._BadArgs(args)
            return
        self.SendMessage("I insult you!", args[2])
        #reading from an insult file would be more oringinal

    def OnSay(self, args):
        self.SendMessage(" ".join(args[2:]))

    def OnCreator(self, args):
        nick = self.GetNickName(args)
        self.SendMessage("My creator is master cgroza.", nick)
        self.SendMessage("All hail my master cgroza.", nick)

    def OnHelp(self, args):
       nick = self.GetNickName(args)
       self.SendMessage(" quit      Closes the bot.")
       self.SendMessage(" help      Presents this screen.")
       self.SendMessage(" insult    Insults the user provided as an argument.")
       self.SendMessage(" hello     Greets the user provided as an argument.")

    def SendMessage(self, msg, usr=""):
        self.sock.send("PRIVMSG " + self.channel + " :" + usr + " " + msg + "\r\n")

    def _LogMessage(self, parsed_line):
        line = "<" + self.GetNickName(parsed_line) + ">"+ parsed_line[2][1]
        self.logger.Write(line)

    def OnMsg(self, args):
        print "Got Message"
        if self.nick_name in args[2][1]:
            nick = self.GetNickName(args)
            #process commands here
            command = args
            if not self._ParseCommand(command):
                self.SendMessage("I am not intelligent. Wish I could chat with you, bit I can't. Try help for a list of commands.", nick)
        else:
            self._LogMessage(args)

    def OnJoin(self, args):
        print "Sending greet"
        nick = self.GetNickName(args)
        self.SendMessage("Welcome", nick)

    def OnQuit(self, args):
        print "Sending goodbye"
        nick = self.GetNickName(args)
        self.SendMessage("Goodbye", nick)

    def JoinMe(self, args):
        print "Joining"
        self.sock.send("JOIN " + self.channel + "\r\n")
       self.SendMessage(" is online", self.nick_name)

    def OnPing(self, args):
        print "Pinging"
        self.sock.send("PONG " + self.channel + "\r\n")

    def GetNickName(self, args):
        return args[0].split("!")[0].strip(":")

    def _ParseCommand(self, args):
        if args[1] == "PRIVMSG":
            s = args[2][1]
            command = s.split()[1]
            if command in self.bot.respond.keys():
                cmd_args = args[2][1].split()
                self.bot.respond[command](cmd_args)
                return True
        return False

    def OnHello(self, args):
        if len(args) < 3:
            self._BadArgs(args)
            return
        self.SendMessage("Hello!", args[2])

class IrcBot(object):
    def __init__(self, sock, channel = "#ufpc", host = "chat.freenode.net", nick_name = "stupid_bot",
            ident = "Stupid Bot", rname = "Botty Bot"):  
        self.channel = channel
        self.host = host
        self.nick_name = nick_name
        self.ident = ident
        self.rname = rname
        self.sock = sock
        self.actions = IrcActions(self,self.sock, self.channel, self.host, self.nick_name, self.ident, self.rname)

        self.respond = {"JOIN" :        self.actions.OnJoin,
                        "MOTD command": self.actions.JoinMe,
                        "PING" :        self.actions.OnPing,
                        "QUIT" :        self.actions.OnQuit,
                        "PRIVMSG":      self.actions.OnMsg,
                        "376" :         self.actions.JoinMe,
                        "help" :        self.actions.OnHelp,
                        "creator" :     self.actions.OnCreator,
                        "quit" :        self.Quit,
                        "insult" :      self.actions.OnInsult,
                        "hello"  :      self.actions.OnHello,
                        "say"    :      self.actions.OnSay
                        }
        self.run = True

    def Identify(self):
        self.sock.send("NICK " + self.nick_name + "\r\n")
        self.sock.send("USER " + self.ident + " 0* :" + self.rname + "\r\n")

    def MainLoop(self):
        while self.run:
            resp = self.sock.recv(1024)
            print "+>>" + resp
            self._ProcessLine(resp)

    def _ProcessLine(self, line):
        if line:
            parsed = parsemsg(line)
            if parsed[1] in self.respond.keys():
               self.respond[parsed[1]](parsed)
            elif "MOTD command" in line:
                self.respond["MOTD command"](parsed)

    def Quit(self, args):
        print "ALERT QUITING"
        self.sock.send("QUIT " + "The stupid bot is shuting down.")
        self.sock.close()
        self.run = False

def main():
    HOST = "irc.freenode.net"
    PORT = 6667

    sock = socket.socket()
    sock.connect((HOST, PORT))

    bot = IrcBot(sock, "#wx-youtube", HOST, "_pybot","Botty Bot", "Botty Bot")
#    bot = IrcBot(sock)
    bot.Identify()

    bot.MainLoop()

if __name__ == "__main__":
    main()


```

---

### Post by red_Marvin on 2011-06-29
How fitting, I am currently writing an irc client for android.
However, I'm pretty sure that the nick command should be issued before joining. Iirc the 1459 rfc lists the order as nick - user - ...

---

### Post by Queue29 on 2011-06-30
> **red_Marvin said:**
> How fitting, I am currently writing an irc client for android.
However, I'm pretty sure that the nick command should be issued before joining. Iirc the 1459 rfc lists the order as nick - user - ...

Ah good catch, my sample bot did the right thing but my overview didn't!

---

### Post by Queue29 on 2011-06-30
> **JupiterV2 said:**
> Certainly an interesting challenge but I wonder if beyond the scope of "beginners?" It will require knowledge of sockets, the protocol and lexical analysis...something beyond simple learning techniques. I guess we'll see when people submit their code. =)

I think that's the cool thing about this project: to get a working bot you don't need anything more than a simple socket connection, and there are hundreds of examples on how to do that for any popular language. (And of course help can be found here as well). But once that is working, a working bot can be made with some simple string manipulation: looking for certain keywords and then generating responses appropriately, which I believe is well within the capabilities of a first year CS student. 

> interesting challenge; ensure that the testing of the bots is done in private channels.


#ufpc is a channel just for this challenge (run by my bot; there is no ChanServ) so testing is welcome there

---

### Post by schauerlich on 2011-07-03
My bot steadily grew as I began working on it... I over-engineered it for this challenge in order to be a bit more flexible should I decide to keep working on it. It spawns a new thread that runs the main loop, and outputs to a log file (./.bot.log by default). My workflow has been to tail -f .bot.log, while having the bot open in Emacs/slime. That way, I can watch the bot's output, while still being able to send commands myself (defined in irc.clj) and recompile code on the fly, so I can make changes to the code without having to disconnect and restart the bot. Very handy. :)

Anyways, here's schauerbot, written in Clojure.

[http://paste.lisp.org/display/123138](http://paste.lisp.org/display/123138)

It could certainly be improved, especially messages.clj.

Example usage: once you have clojure/swank/SLIME working, open core.clj and C-c C-k.

```
user> (ns schauerbot.core)
nil                                                                                                                     
schauerbot.core> (def irc (connect freenode ci))
#'schauerbot.core/irc                                                                                                   
schauerbot.core> (say irc "#ufpc" "Hello, world!")
Sending to:  #ufpc  <>  Hello, world!                                                                                   
nil                                                                                                                     
schauerbot.core> (quit irc)
nil                                                                                                                     
schauerbot.core> 

```

EDIT: added a leiningen project; had to exclude clojure.jar and clojure-contrib.jar for size, so make sure to run lein deps.

---

### Post by ziekfiguur on 2011-07-05
Quite an interesting challenge, though maybe a bit too much for some beginners. I had to use wireshark to sniff my own traffic to find out how ACTION works.
My version is inspired by Bucket and flyingferret from XKCD although much simpler. When nobody says anything for 5 minutes it uses the fortune command to say something random.
If anyone wants to test it, note that it's written for python3, so it will not work with the default python on ubuntu.

[PHP]
#!/usr/bin/env python3

import sys
import socket
import select
import re
import random
from time import time
from subprocess import Popen, PIPE
from optparse import OptionParser

msgexp = re.compile(r'(PING )?:(([^! ]+)(!([^@]+)@(\S+))?)( ([^:]+) :(.*))?')
#\1 = PING
#\3 = nick / server
#\5 = user
#\6 = host
#\8 = command args
#\9 = text

def runcmd(*args):
    return Popen([str(i) for i in args], stdout=PIPE).communicate()[0]

class Connection:
    def __init__(self, options):
        self.host = options.host
        self.port = int(options.port)
        self.channel = options.channel
        self.nick = options.nick
        self.ident = options.ident
        self.rname = options.rname
        self.buffer = ''
        self.sock = socket.socket()
        self.sock.connect((self.host, self.port))

    def send(self, text):
        print('<<', text)
        # encode utf-8 to binary, only necessary in python3
        self.sock.send(text.encode())

    def getline(self):
        # use a buffer so we always get a complete line and not
        # things like:
        # >> ... :adams.freenode.net 376 reallysimplebot :End of /MOTD com
        # >> mand.
        n = self.buffer.find('\r\n')
        while n == -1:
            got = self.sock.recv(1024).decode()
            if got == '':
                line = self.buffer
                self.buffer = ''
                return line
            self.buffer += got
            n = self.buffer.find('\r\n')
        line = self.buffer[:n]
        self.buffer = self.buffer[n + 2:]
        print('>>', line)
        return line

    def data_available(self, timeout=0):
        if timeout < 0:
            timeout = 0
        if len(self.buffer) > 0 or\
        self.sock.fileno() in \
            select.select([self.sock.fileno()], [], [], timeout)[0]:
            return True
        return False

    def init(self):
        self.sendnick()
        self.senduser()
        while True:
            line = self.getline()
            m = msgexp.match(line)
            if m is None:
                print("Error, expression didn't match")
            if m.group(1):
                self.sendpong()
                continue
            elif m.group(9) is not None:
                if 'VERSION' in m.group(9):
                    self.send('VERSION')
                elif 'End of /MOTD command' in m.group(9) or \
                   '376' in m.group(8):
                    break
        self.sendjoin()

    def sendnick(self, nick=None):
        if nick is None:
            nick = self.nick
        else:
            self.nick = nick
        self.send('NICK {0}\r\n'.format(nick))

    def senduser(self, ident=None, rname=None):
        if ident is None:
            ident = self.ident
        else:
            self.ident = ident
        if rname is None:
            rname = self.rname
        else:
            self.rname = rname
        self.send('USER {0} 0 * :{1}\r\n'.format(ident, rname))

    def sendjoin(self, channel=None):
        if channel is None:
            channel = self.channel
        else:
            self.channel = channel
        self.send('JOIN {0}\r\n'.format(channel))

    def sendmsg(self, text, recipient=None):
        if recipient is None:
            recipient = self.channel
        self.send('PRIVMSG {0} :{1}\r\n'.format(recipient, text))

    def sendpong(self):
        self.send('PONG {0}\r\n'.format(self.channel))

    def sendquit(self, msg='Leaving'):
        self.send('QUIT :{0}\r\n'.format(msg))

    def __iter__(self):
        while True:
            line = self.getline()
            if len(line) == 0:
                break
            yield line

class IRCbot:
    def __init__(self, options):
        self.options = options
        self.nick = options.nick
        self.owner = options.owner
        self.replydict = {}
        self.channelmsg = 'PRIVMSG ' + options.channel # for now, ignore private messages
        self.conn = Connection(options)
        self.conn.init()
        self.time = time()

    def talking_to_me(self, text, textexp):
        return re.match(r'^{0}[,:]? {1}$'.format(self.nick, textexp),
                        text)

    def reply(self, nick, text):
        if self.talking_to_me(text, r'creator\?') is not None:
            return 'I was created by Ziekfiguur'
        # this part is inspired by Bucket -- http://wiki.xkcd.com/irc/Bucket
        m = self.talking_to_me(text, r'(.*?) <([^>]+)> (.*)')
        if m is not None and (self.owner is None or self.owner == nick):
            if m.group(2) == 'action':
                self.replydict[m.group(1)] = '\x01ACTION ' + m.group(3) + '\x01'
            elif m.group(2) == 'reply':
                self.replydict[m.group(1)] = '{name}, ' + m.group(3)
            else:
                self.replydict[m.group(1)] = ' '.join(m.groups())
        # this part is inspired by flyingferret, also from #xkcd, can't find the docs
        m = self.talking_to_me(text, r'((.*) or ([^?]+))\??')
        if m is not None:
            print('choose {' + ', '.join(m.group(1).split(' or ')) + '}')
            return nick + ', ' + random.choice(m.group(1).split(' or '))

        if text.strip() in self.replydict:
            return self.replydict[text.strip()].format(name=nick)

    def random(self):
        something = runcmd('fortune', '-sn128', 'science') # replace this if you dont have the fortune command installed
        something = ' '.join(something.decode().split()) # remove unnecessary whitespace, also from in between words
        self.conn.sendmsg(something)

    def mainloop(self):
        while True:
            if self.conn.data_available(self.time + 300 - time()):
                line = self.conn.getline()
                m = msgexp.match(line)
                if m is None:
                    print("Error, expression didn't match")
                    continue
                if m.group(1):
                    self.conn.sendpong()
                    continue
                nick = m.group(3)
                if nick == self.nick: # ignore yourself
                    continue
                command = m.group(8)
                text = m.group(9)
                if command == 'JOIN':
                    self.conn.sendmsg('Welcome {0}!'.format(nick))
                    self.time = time()
                elif command == self.channelmsg:
                    if self.talking_to_me(text, '[Dd]ie!') is not None \
                       and (self.owner is None or self.owner == nick):
                        break
                    r = self.reply(nick, text)
                    if r is not None:
                        self.conn.sendmsg(r)
                    self.time = time()

            if time() > self.time + 300: # if noone joined or said anything in 5 minutes
                self.random()
                self.time = time()
        self.conn.sendquit()

def main(argv):
    parser = OptionParser()
    parser.add_option('-H', '--host', dest='host',
            help='Connect to HOST, default is chat.freenode.net',
            metavar='HOST', default='chat.freenode.net')
    parser.add_option('-p', '--port', dest='port',
            help='Connect to PORT, default is 6667',
            metavar='HOST', default='6667')
    parser.add_option('-c', '--channel', dest='channel',
            help='Join CHANNEL, default is #ufpc',
            metavar='CHANNEL', default='#ufpc')
    parser.add_option('-n', '--nick', dest='nick',
            help='use NICK, default is botz0r',
            metavar='NICK', default='botz0r')
    parser.add_option('-i', '--ident', dest='ident',
            help='use IDENT, default is guest',
            metavar='IDENT', default='guest')
    parser.add_option('-r', '--rname', dest='rname',
            help='use RNAME, default is nobody',
            metavar='RNAME', default='nobody')
    parser.add_option('-o', '--owner', dest='owner',
            help='Only listen to commands from OWNER, if this is not '
            'set, commands will be taken from everyone',
            metavar='OWNER', default=None)
    (options, args) = parser.parse_args(argv)
    try:
        int(options.port)
    except ValueError:
        print('Error, port has to be a number')
        return
    bot = IRCbot(options)
    bot.mainloop()

if __name__ == '__main__':
    main(sys.argv)
[/PHP]

---

### Post by Queue29 on 2011-07-13
I'm thinking this challenge could use another weekend for people to work on things, since that's when I see people connecting the most into #ufpc. So let's have the last day for submissions be on Tuesday, the 18th, and then I'll judge shortly thereafter. 

Does that sound good?

---

### Post by Bodsda on 2011-07-13
Yep, more time please. Still working on my submission.
 
Bodsda
 
EDIT: Not gonna get mine finished soon :(

---

### Post by Queue29 on 2011-07-31
So this challenge has been open for a while... I'll judge what's here next Monday, August 8.

---

### Post by CuracaoThe on 2011-08-05
Written in Ruby. You also can [read the source code on GitHub]("https://github.com/curacao/ubuntutasks/blob/master/lib/ubuntutasks/21_ircbot.rb") (for more convenience).

[PHP]
require 'socket'
require 'open-uri'

=begin

  Really infirm IRC bot implementation.

=end

class IRCBot

  # Initialize required parameters.
  #
  def initialize(host, port, nick, real_name, ident, channels)
    @host = host
    @port = port
    @nick = nick
    @real_name = real_name
    @ident = ident
    @channels = channels # An array of channels, which should be visited by a bot.
  end

  # Connect to server with given parameters.
  #
  def connect
    @server = TCPSocket.new(@host, @port)
    # First two messages, that every client should send to a server.
    # For more details see RFC2812.
    send "NICK #{@nick}"
    send "USER #{@ident} 0 * :#{@real_name}"

    # Join every provided channel.
    @channels.each do |channel|
      send "JOIN #{channel}"
      say channel, "#{@nick} arrived." # Welcome message.
    end
  end

  # Message interchange between client and server.
  #
  def main_loop
    loop do
      recieved_message = @server.gets
      puts recieved_message

      # Capture a channel's name, where the keywords were
      # said, to address a response to the proper channel.
      recieved_message.match(/(#\w+)/)
      channel = $1

      recieved_message.match(/:(\w+)!/) # Extract the applicant's nick.
      applicant = $1

      # Keywords handling.
      case recieved_message

        # '!help' message.
        when /:!help/ then say channel, "No way!"

        # If someone would try to talk to the bot, the latter will
        # respond to the applicant with a one of the predefined phrases.
        #
        # Example:
        #
        #   <Bob> Glitch, how are you?
        #   <Glitch> La-la-la!
        #   <Bob> Glitch: Are you stupid?
        #   <Glitch> WHAAAAT?!
        #   <Bob> Whoa! Okay-okay, could you forgive me, Glitch?
        #   <Glitch> Sure.
        #
        when /:.+[,\s]?#{@nick}[:|,|\.]/
          # Predefined replies.
          replies = ["WHAAAAT?!", "Sure.", "Yes, I know, my name is #{@nick}.",
                     "Nice to meet you. My name is #{@real_name}.", "La-la-la!",
                     "Are you sure about that, #{applicant}?"]
          # On every call, throw a random reply.
          say channel, replies.sample

        # Display some information about author of this program.
        when /:!author/
          say channel, "My master is Kirill Silin <curacaothe@gmail.com>."

        # Ability to throw something at someoglitchne.
        # 
        # Example:
        #
        #   <Bob> !throw a stone Hexadecimal
        #   <Glitch> Bob threw a stone at Hexadecimal.
        #   <Bob> !throw an egg Megabyte
        #   <Glitch> Bob threw an egg at Megabyte.
        #
        when /:!throw ((a|an) \w+) (\w+)/i
          say channel, "#{applicant} threw #{$1} at #{$3}."

        # Required for persistent connection to server.
        when /^PING :(.+)$/ then send "PONG #{$1}"
        
        # URL handling.
        #
        # Example:
        #
        #   <Bob> Guys, there is an article about us!
        #   <Bob> Check this out: http://en.wikipedia.org/wiki/ReBoot
        #   <Glitch> Title: ReBoot - Wikipedia, the free encyclopedia
        #
        when /PRIVMSG #\w+ :.*(https?:\/\/[\S]+)/
          begin
            url = open($1)
          rescue OpenURI::HTTPError => err
            puts "--> Error: #{err}"
          end

          title = url.readlines.join.match(/<title>(.+)<\/title>/)[1] rescue nil

          unless title.nil?
            message = "Title: #{title}"
            say channel, message
          end
      end
    end
  end

  # Quit from server.
  #
  def quit
    @server.close
  end

  private

  # A wrapper around existing 'send' method for more convenience.
  # 
  def send(msg)
    @server.send("#{msg}\r\n", 0)
  end

  # Say something on channel. Visible to all channel participants.
  #
  def say(channel, text)
    send "PRIVMSG #{channel} :#{text}\r\n"
  end

end

channels = %w[ #ufpc ]
bot = IRCBot.new("chat.freenode.net", 6667,
                 "GlitchIRCbot", "Unnamed Unit",
                 "Mainframe", channels)
begin
  bot.connect
  bot.main_loop
rescue Exception => err
  puts "--> Error: #{err}"
ensure
  bot.quit
end

[/PHP]

---

### Post by Queue29 on 2011-08-14
Alright, so I finally got around to judging these, and I hereby declare the winner to be.... **ziekfiguur**! and his bot, botz0r. :KS

I know this was a difficult challenge, but I am quite grateful that you guys all participated. I got all the bots working with just a tweak here and there (for compatibility issues), and it was fun experimenting with clojure and ruby, as I've never used those languages before. ziekfiguur's bot stood out in particular with solid design some pretty awesome regex matching and grouping, so congratulations!

Looking forward to the next challenge!

---

### Post by CuracaoThe on 2011-08-16
Congratulations, ziekfiguur!

It was fun to code IRC bot. Thank you, Queue29 for cool programming task.

---

### Post by ziekfiguur on 2011-08-16
@CuracaoThe Thank you!

I will try to post the next challenge somewhere this week, and i'll try to make it a bit easier than this one :)

---

### Post by kunal00731 on 2011-09-07
Hi  [ziekfiguur]("http://ubuntuforums.org/member.php?u=960698"),
Waiting for the next challenge from you.
Thanks.

---

### Post by Bodsda on 2011-09-07
> **kunal00731 said:**
> Hi [ziekfiguur]("http://ubuntuforums.org/member.php?u=960698"),
Waiting for the next challenge from you.
Thanks.
 
The new challenge has been up for a while
[http://ubuntuforums.org/showthread.php?t=1828128](http://ubuntuforums.org/showthread.php?t=1828128)
 
Bodsda

---

