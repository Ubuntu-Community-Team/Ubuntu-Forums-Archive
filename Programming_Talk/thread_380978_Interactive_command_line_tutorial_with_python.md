---
title: "Interactive command line tutorial with python"
date: 2007-03-10
forum: Programming Talk
---

### Post by raja on 2007-03-10
Hello everyone,
Seeing some requests for an interactive command line tutorial (like the ruby online tutorial), I wrote this tutor with python. I am relatively new to python and would appreciate comments and advice. Please untar the files to your desktop and run cmd_tutor.py from the terminal. As you can see, cmd_tutor.py parses 'lessons' written in a standard format. So it is very easy to extend this by writing more lessons. 
Thanks

**Update March 2009 - A new version can be downloaded from [google code]("http://code.google.com/p/cmd-tutor/").**

---

### Post by tkjacobsen on 2007-03-10
Very nice idea.. Just make the break between showing words shorter.. It is very annoying, because it is slower than I read... (And english is not even my native language).

EDIT:
If you add
#!/usr/bin/env python
as the first line.. The file can be executed with ./cmd_tutor.py

---

### Post by raja on 2007-03-10
> **tkjacobsen said:**
> Very nice idea.. Just make the break between showing words shorter.. It is very annoying, because it is slower than I read... (And english is not even my native language).

Thanks. I am planning to have an optional argument to have it go faster. Of course you can modify the sleep time in the function slowprint to make it faster.

---

### Post by tkjacobsen on 2007-03-10
> **raja said:**
> Thanks. I am planning to have an optional argument to have it go faster. Of course you can modify the sleep time in the function slowprint to make it faster.

I know, but the people who will use it don't.. But it is great if you just add it as a choice when starting the program.

---

### Post by raja on 2007-03-10
> **tkjacobsen said:**
> I know, but the people who will use it don't.. But it is great if you just add it as a choice when starting the program.

Point well taken. Thanks again for taking the time.

---

### Post by enopepsoo on 2007-03-10
I only did lesson 1 but it was pretty cool.  I ended up typing quit and changing the sleep interval like you said though.:)

---

### Post by raja on 2007-04-06
Update !

Here is the new version with the promised '-q' argument that will disable the slow printing. Also there are five brand new lessons. An install script is added so that the program can be installed and called up from the command line easily. More details [here]("http://reachbeyondgrasp.blogspot.com/2007/04/interactive-linux-command-line-tutorial.html").

Suggestions are welcome.

---

### Post by raja on 2007-04-08
No triers yet ?

---

### Post by Mike'sHardLinux on 2007-04-08
At first, I installed it:
```
sudo python install.py install
```

After I did that, cmd_tutor would give me errors. I was only able to run it as sudo. Is this a problem with my configuration or a bug in the install process?

I uninstalled it, and just run it from the src directory and it works fine that way.

I do like it better with the -q option.

---

### Post by raja on 2007-04-08
Thanks Mike. 
There was a problem with the file permissions. I have changed the install script and it will be OK now.

---

### Post by tahrawee on 2007-08-29
hi all
Thank you raja for your effort,
I'm a new linux user and I haven't any idea about the command line instructions, 
I read all replaies but I couldn't run the cmd_tutor
thus please if you can, send me the lines I should write in the terminal to run the your work.
also how to know if python is installed in my system and it's workable?

---

### Post by LaRoza on 2007-08-29
[http://www.mired.org/home/mwm/try_python/](http://www.mired.org/home/mwm/try_python/)

---

### Post by pmasiar on 2007-08-29
> **tahrawee said:**
> how to know if python is installed in my system and it's workable?

What is your system? Ubuntu? Windows? something else?

---

### Post by sacherjj on 2007-08-29
I won't get a chance to check this out on Ubuntu until I get home.  I'm trying the first version on my work laptop, with Windows Python, I get an error on the import of readline.  "ImportError: No module named readline."  Is that typically part of the Python package?

Edit: Looking at the new install for 0.3 looks like it is pretty Unix dependent.  Not a problem.  I'll take a look tonight in Ubuntu.

---

### Post by Vox754 on 2007-08-29
This is essentially the "install" file included in the tar package.

```

To install:

1. Extract cmd_tutor package
  tar -xvfz cmd_tutor-0.3.tar.gz

2. Go to cmd_tutorial directory
  cd cmd_tutor-0.3

3. Install it
  sudo python install.py install

4. Later if you want to uninstall it:
  sudo python install.py uninstall

5. To remove it manually, just delete /usr/bin/cmd_tutor and 
   /usr/share/cmd_tutor/

Once installed you can type "cmd_tutor" in the terminal to start it.
However installation is optional.
You can run the program from the directory directly after you extracted it.
Just enter the src directory and type "python cmd_tutor.py" from the terminal.
You will have to give the path to the lessons if you choose not to install (cmd_tutor-0.3/share/lessons).

Enjoy!

```

You already have Python installed if you use Ubuntu.

Now remember, this tutorial is *written* in python, but *teaches* to use the Unix shell (bash in general). It is intended for those beginners that want to learn to use the terminal.

If you are an experienced programmer you may write additional lessons on harder topics.

This tutorial is very small in size and with enough lessons I believe it could be included easily in future Linux distributions as a quick and fun introduction to the terminal. Having a Windows port would be ideal to those not yet using Linux. In its current state probably it may run under Cygwin.

---

### Post by raja on 2007-08-29
Hello guys,
Thanks for the interest in the program.
I am sorry if it was not clear that this has to be run in the linux terminal for it to work because it is essentially a demo of the functions that are available in the terminal.
The project is now hosted at sourceforge and you can download it [there]("http://sourceforge.net/projects/cmd-tutor/"), but I havent worked on it since there did not seem to be much interest in it. 
Any feedback, suggestions or new lessons are welcome !

---

### Post by bgs100 on 2009-01-14
Cool!  I'd like to try to make my own version writtn in shell script.  Which I will start... now.

---

### Post by myromance123 on 2009-01-14
OH wow ! I did not know there was a program like this! 

 :P

Its dated from 2007!!!?

Woah~
   A program like this should be in the repos and promoted xD

---

### Post by aszxcv on 2009-01-14
heres a good one i found  [http://try-python.mired.org/](http://try-python.mired.org/)

---

### Post by myromance123 on 2009-01-14
Oooo

 Thats cool man :)
I didnt know there were such cool programs available :D

I still think raja's program should be in repos lol so when you dont have the net available you can still learn plus its portable :P

 Thanks man, Ima take full advantage of try python ^.^

:lolflag:

---

### Post by raja on 2009-03-20
Thanks everyone for their interest in the program. I have a new version available for download at [googlecode]("http://code.google.com/p/cmd-tutor"). Any comments and suggestions are welcome.

---

