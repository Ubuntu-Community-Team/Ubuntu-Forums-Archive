---
title: "[Python] subprocess.Popen and writing to stdin"
date: 2010-08-09
forum: Programming Talk
---

### Post by Asday on 2010-08-09
Oh my god, my "token" expired and I lost my whole post.

Short version:  Trying to write something to read from and send commands to some server software, and subprocess.Popen's pipes aren't playing well with me.  I try stdin.write(), and nothing happens, so I .close() it, and that happens to be a one time thing, so I tried .communicate() and that freezes everything.

[PHP]import time
import subprocess

srv = subprocess.Popen("java -Xmx1024M -Xms1024M -jar minecraft_server.jar",
                       stdin=subprocess.PIPE,
                       stdout=subprocess.PIPE,
                       stderr=subprocess.PIPE,
                       shell = True)

while True:
    inp = raw_input("").lower()
    if inp != "q":
        srv.stdin.write(inp)
        time.sleep(0.1)
        print(srv.stderr.readline())
    else:
        break
[/PHP]

It's meant to be used as a kind of interactive interpreter.

---

### Post by zarthon on 2010-08-11
Have you looked at this?
[http://www.minecraftforum.net/viewtopic.php?f=1012&t=23053](http://www.minecraftforum.net/viewtopic.php?f=1012&t=23053)

It looks similar to what you are doing and has some tips on how to organize the files and execute the script which might apply to what you are doing as well.

The script on that page starts in a similar way as your code
They have 
p = subprocess.Popen(args, stdin=subprocess.PIPE, stdout=subprocess.PIPE, stderr=subprocess.PIPE)

Then loop to receive information from the subprocess is controlled like this:
while(p.poll() == None):

For my own knowledge I am going to look up what subprocess.poll() is doing.

Take a look at the readline liberary for making a nice interactive command loop.

You might check out shellium.org. I believe that crew would be interested in this as well.

---

### Post by Asday on 2010-08-12
I used that script to try and understand, but it confounded me, and isn't Free, so I can't edit it myself and redistribute.

Also, I believe because of the infinite-ish loop, the OS kills it silently after a while, and all on the server time out.

Was hoping to solve that by mucking about with pygame, and events, etc.

I'll check out shellium in a short while, I'm entertaining for a half-week now.

Thanks for the help.

---

### Post by -grubby on 2010-08-12
This is the script we're using. it should help to have a working example.

[php]
#!/usr/bin/env python
# -*- coding: utf-8 -*-

import re
import subprocess

ServerArgs = ("java", "-Xmx256M", "-Xms256M", "-jar", "minecraft_server.jar", "n
ogui")
MessageRegexp = "\d\d\d\d-\d\d-\d\d \d\d:\d\d:\d\d \[\w+\] <(\w+)> (.+)"
Admins = ["ExampleGuy1", "SomeOtherGuy2"]

class Server(object):
    def __init__(self):
        self.process = subprocess.Popen(ServerArgs, stdin=subprocess.PIPE, stder
r=subprocess.PIPE)

    def monitor(self):
        while True:
            line = self.process.stderr.readline().strip()
            print line
            match = re.match(MessageRegexp, line)
            if match:
                nickname, text = match.groups()
                if text and text[0] == "!":
                    args = text[1:].split()
                    if args:
                        command = args.pop(0).lower()
                        try:
                            callback = Commands[command]
                        except KeyError:
                            self.say("No such command.")
                        else:
                            callback(self, nickname, args)

    def _write(self, text):
        print ">>>", text
        self.process.stdin.write(text + "\n")

    def say(self, msg):
        self._write("say %s" % msg)

    def give(self, player, id):
        self._write("give %s %s" % (player, id))

def Give(server, nickname, args):
    # Usage: !give [player=self] <id> [count=1]
    if nickname not in Admins:
        server.say("Permission denied.")
        return

    if len(args) == 1:
        player, id, count = nickname, args[0], 1
    elif len(args) == 2:
        try:
            count = int(args[1])
        except ValueError:
            player, id, count = args[0], args[1], 1
        else:
            player, id, count = nickname, args[0], count
    elif len(args) == 3:
        try:
            count = int(args[2])
        except ValueError:
            server.say("Invalid count (not an int).")
            return
        player, id, count = args[0], args[1], count

    for _ in xrange(count):
        server.give(player, id)

Commands = {"give": Give}

def main():
    server = Server()
    server.monitor()

if __name__ == "__main__":
    main()
[/php]

---

