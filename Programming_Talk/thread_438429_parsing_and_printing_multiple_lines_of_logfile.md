---
title: "parsing and printing multiple lines of logfile"
date: 2007-05-09
forum: Programming Talk
---

### Post by nix4me on 2007-05-09
Hi,

I am writing a python script for xchat and I am having some difficulty.

I can grep the logfile just fine, and even split the line of text.  I have the say command setup correctly and the trigger.  The problem is, it only posts 1 line of the grep.  Any ideas on how to post the rest of the lines in the grep?

Here is the code:


```
# new uploads
def uploadsinf(word, word_eol, userdata):
    newup = string.split(commands.getoutput('cat /home/nix4me/ftp.log | grep "MKD"'), '"')
    newuponly = newup[1]
    xchat.command('say %s' % newuponly)

    return xchat.EAT_ALL

# newup info command
xchat.hook_command("uploads", uploadsinf)

```

The newup line correctly splits and parses all of the lines that have MKD.
The newup line correctly stores the needed string of text of the first line in the grep from above.
The say command works for 1 line.
The hook command is the trigger.  So when i type /uploads in a irc channel, its posts the first line of the MKD grep.

But that's it, I want it to paste each instance of MKD on a separate line.

Any help would be appreciated,
nix4me

---

### Post by nix4me on 2007-05-12
bump..

---

### Post by xtacocorex on 2007-05-12
It might be easier to use popen2 for running the cat and grep commands because it creates a pipe that will shove all the data back.
```

# Needed module to import for this to work
from subprocess import *

for pkg in packages:    
    try:       
        # BUG: If the package was removed but not purged, it       
        # still appears in the output of this command.       
        # BUG SQUASHED! 10/20/2006       
        p = Popen('dpkg -s %s | grep Status | cut -d " " -f4' % (pkg), stdin = PIPE, stdout = PIPE, stderr = PIPE, close_fds = True, shell = True)       
        stdout_t, stderr_t = p.communicate()       
        retcode = p.returncode
        if retcode < 0:         
            print >>sys.stderr, "parsing failed by signal", -retcode
       else:         
            inStr = stdout_t.rstrip()         
            if inStr != "installed":             
               needed_packages.append(pkg)     
   
   except OSError, e:       
      print >>sys.stderr, "Execution failed:", e
```This code is taken from an old project of mine called Autokernel.  The code, although it doesn't return multiple lines, does get the data from STDOUT and is parseable.

I'll walk you through what it does:
1) Set p as an popen object that is going to collect the output of the grep'd dpkg -s command, the stdin, stdout, and stderr are set to PIPE so it sends data to the shell (set to TRUE) that popen can read from
2) We want the stdout and stderr data, so that is were the stdout_t, stderr_t = p.communicate() comes from, this command reads the pipes
3) Now we check the return code from the process run to see if it failed, if it does fail, we let the user know otherwise it's on to step 4
4) We passed the check so now we strip the value of stdout_t since it should just contain a line with the data we need, we rstrip the string to get rid of extra whitespace
5) We check that value with the text 'installed' to see if the package is on the system, othewise we add the name of the package to a list of packages to be installed

The try and except are there for error catching and is (evidently) good practice to include in codes like this.  I'm more of a numerical methods programmer, so writing most of this code was an adventure and took lots of trial and error with the python interactively.

I forgot the tutorial where I learned how to use popen.
Hope this helps some.

---

### Post by cwaldbieser on 2007-05-12
> **xtacocorex said:**
> It might be easier to use popen2 for running the cat and grep commands because it creates a pipe that will shove all the data back.
The subprocess module is recommended for new python programs.  It can do everything the older os.system, popen, and popen2 modules could.

---

### Post by nix4me on 2007-05-12
Are there any examples of the subprocess module?

nix4me

---

### Post by cwaldbieser on 2007-05-12
> **nix4me said:**
> Are there any examples of the subprocess module?

nix4me

[http://docs.python.org/lib/node540.html]("http://docs.python.org/lib/node540.html")

---

### Post by Ramses de Norre on 2007-05-12
**cat *file* | grep *match*** is an example of very bad use of the terminal... You should use **grep *match file*** instead.

---

### Post by nix4me on 2007-05-12
ok, i changed the format of the grep command.  It greps the file but my output to the irc command is still 1 single line.

I have no idea how to use the popopen and subprocess techniques.  I suppose I need to learn much more about python.

I thought this would be an easy task, guess not.

nix4me

---

### Post by cwaldbieser on 2007-05-13
> **nix4me said:**
> ok, i changed the format of the grep command.  It greps the file but my output to the irc command is still 1 single line.

I have no idea how to use the popopen and subprocess techniques.  I suppose I need to learn much more about python.

I thought this would be an easy task, guess not.

nix4me

```

import subprocess

command = "ls -l"
p = subprocess.Popen(command, shell=True, stdout=subprocess.PIPE)
output = p.stdout.readlines()
for line in output:
    print line,

```

Note that the readlines() method does not clip the trailing newline from each line.  That is why the print statment includes a trailing comma.

Also, since you are basically just opening a file and matching lines, it may be worth noting you could just dispense with geting the output of shell commands altogether and simply do something like:
```

f = file("/path/to/log/file", "r")
output = f.readlines()
filtered = [line for line in output if line.find("MKD") != -1]
for line in filtered:
    print line,

```

---

### Post by nix4me on 2007-05-13
That works perfectly!  Thanks so much.

Now to make it even better, i need to figure out how to split some of the text out of each line.  I should be able to figure that out hopefully.

Basically, I want to print only the text from MKD to the end of each line.  Can i use the split command on filtered and then print the result?

nix4me

---

### Post by nix4me on 2007-05-13
I got it working now.  This is how i did it:

```
#!/usr/bin/env python

__module_name__ = "ftpparse"
__module_version__ = "0.1"
__module_description__ = "System Information script for xchat, written by nix4me"

import xchat, commands, string, os

def uploadsinf(word, word_eol, userdata):

	f = file("/home/nix4me/ftp.log", "r")
	output = f.readlines()
	filtered = [line for line in output if line.find("MKD") != -1]
	for line in filtered:
		words = string.split(line)
		if len(words) >= 4:
			print words[6]
	return xchat.EAT_ALL
xchat.hook_command("uploads", uploadsinf)

print "testuploads.py loaded"
```

It parses out the column i want to show now and works very well.  This webpage has alot of good information on it: [http://www.oreilly.com/catalog/lpython/chapter/ch09.html](http://www.oreilly.com/catalog/lpython/chapter/ch09.html)

Thanks for all the help!
nix4me

---

