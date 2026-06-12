---
title: "[SOLVED] Any way sending SIGINT signal from Python?"
date: 2008-07-04
forum: Programming Talk
---

### Post by LinuX-M@n1@k on 2008-07-04
Hi, it's me again :). As some of you already know, I'm a newbie with Python.

I've created a script to connect to my modem from telnet, but sometimes telnet needs Ctrl-C to let me enter login name. I need to send that signal from my script to the telnet session.

I'm using the [pexpect](http://www.noah.org/wiki/Pexpect) module to connect to the modem.

adsl-reboot.py:
[php]#!/usr/bin/env python
#
# This script will ping to google.bg and if network is
# unreachable it will connect to the modem and reboot it.

import os
import commands
import pexpect


def adsl_reboot():
    p = pexpect.spawn('telnet 192.168.1.1')

    p.expect('Login user: ')
    p.sendline('root')    # Sending Username.

    p.expect('Password: ')
    p.sendline('password')    # Sending Password.

    p.expect('> ')
    p.sendline('reboot')    # Sending command to the shell.

    os.system('zenity --notification --text="The modem has been rebooted."')
				# Show an icon in the notification area


result = commands.getoutput("ping -c 1 google.bg")

if result.find("Unreachable") == -1:
    result = True
    print 'Connected!'
else:
    result = False
    print 'Not connected! - Rebooting the modem.'

if result == False:
    adsl_reboot()[/php]

---

### Post by days_of_ruin on 2008-07-04
Can you clarify what exactly you mean?

---

### Post by LinuX-M@n1@k on 2008-07-04
> **days_of_ruin said:**
> Can you clarify what exactly you mean?

```
$ telnet 192.168.1.1
Trying 192.168.1.1...
Connected to 192.168.1.1.
Escape character is '^]'.
ADSL Router
**Login: **

```
My script connects to the modem and waits the line "Login: ", then sends "root". But sometimes the telnet session freezes and gets only to "ADSL Router":
```
$ telnet 192.168.1.1
Trying 192.168.1.1...
Connected to 192.168.1.1.
Escape character is '^]'.
**ADSL Router**

```
"Login: " will not come until I press Ctrl-C...

My idea is to add something like this to the script:
[php]p.expect('ADSL Router\n')
p.sendline('the SIGINT signal here')[/php]

So when "ADSL Router" comes, the script will send the signal and the telnet session will display "Login: "... Therefore the script will continue.

I hope you get my idea...

---

### Post by slavik on 2008-07-04
expect should be a timeout option for expect ... that or use expect proper.

---

### Post by days_of_ruin on 2008-07-04
> **LinuX-M@n1@k said:**
> ```
$ telnet 192.168.1.1
Trying 192.168.1.1...
Connected to 192.168.1.1.
Escape character is '^]'.
ADSL Router
**Login: **

```
My script connects to the modem and waits the line "Login: ", then sends "root". But sometimes the telnet session freezes and gets only to "ADSL Router":
```
$ telnet 192.168.1.1
Trying 192.168.1.1...
Connected to 192.168.1.1.
Escape character is '^]'.
**ADSL Router**

```
"Login: " will not come until I press Ctrl-C...

My idea is to add something like this to the script:
[php]p.expect('ADSL Router\n')
p.sendline('the SIGINT signal here')[/php]

So when "ADSL Router" comes, the script will send the signal and the telnet session will display "Login: "... Therefore the script will continue.

I hope you get my idea...
Did you try adding that?

---

### Post by LinuX-M@n1@k on 2008-07-04
> **slavik said:**
> expect should be a timeout option for expect 
Sorry, I didn't get that? What do you mean?
> that or use expect proper.
How?

---

### Post by LinuX-M@n1@k on 2008-07-04
> **days_of_ruin said:**
> Did you try adding that?

It won't help me because I don't know how to send that signal... It will just send 'the SIGINT signal here'...
[php]p.expect('ADSL Router\n')
p.sendline('the SIGINT signal here')   # <- It will send that line,
                                       #      not the signal.[/php]

---

### Post by henchman on 2008-07-04
well i don't know about python but if i dont miss anything, according to that [table]("http://www.physics.udel.edu/~watson/scen103/ascii.html"), the ctrl-c command has the ascii code '3'... if there was any function like php::[chr]("http://us2.php.net/manual/en/function.chr.php"), you could perhaps send it this way..

---

### Post by geirha on 2008-07-04
I looked at the doc of pexpect. [php]p.kill(pexpect.signal.SIGINT)[/php] might work ...

---

### Post by LinuX-M@n1@k on 2008-07-04
> **geirha said:**
> I looked at the doc of pexpect. [php]p.kill(pexpect.signal.SIGINT)[/php] might work ...

Umm.. I think it kills my script :).

test.py:
[php]import os
import pexpect


def adsl_reboot():
    p = pexpect.spawn('telnet 192.168.1.1')

    p.expect ('\w+\r\n')    # Expect the new line after
                                       # the last word
    p.kill(pexpect.signal.SIGINT)

    p.expect('Login user: ')
    p.sendline('root')    # Sending Username.

    p.expect('Password: ')
    p.sendline('password')    # Sending Password.

    p.expect('> ')
#   p.sendline('reboot')    # Sending command to the shell.
    p.interact()      # Gives the control to the user.

    os.system('zenity --notification --text="The modem has been rebooted."')
				# Show an icon in the notification area.

adsl_reboot()[/php]

When I execute the script it crashes. Output:
```
$ python test.py
Traceback (most recent call last):
  File "test.py", line 31, in <module>
    adsl_reboot()
  File "test.py", line 18, in adsl_reboot
**    p.expect('Login user: ')** *### << I think here it kills my script*
  File "/usr/lib/python2.5/site-packages/pexpect.py", line 1311, in expect
    return self.expect_list(compiled_pattern_list, timeout, searchwindowsize)
  File "/usr/lib/python2.5/site-packages/pexpect.py", line 1325, in expect_list
    return self.expect_loop(searcher_re(pattern_list), timeout, searchwindowsize)
  File "/usr/lib/python2.5/site-packages/pexpect.py", line 1396, in expect_loop
    raise EOF (str(e) + '\n' + str(self))
pexpect.EOF: End Of File (EOF) in read_nonblocking(). Exception style platform.
<pexpect.spawn object at 0xb7d3104c>
version: 2.3 ($Revision: 399 $)
command: /usr/bin/telnet
args: ['/usr/bin/telnet', '192.168.1.1']
searcher: searcher_re:
    0: re.compile("Login user: ")
buffer (last 100 chars): 
before (last 100 chars): 
after: <class 'pexpect.EOF'>
match: None
match_index: None
exitstatus: None
flag_eof: True
pid: 7022
child_fd: 3
closed: False
timeout: 30
delimiter: <class 'pexpect.EOF'>
logfile: None
logfile_read: None
logfile_send: None
maxread: 2000
ignorecase: False
searchwindowsize: None
delaybeforesend: 0.05
delayafterclose: 0.1
delayafterterminate: 0.1
$ 
```
I'm not sure... probably I'm missing something.

---

### Post by geirha on 2008-07-04
Seems like it killed it allright. Try sending Ctrl+C with the send-method then.
[php]p.send(chr(3))[/php]

EDIT: As henchman already suggested in post #8. Sorry :)

---

### Post by henchman on 2008-07-04
> **geirha said:**
> Seems like it killed it allright. Try sending Ctrl+C with the send-method then.
[php]p.send(chr(3))[/php]

hey geirha, don't steal my idea :popcorn:

edit: :KS ;)

---

### Post by LinuX-M@n1@k on 2008-07-04
> **geirha said:**
> Seems like it killed it allright. Try sending Ctrl+C with the send-method then.
[php]p.send(chr(3))[/php]

Yes, Finally, Thank you!!
But where did you find these commands? I must be blind not to see them :D.

---

### Post by geirha on 2008-07-04
> **LinuX-M@n1@k said:**
> Yes, Finally, Thank you!!
But where did you find these commands? I must be blind not to see them :D.

What commands are you referring to exactly?

---

### Post by LinuX-M@n1@k on 2008-07-04
> **geirha said:**
> What commands are you referring to exactly?

p.send(chr(3))

And what does 'chr(3)' stands for? Character maybe? Where can I find more examples? It confuses me a bit. I can't understand so much things in Python...

For example: what does ```
if __name__ == '__main__':
...
``` means? I never declared '__name__' in the script (this is from another script). Where does it come from? And why should I use it? If I want it to be 'True' I would use ```
if true:
...
``` wouldn't I?

I bet that you don't even understand what I mean :)... Because I don't.

---

### Post by henchman on 2008-07-04
a good start for me (surely more noob than you :KS) would be the official documentation...

[http://docs.python.org/lib/built-in-funcs.html](http://docs.python.org/lib/built-in-funcs.html)

there is also a part about chr().


edit: found the page for __name__
[http://docs.python.org/ref/types.html]("http://docs.python.org/ref/types.html")
it always has the function name as it's value...

---

### Post by geirha on 2008-07-04
> **LinuX-M@n1@k said:**
> p.send(chr(3))

Most python modules contain documentation, so I just opened a python-shell and ran 
```

>>> import pexpect
>>> help(pexpect.spawn)

```
The dir() function is also useful. E.g. dir(p) would list all members of that object.
```

>>> import pexpect
>>> p= pexpect.spawn('cat')
>>> dir(p)
['STDERR_FILENO', 'STDIN_FILENO', ... long array or strings ... ]
>>> help(p)

```
> **LinuX-M@n1@k said:**
> 
And what does 'chr(3)' stands for? Character maybe? Where can I find more examples? It confuses me a bit. I can't understand so much things in Python...

chr is a built-in function. Get help about it by running help(chr) in a python-shell, and to get a list of all built-in functions and variables and what-not, do dir(__builtins__)

> **LinuX-M@n1@k said:**
> 
For example: what does ```
if __name__ == '__main__':
...
``` means? I never declared '__name__' in the script (this is from another script). Where does it come from? And why should I use it? If I want it to be 'True' I would use ```
if true:
...
``` wouldn't I?

I bet that you don't understand what I want to say :)... Because I don't.

__name__ is a special variable, and it will only equal '__main__' if you run the script. That means that if you import it as a module, __name__ will not equal '__main__'.

Consider this file, foo.py :
[php]
print "Always"
if __name__ == '__main__':
    print "Not always"
[/php]
Now run it normally
```
$ python foo.py
Always
Not always

```
But if you import it as a module:
```
$ python -c 'import foo'
Always

```

Did that make any sense?

---

### Post by LinuX-M@n1@k on 2008-07-04
> **geirha said:**
> Did that make any sense?

Yes, Thank you :).

I have one more question though:
```
>>> import pexpect
>>> p= pexpect.spawn('cat')
>>> dir(p)
['STDERR_FILENO',... '__class__',...  '_spawn',... 'cwd',... ]
```
Why there is STDERR_FILENO, not stderr_fileno; __class__, not class; _spawn, not spawn?

----
**@ henchman:** Thank you! ;) (And there's no way you are more noob than me :-P)

----
I sure will post more dumb questions in future :).

---

### Post by mssever on 2008-07-04
> **LinuX-M@n1@k said:**
> Why there is STDERR_FILENO, not stderr_fileno; __class__, not class; _spawn, not spawn?
Those are Python conventions. A variable in all caps indicates a constant. A variable surrounded by double underscores is magical, and one beginning with a single underscore is private. Note that these are conventions that should be followed, but that Python doesn't actually enforce them.

---

### Post by LinuX-M@n1@k on 2008-07-04
> **mssever said:**
> Those are Python conventions. A variable in all caps indicates a constant. A variable surrounded by double underscores is magical, and one beginning with a single underscore is private. Note that these are conventions that should be followed, but that Python doesn't actually enforce them.

Um... uh... okay, I think I get it... Thanks.

Can you give me some examples too?
Sorry, I do have a book about programming in Python, but I can't understand all the things I read.

---

### Post by mssever on 2008-07-04
> **LinuX-M@n1@k said:**
> Um... uh... okay, I think I get it... Thanks.

Can you give me some examples too?
Sorry, I do have a book about programming in Python, but I can't understand all the things I read.
Well, a possible example of a constant might be &#960;. You don't want to have to type 3.1415... everytime you want that value, so you set up a constant PI. You write it in all caps to remind folks that no one should assign a different value to PI.

Magical variables get their value through some means other than direct assignment. For example, __name__ is set to '__main__' if you're running the module directly. If you imported the module, __name__ has a different value. The variable __doc__ refers to the object's docstring. Python contains many magic variables. In some languages, such as Ruby and PHP (I don't know about Python), __FILE__ refers to the current filename and __LINE__ refers to the current line number.

For a discussion of what the term private means, see the documentation. You need to understand objects, inheritance, etc. in order to understand a private variable or function.

---

### Post by LinuX-M@n1@k on 2008-07-04
> **mssever said:**
> Well, a possible example of a constant might be &#960;. You don't want to have to type 3.1415... everytime you want that value, so you set up a constant PI. You write it in all caps to remind folks that no one should assign a different value to PI.

Magical variables get their value through some means other than direct assignment. For example, __name__ is set to '__main__' if you're running the module directly. If you imported the module, __name__ has a different value. The variable __doc__ refers to the object's docstring. Python contains many magic variables. In some languages, such as Ruby and PHP (I don't know about Python), __FILE__ refers to the current filename and __LINE__ refers to the current line number.

For a discussion of what the term private means, see the documentation. You need to understand objects, inheritance, etc. in order to understand a private variable or function.

Oh, now I get it! Thank you. :)

---

### Post by pmasiar on 2008-07-04
> **LinuX-M@n1@k said:**
> And what does 'chr(3)' stands for?

IMHO you are trying to bite too big a chunk of Python. Try learning basics before touching advanced stuff. Read through docs, just once, just to have idea what is there. You don't have to remember details, just recall there is something there, so you can go back and find the details.

Try your hand on solving simple problems. Solve a dozen or three of Project Euler tasks, and dig into Python Challenge. Solving those task will prepare you to solve harder tasks, and you will learn plenty of neat tricks on the way. Check also "beginner's mistakes" part of my wiki (in sig).

> I never declared '__name__' in the script

Python declared it for you - and many other time saving tricks. To be effective programmer, you may want to learn them. Try Bruce Eckel's online book draft "Thinking in Python". But you are just beginner, you may want to read more basic books first - see my wiki. "Dive into Python" might be good book for you, if you have previous programming experience, and wiki links to more online books.

Read it to save yourself time and embarrassment. You will learn more if you learn from gurus, and not from (even if valid) answers to questions you stumble during your blind wandering.

---

### Post by slavik on 2008-07-05
> **mssever said:**
> Those are Python conventions. A variable in all caps indicates a constant. A variable surrounded by double underscores is magical, and one beginning with a single underscore is private. Note that these are conventions that should be followed, but that Python doesn't actually enforce them.
looks just like C. ;)

---

### Post by ghostdog74 on 2008-07-05
> **mssever said:**
>  Python contains many magic variables. In some languages, such as Ruby and PHP (I don't know about Python), __FILE__ refers to the current filename and __LINE__ refers to the current line number.

Python does have one __file__. For __LINE__ equivalent.
```

>>> import inspect
>>> inspect.currentframe().f_lineno
1

```

---

