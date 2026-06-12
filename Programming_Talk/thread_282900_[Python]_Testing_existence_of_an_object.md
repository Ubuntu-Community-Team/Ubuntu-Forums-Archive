---
title: "[Python] Testing existence of an object"
date: 2006-10-23
forum: Programming Talk
---

### Post by mithras86 on 2006-10-23
I'm busy with [my first python project]("http://ubuntuforums.org/showthread.php?t=282873"), but I've done something in a very dirty way. I created an object, called 'connection'. When closing the program, the existence of this object has to be tested. If the object exists ("there has a connection been made"), this object should be deleted first.

I've done it with this peace of code:
```
self.connection = Connection(self.profile)
self.connected = "1"
```When the program closes, I test wheter self.connected == "1" (when the program starts, I set this veriable to "0").
But I need something like this
```
if existence(self.connection):
    print "A VPN connection is still active, need to disconnect that first"
    self.Disconnect('MainWindow')
```The Disconnect function removes my connection object. Can someone help me with this?

---

### Post by DirtDawg on 2006-10-23
A good way to test for existance is:
```
 if <object>:
    do something 
```

For example, in the interactive prompt try: 
```
 ls= [1,2]
 if ls: print "ya sure"

```
Because ls exists, the command is executed. I'm not entirely sure this addresses your problem. I hope it helps.

---

### Post by duff on 2006-10-23
```
try:
   y = x
except NameError:
   print 'x does not exists'

```

---

### Post by mithras86 on 2006-10-23
> **DirtDawg said:**
> A good way to test for existance is:
```
 if <object>:
    do something 
```For example, in the interactive prompt try: 
```
 ls= [1,2]
 if ls: print "ya sure"

```Because ls exists, the command is executed. I'm not entirely sure this addresses your problem. I hope it helps.Thanks for your reply, but I've tested it, and it doens't work when the object is destroyed:```
self.connection = Connection()
if self.connection:
    print "There is a connection made"
del self.connection
if self.connection:
    print "There is still a connection after is's deleted"
else:
    print "The connection is destroyed"
```Gives the output:```
There is a connection made
Traceback (most recent call last):
  File "gDialer.py", line 96, in Quit
    if self.connection:
AttributeError: gDialer instance has no attribute 'connection'
```So I think duff has it right:
> **duff said:**
> ```
try:
   y = x
except NameError:
   print 'x does not exists'

```For me this works:```
try:
    self.test = self.connection
except:
    print "No connection found"
else:
    print "A VPN connection is still active, need to disconnect that first"
```But then I have a final question. Could this be simplified with this:```
try:
    self.connection
except:
    print "No connection found"
else:
    print "A VPN connection is still active, need to disconnect that first"
```I tested it, and it does work, but is it correct and can I use it this way?

---

### Post by mithras86 on 2006-10-23
I have a final question: I have this piece of code:```
        print "Connecting..."
        try:
            os.system('vpnc-connect ' + self.profile + '&')
        except:
            print "No connection could be made, aborting connection attempt"
        else:
            print "Connection succesful to " + self.profile + "\n"
```But the output is this:```
Connecting...
Connection succesful to tudelft\ withpass\.conf

VPNC started in background (pid: 23085)...
```The os.system output is placed behind the else statement. I'd like to have the print message behind the os.system output. How can I handle that?

---

### Post by duff on 2006-10-23
Take off the ampersand.

---

### Post by mithras86 on 2006-10-23
> **duff said:**
> Take off the ampersand.Thanks for helping me so much! I really appreciate it :-D 

I see that the question above was not my final question, sorry ;) If someone can help me out with this, my first Python program is almost ready for use!
Like i said before, this is my function to create a connection:
```
os.system('vpnc-connect ' + self.profile)
```
Now this works when the rule *Xauth password [password]* is in your configuration. If it is not, you have to type your password in the terminal.

But how can I handle that? I cannot give a command with os.system, because the terminal waits for output... 
The command vpnc cannot have an extra argument for password, since you can only provide it in your configuration profile. But when it's not there, I have to enter the password "manually" with Python. 
Thanks in advance.

---

### Post by dabear on 2006-10-23
You could take a look at the subprocess-module in the standard library, or at pexcept:
[http://pexpect.sourceforge.net/](http://pexpect.sourceforge.net/)

---

### Post by mithras86 on 2006-10-24
> **dabear said:**
> You could take a look at the subprocess-module in the standard library, or at pexcept:
[http://pexpect.sourceforge.net/](http://pexpect.sourceforge.net/)Ok thanks. Pexpect seems to be the module i need. 
I tried it in my class, but I get a syntax error. This is my class:```
class Connection:
	def __init__(self,profile,password=None):
		import re, pexpect
		print "Connecting..."
		try:
			self.command = 'vpnc-connect ' + re.escape(profile)
			self.child = pexpect.spawn(self.command)
    			self.child.expect('password')
    			self.child.sendline (password)
		except:
			print "No connection could be made, aborting connection attempt"
		else:
			print "Connection succesful to " + profile + "
```And this is the output when I run my file:```
root@karlijn:~/Dialer# python gDialer.py
  File "gDialer.py", line 99
    self.child.expect('password')
       ^
SyntaxError: invalid syntax
root@karlijn:~/Dialer# 
```I installed the pexpect module correctly, because *print bin(self.child)* gives a list, where expect and sendline are also listen in...

---

### Post by mithras86 on 2006-10-24
Nobody an idea? I tried a lot, but unfortunately nothing worked...

---

### Post by cwaldbieser on 2006-10-24
> **mithras86 said:**
> Ok thanks. Pexpect seems to be the module i need. 
I tried it in my class, but I get a syntax error. This is my class:```
class Connection:
	def __init__(self,profile,password=None):
		import re, pexpect
		print "Connecting..."
		try:
			self.command = 'vpnc-connect ' + re.escape(profile)
			self.child = pexpect.spawn(self.command)
    			self.child.expect('password')
    			self.child.sendline (password)
		except:
			print "No connection could be made, aborting connection attempt"
		else:
			print "Connection succesful to " + profile + "
```And this is the output when I run my file:```
root@karlijn:~/Dialer# python gDialer.py
  File "gDialer.py", line 99
    self.child.expect('password')
       ^
SyntaxError: invalid syntax
root@karlijn:~/Dialer# 
```I installed the pexpect module correctly, because *print bin(self.child)* gives a list, where expect and sendline are also listen in...

Can you post the entire program (or something that we can try to run)?  The snippet you already put up looks syntactically correct, but the interpreter is complaining about syntax.

---

### Post by mithras86 on 2006-10-25
You can find the script+gladfile [here]("http://juriansluiman.nl/vpndialer.tar.gz").

---

### Post by cwaldbieser on 2006-10-25
> **mithras86 said:**
> You can find the script+gladfile [here]("http://juriansluiman.nl/vpndialer.tar.gz").

You don't have your code indented correctly.  What editor are you using?  I opened the file up in kate, and it became pretty obvious what the problem is:
```

class Connection:
	def __init__(self,profile,password=None):
		import re, pexpect
		print "Connecting..."
		self.profile = profile
		self.profile_text = open("/etc/vpnc/" + self.profile, "r").read()
		#Determine if configuration has already a password assigned 
		if re.search("Xauth\ password",self.profile_text)!=None:
			try:
				os.system("vpnc-connect " + re.escape(self.profile))
			except:
				print "Connection failed"
				vpnDialer.statusbar.new_message("Connection failed")
			else:
				print "Connection succesful to " + self.profile + "\n"
				vpnDialer.statusbar.new_message("Connection succesful to " + self.profile)
				vpnDialer.tray.set_from_stock("gtk-connect")
				vpnDialer.tray.set_tooltip("vpnDialer (connected)")
		else:
			try:
				self.command = 'vpnc-connect ' + re.escape(profile)
				self.child = pexpect.spawn(self.command)
    			self.child.expect('password')
    			self.child.sendline (password)
			except:
				print "Connection failed"
				vpnDialer.statusbar.new_message("Connection failed")
			else:
				print "Connection succesful to " + self.profile + "\n"
				vpnDialer.statusbar.new_message("Connection succesful to " + self.profile)
				vpnDialer.tray.set_from_stock("gtk-connect")
				vpnDialer.tray.set_tooltip("vpnDialer (connected)")

```
See how the last two lines in the 2nd try block are not indented to the same level as the others?  There's your syntax error.  There are some other errors, but I am guessing you will be able to take it from here.

Let us know if you have any other problems.

---

### Post by mithras86 on 2006-10-26
Ok, damn. That was very stupid. I use bluefish, but I hadn't seen it because I use tabs to indent and those two lines had one tab and some spaces. Thanks a lot!

I think it's going well now, except for one critical thing :p
When I'm creating the class, the connection is being made. I don't understand why the process is killed immediately. I tried already to release the process with self.child.interact(), but that didn't work.
How can I solve this?

---

### Post by cwaldbieser on 2006-10-26
> **mithras86 said:**
> Ok, damn. That was very stupid. I use bluefish, but I hadn't seen it because I use tabs to indent and those two lines had one tab and some spaces. Thanks a lot!

I think it's going well now, except for one critical thing :p
When I'm creating the class, the connection is being made. I don't understand why the process is killed immediately. I tried already to release the process with self.child.interact(), but that didn't work.
How can I solve this?

Sorry, I am not quite understanding the problem.  What process is killed immediately?  The python process you launched?  The subprocess you launched with pexpect?

---

### Post by mithras86 on 2006-10-27
Ok, sorry. I summarized my post a bit. This is the complete story:

I have started writing now my first program, a graphical vpn dialer for a Linux system, using pygtk. But when the password isn't provided with the configuration file, the user has to type in his password. I'm using pexpect to handle this. The code where no password is needed, works fine. Only the else clause (line #21) is my problem.

First some code. This is my class. To connect, I create this object, with a given profile and (if needed) password. Deleting the object causes the disconnection of my vpn bridge.
```
class Connection:
	def __init__(self,profile,password=None):
		import re, pexpect
		self.profile = profile
		self.profile_text = open("/etc/vpnc/" + self.profile, "r").read()
		#Determine if configuration has already a password assigned 
		if re.search("Xauth\ password",self.profile_text)!=None:
			try:
				print "Connecting without password..."
				os.system("vpnc-connect " + re.escape(self.profile))
			except:
				print "Connection failed"
				print "Deleting connection...\n"
				self.__del__
			else:
				print "Connection succesful to " + self.profile + "\n"
		else:
			try:
				print "Connecting with given password..."
				self.child = pexpect.spawn("vpnc-connect " + re.escape(profile))
				self.child.expect(".* password .*: ")
				self.child.sendline(password)
				self.child.close(False)
			except:
				print "Connection failed"
				print "Deleting connection...\n"
				self.__del__
			else:
				print "Connection succesful to " + self.profile + "\n"
	def __del__(self):
		print "Disconnecting..."
		os.system("vpnc-disconnect")
		print "Connection succesful closed from " + self.profile + "\n"
```But after line #26, the connection process is killed immediately. As you see, I tried close(False). I also left it blank (did nothing after the sendline() ). Furthermore, terminate() certainly won't work.

The thing I actually want, is that I create a (new) process ("vpnc-connect"), and the scripts goes on. Deleting the connection (==deleting the connection object) calls the vpnc-disconnect function, so the vpn connection is closed safely. But within the spawn class, I cannot detach the subprocess ("vpnc-connect") from the thread where my script is running in. 

So how can I handle it that my script get's on, and my vpn process runs normally?

---

### Post by cwaldbieser on 2006-10-28
> **mithras86 said:**
> Ok, sorry. I summarized my post a bit. This is the complete story:

I have started writing now my first program, a graphical vpn dialer for a Linux system, using pygtk. But when the password isn't provided with the configuration file, the user has to type in his password. I'm using pexpect to handle this. The code where no password is needed, works fine. Only the else clause (line #21) is my problem.

First some code. This is my class. To connect, I create this object, with a given profile and (if needed) password. Deleting the object causes the disconnection of my vpn bridge.
```
class Connection:
	def __init__(self,profile,password=None):
		import re, pexpect
		self.profile = profile
		self.profile_text = open("/etc/vpnc/" + self.profile, "r").read()
		#Determine if configuration has already a password assigned 
		if re.search("Xauth\ password",self.profile_text)!=None:
			try:
				print "Connecting without password..."
				os.system("vpnc-connect " + re.escape(self.profile))
			except:
				print "Connection failed"
				print "Deleting connection...\n"
				self.__del__
			else:
				print "Connection succesful to " + self.profile + "\n"
		else:
			try:
				print "Connecting with given password..."
				self.child = pexpect.spawn("vpnc-connect " + re.escape(profile))
				self.child.expect(".* password .*: ")
				self.child.sendline(password)
				self.child.close(False)
			except:
				print "Connection failed"
				print "Deleting connection...\n"
				self.__del__
			else:
				print "Connection succesful to " + self.profile + "\n"
	def __del__(self):
		print "Disconnecting..."
		os.system("vpnc-disconnect")
		print "Connection succesful closed from " + self.profile + "\n"
```But after line #26, the connection process is killed immediately. As you see, I tried close(False). I also left it blank (did nothing after the sendline() ). Furthermore, terminate() certainly won't work.

The thing I actually want, is that I create a (new) process ("vpnc-connect"), and the scripts goes on. Deleting the connection (==deleting the connection object) calls the vpnc-disconnect function, so the vpn connection is closed safely. But within the spawn class, I cannot detach the subprocess ("vpnc-connect") from the thread where my script is running in. 

So how can I handle it that my script get's on, and my vpn process runs normally?

I am not quite sure why your VPN connection should terminate once the "vpnc-connect" process ends.  If you run the command directly from the shell, does it return you to a shell prompt after the connection is made?  Or do you not get a shell prompt back until you end your connection?

I have only ever used "vpnc" (not "vpnc-connect"), and that command starts up a daemon in the background, so even after the process exits the connection persists until you kill the daemon.  If vpnc-connect works in a similar fashion, I'm not sure why your connection would die suddenly.

---

### Post by mithras86 on 2006-10-28
> **cwaldbieser said:**
> I am not quite sure why your VPN connection should terminate once the "vpnc-connect" process ends.  If you run the command directly from the shell, does it return you to a shell prompt after the connection is made?  Or do you not get a shell prompt back until you end your connection?

I have only ever used "vpnc" (not "vpnc-connect"), and that command starts up a daemon in the background, so even after the process exits the connection persists until you kill the daemon.  If vpnc-connect works in a similar fashion, I'm not sure why your connection would die suddenly.That is the problem ;) Using vpnc or vpnc-connect shouldn't make any difference. I tried both, but with the same result. 

It's correct that vpnc (or vpnc-connect) should starting up a daemon and bring you back to the prompt, but it doesn't! Using os.system works fine, but the pexpect module handles different, and I really don't know why the connection is broken. Does pexpect do that, is something else going wrong? The problem is that pexpect doesn't output anything. Outputting the sys.stdout doesn't provide much information...

---

### Post by cwaldbieser on 2006-10-28
> **mithras86 said:**
> That is the problem ;) Using vpnc or vpnc-connect shouldn't make any difference. I tried both, but with the same result. 

It's correct that vpnc (or vpnc-connect) should starting up a daemon and bring you back to the prompt, but it doesn't! Using os.system works fine, but the pexpect module handles different, and I really don't know why the connection is broken. Does pexpect do that, is something else going wrong? The problem is that pexpect doesn't output anything. Outputting the sys.stdout doesn't provide much information...

Hmm-- it seems that pexpect isn't really supposed to work with a process that detaches itself from the terminal.  So maybe you could do this:

Have a small pexpect script whose sole purpose is to launch vpnc-connect and force feed it the password you want.  Let's say it is called something like "vpnc-connect-passwd.py".  Then from your main program, you can just os.system("/usr/bin/python vpnc-connect-passwd.py").

That should launch vpnc-connect and feed it the password.  Later, vpnc-disconnect will terminate the connection.  The only thing I am not sure of is if the vpnc-connect process will end at that point.

---

### Post by mithras86 on 2006-10-28
I think it's going wrong when I do the sendline():
```
root@karlijn:/usr/lib/vpndialer# python
Python 2.4.4c1 (#2, Oct 11 2006, 21:51:02) 
[GCC 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import pexpect
>>> child = pexpect.spawn("vpnc-connect tudelft\ nopass.conf")
>>> child.expect(".* password .*: ")
0
>>> child.sendline("[here_my_password]")
7
```I am certainy right the password is correct. You see the sendline returns a exit code 7. What I know is that every exit code != 0 means there went something wrong. 

What happened exactly, I don't know but i have found an example [here]("http://www.jinx.com/forum/topic.asp?TOPIC_ID=53947"), where child.sendline returns an exit code 10:-k

---

### Post by cwaldbieser on 2006-10-28
> **mithras86 said:**
> I think it's going wrong when I do the sendline():
```
root@karlijn:/usr/lib/vpndialer# python
Python 2.4.4c1 (#2, Oct 11 2006, 21:51:02) 
[GCC 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import pexpect
>>> child = pexpect.spawn("vpnc-connect tudelft\ nopass.conf")
>>> child.expect(".* password .*: ")
0
>>> child.sendline("[here_my_password]")
7
```I am certainy right the password is correct. You see the sendline returns a exit code 7. What I know is that every exit code != 0 means there went something wrong. 

What happened exactly, I don't know but i have found an example [here]("http://www.jinx.com/forum/topic.asp?TOPIC_ID=53947"), where child.sendline returns an exit code 10:-k
If you do a "help(child.sendline)", it says that the return value is the number of bytes written.

---

### Post by mithras86 on 2006-10-29
But can you create a connection in python with these lines? If you can, there is something wrong with my module. Otherwise my code is wrong.

But thanks for the tip help()!

---

### Post by cwaldbieser on 2006-10-30
> **mithras86 said:**
> But can you create a connection in python with these lines? If you can, there is something wrong with my module. Otherwise my code is wrong.

But thanks for the tip help()!

I don't have a Cisco VPN server to connect to currently, or I'd try it out.  Can you get the module to work with a simple command like "bash"?  You could sendline("ls") to it and try reading the output.

There also seems to be an "interact" method that lets you work interactively for testing.

---

