---
title: "Python Chating script"
date: 2016-02-08
forum: Programming Talk
---

### Post by scoutchorton on 2016-02-08
[B][U][SIZE=3]Before anyone says that this is really unnessecary or I shouldn't waste time, I just want to experience. Thank you.
[/SIZE][/U][/B][SIZE=3][SIZE=2]
So, I was working on a Python script where if you run it, you can get on at it writes to a file and then reads the file. I had a friend get on with SSH (I changed my computer's password, and they don't know the Ubuntu terminal, so I didn't worry) and start the script, and it was working, sort of.

The way I set it up was weird, and that the messages would reload when you send a message. I personally don't know how to make it test for new messages and cancel raw_input (Python 2.7.10), but if there are any other experienced users out there that know how, that would mean a lot.

Here is the code:
[/SIZE][/SIZE]```
from time import sleep
name = raw_input("What is your name: ")
print "You will go by " + name + " in the chat."
sleep(1)
print "Chat updates when you send a message."
sleep(2)
print "Send a blank message to just update it."
sleep(2)
print "Entering chat..."
sleep(2)
while True:
    r = open('chat', 'r')
    var = raw_input("Chat - " + name + ": ")
    if var != "" or var != " ":
        with open('chat', 'a') as w:
            w.write("\n" + name + ": " + var)
    else:
    True = True
    if var == "/clear":
        w = open('chat', 'w')
        w.write("")
    print "\n" * 100
    print r.read()

```

---

