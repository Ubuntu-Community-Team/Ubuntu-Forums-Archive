---
title: "My first Python program... Doesn’t work"
date: 2010-06-21
forum: Programming Talk
---

### Post by kevin11951 on 2010-06-21
Ok, so I needed a program that would allow me to select between two servers to ssh into (terminal based).  I decided that its time to learn Python, and I went for it.  I got the book "Byte of Python" or something like that, and tried to write the program below.  Now I basically have NO idea about anything Python, but I used a few examples, and reverse engineered this little puppy.

Here is my first go:

```

#! /usr/bin/python

import subprocess

print 'Please select which of the following servers you would like to connect to:'
print ' '
print '[1] kviero'
print '[2] www2'
print ' '
SSH1 = 1
SSH2 = 2
running = True

while running:
	select = int(raw_input('Enter an option: '))
	if select == SSH1:
		subprocess.call(['ssh -XC root@kviero.no-ip.org'])
		
	elif select == SSH2:
		subprocess.call(['ssh -XC root@10.0.0.110'])
		
	else:
		print 'Error, Invalid Option Specified'
		running = False

print 'Exiting'

```

Error is:

```

Please select which of the following servers you would like to connect to:
 
[1] kviero
[2] www2
 
Enter an option: 1
Traceback (most recent call last):
  File "ssh.py", line 17, in <module>
    subprocess.call(['ssh -XC root@kviero.no-ip.org'])
  File "/usr/lib/python2.6/subprocess.py", line 470, in call
    return Popen(*popenargs, **kwargs).wait()
  File "/usr/lib/python2.6/subprocess.py", line 623, in __init__
    errread, errwrite)
  File "/usr/lib/python2.6/subprocess.py", line 1139, in _execute_child
    raise child_exception
OSError: [Errno 2] No such file or directory

```

---

### Post by NoBugs! on 2010-06-21
"import os" and [os.system]("http://docs.python.org/library/os.html#os.system")(command), should work.

---

### Post by kevin11951 on 2010-06-21
> **NoBugs! said:**
> "import os" and [os.system]("http://docs.python.org/library/os.html#os.system")(command), should work.

That worked! Thank you so much!

---

### Post by Bachstelze on 2010-06-21
> **kevin11951 said:**
> That worked! Thank you so much!

It is generally not recommended to use os.system() if you can avoid it.

> The subprocess  module provides more powerful facilities for spawning new processes and retrieving their results; **using that module is preferable to using this function**. Use the subprocess  module. Check especially the Replacing Older Functions with the subprocess Module section.

The kosher way is

```
subprocess.call(['ssh', '-XC', 'root@kviero.no-ip.org'])
```

---

### Post by kevin11951 on 2010-06-21
> **Bachstelze said:**
> It is generally not recommended to use os.system() if you can avoid it.



The kosher way is

```
subprocess.call(['ssh', '-XC', 'root@kviero.no-ip.org'])
```

Thank you, that worked too.

any idea on how to make it so that i can type "exit" into the terminal to exit?  the "int" after "select =" is what is stopping me, but i dont know what to change it to...

---

### Post by Bachstelze on 2010-06-21
> **kevin11951 said:**
> Thank you, that worked too.

any idea on how to make it so that i can type "exit" into the terminal to exit?  the "int" after "select =" is what is stopping me, but i dont know what to change it to...

You must do it in two steps, like this:

```

#! /usr/bin/python

import subprocess

print 'Please select which of the following servers you would like to connect to:'
print ' '
print '[1] kviero'
print '[2] www2'
print ' '
SSH1 = 1
SSH2 = 2
running = True

while running:
	select = raw_input('Enter an option: ')
        if select == 'exit':
                break
        else:
                select = int(select)

	if select == SSH1:
		subprocess.call(['ssh -XC root@kviero.no-ip.org'])
		
	elif select == SSH2:
		subprocess.call(['ssh -XC root@10.0.0.110'])
		
	else:
		print 'Error, Invalid Option Specified'
		running = False

print 'Exiting'

```

Normally, you'd need some stronger input validation to make sure the user did enter an int, and not some bogus text that would make your program crash, but I guess you can get to that later.

---

### Post by wmcbrine on 2010-06-21
Just ditch the "int", and compare against '1' and '2'.

```
import subprocess

print 'Please select which of the following servers you would like to connect to:'
print ' '
print '[1] kviero'
print '[2] www2'
print ' '
SSH1 = '1'
SSH2 = '2'
running = True

while running:
    select = raw_input('Enter an option: ')
    if select == 'exit':
        running = False
    elif select == SSH1:
        subprocess.call(['ssh', '-XC', 'root@kviero.no-ip.org'])
    elif select == SSH2:
        subprocess.call(['ssh', '-XC', 'root@10.0.0.110'])
		
    else:
        print 'Error, Invalid Option Specified'
        running = False

print 'Exiting'
```

This has the added virtue of avoiding an exception if the user enters some other value.

---

### Post by kevin11951 on 2010-06-22
Ok, here is my latest "release", I think it is starting to look like an actual program!  (still technically a script though :()

Used a Pastbin for the syntax highlighting:

[http://paste.pocoo.org/show/228323/](http://paste.pocoo.org/show/228323/)

---

### Post by Tony Flury on 2010-06-22
Just a small - pythonic improvement : Why not create a list of Servers - and generate prompts off the list, and just pick data out of the list to do your connect.
That means you can ditch the if statements, and your SSH1 and SHH2 "constants"

Makes the code clearner - and makes it easier to add new servers.

---

### Post by kevin11951 on 2010-06-22
> **Tony Flury said:**
> Just a small - pythonic improvement : Why not create a list of Servers - and generate prompts off the list, and just pick data out of the list to do your connect.
That means you can ditch the if statements, and your SSH1 and SHH2 "constants"

Makes the code clearner - and makes it easier to add new servers.

Like i have said earlier, I am new to python, is there a tutorial, or at least something to get an idea about how to do that?

I do like the idea a lot though.

---

### Post by Tony Flury on 2010-06-22
> 
Like i have said earlier, I am new to python, is there a tutorial, or at least something to get an idea about how to do that?

I do like the idea a lot though.


This is an untested example.

[PHP]
import subprocess

# define a list - one entry per server - each entry is a tuple - 1st entry is the friendly name - 2nd entry is the address.

servers = [('kviero','root@kviero.no-ip.org'), ('www2', 'root@10.0.0.110') ]

print 'Please select which of the following servers you would like to connect to:'
print ' '
foreach s in servers
   print "[" + str(s.index())+1 "] " + s[0]
print "[exit]"

running = True

while running:
    select = raw_input('Enter an option: ')
    if select == 'exit':
        running = False
    else:
        # Look for a numeric input
        # Use an exception to catch any errors
        # Could either be a non numeric input
        # or a numeric input that is out of range
        try:
            select = int(select)
            subprocess.call(['ssh', '-XC', servers[select][1] )
        except:
            print 'Error, Invalid Option Specified'
            running = False

print 'Exiting'[/PHP]

An example - not tested, but you get the idea hopefully

---

### Post by Barrucadu on 2010-06-22
Here's a simple example, with error handling. It doesn't do the SSHing, only the selection of a server:

```
#!/bin/python

def getint(prompt):
    out = None

    while out is None:
        ans = raw_input(prompt + ": ")

        try:
            out = int(ans)
        except ValueError:
            print "Enter an integer."

    return out

def getfromoptions(options):
    ans = None

    print "Select an option to continue:"
    
    for i in range(0, len(options)):
        print "  [" + str(i) + "] " + options[i]

    while ans is None:
        inp = getint("Enter your choice now")

        try:
            ans = options[inp]
        except IndexError:
            print "Answer out of range."
    
    return ans

servers = {'server1' : 'host1',
           'server2' : 'host2',
           'server3' : 'host3'}

choice = getfromoptions(servers.keys())

# choice now contains the name of the server

print "You chose server " + choice + " which has hostname " + servers[choice] + "."

```

Sample output:
```
Select an option to continue:
  [0] server1
  [1] server2
  [2] server3
Enter your choice now: 7
Answer out of range.
Enter your choice now: a
Enter an integer.
Enter your choice now: 0
You chose server server1 which has hostname host1.
```

---

### Post by kevin11951 on 2010-06-22
> **Tony Flury said:**
> This is an untested example.

[PHP]
import subprocess

# define a list - one entry per server - each entry is a tuple - 1st entry is the friendly name - 2nd entry is the address.

servers = [('kviero','root@kviero.no-ip.org'), ('www2', 'root@10.0.0.110') ]

print 'Please select which of the following servers you would like to connect to:'
print ' '
foreach s in servers
   print "[" + str(s.index())+1 "] " + s[0]
print "[exit]"

running = True

while running:
    select = raw_input('Enter an option: ')
    if select == 'exit':
        running = False
    else:
        # Look for a numeric input
        # Use an exception to catch any errors
        # Could either be a non numeric input
        # or a numeric input that is out of range
        try:
            select = int(select)
            subprocess.call(['ssh', '-XC', servers[select][1] )
        except:
            print 'Error, Invalid Option Specified'
            running = False

print 'Exiting'[/PHP]

An example - not tested, but you get the idea hopefully

I like the idea, it seems easier, but I got this error:
```

  File ".ssh.py", line 31
    foreach s in servers
            ^
SyntaxError: invalid syntax
```

---

### Post by Barrucadu on 2010-06-22
I expended my little example into a full solution:

```
#!/bin/python

import subprocess

def getint(prompt, allowexit):
    out = None

    while out is None:
        ans = raw_input(prompt + ": ")

        try:
            if allowexit and ans == "exit":
                out = -1
            else:
                out = int(ans)
        except ValueError:
            print "Enter an integer."

    return out

def getfromoptions(options, allowexit=False):
    ans = None

    print "Select an option to continue:"
    
    for i in range(0, len(options)):
        print "  [" + str(i) + "] " + options[i]

    if allowexit:
        print "Or type 'exit' to quit."

    while ans is None:
        inp = getint("Enter your choice now", allowexit)

        try:
            if not inp == -1:
                ans = options[inp]
            else:
                ans = inp
        except IndexError:
            print "Answer out of range."
    
    return ans

servers = {'desktop' : 'azathoth',
           'server'  : 'eihort',
           'netbook' : 'randolph'}

choice = getfromoptions(servers.keys(), True)

if not choice == -1:
    subprocess.call(['ssh', '-XC', servers[choice]])

```

---

### Post by Tony Flury on 2010-06-22
> **kevin11951 said:**
> I like the idea, it seems easier, but I got this error:
```

  File ".ssh.py", line 31
    foreach s in servers
            ^
SyntaxError: invalid syntax
```

I did say it wasn't tested ;-)
That for loop should be : 
[PHP]
for s in servers
   print "[" + str(servers.index(s))+1 "] " + s[0] 
[/PHP]

---

### Post by wmcbrine on 2010-06-22
> **Tony Flury said:**
> I did say it wasn't tested ;-)
That for loop should be : 
[PHP]
for s in servers
   print "[" + str(servers.index(s))+1 "] " + s[0] 
[/PHP]You're still missing a colon.

Also, adding an int to a string. Followed by an unconnected string...

---

### Post by juancarlospaco on 2010-06-22
*add python 3000 compatibility and GUI *:)

---

### Post by Tony Flury on 2010-06-23
> **wmcbrine said:**
> You're still missing a colon.

Also, adding an int to a string. Followed by an unconnected string...

Very true - my excuse - Lazy typing after a successful test :-)

doh !

---

