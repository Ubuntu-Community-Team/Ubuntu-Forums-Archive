---
title: "Python - execute command without blocking"
date: 2008-12-25
forum: Programming Talk
---

### Post by tom66 on 2008-12-25
I'm trying to get the information from this:

```

	command_lines = os.system('sudo apt-get autoremove')

```

But the command blocks when it asks if I want to continue. How do I get my information in a string and then get the process to stop? Or is there another way of accessing the information I want? (the space used by packages which could be automatically removed). 

Thanks

---

### Post by Jacks0n on 2008-12-25
What do you mean it blocks? You mean it waits for the user's input? Technically you can interact with the shell using subprocess.Popen, but in your case I'd change the command to...

```
command_lines = os.system('gksudo apt-get -y autoremove')
```

This means it'll use a graphical program to get the user's password and won't hang when asking for it at the terminal. Plus the y flag means automatically say yes to whatever apt-get asks, so it'll no longer ask to confirm.

- Jackson

---

### Post by tom66 on 2008-12-25
I mean it waits for user input. I'm aware of the -y flag, it doesn't do what I need - I need to get the information, such as the size of the autoremove data, without executing the command fully. I can parse a load of text if necessary.

---

### Post by Ahadiel on 2008-12-26
AFAIK, os.system returns the PID of the command being run. You want to use os.popen
```
command_lines = os.popen("sudo apt-get -y autoremove").readlines()
```
That will make command_lines a list containing each line of the command's output.

---

### Post by tom66 on 2008-12-26
Will I be able to get the contents of the command and read it if it is waiting for user input? I'm aware of the -y flag and it doesn't do what I want in particular. What I need to do is get the line that says "After this operation, 354MB disk space will be freed", then terminate the command. Is it possible to read the lines as they come in one-by-one and then terminate on demand? Or, is there a better way of going after the data which I need - the amount of space used by autoremove data. Like using a dpkg library for python. 

Thanks.

---

### Post by Ahadiel on 2008-12-26
```
command_lines = os.popen("echo 'y' | gksudo apt-get autoremove").readlines()
```

---

### Post by nvteighen on 2008-12-26
I guess there's some way to do this using a call to the APT library.

---

### Post by imdano on 2008-12-26
I would use subprocess.Popen(), which is designed to replace os.popen().
> **tom66 said:**
> Will I be able to get the contents of the command and read it if it is waiting for user input? I'm aware of the -y flag and it doesn't do what I want in particular. What I need to do is get the line that says "After this operation, 354MB disk space will be freed", then terminate the command. Is it possible to read the lines as they come in one-by-one and then terminate on demand? Or, is there a better way of going after the data which I need - the amount of space used by autoremove data. Like using a dpkg library for python. 

Thanks.Yes.  Once you get the Popen object back you can created a loop that call readline() on the handle to stdout, which will let you read the output of the command line by line.  You can then do whatever you want based on what you read in, including writing to the process' stdin.

edit: It is probably a good idea to follow nvteighen's suggestion and see if you can get the information through calls to the libapt.  Install the python-apt package to get python bindings for it.

---

### Post by Flimm on 2008-12-27
I think you would find [pexpect](http://www.noah.org/wiki/Pexpect) useful, it allows you to control other processes as if it were a human typing in a terminal. The site has some easy to understand examples.

---

