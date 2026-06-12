---
title: "Running Python Programs from Arbitrary Directory"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by Umenzi on 2008-08-11
I am just getting situated in Ubuntu, and I am having trouble running python programs. I've used python on other systems before.
The trouble is, when I try to run a python program from the terminal, it ends up like this:
```
$ python helloworld.py
python: can't open file 'helloworld.py': [Errno 2] No such file or directory
```

That is, of course, when I have helloworld.py stored somewhere besides my user folder. It works in my user folder, but I would rather not keep python programs there. It also works when I change the terminal directory:
```
cd ~/Desktop/Folder
python helloworld.py
Hello, World!
```

But is there a way to conveniently run python programs from a separate folder, without having to change the terminal directory?

FYI, I have tried sys.path.append(), PATH=$PATH:, and yes, the first line of code is #!/usr/bin/python

Thanks,
Umenzi

---

### Post by ad_267 on 2008-08-11
You can put them in ~/bin or in /usr/bin or you can modify your path. Not your python path but your bash path. In a terminal enter:
```
PATH=$PATH:/home/your_user_name/Desktop/Folder
```

I just put all my scripts in ~/bin which should already be in your path.

---

### Post by adult swim on 2008-08-11
also you can type in a terminal
```
echo $PATH
``` and it will give you all of the directories that it will check for your hello world file.  if you move it to one of the directories that is displayed it will work.

---

### Post by Umenzi on 2008-08-12
PATH=$PATH:x

Doesn't seem to work, nor does copying my python file into one of the directories already listed in "echo $PATH". Also, the new directory will show up in echo, but it won't find files from there. I'm confused, by for now I guess I'll just change my terminal directory.

---

### Post by ad_267 on 2008-08-13
Ahh I think I get what you're doing wrong now.

You need to put as the **very first** line in your python file:
```
#!/usr/bin/env python
```

And then don't run the script with "python helloworld.py", just use "helloworld.py"

---

### Post by kpkeerthi on 2008-08-13
... and make sure helloworld.py is executable. ```
chmod u+x helloworld.py
```

---

### Post by Decommissioner on 2009-08-02
I was having the same problem as the above users, and not saving it to the desktop seemed to work, except for the fact that I am greeted with a new error message that reads as follows:

```
python helloworld.py
  File "helloworld.py", line 1
    Python 2.5.4 (r254:67916, Apr  4 2009, 17:55:16) 
             ^
SyntaxError: invalid syntax

```

I know I am running 2.6.2, So what does this even mean?

---

### Post by ad_267 on 2009-08-03
You probably should have started a new thread rather than resurrecting this old one. What does the first line of your file look like? It shouldn't say "Python 2.5.4" so delete that if it does. It should only say "#!/usr/bin/env python"

---

### Post by colau on 2009-08-31
> **Umenzi said:**
> I am just getting situated in Ubuntu, and I am having trouble running python programs. I've used python on other systems before.
The trouble is, when I try to run a python program from the terminal, it ends up like this:
```
$ python helloworld.py
python: can't open file 'helloworld.py': [Errno 2] No such file or directory
```

That is, of course, when I have helloworld.py stored somewhere besides my user folder. It works in my user folder, but I would rather not keep python programs there. It also works when I change the terminal directory:
```
cd ~/Desktop/Folder
python helloworld.py
Hello, World!
```

But is there a way to conveniently run python programs from a separate folder, without having to change the terminal directory?

FYI, I have tried sys.path.append(), PATH=$PATH:, and yes, the first line of code is #!/usr/bin/python

Thanks,
Umenzi

Can you post your complete code?

---

