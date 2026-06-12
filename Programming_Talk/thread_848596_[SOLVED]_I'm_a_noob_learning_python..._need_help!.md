---
title: "[SOLVED] I'm a noob learning python... need help!"
date: 2008-07-03
forum: Programming Talk
---

### Post by LinuX-M@n1@k on 2008-07-03
I'm making a script, but I need a function like 'grep'.

For example:
```

ping google.com

if ("1 packets transmitted, 1 received" exists):
    print "result1"
elif (1 packets transmitted, 0 received" exists):
    print "result2"
```

I'm making that script for 3 hours and I'm stuck here :(

Here's the idea - ping google.com, if the packet is received -> ok; if not -> reboot my adsl modem.

Please, Help me!

---

### Post by walkerk on 2008-07-03
[php]
#!/usr/bin/python


import socket

def net_test():
	print "\nTesting your network connection..."	

	try:
		s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
		s.connect(("www.google.com", 80))
		return True

	except socket.error:
		return False

if __name__ == "__main__":
	# Testing network connection
	network = net_test()
	if network == True: 
		print "Good to go"
    else:
        print "Reboot it"

[/php]

---

### Post by azzamite on 2008-07-03
I can't give a good answer with such a sort description, but

If you're working with strins, you can try somenthing with the function "find".
```
>>> 'asdf'.find('a')
0
>>> 'asdf'.find('f')
3
>>> 'asdf'.find('x')
-1
```

If you're using the function that let you execute a command, just add
the grep in there 'ping [www.google.com](www.google.com) | grep "1 received"'

---

### Post by walkerk on 2008-07-03
[PHP]
#!/usr/bin/python

import os, sys

temp = "ping www.google.com -C 3"

ping_raw = os.popen(temp)
ping_output = ping_raw.read()


if ping_output.find("bytes") != -1:
	print "network there"
else:
    print "reboot"
[/PHP]

I suggest my first option

---

### Post by days_of_ruin on 2008-07-03
```
#!/usr/bin/env python
import commands
result = commands.getoutput("ping -c 1 google.com")
if result.find("Unreachable") == -1:
   result = True
else:
   result = False

if result == False:
#restart modem

```

---

### Post by LinuX-M@n1@k on 2008-07-03
Thank you all!! I have One more thing to do:
Sometimes the telnet session to my modem freezes and needs '^]' (Ctrl-C)... Is there any possible way to send that signal from python?

---

### Post by days_of_ruin on 2008-07-03
> **walkerk said:**
> [PHP]
#!/usr/bin/python

import os, sys

temp = "ping www.google.com"

ping_raw = os.popen(temp)
ping_output = ping_raw.read()


if ping_output.find("bytes") != -1:
	print "network there"
else:
    print "reboot"
[/PHP]

I suggest my first option
This won't even work because it will ping forever.
You need to add "-c N" where N is the number of "pings" to
attempt(see my other post).

Your first one works though;)

---

### Post by walkerk on 2008-07-03
> **days_of_ruin said:**
> This won't even work because it will ping forever.
You need to add "-c N" where N is the number of "pings" to
attempt(see my other post).

Your first one works though;)

lol.. good catch :P

---

### Post by days_of_ruin on 2008-07-03
> **LinuX-M@n1@k said:**
> Thank you all!! I have One more thing to do:
Sometimes the telnet session to my modem freezes and needs '^]' (Ctrl-C)... Is there any possible way to send that signal from python?

Don't know if there is a way to do that.That would involve interaction
with a different process which can be done in python
but I have never done it.

Maybe doing "killall *nameofprocess*".
How would you signal to run that though?

EDIT:Would having your telnet session freezing make pinging google fail?
Then you could just ad that to whatever script you are using.

---

### Post by LinuX-M@n1@k on 2008-07-03
> **days_of_ruin said:**
> Don't know if there is a way to do that.That would involve interaction
with a different process which can be done in python
but I have never done it.

Maybe doing "killall *nameofprocess*".
How would you signal to run that though?

EDIT:Would having your telnet session freezing make pinging google fail?
Then you could just ad that to whatever script you are using.

Well, I can wait one minute and it will pass over that part and let me log into the modem :) Anyway... THANK YOU!! Thank you very much for the help! I'll post the final script in a minute.

Edit: No, it doesn't block the ping... It just doesn't let me log into the modem.

---

### Post by LinuX-M@n1@k on 2008-07-03
Here it is!!! My first Python script!
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
    p.sendline('GSrootaccess')    # Sending Password.

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
    adsl_reboot()


#
# This was my first script.
# Author: Boris Bolgradov
#
# Big thanks to: walkerk, days_of_ruin and Psykotik!
# http://ubuntuforums.org[/php]
[http://ubuntuforums.org/showthread.php?t=847218](http://ubuntuforums.org/showthread.php?t=847218)
[http://www.noah.org/wiki/Pexpect#Description_of_Pexpect](http://www.noah.org/wiki/Pexpect#Description_of_Pexpect)

Edit: I fixed it. Thanks LaRoza.

---

### Post by LaRoza on 2008-07-03
> **LinuX-M@n1@k said:**
> 
Edit: Oops, it's not working... I'll try to fix it myself.

Remove those braces...

---

### Post by days_of_ruin on 2008-07-03
> **LinuX-M@n1@k said:**
> Here it is!!! My first Python script! I started learning Python 4 hours ago :-P.
[php]#!/usr/bin/env python

import os
import socket
import pexpect


### BEGINNING OF THE SCRIPT: ###

def net_test():
    print "\nTesting your network connection..."    

    try:
        s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
        s.connect(("www.google.com", 80))
        return True

    except socket.error:
        return False


def adsl_reboot():
    child = pexpect.spawn('telnet 192.168.1.1')

    child.expect('Login user: ')
    child.sendline('root')    # Sending Username.

    child.expect('Password: ')
    child.sendline('password')    # Sending Password.

    child.expect('> ')
    child.sendline('reboot')    # Sending command to the shell.

    os.system('''zenity --info --text="Sorry for interrupting you,\
 Mr. Bolgradov\!\n\nI couldn\'t ping www.google.bg.\nI\'ve rebooted\
 the modem.\n\n - Linux"''') # Shows a pop-up window saying that
			     # the modem was rebooted :).


if __name__ == "__main__":
    network = net_test()    # Testing network connection.

    if network == True: 
        print "Good to go!"

    else:
        print "Rebooting it!"
        adsl_reboot()    # Rebooting the modem.



### END OF THE SCRIPT! ###
# This was my first script.
# Python ROCKS !! I love it !! :D

# Author: Boris Bolgradov

# Big thanks to: walkerk, days_of_ruin and Psykotik!
# Thank you guys! :P[/php]
[http://ubuntuforums.org/showthread.php?t=847218](http://ubuntuforums.org/showthread.php?t=847218)
[http://www.noah.org/wiki/Pexpect#Description_of_Pexpect](http://www.noah.org/wiki/Pexpect#Description_of_Pexpect)

Edit: I fixed it. Thanks LaRoza. And I also used the first method posted by walkerk (It was the only method that worked :))

Why didn't the other ways work?

---

### Post by LinuX-M@n1@k on 2008-07-03
> **days_of_ruin said:**
> Why didn't the other ways work?

I don't know they gave some strange errors.. I don't remember them exactly. Let me try them again and I'll post the errors.

> #!/usr/bin/env python

import commands

result = commands.getoutput("ping -c 1 google.com")
if result.find("Unreachable") == -1:
   result = True
else:
   result = False

**if result == False:**
   ping 'asd'
Maybe because of that second  equal sign(?) (sorry, my english is not very good and I'm sleepy)
```
$ python test.py 
  File "test.py", line 12
    ping 'asd'
             ^
SyntaxError: invalid syntax
$ 
```

----
> #!/usr/bin/python

import os, sys

**temp = "ping [www.google.com](www.google.com) -C 3"**

ping_raw = os.popen(temp)
ping_output = ping_raw.read()


if ping_output.find("bytes") != -1:
    print "network there"
else:
    print "reboot" 
Actually I'm trying this for first time since you said that it wont work because it will ping forever :).
Here -C should be -c and I think this works too.
Okay, see you tomorrow, good night... it's 3 AM here in Bulgaria ;/

---

### Post by days_of_ruin on 2008-07-03
> **LinuX-M@n1@k said:**
> I don't know they gave some strange errors.. I don't remember them exactly. Let me try them again and I'll post the errors.


Maybe because of that second  equal sign(?) (sorry, my english is not very good and I'm sleepy)
```
$ python test.py 
  File "test.py", line 12
    ping 'asd'
             ^
SyntaxError: invalid syntax
$ 
```

----

Actually I'm trying this for first time since you said that it wont work because it will ping forever :).
Here -C should be -c and I think this works too.
Okay, see you tomorrow, good night... it's 3 AM here in Bulgaria ;/
what in the world is:```
ping 'asd'
```

---

### Post by slavik on 2008-07-03
> **walkerk said:**
> [php]
#!/usr/bin/python


import socket

def net_test():
	print "\nTesting your network connection..."	

	try:
		s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
		s.connect(("www.google.com", 80))
		return True

	except socket.error:
		return False

if __name__ == "__main__":
	# Testing network connection
	network = net_test()
	if network == True: 
		print "Good to go"
    else:
        print "Reboot it"

[/php]
I am not knocking your code, but since you have 2 functions that can throw an exception, what happens when the function does return false, is it because creating a socket failed (no permission, no network card, etc.) or because it couldn't connect to [www.google.com:80](www.google.com:80) (bad DNS, can't establish connection, etc.)

Shouldn't you return the error (or in this case throw the exception up once more) instead of "Something error happen." (this actually gets returned as an error in one of the VPN software that is semi-widely used on FreeBSD.

EDIT: Please note, that I dislike exceptions in general. (They are easy to misuse, IMHO.)

---

### Post by LinuX-M@n1@k on 2008-07-04
> **days_of_ruin said:**
> what in the world is:```
ping 'asd'
```

hahahahaha! :lolflag: I'm an idiot :lol:

---

### Post by LaRoza on 2008-07-04
> **slavik said:**
> 
EDIT: Please note, that I dislike exceptions in general. (They are easy to misuse, IMHO.)

They seem worse than goto's sometimes and can be very unstructured.

---

### Post by henchman on 2008-07-04
> **LaRoza said:**
> They seem worse than goto's sometimes and can be very unstructured.

Don't you think that using Exceptions in general, code obtains more clarity?

edit: I see that they are much like goto statements, but they enable the programmer to replace many ifs and elses by only some throw / try / catch and can even contain data to transport a message.. 

otherwise you would have to use for example integer return values and every value would stand for a specific error... this sounds very much confusing..

---

### Post by LaRoza on 2008-07-04
> **henchman said:**
> Don't you think that using Exceptions in general, code obtains more clarity?
No, nothing is magical. My Fortran code is readable, because it is structured. And I have read Python code that is unreadable because it isn't structured.


> 
edit: I see that they are much like goto statements, but they enable the programmer to replace many ifs and elses by only some throw / try / catch and can even contain data to transport a message.. 
They also enable the programmer to misuse them, and feel compelled to use them to the point they are using "Expectation handling".

> 
otherwise you would have to use for example integer return values and every value would stand for a specific error... this sounds very much confusing..

Well, it can be and it cannot be. Testing for a successful return is simple in both ways (returns and exceptions), and both require a bunch of other blocks for getting individual reasons for failure.

---

### Post by pmasiar on 2008-07-04
I consider your dislike of exception irrational. It is understandable if most of your experience is in languages which lack of proper exception handling, like C, Fortran or Perl. But exceptions are exactly the structured answer on handling errors by goto (or checking return codes after each system call). They need some time to get used to, but once you do, they are natural - especially if flexible like in Python and not statically checked like in Java.

Of course you are free to develop own biases, just don't fell into the blub trap :-)

---

### Post by henchman on 2008-07-04
> No, nothing is magical. My Fortran code is readable, because it is structured. And I have read Python code that is unreadable because it isn't structured.

Well I know exceptions aren't magic :) And only because a language is newer doesn't mean it's code is _ALWAYS_ more readable. And this doesn't have to do with exceptions only. If an ape codes in python, it will be messy for sure :)

> They also enable the programmer to misuse them, and feel compelled to use them to the point they are using "Expectation handling".

You are surely right. But only because a technology can be misused, should we call the technology 'bad'? 
Thats why for example PHP is IMHO being biased as 'insecure'. Only because many 'not too experienced' people are e.g. forgetting to sanitize their variable. 

Of course a senseful use of every technology is needed, otherwise you wouldn't need the technology... and again it isn't always needed to put everything into an Exception-Box... sometimes its surely more senseful to use a simple boolean/int return value :)

edit: 

> They can be misused and that is what I dislike.

mkay, same opinion here...

---

### Post by LaRoza on 2008-07-04
> **pmasiar said:**
> I consider your dislike of exception irrational. 

Mine or slavik's?

> 
It is understandable if most of your experience is in languages which lack of proper exception handling, like C, Fortran or Perl. 
Slavik and I both use C, I mentioned Fortran, and he is a known Perl user. 

I will assume you are talking to me, although I think you may be addressing both of us, or just him.

> 
But exceptions are exactly the structured answer on handling errors by goto (or checking return codes after each system call). They need some time to get used to, but once you do, they are natural - especially if flexible like in Python and not statically checked like in Java.

I didn't say I disliked exceptions, only that they are a tad over rated and are not magical. They have the same function as checking error codes, and have their own problems. They can be misused and that is what I dislike.

> 
Of course you are free to develop own biases, just don't fell into the blub trap :-)

I am actually going to rewrite my system restore program (er..refactor, as I am just fixing the way it handles errors) using exceptions rather than error codes (actually, it just returns a tuple: True or False, Message) before releasing it. I have been able to use it for my own personal use, so if it is useful to me, it must be for others.

---

### Post by slavik on 2008-07-04
> **pmasiar said:**
> I consider your dislike of exception irrational. It is understandable if most of your experience is in languages which lack of proper exception handling, like C, Fortran or Perl. But exceptions are exactly the structured answer on handling errors by goto (or checking return codes after each system call). They need some time to get used to, but once you do, they are natural - especially if flexible like in Python and not statically checked like in Java.

Of course you are free to develop own biases, just don't fell into the blub trap :-)
then explain how to handle this:

```

def func foo()
  try:
    can_throw_exception()
    can_throw_exception_too()
  except:
    return False

if (foo() == False):
  print "An exception was thrown"

```

don't forget that exceptions are more expensive than an if statement (it's a subtraction followed by looking at the flags) and you don't even know where the error came from. What happens when can_throw_exception() allocates memory in the heap, but can_throw_exception_too() fails ... the memory is still allocated and even though the kernel will recover it when the process gets killed, whatever memory is unavailable to anyone while the process is still there (and you are probably not using it, either, which makes this even worse).

---

### Post by henchman on 2008-07-04
Iam not completely sure as it's late here and iam no 'python pro'...

but as I said before, only because one sais that exceptions are not generally evil knevil, you don't have to put everything into an "exception box"... it's like with all technologies... when you have the choice, choose the most appropriate one :)

as with your code, imho its useless to use :KS exceptions, because you transfer no data, so you could just return a bool in each function and if one of them returns false, foo returns false, too...

as i said ... /me = tired

edit: so to say: your example is not a good exception example :)


edit2: 

> What happens when can_throw_exception() allocates memory in the heap, but can_throw_exception_too() fails ... the memory is still allocated

well you would have to check your pointers and if needed, free the heap space... i don't see a difference with this issue when using exceptions / return values... and if (c++) you use autopointer, they get freed automatically...

---

### Post by slavik on 2008-07-04
> **henchman said:**
> Iam not completely sure as it's late here and iam no 'python pro'...

but as I said before, only because one sais that exceptions are not generally evil knevil, you don't have to put everything into an "exception box"... it's like with all technologies... when you have the choice, choose the most appropriate one :)

as with your code, imho its useless to use :KS exceptions, because you transfer no data, so you could just return a bool in each function and if one of them returns false, foo returns false, too...

as i said ... /me = tired

edit: so to say: your example is not a good exception example :)


edit2: 



well you would have to check your pointers and if needed, free the heap space... i don't see a difference with this issue when using exceptions / return values... and if (c++) you use autopointer, they get freed automatically...
the point is that the code is a bad example of using an exception (also look at the first reply).

don't take my code literally ...

but if you are checking the pointer, what is the point for using an exception to handle an out of memory error???

---

### Post by henchman on 2008-07-04
well, youre right. the worst point to allocate space for an exception is when you are out of memory :)

i must admit (smash me ;) ) i never checked for out of memory. i just know that c++ by default throws an std::bad_alloc exception when it's out of memory. so it somehow has to work, hasn't it? so either my brain or otherwise all c++ implementations are somehow useless.

but again its much more easy to have _few__ large try/catch-blocks catching std::bad_alloc, eg in your main loop, than always checking if the malloc function returned a NULL-ptr after every heap allocation...

---

### Post by ghostdog74 on 2008-07-04
> **slavik said:**
> 
don't forget that exceptions are more expensive than an if statement (it's a subtraction followed by looking at the flags) and you don't even know where the error came from. What happens when can_throw_exception() allocates memory in the heap, but can_throw_exception_too() fails ... the memory is still allocated and even though the kernel will recover it when the process gets killed, whatever memory is unavailable to anyone while the process is still there (and you are probably not using it, either, which makes this even worse).
i would catch the specific errors in each function themselves, can_throw_exception() and can_throw_exception_too() instead of outside, like in function foo().

---

### Post by pmasiar on 2008-07-04
> **LaRoza said:**
> I will assume you are talking to me

Both, but more to you, because you are more open to listen to my arguments :-)


> exceptions, ... are not magical. They have the same function as checking error codes, and have their own problems. They can be misused and that is what I dislike.

Anything can be misused. 

Exceptions are simpler what checking codes because
1) checking does not pollute the code
2) you can handle exceptions far from where it was detected, if that is more convenient/makes more sense.

Simple examples of exceptions are necessarily misleading - real-life code of often more convoluted. We can safely say that exceptions were added because they are useful in practical programming, not as academic exercise in the concept.


> so if it is useful to me, it must be for others.

it might but does not HAVE to :-)

---

### Post by pmasiar on 2008-07-05
> **slavik said:**
> then explain how to handle this:

How to handle bad design?

Many possibilities: Do both subroutines raise same exception type? In Python, unlike Perl, exeption can have a type (including custom type), so we can tell what happened, if we do it right.

> don't forget that exceptions are more expensive than an if statement 

In language like Python, check for exceptions happens anyway (and is fast enough), so if exception happens often, is **faster** to NOT do special test. Example:

[php]
dic = {}
# process some data

# this might be slower
if key in dic.keys():
   dic[key] += 1
else:
   dic[key] = 1

# this might be faster
try:
   dic[key] += 1
except KeyError:
   dic[key] = 1
[/php]

Why faster with exceptions? Because we **DON'T** do useless "if .. in keys()". If key exists most of the time, exception will not fire most of the time, and we avoid if.

> What happens when can_throw_exception() allocates memory in the heap, but can_throw_exception_too() fails ... the memory is still allocated 

garbage collection will sweep it if nothing refers to it, no?

---

### Post by slavik on 2008-07-05
```

#!/usr/bin/perl

#strict not used for demonstrative purposes

$var++;
print $var;

```

Since you programmed Perl, you know what the output will be and there is no need for exceptions. :)

EDIT: try catch blocks are expensive to set up, because an exception is an interrupt, not a return value. If you cannot see that a try catch block is more expensive (even if there is no exception) than a useless if statement (btw, in Perl, it a simple check "if (defined $hash{$key}) { print "key $key is defined in hash.\n" }) then you need help.

---

### Post by LaRoza on 2008-07-05
> **pmasiar said:**
> Both, but more to you, because you are more open to listen to my arguments :-)

Arguments? How many do you take? 

> 
Anything can be misused. 

Yes, but I see exceptions are being a good case for misusing widely, at least, what I see (could be just the code of new programmers getting to me though)

> 
it might but does not HAVE to :-)
Well, I was referring to the program in particular. If a system restore program which I have mocked as being useless and detrimental (and prone to spreading more ignorance about Linux) is actually useful to me, then it won't be so bad to release it.

---

### Post by LinuX-M@n1@k on 2008-07-05
Guys, I have a question - can I comment multiple lines in Python as in C (/* this is comment */) ? Or I must comment all the lines one by one ? There must be easier way to do this.

---

### Post by ghostdog74 on 2008-07-05
this is your editor's job. Otherwise, you can use """ and """

---

### Post by pmasiar on 2008-07-05
> **ghostdog74 said:**
> this is your editor's job. Otherwise, you can use """ and """

translated: most decent editors can toggle comment on whole block. If not, you can use multiline string ("""), if not assigned anywhere it is ignored.

---

### Post by days_of_ruin on 2008-07-05
> **slavik said:**
> 
EDIT: Please note, that I dislike exceptions in general. (They are easy to misuse, IMHO.)
Unlike perl of course, which is just hard to use.
:lolflag:

---

