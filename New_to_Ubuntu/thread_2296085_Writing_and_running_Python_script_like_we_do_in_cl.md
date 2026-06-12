---
title: "Writing and running Python script like we do in class."
date: 2015-09-23
forum: New to Ubuntu
---

### Post by brian95 on 2015-09-23
Hey all!
This is my first post ):P

In my programming class we're learning Python 3.4 using Windows based machines.
[LIST=1]
[*]I write the script in notepad and save with the .py file extension
[*]I run the script from the command line in windows by going to the drive ( ex: **F: python pythagoreantheorum.py**)
[*]My first simple program works.
[/LIST]

My question: I'm running Ubuntu 14.04, but don't know what notepad style app I can write my code in, and don't know how I would run the code from the command line.
[LIST]
[*]I do know how to get to the terminal (ctrl 1) buuuut thats about it
[*]There's allot of independent learning in this class (wink) so I really need your help guys!
[/LIST]
THANK YOU

---

### Post by ian-weisser on 2015-09-23
Any 'notepad style app' (called a *text editor*) will work, including both GUI (gedit, leafpad) and terminal-based (vi, nano) editors. Any of them.
You run the code by specifing, just as in Windows, the location of the Python interpreter you wish to use. In Ubuntu, there are currently two to choose from.
Outside Windows, the .py suffix is irrelevant. You don't need it here. You are welcome to use it, if you find it useful...but your system won't.

Examples of how to run a python script in Ubuntu
```
python pythagoreantheorum
/usr/bin/python pythagoreantheorum
python3 pythagoreantheorum
/usr/bin/python3 pythagoreantheorum
```

Er, please don't wink at me.

---

### Post by branau on 2015-09-23
If you're looking for a notepad-style app, Ubuntu has one that it comes with called gedit. It's a pretty handy tool, but I myself prefer to use either Vim or Sublime Text for my coding. If you're just starting out, I wouldn't use Sublime yet though as it's a good idea to get into the habit of writing good code without the help of an IDE. Helps with debugging too.

As for running the scripts, I'd highly recommend you use a virtual environment for all of your developing, as some apps depend on python and if you were to somehow mess things up with it, you migh find yourself in need of a re-installation. I personally use [pyenv]("https://github.com/yyuu/pyenv"), and it's good, but feel free to take a look around. As long as you're not installing python packages with apt-get, you should be alright. When it comes to actually running your scripts, just make sure that you're in the same directory as the script, and all you do is run ```
python your-script.py
```
If you haven't already, [get familiar with the linux terminal](http://linuxcommand.org/lc3_learning_the_shell.php).

Here are just a couple of basic commands to get you started though:

```
cd FOLDER
```

This will move you into the folder that you specify

```
cd ..
```

This will move you to the folder that contains the folder you're currently in (one level up)

```
ls
```

This will display all of the contents of the current directory so you can make sure you're in the right spot

That should be all you need to get started. Happy coding!

---

