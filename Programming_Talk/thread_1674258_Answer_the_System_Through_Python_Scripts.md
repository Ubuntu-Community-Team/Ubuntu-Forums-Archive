---
title: "Answer the System Through Python Scripts"
date: 2011-01-23
forum: Programming Talk
---

### Post by FelipeAragao on 2011-01-23
Hi. I was wondering if there is a way to automate the input inside a (python) script that controls the system.

Example:
in order to halt the system through python, I could use the following:
```
import os
os.popen("halt")
```
But, for example, suppose I have to open a file /etc/somefile.txt inside gedit and be able to save it. Well, I'd need to use sudo:
```
os.popen("sudo gedit /etc/somefile.txt")
```
But it will ask me for my password on-the-run! And I don't want it.
How can I make the application answer that?

---

### Post by CaptainMark on 2011-01-23
I would also like to know this, if its possible in python is it possible in bash scripting too?

---

### Post by Tony Flury on 2011-01-24
The whole point of it asking you the password is security. 

If it was possible (without using sudo) for you via Python or bash (or another language) to generally circumvent the password prompt - it would be also be possible for me to hand you an executable (python script, binary etc)that used the same trick to circumvent the password and then execute "sudo rm -rf /".

You could (I think) - on your system - edit sudoers config file to allow the use of gedit without the password being prompted for your user, but it would not prompt for the password for any gedit operation. Alternatively you could allow your application to run under sudo without password prompting - again by editing the sudoers config - and then you can do a sudo <my script> from the command line - and it will run as root and not prompt for a password.

---

### Post by Cheesehead on 2011-01-24
@Tony Flury is 100% correct when he points out that trying to script workarounds to basic system security measures is very unwise.

@FelipeArago hasn't given us enough information for a useful answer. The simple answer is: Yes, it's usually possible to script things like editing in gedit, but it's generally not worth the effort. There are much easier ways to edit text from a script. There are also ways to automate system config file edits without trying to trick or defeat the security measures. What are you really trying to accomplish?

@Captainmark, there are textual or shell or pythonic or perl or or C++ or [favorite language] ways to accomplish most similar end results without trudging about through inefficient GUI applications. Which language usually isn't important - most have the right bindings/bridges/modules/functions/APIs to do whatever you want to accomplish.[PHP][/PHP]

---

### Post by FelipeAragao on 2011-01-25
Hello.
Looks like I didn't make my point clear. The whole thing about passwords and editing the text was just an example. When you manually run scripts in terminal, many times you are asked to input passwords, answers, files etc.

If we run the command "sudo gedit /etc/somefile.txt"
```

import os
os.popen("sudo gedit /etc/somefile.txt")

```
the script would, on-the-run, "lose" the control of the flow, and the command would prompt and ask me for the password.

What if I had already given my password to the program and, having it stored in the memory, it answered that?

How would i code it?

---

### Post by Tony Flury on 2011-01-25
It depends - you would want to be reading the output stream of the command, and recognise the prompt for password in that output stream, and send the password in the input stream.

In the case of something like Sudo though - I am not sure that the password prompt actually appears on Stdout or Stderr - i might be wrong though.

---

### Post by FelipeAragao on 2011-01-25
dont have to read the stream, just be able to write to it...
perhaps
```
print('*****',file=sys.stdin)
```rsrs

run the code on python interpreter and see what im saying. (the os.popen("sudo gedit /etc/somefile.txt") code)

---

### Post by Tony Flury on 2011-01-25
In your example - yes - you only need to write to stdin (since the programme you are calling only asks one question) - but if your application is more complex - reading stdout might help so you know what the application you are calling is actually asking for.

Having said that - there are so many bindings available for python, most things you might want to do can be done without resorting to calling external programms..

---

### Post by Cheesehead on 2011-01-25
'sudo' password prompting seems like an unfortunate example that has distracted from the original question: You are looking to answer *any* prompt. The answer to that is: Check any convenient search engine for 'python expect'. I haven't used expect or pexpect commands, but that seems the direction you are heading. expect/pexpect is the theoretical answer to your hypothetical question.

But when you get into the details, it may not be the best answer for each situation.

For example, an easier solution to the 'sudo' prompt dilemma is to give your script the right permissions in the first place. You can avoid all the 'sudo' silliness by having root run the (carefully tested) script instead of a user.

For another example, you could use pexpect for the login prompt on a web page...though I think that's the hard way. You could also use wget (or curl) - both have built-in ability to log in to most web pages. Most good bash utilites are meant to be run from scripts and avoid interactive prompting. Or you could use a different python toolset, base64string and urllib2, to log in faster and more securely.

---

### Post by FelipeAragao on 2011-01-25
@Cheesehead
I see what you're saying. But doesn't work. I'd have to search a lot and install lots of libraries just to switch from "sudo apt-get update" to "sudo rfkill block all".

@Tony Flury
Do you know how can I make to read and write to the stream? Even with the script stopped waiting for the input? I'll try something here anyway.

---

### Post by Tony Flury on 2011-01-25
I have never tried reading and writing to running proceses - sorry - but i do recall seeing something about being able to do it, in the sub-process module.

---

