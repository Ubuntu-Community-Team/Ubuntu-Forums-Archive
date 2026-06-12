---
title: "Installing From Source Code and Make.sh"
date: 2011-07-04
forum: Programming Talk
---

### Post by zachnap on 2011-07-04
ubuntu 11.04 64 bit.

Hello. I am going through a book called Python Scripting for Computational Science and it is wanting me to build a program already contained in the resource for the text. It is a simulation program that the book uses to demonstrate how to script with python. Anyway, it provides source code and a make.sh in Fortran 77. I have already installed gfortran and g77 but I am having trouble running the make file and getting it to install the program to the directory in the make script. I haven't even gotten to trying to add the path yet. Actually, if I just double-click the run script then it plots out the result - so, there isn't a problem reading Fortran.

Here is the content of the make.sh:
> 
#!/bin/sh -x
compiler=gfortran
options=-O3
$compiler -o oscillator $options oscillator.f

# install the oscillator executable:
if [ ! -d $scripting/$MACHINE_TYPE/bin ]; then
  mkdirhier $scripting/$MACHINE_TYPE/bin
fi
mv -f oscillator $scripting/$MACHINE_TYPE/bin


I'm fairly new to all this but I've messed around with some basics before, just not enough. I get some of the Bourne shell script but I'm still a bit new. I am guessing that some of the syntax is wrong for my Linux dist.?

I don't know if I am giving enough information here but maybe someone could give some idea how to proceed. Thanks

---

### Post by Toz on 2011-07-05
Firstly, you need to have the package **xutils-dev** installed to use the **mkdirhier** command. Search for it in the Software Centre or open a command window and: ```
sudo apt-get install xutils-dev
```or, in place of **mkdirhier**, you can use **mkdir -p**

Secondly, the $scripting and $MACHINE_TYPE variables are not defined. You could add the lines ```
scripting=scripts
MACHINE_TYPE=x86
``` to the beginning of the code (assuming your machine type is x86).

Therefore, the file could like like:
```
#!/bin/sh -x
scripting=scripts
MACHINE_TYPE=x86
compiler=gfortran
options=-O3
$compiler -o oscillator $options oscillator.f

# install the oscillator executable:
if [ ! -d $scripting/$MACHINE_TYPE/bin ]; then
  mkdir -p $scripting/$MACHINE_TYPE/bin
fi
mv -f oscillator $scripting/$MACHINE_TYPE/bin
```

After you've run this script, you will find the executable in **scripts/x86/bin**

---

### Post by zachnap on 2011-07-05
Thanks

OK, so the **mikdirhier** creates a directory hierarchy rather than just one 'folder'?

I don't really understand the defining variables part. e.g., scripting=scripts... aren't these just folder names? I don't understand why they need to be defined.

---

### Post by Toz on 2011-07-05
> **zachnap said:**
> OK, so the **mikdirhier** creates a directory hierarchy rather than just one 'folder'?
Yes. As does **mkdir -p**

> I don't really understand the defining variables part. e.g., scripting=scripts... aren't these just folder names? I don't understand why they need to be defined.
Yes, they are just folder names. I'm not sure why the author of that book is doing it that way, but to make it work, you need to have those variables defined.

---

### Post by zachnap on 2011-07-05
Awesome, that worked. Before it was dumping the x-ecutable into the same folder. But it didn't create a file called 'x86', just 'bin'.

Alright, I know I'm being a pain here, but... I added the directory to the path and then checked my path ($PATH) and it has the ~/scripts/bin listed but typing the name of the executable only brings up 'command not found'. The cursor should be awaiting some kind of input... right?

---

### Post by Toz on 2011-07-05
The script is not executable. There are two ways:

1. Execute the script via sh:```
sh oscillator
```

2. Make the script executable:```
chmod +x ~/scripts/bin/oscillator
```
and then
```
osciallator
```

---

### Post by zachnap on 2011-07-05
It isn't working for some reason. i gave myself permissions I tried chmod +x - sudo chmod 700, etc. It seems it isn't treating oscillator as an executable or something. 

EDIT: It makes no sense... if I run the Bash script he made to open oscillator: **oscillator < inp**, it runs the program and plots with gnu. Why then can't I run it from terminal?

---

### Post by pafoo on 2011-07-05
> **zachnap said:**
> It isn't working for some reason. i gave myself permissions I tried chmod +x - sudo chmod 700, etc. It seems it isn't treating oscillator as an executable or something. 

EDIT: It makes no sense... if I run the Bash script he made to open oscillator: **oscillator < inp**, it runs the program and plots with gnu. Why then can't I run it from terminal?

If you set the executable bit already you can only run 1 of 3 ways in a terminal.
You do not have to use sh oscillator because in the script the very first statment is
#!/bin/sh -x
that command tell the kernel which shell to use as the interpreter
The dash -x tells it to run the script in debug mode. 
Also you did a chmod 700, verify that you are the owner of the file.

```

# First method Old Skool
source oscillator

#Second method, more commonly used, must cd to that directory first
./oscillator

#3rd absolute path
/usr/local/bin/oscillator

```

---

### Post by Toz on 2011-07-05
> **zachnap said:**
> It isn't working for some reason. i gave myself permissions I tried chmod +x - sudo chmod 700, etc. It seems it isn't treating oscillator as an executable or something. 

EDIT: It makes no sense... if I run the Bash script he made to open oscillator: **oscillator < inp**, it runs the program and plots with gnu. Why then can't I run it from terminal?

What does: ```
echo $PATH
```return? Lets confirm that ~/scripts/bin is in your path.

What does: ```
ls -l ~/scripts/bin
```return? Lets verify the permissions and ownership.

Also, you are using an input file **<inp**. For that to work, you will need to put the full path to the inp file. Something like (assuming oscillator is owned by you, executable, and in your path):
```
oscillator < ~/scripts/bin/inp
```
In this case, it may be easier, as pafoo suggests, to go to ~/scripts/bin first then execute:
```
oscillator < inp
```

@pafoo - **sh -x** isn't auto-executing the file. Here is a test:
```
~/bin$ pwd
/home/toz/bin

~/bin$ ls -l tester
-rw-r--r-- 1 toz toz 26 2011-07-05 22:49 tester

~/bin$ cat tester
#!/bin/sh -x
echo tester

~/bin$ tester
bash: /home/toz/bin/tester: Permission denied

~/bin$ sh tester
tester

```

---

### Post by pafoo on 2011-07-05
I did not say it auto executes. I said it automatically tell the kernel which shell to use to interpret the script. You can make it anything

#!/bin/sh
#!/bin/bash
#!/bin/ksh
#!/bin/csh
#!/usr/bin/python

which once you run it, it already knows which shell/interpreter to use be it bourne, bourne again, korne shell, c shell, python etc

Which is why the sh oscillator is a redundant way to run a script when you specify.

If you are in the directory, if you do not type source or ./ the script will NOT run. It will give a error "command not found"

example
```


cd /usr/local/bin
cat test.sh

#!/bin/bash
echo "Hello world!"

./test.sh
Hello world!

```

---

### Post by Toz on 2011-07-05
But it will execute the file if you prefix it with the shell that it was written for _if_ the file does not have the executable bit set. 
```
sh test.sh
```

---

### Post by pafoo on 2011-07-05
lol i never said you were wrong =)

---

### Post by zachnap on 2011-07-07
Sorry, I was away from the comp for a while.

I did an ECHO on $PATH and that folder did not show up in the path, but it was there previously. 

I ended up typing ```
./oscillator
``` and I got a hanging cursor. Then I gave it the inp and a graph popped up. 

The other commands weren't working.

---

### Post by pafoo on 2011-07-07
> **zachnap said:**
> Sorry, I was away from the comp for a while.

I did an ECHO on $PATH and that folder did not show up in the path, but it was there previously. 

I ended up typing ```
./oscillator
``` and I got a hanging cursor. Then I gave it the inp and a graph popped up. 

The other commands weren't working.

Lets save you some pain, edit you /home/user/.bashrc and enter the following line 

PATH="/usr/local/bin:/usr/local/sbin:/sbin:/bin:/usr/bin:/usr/sbin:" 

etc etc, put ALL the path's that you want that account to automatically have in your $PATH. So everytime you log in, your path's will be set! Then you could just type oscillator and it will work!

---

### Post by zachnap on 2011-07-07
^So what you're saying is that generally you would only want to temporarily add a particular path, but maybe there are paths that you always use or always want accessible so there is an alternative method to "permanently" add a path...?

---

### Post by pafoo on 2011-07-07
> **zachnap said:**
> ^So what you're saying is that generally you would only want to temporarily add a particular path, but maybe there are paths that you always use or always want accessible so there is an alternative method to "permanently" add a path...?

No. Im saying that if you dont want to type the absolute path anymore for that particular executable/s in that particular directory add those path's to your $PATH variable. I mean in command line you can type PATH='   '  But that will only last until you log out. By putting it in your .bashrc it will set it everytime you log in to that account.

Let me give an example, this is an any directory

```

echo $PATH

ifdown --help
-bash: ifdown: command not found

PATH="/sbin"

echo $PATH
/sbin

ifdown --help
usage: ifdown <device name>

```

So what $PATH does is when I type ifdown, Linux looks if that command exists any any of the directory's listed in $PATH, which automatically puts /sbin/ in front of ifdown for you. What it also does is gather a list of all executable's in those paths so you can use TAB completion.

---

### Post by zachnap on 2011-07-08
> No. Im saying that if you dont want to type the absolute path anymore  for that particular executable/s in that particular directory add those  path's to your $PATH variable. I mean in command line you can type  PATH='   '  But that will only last until you log out. By putting it in  your .bashrc it will set it everytime you log in to that account.

Yeah, that is what I said. PATH is only temporary, editing the .bashrc is "permanent".

---

### Post by pafoo on 2011-07-08
Oops, yes, thats correct =)

---

### Post by zachnap on 2011-07-11
Anyway, thanks. I'll keep working on it...

---

