---
title: "Beginners Challenge #7"
date: 2009-08-14
forum: Programming Talk
---

### Post by sdennie on 2009-08-14
Sorry for the long delay...

**Beginners Challenge #7: Write a basic bash-like shell**

The idea is to write a simple shell that behaves more or less like a normal Unix shell.

Requirements:

- You must present a prompt and take input from the keyboard
- You must support running of commands based on the $PATH environment variable
- You must support the following builtin commands: "cd" and "exit"
- You must wait for and properly cleanup any commands the shell starts
- You must inform the user if the input is an invalid command/builtin
- You must cleanly handle the case where users hit return without typing anything

Though not required, bonus points will be added for clean implementations of any of the following:

- Supporting ~/ and ~user
- Supporting proper Ctrl-C behavior
- Supporting background processes (extra bonus points for properly handling Ctrl-Z, bg, fg and jobs).
- Supporting history type functionality
- Supporting manipulation of environment variables
- Supporting pipes and redirection
- Supporting tab completion
- Supporting an rc file
- Supporting scripting functionality

Rules:

- You may use readline if you wish
- You may not use any languages/libraries that aren't in the Ubuntu repos

Judging will happen in approximately 2 weeks.  At which time I'll appoint someone to write the next challenge.

---

### Post by snova on 2009-08-15
Ok, simple Python implementation.

[PHP]
#!/usr/bin/env python
# -*- coding: utf-8 -*-

import os
import readline
import subprocess
import sys

def CD(args):
    if len(args) > 1:
        os.chdir(args[1])
    else:
        try:
            os.chdir(os.environ["HOME"])
        except KeyError:
            # This probably shouldn't happen, but after the last bug... ;)
            print "Error: No directory specified and cannot determine $HOME"

def Exit(args):
    sys.exit(int(args[1]) if len(args) > 1 and args[1].isdigit() else 0)

Builtins = {
    "cd": CD,
    "exit": Exit
    }

while True:
    try:
        line = raw_input("snova$ ")
    except EOFError:
        sys.exit()
    except KeyboardInterrupt:
        continue

    args = line.split()
    if not args:
        continue

    if args[0] in Builtins:
        Builtins[args[0]](args)
    else:
        try:
            process = subprocess.Popen(args)
        except OSError as error:
            print error
            continue

        try:
            process.wait()
        except KeyboardInterrupt:
            pass
[/PHP]

It meets all of the requirements and these two extras:

- Ctrl-C
- History (to a point; while it is available in the shell it does not persist between sessions)

---

### Post by credobyte on 2009-08-16
> **snova said:**
> Ok, simple Python implementation.

It meets all of the requirements and these two extras:

- Ctrl-C
- History (to a point; while it is available in the shell it does not persist between sessions)

```
snova$ cd
Traceback (most recent call last):
  File "./Shell.py", line 36, in <module>
    Builtins[args[0]](args)
  File "./Shell.py", line 13, in CD
    os.chdir(args[1])
IndexError: list index out of range
```

---

### Post by sdennie on 2009-08-16
> **credobyte said:**
> ```
snova$ cd
Traceback (most recent call last):
  File "./Shell.py", line 36, in <module>
    Builtins[args[0]](args)
  File "./Shell.py", line 13, in CD
    os.chdir(args[1])
IndexError: list index out of range
```

I didn't explicitly say that "cd" should mean "cd $HOME" but, it should.  The basic requirements seem very simple but, the further you delve into them, the more special cases you have to handle.  I'm not looking for a full on bash replacement in 50 lines of code but, Snova's submission is a good start.  Although, it's -10,000 bonus points for using python...  ;)

---

### Post by credobyte on 2009-08-16
> **sdennie said:**
> I didn't explicitly say that "cd" should mean "cd $HOME" but, it should.  The basic requirements seem very simple but, the further you delve into them, the more special cases you have to handle.  I'm not looking for a full on bash replacement in 50 lines of code but, Snova's submission is a good start.  Although, it's -10,000 bonus points for using python...  ;)

I wouldn't say a single word in case of an "invalid syntax" message ( let's say, it would be enough to recognize it as a command ) :) The main point was, it shouldn't end up as an *IndexError*.

---

### Post by sdennie on 2009-08-16
> **credobyte said:**
> I wouldn't say a single word in case of an "invalid syntax" message ( let's say, it would be enough to recognize it as a command ) :) The main point was, it shouldn't end up as an *IndexError*.

Haha.  Fair enough.  Bad snova!  Bad!  Minus 10,010 points!

---

### Post by lisati on 2009-08-16
> **credobyte said:**
> The main point was, it shouldn't end up as an *IndexError*.

Does snova gain extra points for not sweating it and revising the code to avoid the error?

---

### Post by sdennie on 2009-08-16
> **lisati said:**
> Does snova gain extra points for not sweating it and revising the code to avoid the error?

Yes.  snova now stands at:

- +10 points for getting the general idea down
- -10,000 points for using python
- -10 points for not handling "cd"
- +10 points for handling "cd"

That puts snova at -9990 points.  Which, it should be noted, is the highest score thus far.

---

### Post by Can+~ on 2009-08-16
> **sdennie said:**
> 
- -10,000 points for using python


And using assembly would yield +1337 points?

Y no había leído que eras de Buenos Aires :P.

---

### Post by sdennie on 2009-08-16
> **Can+~ said:**
> And using assembly would yield +1337 points?


Only if you simultaneously use the SSE and 387 instructions.  For a shell.

> 
Y no había leído que eras de Buenos Aires :P.

I'm not.  But, I play a Porteño on T.V.

---

### Post by snova on 2009-08-16
> **lisati said:**
> Does snova gain extra points for not sweating it and revising the code to avoid the error?

I wasn't here. :P

Silly me, I changed the builtins API after I wrote CD(). I'll go fix it...

---

### Post by credobyte on 2009-08-17
Let's give it a try .. Source code, binary and configuration files attached ( download, compile with g++, use ) :) Implemented simple cd, echo and history functions.

```
/* 

- Author:         credobyte [-Dainis-] @ ubuntuforums.org
- Released:        17.08.2009
- Version:        1.0.1

*/

#include <iostream> 
#include <string> 
#include <vector> 
#include <fstream> 
#include <stdlib.h> 
#include <dirent.h> 
#include <errno.h> 
 
using namespace std; 
 
vector<string> cmdhistory; 
vector<string> envtable; 
vector<string> envvar_alias; 
vector<string> envvar_path; 
string location = "~"; 
 
void SH_AcceptInput(); 
void SH_ParseInput(string input); 
void SH_LoadEnvTable(); 
void SH_LoadEnvTableVars(string path); 
void SH_ChangeDir(string dir); 
int SH_CheckDir(string dir);
void SH_ShowHistory(); 
 
int main(int argc, char *argv[]) 
{ 
    SH_LoadEnvTable();
    SH_AcceptInput();
 
    return 0;
} 
 
void SH_LoadEnvTable() 
{ 
    string line;
    string strp;
     
    ifstream configfile ("pathconf.list");
    if (configfile.is_open()) {
        while (!configfile.eof()) {
            getline(configfile, line);
            strp = line.erase(0, 6);
            envtable.push_back(strp);
        }
 
        configfile.close();
 
        for (int i = 0; i < envtable.size()-1; i++) {
            SH_LoadEnvTableVars(envtable[i]); 
        }
    } else {
        cout << "[ERROR] Environment tables can't be loaded - pathconf.list doesn't exist. \n";
        exit(0);
    }
} 
 
void SH_LoadEnvTableVars(string path) 
{ 
    DIR *dp;
    struct dirent *dirp;
 
    if ((dp = opendir(path.c_str())) == NULL) {
        cout << "[ERROR - " << errno << "] opening " << path << "\n";
        exit(0);
    }
 
    while ((dirp = readdir(dp)) != NULL) {
        envvar_alias.push_back(dirp->d_name);
        envvar_path.push_back(path);
    }
 
    closedir(dp);
} 
 
void SH_AcceptInput() 
{ 
    char user_input[1024];
 
    cout << "shell:" << location << "$ ";
    cin.getline(user_input, 1024);
 
    SH_ParseInput(user_input);
    SH_AcceptInput();
} 
 
void SH_ParseInput(string input) 
{
    if (input.length() <= 0) {
        SH_AcceptInput();
        return;
    }
    
    cmdhistory.push_back(input);
 
    if (input == string("exit")) {
        exit(0);
    } else if (input.find("cd") <= 0) {
        string new_location = input.erase(0, 3); 
        if (SH_CheckDir(new_location) == 1) { 
            SH_ChangeDir(new_location); 
        } else { 
            cout << "Directory doesn't exist! \n"; 
        } 
        return; 
    } else if (input == string("history")) {
        SH_ShowHistory();
    } else {
        // check for environment commands
        for (int i = 0; i < envvar_alias.size(); i++) {
            if (input.find(envvar_alias[i]) <= 0) { 
                string cmd = envvar_path[i] + "/" + envvar_alias[i];
                string cmdargs = input.erase(0, envvar_alias[i].length());
                  string fullcmd = cmd + " " + cmdargs;
                system(fullcmd.c_str()); 
                return; 
            } 
        }
 
        cout << "Command not found!\n";
    }
} 
 
void SH_ChangeDir(string dir) 
{ 
    location = dir;
    chdir(dir.c_str()); 
} 
 
int SH_CheckDir(string dir) { 
    bool found = false; 
    DIR* directory; 
 
    directory = opendir(dir.c_str()); 
    if (directory) { 
        found = true; 
    } else { 
        found = false; 
    } 
 
    closedir(directory); 
    return found; 
}

void SH_ShowHistory()
{
    for (int i = 0; i < cmdhistory.size(); i++) {
        cout << i << ": " << cmdhistory[i] << endl;
    }
}
```

---

### Post by sdennie on 2009-08-23
This challenge seems to be stagnating so, I'll post a simple perl solution as both a bump and an example of just how easy the problem is:

```

#!/usr/bin/perl

_((_).(_).(_));     while(<>){chomp;    s}^\s*(.+)}$1}g;    _(_),
,next     if!(~     ~$_);               split      ?\s+?    ;;$_=     
shift     @_;;;     /cd/g               ?(42,      chdir    @_[(_
)]||_exit_("$_"     .qq?\x3A\x20@_?,    $!)):?exit??exit    @_[0+
sqrt(               13+(2               *8-sqrt             (169)
))-!!               sqrt(               256)]  :fork?       wait:
$wait               ?(_):(exec $_,@_    or(1)   ,_exit_(    $_,$!),{_},exit

);sub _{(_)?print qq/\x3E\x20/:exit}sub _exit_ {s__exit__exit_ or exit;print 
qq/\x70\x6c\x73\x68\x3A\x20$_[0]\x3A\x20$_[1]\n/; }_(____)unless(_)};reverse

```

---

### Post by jacksaff on 2009-08-23
You can do this in Perl with just a four letter word? Wow!

---

### Post by Lux Perpetua on 2009-08-23
> **jacksaff said:**
> You can do this in Perl with just a four letter word? Wow!I can do it with a four-letter word: ```
bash
```It's a shell script.

---

### Post by cmay on 2009-08-23
> **sdennie said:**
> This challenge seems to be stagnating so, I'll post a simple perl solution as both a bump and an example of just how easy the problem is:

```

#!/usr/bin/perl

_((_).(_).(_));     while(<>){chomp;    s}^\s*(.+)}$1}g;    _(_),
,next     if!(~     ~$_);               split      ?\s+?    ;;$_=     
shift     @_;;;     /cd/g               ?(42,      chdir    @_[(_
)]||_exit_("$_"     .qq?\x3A\x20@_?,    $!)):?exit??exit    @_[0+
sqrt(               13+(2               *8-sqrt             (169)
))-!!               sqrt(               256)]  :fork?       wait:
$wait               ?(_):(exec $_,@_    or(1)   ,_exit_(    $_,$!),{_},exit

);sub _{(_)?print qq/\x3E\x20/:exit}sub _exit_ {s__exit__exit_ or exit;print 
qq/\x70\x6c\x73\x68\x3A\x20$_[0]\x3A\x20$_[1]\n/; }_(____)unless(_)};reverse

```

There is a assignment in the minix book to write a basic shell from a skeleton proved in the  text. and a small example of a shell in the book Advanced programming in the unix environment. i have already played around with the minix 3 book assignement but it does not yet meet the requements for this challenge. it dont do cdhdir . or exit .it just forks.  if i can write a better version wihtin the time limit of this challenge i will try if i have time. how long is the challenge up for ?

---

### Post by sdennie on 2009-08-23
> **cmay said:**
> how long is the challenge up for ?

Until Friday.

---

### Post by JordyD on 2009-08-23
> **sdennie said:**
> This challenge seems to be stagnating so, I'll post a simple perl solution as both a bump and an example of just how easy the problem is:

```

#!/usr/bin/perl

_((_).(_).(_));     while(<>){chomp;    s}^\s*(.+)}$1}g;    _(_),
,next     if!(~     ~$_);               split      ?\s+?    ;;$_=     
shift     @_;;;     /cd/g               ?(42,      chdir    @_[(_
)]||_exit_("$_"     .qq?\x3A\x20@_?,    $!)):?exit??exit    @_[0+
sqrt(               13+(2               *8-sqrt             (169)
))-!!               sqrt(               256)]  :fork?       wait:
$wait               ?(_):(exec $_,@_    or(1)   ,_exit_(    $_,$!),{_},exit

);sub _{(_)?print qq/\x3E\x20/:exit}sub _exit_ {s__exit__exit_ or exit;print 
qq/\x70\x6c\x73\x68\x3A\x20$_[0]\x3A\x20$_[1]\n/; }_(____)unless(_)};reverse

```

That's scary. And it actually works.

---

### Post by pepperphd on 2009-08-23
> **JordyD said:**
> That's scary. And it actually works.

I think I was just convinced to never learn Perl.

---

### Post by sdennie on 2009-08-23
> **pepperphd said:**
> I think I was just convinced to never learn Perl.

Naaa.  The original code is perfectly readable.  I just posted the product of a bored perl hacker with too much time on his hands.

```

#!/usr/bin/perl

use strict;

prompt();
while(<>)
{
    chomp;
    s/^\s+//;

    prompt(), next unless $_;

    split /\s+/;
    $_ = shift @_;

    /cd/   ? (chdir @_[0] or error("$_: @_", $!)) :
    /exit/ ? exit @_[0] :
    fork   ? wait : (exec $_, @_ or error($_, "Invalid command"), exit);
    
    prompt();
}

sub prompt { print "> " }
sub error { print "plsh: $_[0]: $_[1]\n"; }

```

---

### Post by pepperphd on 2009-08-23
Is this too cheap to count? I think it meets all the reqs plus a kind of history ( you have to enter "hist" ). And because it just throws your input to sh, it also supports pipes and redirection.  Yeah pretty cheap.

EDIT: **IMPORTANT: **You cannot run this from the interpreter or cd won't work.  Try instead compiling/chmod'ing it.

[php]#! /usr/bin/env python

import os

def prompt():
    user = os.environ['USER']
    cdir =  os.getcwd()[os.getcwd().rfind("/") + 1:]
    return user + ":" + cdir + "~$ "


command = ""
history = []
while command != "exit":
    command = raw_input(prompt())
    history.append(command)
    if command.startswith("cd"):
        if len(command) > 2:
            try:
                os.chdir(command[3:])
            except OSError:
                print command[3:] + " not found"
                del history[len(history) -1]
        else:
            os.chdir(os.environ['HOME'])
    elif command == "hist":
        for entry in history:
            print entry
    else:
        if os.system(command) == 32512: #bash returns this on failure
            del history[len(history) -1][/php]

---

### Post by credobyte on 2009-08-23
> **sdennie said:**
> Naaa.  The original code is perfectly readable.  I just posted the product of a bored perl hacker with too much time on his hands.

```

#!/usr/bin/perl

use strict;

prompt();
while(<>)
{
    chomp;
    s/^\s+//;

    prompt(), next unless $_;

    split /\s+/;
    $_ = shift @_;

    /cd/   ? (chdir @_[0] or error("$_: @_", $!)) :
    /exit/ ? exit @_[0] :
    fork   ? wait : (exec $_, @_ or error($_, "Invalid command"), exit);
    
    prompt();
}

sub prompt { print "> " }
sub error { print "plsh: $_[0]: $_[1]\n"; }

```

Still pretty scary ( first example looked like Java class file opened with a text editor :D ) 8-[

---

### Post by cmay on 2009-08-23
> **sdennie said:**
> Until Friday.
sounds good. :) i

---

### Post by Frak on 2009-08-23
> **sdennie said:**
> This challenge seems to be stagnating so, I'll post a simple perl solution as both a bump and an example of just how easy the problem is:

```

#!/usr/bin/perl

_((_).(_).(_));     while(<>){chomp;    s}^\s*(.+)}$1}g;    _(_),
,next     if!(~     ~$_);               split      ?\s+?    ;;$_=     
shift     @_;;;     /cd/g               ?(42,      chdir    @_[(_
)]||_exit_("$_"     .qq?\x3A\x20@_?,    $!)):?exit??exit    @_[0+
sqrt(               13+(2               *8-sqrt             (169)
))-!!               sqrt(               256)]  :fork?       wait:
$wait               ?(_):(exec $_,@_    or(1)   ,_exit_(    $_,$!),{_},exit

);sub _{(_)?print qq/\x3E\x20/:exit}sub _exit_ {s__exit__exit_ or exit;print 
qq/\x70\x6c\x73\x68\x3A\x20$_[0]\x3A\x20$_[1]\n/; }_(____)unless(_)};reverse

```
Now, write one that makes toast.

I'm hungry!

---

### Post by exutable on 2009-08-26
Hey guys,

here is my python 3 solution, couldn't find a way to take keyboard events in console(don't think it's possible), so the history command is history [index] in the history list.  I also included my grep from the last challenge for fun :)

shell.py
```
#! /usr/bin/python3

import sys, os, grep

commands = ["cd", "exit", "grep", "history"]
history = []
currentdir = os.environ["HOME"]

def prompt():
	try:
		command = str(input(currentdir+">"))
		breakdown = command.split()
		if breakdown[0] not in commands:
			print("Sorry", breakdown[0], "is not a valid command")
		else:
			history.append(command)
			analyzecommand(breakdown)
	except IndexError as err:
		prompt()

def analyzecommand(commandinlist):
	global currentdir, history
	comlength = len(commandinlist)
	if commandinlist[0] == "cd":
			if comlength == 1:
				currentdir = os.environ["HOME"]
			elif comlength == 2:
				if os.path.isdir(commandinlist[1]):
					currentdir = commandinlist[1]
				else:
					print("Sorry can't locate directory")
			else:
				print("Sorry, the proper usage of cd is cd [dir]")
	elif commandinlist[0] == "exit":
		if commandinlist[1]:
			sys.exit()
		else:
			print("exit takes zero parameters, so please just type exit")
	elif commandinlist[0] == "grep":
		if comlength == 3:
			grep.main(commandinlist[1], commandinlist[2], currentdir)
		else:
			print("Sorry but grep takes 2 parameters, grep [word] [dir]")
	elif commandinlist[0] == "history":
		if comlength == 1:
			print(history)
		elif comlength == 2:
			try:
				analyzecommand(history[int(commandinlist[1])].split())
			except IndexError:
				print("Sorry that's out of the index of the history list")
				print(history)
			except ValueError:
				print("Sorry but the history command only takes ints")

def main():
	while True:
		prompt()
		
main()

```

grep.py
```
#! /usr/bin/python3

import sys


def main(searchword, file, dir):	
	
	try:	
		fopen = open(dir+file, "r")

		for i, line in enumerate(fopen):
			if searchword in line:
				print("line", str(i+1)+':', line.strip())
	
	except IOError as err:
		print(err, "Sorry can't find the file")


```

execute with python3

---

### Post by Can+~ on 2009-08-26
@Exutable

[PHP]	elif commandinlist[0] == "exit":
		...
	elif commandinlist[0] == "grep":
		...
	elif commandinlist[0] == "history":
		...[/PHP]

That's C's switch-casing. You can make it more efficient (and ordered) with a dictionary and functions

[PHP]#!/usr/bin/env python

def cmd_exit(*args, **kargs):
	# do stuff here
	pass
	
def cmd_grep(*args, **kargs):
	# do stuff here
	pass

def cmd_history(*args, **kargs):
	# do stuff here
	pass

# Function Dictionary
commandlist = {
	"exit" : cmd_exit
	"grep" : cmd_grep
	"history" : cmd_history
}

# Usage
commandlist[commnad[0]](...)
[/PHP]

---

### Post by exutable on 2009-08-26
I definitely see how that is more efficient but I'm not sure I get the implemenation.

How would I handle the extra parameters? Like that method is MUCH better but how do I check if they enter too many parameters or what they enter as parameters?

---

### Post by pepperphd on 2009-08-26
> **Can+~ said:**
> ]That's C's switch-casing. You can make it more efficient (and ordered) with a dictionary and functions

Actually, I'm pretty sure that the if/elif/else format is more efficient for switches in Python than dictionaries.  The reason is that the interpreter will stop on the first if/elif that evaluates to true, while it will check every condition in the dictionary.

---

### Post by Can+~ on 2009-08-26
> **pepperphd said:**
> Actually, I'm pretty sure that the if/elif/else format is more efficient for switches in Python than dictionaries.  The reason is that the interpreter will stop on the first if/elif that evaluates to true, **while it will check every condition in the dictionary**.

Not sure what you mean by **that**.

[http://www.python.org/doc/faq/general/#how-are-dictionaries-implemented](http://www.python.org/doc/faq/general/#how-are-dictionaries-implemented)

Hashes are structures that provide O(1) access time, as it's implemented as a function.

> **pepperphd said:**
> How would I handle the extra parameters? Like that method is MUCH better but how do I check if they enter too many parameters or what they enter as parameters?

You can define a limited number of arguments to all functions (easy), pack all inside a list/dict/tuple (easy, but redundant), or you can accept a tuple (for normal argument) and a dictionary (for x=y arguments).

For example

[PHP]#!/usr/bin/env python

def multipleargs(*args, **kwargs):
	print "Args:", args
	print "Kwargs:", kwargs

multipleargs(2, 5, 3.4, "hello", x="y", y=10)[/PHP]

---

### Post by pepperphd on 2009-08-26
> **Can+~ said:**
> Not sure what you mean by **that**.

I thought I'd read somewhere that using a dictionary instead of if/elif/else was less efficient.  Thanks for clearing that up.

---

### Post by exutable on 2009-08-27
The problem with that implemenation is that I run into a problem when I have to check the dictionary for commands because, depending on the command it takes a different amount of arguments.

So when I do something like

```
commands[commandinlist[0](commandinlist[1], commandinlist[2])
```

it might give me an error because cd only takes 1 parameter but grep takes 2?


Here is my edit using the suggested method that doesn't work at all, not really sure why:
```

#! /usr/bin/python3

import sys, os, grep

commands = {"cd": "cmd_cd","exit": "cmd_exit","grep": "cmd_grep","history": "cmd_history"}
history = []
currentdir = os.environ["HOME"]

def prompt():
	try:
		command = str(input(currentdir+">"))
		breakdown = command.split()
		if breakdown[0] not in commands:
			print("Sorry", breakdown[0], "is not a valid command")
		else:
			history.append(command)
			commands(breakdown[0](breakdown[1], breakdown[2]))
	except IndexError as err:
		prompt()

def cmd_cd(args, currentdir):
	if not args:
		currentdir = os.environ["HOME"]
	elif os.path.isdir(args):
		currentdir = args
	else:
		print("Sorry can't locate directory")

def cmd_exit():
	sys.exit()
	
def grep(args, kargs, currentdir):
	grep.main(args, kargs, currentdir)
	
def history(args):
		commands(history[args])

def main():
	while True:
		prompt()
		
main()

```

---

### Post by Can+~ on 2009-08-27
@exutable

[PHP]#!/usr/bin/env python

import os
import sys

def cmd_exit(*args):
	raise EOFError("Quit issued")
	
def cmd_cd(*args):	
	if len(args) == 0:
		print "usage: cd <directory>"
		return
	
	if os.path.exists(args[0]):
		os.chdir(args[0])

def cmd_ls(*args):
	for fname in os.listdir(os.getcwd()):
		if os.path.isdir(fname):
			print fname,
		
			if "-l" in args:
				print
	print 

cmdlist = {
	"exit":cmd_exit,
	"ls":cmd_ls,
	"cd":cmd_cd
}

def parse(command, *args):
	cmdlist[command](*args)

def init():
	
	while True:
		try:
			command = raw_input("%s@pyshell:%s~$ " % (os.environ["USER"], os.getcwd())).strip().split()
			parse(*command)
		except TypeError:
			pass
		except KeyError:
			print "Error: Unknown action"
		except EOFError, KeyboardInterrupt:
			break
			
init()[/PHP]

Dictionary, n-ary arguments, leave the parsing for each individual section and raise errors accordingly.

---

### Post by credobyte on 2009-08-29
2 weeks passed, thread needs a *bump* :-\"

---

### Post by exutable on 2009-08-29
> **Can+~ said:**
> @exutable

[PHP]#!/usr/bin/env python

import os
import sys

def cmd_exit(*args):
	raise EOFError("Quit issued")
	
def cmd_cd(*args):	
	if len(args) == 0:
		print "usage: cd <directory>"
		return
	
	if os.path.exists(args[0]):
		os.chdir(args[0])

def cmd_ls(*args):
	for fname in os.listdir(os.getcwd()):
		if os.path.isdir(fname):
			print fname,
		
			if "-l" in args:
				print
	print 

cmdlist = {
	"exit":cmd_exit,
	"ls":cmd_ls,
	"cd":cmd_cd
}

def parse(command, *args):
	cmdlist[command](*args)

def init():
	
	while True:
		try:
			command = raw_input("%s@pyshell:%s~$ " % (os.environ["USER"], os.getcwd())).strip().split()
			parse(*command)
		except TypeError:
			pass
		except KeyError:
			print "Error: Unknown action"
		except EOFError, KeyboardInterrupt:
			break
			
init()[/PHP]

Dictionary, n-ary arguments, leave the parsing for each individual section and raise errors accordingly.

What does the * in front of stuff do?

---

### Post by Bodsda on 2009-08-31
> **exutable said:**
> What does the * in front of stuff do?

Yeah, ermm... dont listen to me, see Snova's post below :)

---

### Post by snova on 2009-08-31
> **Bodsda said:**
> When used in regular expressions, a * matches anything and everything until its following character is reached. For example, *.jpg will match any ncombination of characters before a string of '.jpg' appears.

Actually, I believe that's a glob. :twisted: I think you need .* or similar in a regular expression.

> In the example you quoted though, I would put my money on pointers or something to do with args.

The ***args** syntax in a function declaration denotes that it can take any number of arguments, which will be combined into a list and passed as "args":

[PHP]
def foo(*args):
    print args
foo(1)
foo(1, 2)
foo(1, 2, 3)
[/PHP]

(This would print the numbers in the obvious way, though as a list.)

When calling with something like **func(*l)** it takes a list l and unpacks it to match the expected arguments:

[PHP]
def foo(a, b, c):
    print a, b, c
a = [1, 2, 3]
foo(*a)
[/PHP]

Would also print the numbers.

---

### Post by petrus4 on 2009-08-31
> **pepperphd said:**
> I think I was just convinced to never learn Perl.

Yes, Perl is an ugly language.  I tried learning some XML chopping with it a bit back, and nearly had a migraine trying to figure it out.

Now I'm in the process of learning Awk, and instead of XML, just use plain text.  I'm finding it a lot easier.

---

### Post by Can+~ on 2009-08-31
*something means unpack

for example

[PHP]>>> def f(a, b, c):
...     print a + b * c
... 
>>> f(2, 3, 4)
14
>>> x = (3, 1, 2)
>>> f(x)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: f() takes exactly 3 arguments (1 given)
>>> f(*x)
5[/PHP]

* broke the content of the tuple into each argument. When you use it as a parameter, it will do the opposite, it will take every argument as inside a tuple.

---

### Post by ibuclaw on 2009-09-05
Modded Vor's shell to interact with the Command-Not-Found database in Ubuntu.

```

#!/usr/bin/perl

use strict;
use GDBM_File;
use Data::Dumper;

$ENV{SHELL} = $0;
prompt();
while(<>)
{   chomp;
    s/^\s+//;

    prompt(), next unless $_;

    @_ = parse($_);
    $_ = shift @_;

    /cd/   ? (chdir @_[0] or error("$_: @_", $!)) :
    /exit/ ? exit @_[0] :
    /pwhich/ ? (cnf_main("--", @_[0])) :
    /penv/ ? eval { if(defined @_[0]){ print "$ENV{@_[0]}\n"; }else{ print Dumper(\%ENV); } } :
    /pset/ ? ($ENV{@_[0]} = @_[1]) :
    /punset/ ? (delete $ENV{@_[0]}) :
    eval
    {   if("$_ @_" !~ /\|/)
        {   fork   ? wait : (exec $_, @_ or error($_, "Invalid command"), exit);
            child_error($?);
        }
        else
        {   my $rand = rand;
            open(CMD, "($_ @_ | sed 's/^/$rand:/') 2>&1 |") or error($_, "Can't fork");
            while(<CMD>)
            {   if(s/^$rand://)
                {   print STDOUT;
                }
                elsif(s/^sh: (\S*): not found$//)
                {   error($1, "Invalid command");
                }
                else
                {   print STDERR;
                }
            }
            close EVAL;
        }
    };
    prompt();
}

sub prompt
{   printf "$ENV{USER}%s> ", ($< == 0) ? "#" : "\$";
}

sub error
{   my $cmd = $_[0];
    cnf_main("--", $cmd);
    print "plsh: $cmd: $_[1]\n";
}

sub parse
{   my @tok;
    my($line) = @_;
    my @quot = split /"/, $line;

    while(@quot)
    {   my $nonquot = shift @quot;
        $nonquot =~ s/^\s*//;
        push @tok, split(/\s+/, $nonquot);
        if("@quot" !~ /^\s*$/)
        {   push @tok, shift @quot;
        }
    }
    return @tok;
}

sub child_error
{   my($err) = @_;
    my $ret =
      ($err eq 1) ? "Hangup\n" :
      ($err eq 3) ? "Quit\n"   :
      ($err eq 4) ? "Illegal Instruction\n" :
      ($err eq 5) ? "Trace/breakpoint trap\n" :
      ($err eq 6) ? "Aborted\n" :
      ($err eq 7) ? "Bus error\n" :
      ($err eq 9) ? "Killed\n" :
      ($err eq 10) ? "User defined signal 1\n" :
      ($err eq 11) ? "Segmentation Fault\n" :
      ($err eq 12) ? "User defined signal 2\n" :
      ($err eq 14) ? "Alarm Clock\n" :
      ($err eq 15) ? "Terminated\n" :
      ($err eq 16) ? "Stack fault\n" :
      ($err eq 24) ? "CPU time limit exceeded\n" :
      ($err eq 25) ? "File size limit exceeded\n" :
      ($err eq 26) ? "Virtual timer expired\n" :
      ($err eq 27) ? "Profiling timer expired\n" :
      ($err eq 29) ? "I/O possible\n" :
      ($err eq 30) ? "Power failure\n" :
      ($err eq 31) ? "Bad system call\n" : "";
    print $ret;
}


###########################
#    Command Not Found    #
###########################

my $shell_call = 0;
my $program;
my @paths;
my @packages;
my @sources;

sub usage
{   print "Usage: command-not-found -- <command-name>\n\n",
          "command-not-found: error: no such option: $_[0]\n";
    return -1;
}

sub find_command
{   my $data_path = "/usr/share/command-not-found/programs.d/";
    return if(&is_installed);
    local *DIR;
    if(opendir(DIR, $data_path))
    {   for (readdir(DIR))
        {   if(/\.db$/)
            {   my $source = $_;
                tie my %db, 'GDBM_File', $data_path.$source, &GDBM_READER, 0644;
                if(defined $db{$program})
                {   my @tmp = split /\|/, $db{$program};
                    for my $dbapp (@tmp)
                    {   push @packages, $dbapp;
                        push @sources, $source;
                    }
                }
                untie %db;
            }
        }
        closedir(DIR);
        return;
    }
    return 127;
}

sub is_installed
{   for (qw "/usr/local/sbin /usr/local/games /usr/local/bin /usr/sbin /usr/games /usr/bin /sbin /bin") {
        push @paths, "$_" if( -e "$_/$program");
    }
    if(scalar @paths)
    {   return 1;
    }
    return 0;
}

sub command_not_found
{   my $release = &get_release;
    if(scalar @packages == 1)
    {   my $package = shift @packages;
        my $source = shift @sources;
        $source =~ s/^.*\-(.+?)\.db$/$1/;
        print "The program '$program' is currently not installed.  ";
        if($> == 0)
        {   print "You can install it by typing:\n";
            print "apt-get install $package\n";
        }
        elsif(&can_sudo)
        {   print "You can install it by typing:\n";
            print "sudo apt-get install $package\n";
        }
        else
        {   print "To run '$program' please ask your administrator to install the package '$package'\n";
        }
        if(not source_enabled($source, $release))
        {   print "You will have to enable the component called '$1'\n";
        }
    }
    elsif(scalar @packages > 1)
    {   print "The program '$program' can be found in the following packages:\n";
        for my $package(@packages)
        {   my $source = shift @sources;
            $source =~ s/^.*\-(.+?)\.db$/$1/;    
            if(not source_enabled($source, $release))
            {   print " * $package  You will have to enable the component called '$source'\n";
            }
            else
            {   print " * $package\n";
            }
        }
        if($> == 0)
        {   print "Try: apt-get install <selected package>\n";
        }
        elsif(&can_sudo)
        {   print "Try: sudo apt-get install <selected package>\n";
        }
        else
        {   print "Ask your administrator to install one of them\n";
        }
    }
    return 0;
}

sub command_found
{   my @missing;
    if(scalar @paths == 1)
    {   my $path = shift @paths;
        print "Command '$program' is available in '$path'\n";
        unless($ENV{PATH} =~ /:$path|$path:|^$path$/)
        {   push @missing, $path;
        }
    }
    else
    {   print "Command '$program' is available in the following places\n";
        for my $path(@paths)
        {   print " * $path/$program\n";
            unless($ENV{PATH} =~ /:$path|$path:|^$path$/)
            {   push @missing, $path;
            }
        }
    }
    if(scalar @missing)
    {   my $path = (scalar @missing > 1) ? join ':', @missing : $missing[0];
        print "The command could not be located because '$path' is not included in the PATH environment variable.\n";
        if($path =~ /sbin/)
        {   print "This is most likely caused by the lack of administrative priviledges associated with your user account.\n";
        }
    }
    return 0;
}

sub get_release
{   my $release = undef;
    open(RELEASE, '</etc/lsb-release');
    while(<RELEASE>)
    {   if($_ =~ /DISTRIB_CODENAME=(.+)/)
        {   $release = $1;
            last;
        }
    } 
    close RELEASE;
    return $release;
}

sub can_sudo
{   open GROUPS, "</etc/group";
    my @admin_group = grep /^admin/, <GROUPS>;
    close GROUPS;
    if($admin_group[0] =~ /$ENV{USER}/)
    {   return 1;
    } 
    return 0;
}

sub source_enabled
{   my($source, $release) = @_[0,1];
    local *DIR;
    if(opendir(DIR, '/var/lib/apt/lists/'))
    {   my $count = 0;
        for (readdir(DIR))
        {   return 1 if(/$release\_$source.*Packages$/);
        }
        closedir(DIR);
    } 
    return 0;
}

sub cnf_main
{   while(my $argp = $_[0])
    {   if(not defined $argp)
        {   return 127;
        }
        elsif ($argp =~ /^[-]{1,2}(.*)$/)
        {   if($1 =~ /^$/)
            {   $shell_call++;
            }
            else
            {   return usage($argp);
            }
        }
        elsif($shell_call)
        {   $program = $argp;
        }
        shift @_;
    }
 
    if(defined $program)
    {   &find_command;
        &command_not_found if(scalar @packages);
        &command_found if(scalar @paths);
    }
    
    return 127;
}

```

Oh, and added a 'penv', 'pset' and 'punset' commands to list and modify shell variables.

The only things that are really dearly missing are:
[LIST=1]
[*]catching signals
[*]history view
[/LIST]

But I'm probably not going to implement them. :)

Regards
Iain

*Revision 1*: Added sub parse() to that makes tokens from "quoted strings"
ie: 'grep "Hello World" foo.c' => gets parsed to => ("grep", "Hello World", "foo.c");

---

### Post by credobyte on 2009-09-06
What's up with this challenge ? It's been like 3 weeks since it was opened .. :-k

---

