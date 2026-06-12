---
title: "Xchat python scripting - newbie needs help"
date: 2011-08-15
forum: Programming Talk
---

### Post by b0whunter on 2011-08-15
Hi,

Im just starting to learn programming, doing a little bit of C and python. After looking at the last beginner challenge, it gave me the idea to challenge myself and write an Xchat script with python.

For starters I just wanted every CAPital letters sent through chat to be modified in small letters.

I thought of using something like [chat_string = raw_input()] to capture my input and use xchat.command to send it. But it appears that when loading a script with Xchat, it wont accept any input() by the user, giving me an unexpected EOF error.

Is there a way around this?

[EDIT]
I DID IT!!!

```
#!/usr/bin/python
__module_name__ = "CAPS STRIPPER"
__module_version__ = "1.0"
__module_description__ = "learningPYscripting"
__module_author__ = "b0whunter"
import xchat
def caps(word, word_eol, userdata):
    if len(word) < 2:
        print "Second argument mst be the message!"
    else:
        s = word_eol[1]
        s = s.replace("A", "a")
# And so on...        
        xchat.command("msg #channel %s" % s) # here you could use:
 #   (xchat.get_info("channel") to select channel your in...
          return xchat.EAT_ALL
        xchat.hook_command("caps", caps, help="/caps <message> Sends message to channel and replaces capital letters by small letters")
print "CAPS STRIPPER script loaded"
```

---

### Post by Bachstelze on 2011-08-15
There is probably a Xchat-specific mechanism to get the input, just like there is one to send lines to the chat. I can't tell you mor,e I've never done xchat scripts.

---

### Post by b0whunter on 2011-08-15
Well maybe I gave myself too much of a challenge. I found a script online of someone that translate his input into another language and I dont understand much of his code :(

---

### Post by Bachstelze on 2011-08-15
That's probably more complicated than just changing the case of the letters, though. ;) It would surprise me if that was too complicated, you just need to find out how to get the input.

---

### Post by b0whunter on 2011-08-15
Yeah I guess I need to find a simpler script to help me understand better what are the functions I'm looking for. The docs on xchat.org arent very elaborate. Im not giving up yet! :D

---

### Post by b0whunter on 2011-08-15
I think it has to do with this: 
[B]xchat.hook_command(name, callback, userdata=None, priority=PRI_NORM, help=None)
[/B]

where word and word_eol are likely what I want to modify...

aaah still lost lol

---

### Post by b0whunter on 2011-08-15
Well im finally making some sense of the docs at xchat.org! :)

```

def caps(word, word_eol, userdata):
    if len(word) < 2:
        print "Second argument mst be the message!"
    else:
        xchat.command("msg #channel %s" % word_eol[1])
    return xchat.EAT_ALL
xchat.hook_command("caps", caps, help="/caps <message> Sends message to channel")
```

Now I need to modify word_eol[1] so that caps are replaced!  :guitar:

---

### Post by Smart Viking on 2011-08-16
```
s = s.replace("A", "a")
# And so on...
```So you do that for each character in the alphabet? :P

Python have some built-in functions that can save you quite some time, you could do all that simply with:
```
s = s.lower()
```Good luck! :)

---

### Post by b0whunter on 2011-08-16
> **Smart Viking said:**
> ```
s = s.replace("A", "a")
# And so on...
```So you do that for each character in the alphabet? :P

Python have some built-in functions that can save you quite some time, you could do all that simply with:
```
s = s.lower()
```Good luck! :)

Sweet! Thank! :popcorn:

---

