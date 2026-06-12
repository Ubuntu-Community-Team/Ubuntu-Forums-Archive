---
title: "[SOLVED] Saving data between sessions"
date: 2007-08-13
forum: Programming Talk
---

### Post by NeillHog on 2007-08-13
I am writing a small utility for wrapping the command line program "GPSBabel.

I want to save data between sessions so that when the user restarts the program it has the last data from last time already there.

In Windows I would have created an ini file in either the same directory as the program or (better) an ini file in the users "own data" directory.

My questions are:
1. How is the normal means of saving such data in Linux? Ini file or something else?
2. Where should this file be in the file structure.

Thanks for any and all help

Neill

---

### Post by AlexThomson_NZ on 2007-08-13
The Linux way is to have a .filename directory in the user's home directory where preferences are stored

---

### Post by NeillHog on 2007-08-13
Thank you!

Do you mean a directory that is actually called ".filename" and thus hidden in which I could have a file called for example foo.conf (assuming my program is called foo).

All the Linux configuration files I have seen up to now have been called xxx.conf
Are there special routines for reading and writing to these files in python or do you have to program everything.

Thanks again
Neill

Ignore the second bit - I just found
[http://docs.python.org/lib/module-ConfigParser.html](http://docs.python.org/lib/module-ConfigParser.html)

---

### Post by batrick on 2007-08-13
Usually you make a hidden directory only if you have many files you want to save between sessions (config files). If it's just one then make a hidden file .foo.conf

---

### Post by AlexThomson_NZ on 2007-08-13
I'm not sure what the "best practice" is, but I do it the same way as most other programs do:

For example, if I write a program "squirrel-sql", I create a ".squirrel-sql" directory, and have  the (non-hidden) config files in there.  I don't think the suffix of the config file is particularly important, but I usually use .xml or .config.

Not 100% sure about Python, but I would suspect it would be the same as C, where you have to parse it yourself (no biggie if you keep the format simple- I try to use property/value pairs)

---

### Post by pmasiar on 2007-08-13
> **AlexThomson_NZ said:**
> 
Not 100% sure about Python, but I would suspect it would be the same as C, where you have to parse it yourself

Not so. One of best things in Python is, that it comes **"batteries included"** - whole lot of useful modules are installed by default, and many more are in module repository (called cheeseshop after Monty Python sketch)

By default you have [all these modules](http://docs.python.org/modindex.html)  including [ConfigParser](http://docs.python.org/lib/module-ConfigParser.html)

---

### Post by AlexThomson_NZ on 2007-08-13
Wow- colour me impressed! :)

---

### Post by NeillHog on 2007-08-14
Thank you all of you.
These forums are amazing - post questions and get informed answers. No flaming. No complaining about the people asking being stupid. Great! 

You have all helped me greatly.

So I will keep my data in a file at /home/[user]/.GPSBabelWrapper.conf
Add some comments at the start telling people what it is for 
and then use configParser to read and write to it.

Programming is fun with this sort of support :-)

Neill

---

### Post by NeillHog on 2007-11-17
A few months later and now I am actually implementing this idea.

As I understood things the idea was to write to a file
/home/[user]/.GPSBabelWrapper.conf

Now, I do not know who the [user] is but I thought that writing to 
~GPSBabelWrapper.conf
would always write to his/her home directory.

What it actually does is writes to a file called
~GPSBabelWrapper.conf
in the actual directory.

Could some one tell me where my mistake is.

Thanks again to all of you :-)
Neill

---

### Post by aks44 on 2007-11-17
~[COLOR="Red"]**/**[/COLOR].GPSBabelWrapper.conf ;)

---

### Post by NeillHog on 2007-11-17
Thank you!

---

### Post by slavik on 2007-11-17
try '~/.stuff'

---

### Post by NeillHog on 2007-11-18
Thank you for that suggestion.
I tried it with the following result

fpConf=open(CONFIG_FILE, "w")
IOError: [Errno 2] No such file or directory: '~/GPSBabelWrapper.conf'

Calling it ~GPSBabelWrapper.conf doesn't bring an error as doesn't GPSBabelWrapper.conf but as I wrote above both result in the file being written to the actual directory.

So what am I doing wrong.
Please help :-)

Neill

Using /home/neill/GPSBabelWrapper.conf
works.

very strange

---

### Post by NeillHog on 2007-11-18
I don`t know if it is relevant but I am using Kubuntu. And I obviously have all rights on my home directory.
I thought that the tilde was equal to /home/neill

---

### Post by [h2o] on 2007-11-18
You need the full path since pythons "open()"-function will not do the "~" -> "/home/<current_user>/" mapping for you.

I know I have seen some kind of function for getting the current users home directory though. Use that instead. Is probably in the "os" module.

---

### Post by NeillHog on 2007-11-18
That worked !

configFile = os.path.expanduser("~") + '/GPSBabelWrapper.conf'

thanks!

---

### Post by [h2o] on 2007-11-18
> **NeillHog said:**
> That worked !

configFile = os.path.expanduser("~") + '/GPSBabelWrapper.conf'

thanks!
Or you could make it even easier:

configFile = os.path.expanduser("~/.gpsbabelwrapper")

1) Configfiles are normally hidden. Let them start with a dot.
2) Files in Linux are usually not written with capitalized letters. Do a "ls -d .*" in your home directory and watch how the config files are named. Of the 130 hidden files in my home dir, there is not one single capitalized letter.

Good luck with your project.

---

### Post by NeillHog on 2007-11-18
OK! Thank you for both tips. It is the friendly, informed, helpfull users that make Ubuntu/Python so much fun.
T anks
Neill

---

