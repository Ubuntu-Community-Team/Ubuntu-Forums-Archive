---
title: "Program as system command"
date: 2013-01-22
forum: Programming Talk
---

### Post by MadsRC on 2013-01-22
While I learn to write Python, I've decided to take on a project, which mainly started because my workplace nedded a small tool to to a certain job.

Now, I've gotten the software to what you'd call an early beta, and I'd like to experiment with adding the program as a, guess you can call it system command. Just like sed, ping and so forth.
What do I need to do in my program (Well, I proberly need to do it to the system and not the program) to execute it without .py at the end?

Is there any such documentaiton anywhere?

---

### Post by Cheesemill on 2013-01-22
Whether or not you have .py at the end doesn't make a difference. Linux doesn't use filename extensions in the same way as windows.

All you need to do is make sure that the shebang at the start of your program points to the correct python interpreter, that the file is executable, and it is in your system path somewhere. I've created the following as an example...

```
rob@arch:~$ ls /usr/bin/pytest
-rwxr-xr-x 1 root root 41 Jan 22 19:39 /usr/bin/pytest
rob@arch:~$ 
rob@arch:~$ cat /usr/bin/pytest
#!/usr/bin/python2
print "Hello, world!"
rob@arch:~$ 
rob@arch:~$ pytest
Hello, world!
rob@arch:~$ 
```

---

### Post by The Cog on 2013-01-22
The .py at the end is not required - the file name makes no difference to how executable it is. However, the .py does serve as a hint to text editors that do syntax highlighting, so you may choose to only change the flename after you have it working.

To be executable as a command, two things need to happen. Firstly, the first line of the file must be:
```
#!/usr/bin/python
```which tells the OS which interpreter to use to run the file.

Secondly, the file must be marked as executable. You can do this in a file manager by right-clicking the file and editing its properties, or you can use the chmod command, e.g.
```
chmod +x myprogram.py
```

Now you can run it as a command. e.g. ```
./myprogram.py
```

You may wish to place a copy in somewhere that is in your search path, so that you don't have to give the full path to the file every time you use it. The best place to put it is probably in /usr/local/bin - you need to be root to write into that directory, so use a command like this (the command below renames the file as it copies it to remove the ".py":
```
sudo cp myprogram.py /usr/local/bin/myprogram
```

---

### Post by Tony Flury on 2013-01-23
> **The Cog said:**
> The .py at the end is not required - the file name makes no difference to how executable it is. However, the .py does serve as a hint to text editors that do syntax highlighting, so you may choose to only change the flename after you have it working.

To be executable as a command, two things need to happen. Firstly, the first line of the file must be:
```
#!/usr/bin/python
```which tells the OS which interpreter to use to run the file.

Secondly, the file must be marked as executable. You can do this in a file manager by right-clicking the file and editing its properties, or you can use the chmod command, e.g.
```
chmod +x myprogram.py
```

Now you can run it as a command. e.g. ```
./myprogram.py
```

You may wish to place a copy in somewhere that is in your search path, so that you don't have to give the full path to the file every time you use it. The best place to put it is probably in /usr/local/bin - you need to be root to write into that directory, so use a command like this (the command below renames the file as it copies it to remove the ".py":
```
sudo cp myprogram.py /usr/local/bin/myprogram
```

I would actually suggest that for things like this it is better to have a user local bin directory - i.e. "~/bin", and add it to your PATH rather than manually copying stuff into /usr/local/bin - where it could overwrite or contaminate system wide applications. 

you can add a directory to your path easily enough - edit your "~/.profile" file and re-login - you might not even need to edit "~/.profile" - you might just have to logout after you create it to make it appear in PATH.

---

### Post by Cheesemill on 2013-01-23
> **Tony Flury said:**
> I would actually suggest that for things like this it is better to have a user local bin directory - i.e. "~/bin", and add it to your PATH rather than manually copying stuff into /usr/local/bin - where it could overwrite or contaminate system wide applications. 

you can add a directory to your path easily enough - edit your "~/.profile" file and re-login - you might not even need to edit "~/.profile" - you might just have to logout after you create it to make it appear in PATH.
Ubuntu will automatically add a users ~/bin directory to PATH if it exists, this is done by an if statement in the ~/.bashrc file.

For early development and for scripts that are only going to be used by one person then this is an ideal setup, I was only suggesting that the script should be in a system directory because it sounded like it was going to be used by more than one person.

---

### Post by ssam on 2013-01-24
python generally uses '#!/usr/bin/env python' instead of '#!/usr/bin/python'

[http://stackoverflow.com/questions/5709616/whats-the-difference-between-these-two-python-shebangs](http://stackoverflow.com/questions/5709616/whats-the-difference-between-these-two-python-shebangs)

if you think that it might be a generally useful command you could try packaging it or getting it added to moreutils.

---

