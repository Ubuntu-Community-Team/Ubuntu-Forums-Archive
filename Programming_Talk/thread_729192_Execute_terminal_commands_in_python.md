---
title: "Execute terminal commands in python"
date: 2008-03-19
forum: Programming Talk
---

### Post by rob1101 on 2008-03-19
Sorry for the simple question, but how can i run terminal commands in python?

---

### Post by LaRoza on 2008-03-19
```

import os
os.system("echo 'hello world'")

```

---

### Post by rob1101 on 2008-03-19
thanks for the extremely fast reply but i have 1 more question (hopefully :P )

how would I use variables with that?

example

```

import os

x = "hello world"

os.system("echo x")

```

EDIT: On a different note is it possible to run this through the IDLE IDE? or do i have to run the script through the terminal?

---

### Post by LaRoza on 2008-03-19
> **rob1101 said:**
> thanks for the extremely fast reply but i have 1 more question (hopefully :P )

how would I use variables with that?


system() takes a string, so any string can be passed.

```

echo = "echo"
helloWorld = "Hello world"
os.system(echo + " " + helloworld)

```

It does run in IDLE, but I didn't see the results as IDLE isn't a terminal.

---

### Post by LaRoza on 2008-03-19
You can also use popen: [http://docs.python.org/lib/module-popen2.html](http://docs.python.org/lib/module-popen2.html)

---

### Post by bescritt on 2008-03-19
To get exit status you can do the following:

```
import commands
onAC_Power=True if comands.getstatus("on_ac_power")==0 else False
```

---

### Post by rob1101 on 2008-03-20
thanks for all the help guys it was just what i needed.

another question though. How would i put all of my functions into a seprate file and include them in the main program?

---

### Post by LaRoza on 2008-03-20
> **rob1101 said:**
> thanks for all the help guys it was just what i needed.

another question though. How would i put all of my functions into a seprate file and include them in the main program?

Put them in the file, put this at the top of the file that uses them:

```

import filename
#Do not type the extension!

```

---

### Post by Quikee on 2008-03-20
> **bescritt said:**
> To get exit status you can do the following:

```
import commands
onAC_Power=True if comands.getstatus("on_ac_power")==0 else False
```

umm.. minor detail but it is just enough to say:
[PHP]onAC_Power=comands.getstatus("on_ac_power") == 0[/PHP]

---

### Post by rob1101 on 2008-03-20
> **LaRoza said:**
> Put them in the file, put this at the top of the file that uses them:

```

import filename
#Do not type the extension!

```

ok thanks, i had it right but didn't know about not putting the file extension. Thats why it didn't work.

thanks everyone for the help.

---

### Post by harakiri1976 on 2008-04-08
Hi guys!


How can I get autocompletion in bash command in Python?
What I am saying is, imagine you have a script in Python and you want to select a file called file123.avi in your current working directory but you want to type it just the initial characters and TAB it just like you do it in the shell. I am trying to do that and I can't see how! :(

For instance:
```

import os

[COLOR="Red"]a = str(raw_input('Choose the file: '))[/COLOR]
b = os.getcwd()


```

...in [COLOR="Red"]a[/COLOR] I wanted to write just 2 or 3 characters of the file and then "TAB" it. Can you help me?
I also tried to import bash this way...

```

import os

a = os.system('bash')

```

But then I can't "TAB" it to chose the file :(

---

### Post by pmasiar on 2008-04-09
I don't think it is possible. And you are much better off starting own thread instead of hijacking existing one, likely unrelated to your question.

Also, you imported os, not bash -- you tried to execute bash, likely to no success?

---

### Post by bescritt on 2008-04-09
It is possible to enable completion.
Look at the readline module.

Use
```
import readline
```
and now input will use completion.

Not sure whether it supports filename completion though.

---

### Post by harakiri1976 on 2008-04-09
bestcritt....

Thank you! But [COLOR="Blue"]***readline***[/COLOR] works for completion just in Python commands. Thank you anyway!


pmasiar...


If you read back, you can see I imported [COLOR="Blue"]**os**[/COLOR] but I also "called" [COLOR="Blue"]**bash**[/COLOR]. And Python did what was supposed to do. Which was, put me in bash. If I press CTRL+D I am again in Python prompt.
Thanks anyway

---

### Post by pmasiar on 2008-04-09
I was under impression that what you want is to have bash-like filename completion in input of raw_input(). So starting bash is not a success, right? 

It is hard to guess what is your level of expertize and on what level I should answer. I probably should just say nothing, as I did not have time to do deeper research. OK, next time I will try to ignore more questions and say less. Easier life for me :-)

---

### Post by harakiri1976 on 2008-04-09
Yes, that's right! :) I wanted filename completion.
..."start bash" wasn't a success. 
No, no...any help is HELP. Thank You anyway! ;)

It's just a script to convert .FLV video to .AVI using mencoder commands. So it runs in the current working directory but the Input file (.flv Video) must be typed by hand. I was just trying to complete it with bash-like behavior. Can you see the point? :)

It works well though.
I wrote the instructions in Portuguese. I'll translate it later and post the code here...

Thanks!

---

### Post by nanotube on 2008-04-10
about executing commands, you really should use the subprocess module, which replaces os.system, popen2, commands, and all related friends. see tho documentation for it here:
[http://docs.python.org/lib/module-subprocess.html](http://docs.python.org/lib/module-subprocess.html)

---

### Post by N369 on 2008-06-29
Suppose I wanted to have a list variable that contains all the files in a given directory...

In Perl, this would be:
@files = `ls /home/user/`;

and then I could use a subscript on the array @files to access each file.

How can I do this in python?

---

### Post by nanotube on 2008-06-29
> **N369 said:**
> Suppose I wanted to have a list variable that contains all the files in a given directory...

In Perl, this would be:
@files = `ls /home/user/`;

and then I could use a subscript on the array @files to access each file.

How can I do this in python?

```
import os
fileslist = os.listdir('/home/user')
```

in general, you can look around in the documentation for os and os.path modules for a number of ways to do it. ([http://www.python.org/doc](http://www.python.org/doc))

---

### Post by eng_akyq on 2009-05-15
Dear Forum Expert
I need your help to insert a terminal command in Python for the following Python Script:

import bluetooth

print "performing inquiry..."

nearby_devices = bluetooth.discover_devices(lookup_names = True)

print "found %d devices" % len(nearby_devices)

for name, addr in nearby_devices:
    print "  %s - %s" % (addr, name)

I need after finding the bluetooth devices, the command sending a text file to them by Obexftp terminal command.

Thank you very much

---

### Post by ibuclaw on 2009-05-15
eng_akyq, you will be better off creating a thread about your problem, rather than posting in an old one that hasn't had activity in 11 months, which is considered rather taboo here. If you wish to further pursue asking your question, please do so clicking here:
[http://ubuntuforums.org/newthread.php?do=newthread&f=39](http://ubuntuforums.org/newthread.php?do=newthread&f=39)
Which will create a new thread in this forum.

Due to (now) being offtopic to the original thread question, and being inactive for so long, this thread has been closed.

Regards
Iain

---

