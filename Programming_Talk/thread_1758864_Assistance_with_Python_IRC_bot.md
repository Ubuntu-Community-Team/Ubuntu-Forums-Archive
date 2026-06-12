---
title: "Assistance with Python IRC bot"
date: 2011-05-15
forum: Programming Talk
---

### Post by Datweakfreak on 2011-05-15
I'm writing an IRC bot in Python, and wish to implement functionality so that it echoes any message that is written in the channel.

Normally, I could write for specific messages:

```
if data.find ( 'Hiya' ) != -1:
      s.send ( 'PRIVMSG %s :%s\r\n' % (CHANNEL, 'Hiya' ))
```Now, how do I write a condition for detecting ANY string, not just 'Hiya', and echo it?

Like, if someone posts something in the channel, just re-post it.

Thanks in advance :)

---

### Post by simeon87 on 2011-05-15
Why not send the data right away?

```
s.send ( 'PRIVMSG %s :%s\r\n' % (CHANNEL, data ))
```

---

### Post by Datweakfreak on 2011-05-15
Still, I'd need a condition, right?

As in, if some data is found, return that data.

Like you said:
[B]
if data.find ( 'Hiya' ) != -1:
s.send ( 'PRIVMSG %s :%s\r\n' % (CHANNEL, data))[/B]

That would work great, but I need a condition to replace the 'Hiya' with ANY possible string. That's what I'm looking for :)

---

### Post by simeon87 on 2011-05-15
> **Datweakfreak said:**
> Still, I'd need a condition, right?

As in, if some data is found, return that data.

Like you said:
[B]
if data.find ( 'Hiya' ) != -1:
s.send ( 'PRIVMSG %s :%s\r\n' % (CHANNEL, data))[/B]

That would work great, but I need a condition to replace the 'Hiya' with ANY possible string. That's what I'm looking for :)

```
if data:
    s.send ( 'PRIVMSG %s :%s\r\n' % (CHANNEL, data))
```

---

### Post by Datweakfreak on 2011-05-15
Tried that, but doesn't work :S

The thing is, I want to be able to get whatever string is found and pass it as a parameter to another function.

Say, if the user types **Name**, I'd pass it to another function like a string inverter, which would return **emaN** and the bot would say that.

Something like:

```
if data.find(anystring):
     stringinverter.invert(anystring)
```But when I write that, it returns an error**[B]:** [/B][B]name 'anystring' is not defined
[/B]
I do get what it's trying to say, but how do I tell python that by 'anystring', I mean any string that is found?

---

### Post by simeon87 on 2011-05-15
> **Datweakfreak said:**
> Tried that, but doesn't work :S

The thing is, I want to be able to get whatever string is found and pass it as a parameter to another function.

Say, if the user types **Name**, I'd pass it to another function like a string inverter, which would return **emaN** and the bot would say that.

Something like:

```
if data.find(anystring):
     stringinverter.invert(anystring)
```But when I write that, it returns an error**[B]:** [/B][B]name 'anystring' is not defined
[/B]
I do get what it's trying to say, but how do I tell python that by 'anystring', I mean any string that is found?

Why are you searching for something in data? If data is a string then all you need to do is check whether data is not an empty string, which is what I did with ```
if data:
```

If you wish to modify data, then you can do: ```
data = f(data)
``` where f returns a modified string.

---

### Post by Datweakfreak on 2011-05-15
I understand, but if I just use, 

```
if data:
```the bot does not connect, it doesn't even return an error, it just keeps printing empty lines in the output like in an infinite loop :(

---

### Post by simeon87 on 2011-05-15
> **Datweakfreak said:**
> I understand, but if I just use, 

```
if data:
```the bot does not connect, it doesn't even return an error, it just keeps printing empty lines in the output like in an infinite loop :(

Then there may be a problem elsewhere in the design of your IRC bot. Basically the idea should be that if you get some data, then do something, otherwise, do nothing.

---

### Post by Datweakfreak on 2011-05-15
Alright, I found a solution.

```
if data.find("PRIVMSG"):
```

And then I could just parse out the contents.

Thanks a lot for your time and help! :)

---

