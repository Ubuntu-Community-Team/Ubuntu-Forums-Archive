---
title: "Need help with python script commands"
date: 2014-07-08
forum: New to Ubuntu
---

### Post by Ian.kz.ma on 2014-07-08
I have to do a bunch of file copying, moving, svn check out commands, directory checking etc. and I'm trying to make a script to do it for me. I have basic python syntax, but I'm not sure how to use python to execute linux commands.
I know the linux commands needed for example **sudo apt-get install subversion **i just don't know how to wrap python around it.

Specifically, could anyone give examples on how to:

- Check if a package (like svn) is installed, if not then install it. I know this is a simple if-statement but no idea how to write it...
- Check if a folder with a specific name is installed, if not create it on the desktop/some other directory. Similar to the above I would assume.
- Move to a certain directory and execute a command (like I want to extract a .tgz file in a certain directory)

There's more but I want to grasp basic principles and actually learn how to execute linux commands using python scripting. Thanks for your time~

---

### Post by slooksterpsv on 2014-07-08
Here's how to execute system commands via python:

```

os.system ("*type_command_here*")

```
You probably need some return values so you might need to do process spawn 
```

>>> import subprocess
>>> p = subprocess.Popen(['ls', '-a'], stdout=subprocess.PIPE, 
...                                    stderr=subprocess.PIPE)
>>> out, err = p.communicate()
>>> print out

```

Popen, you have to have each part of the command in an array e.g. ls -l -a -h would equal ["ls", "-l", "-a", "-h"] which you could execute like this:
Popen("ls -a -l -h".split(), .........)

EDIT: Easiest way, in my opinion, it to output to a text file, open it, read for what you need, and process accordingly.

---

