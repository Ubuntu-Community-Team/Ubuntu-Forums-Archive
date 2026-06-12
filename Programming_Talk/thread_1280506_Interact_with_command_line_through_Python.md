---
title: "Interact with command line through Python"
date: 2009-10-02
forum: Programming Talk
---

### Post by peterbrewer on 2009-10-02
Hi.  I am trying to run some commands from within python such that python will automatically respond to the command line questions for me.

Effectively I want to be able to make it so when a command line asks if I want to continue or some similar question I can get Python to automatically tell it to continue.

I have mucked around with os.system and command.getoutput thought can't seem to work out how to send a response to a running command.

Any advice would be greatly appreciated.

---

### Post by A_Fiachra on 2009-10-02
I'm not clear on what you want to accomplish.

Are you thinking of a Python-esque shell?  Like some hybrid of bash and Python?  Like [this]("http://pysh.sourceforge.net/")?

Or do you have in mind a natural language interpreter written in Python?  Like a chatbot?

Or are you looking to run system commands from within a Python program interactively?

Can you give an example of some mock input and desired output?

== AF

---

### Post by peterbrewer on 2009-10-02
I'm trying to automate a process I use for setting up machines.  The process makes use of several command line tools some of which ask for user input half way through running, for example confirmation on erasing a disk before copying an image to it.

I can currently send my commands to the command line from python but I am unsure as how I would send responses to queries posed by a command line application which I interact with.

---

### Post by braddcadd on 2009-10-02
I am not sure how to do this in python but I accomplish this with a bash script.  <<END_SCRIPT starts the interactive session.  The session then enters a password twice.  If you have multiple questions that must be answered, pay close attention to the order in which they are asked and make sure the order is matched in your script. END_SCRIPT again will stop the interactive mode and go back to the bash shell.  Hope this helps.

```

htpasswd -c .htpasswd $admin1 <<END_SCRIPT
$pass1
$pass1
END_SCRIPT

```

---

### Post by unutbu on 2009-10-02
If there is a way to modify the command-line commands
so they do not need user input, that might be best. braddcadd's method is also good. However, if you'd like to do it using python, you could use the python-pexpect package.

See [http://www.palovick.com/code/python/python-ssh-client.php](http://www.palovick.com/code/python/python-ssh-client.php) for an example. 

If you install python-pexpect, you'll also find examples and documentation in /usr/share/doc/python-pexpect.

---

### Post by peterbrewer on 2009-10-02
Thanks for the responses guys, I might look into pexpect to see how it does its thing, I'd still rather use some build in python stuff.

---

### Post by spupy on 2009-10-02
> **peterbrewer said:**
> Thanks for the responses guys, I might look into pexpect to see how it does its thing, I'd still rather use some build in python stuff.

[_[COLOR="DarkRed"]Python Subprocess Module[/COLOR]_.]("http://docs.python.org/library/subprocess.html")
You can create subprocesses, control them, receive/send from standard input/output. I think it is what you need.

---

