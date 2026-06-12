---
title: "[SOLVED] Why doesn't chmod 111 let me execute?"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by Znupi on 2008-09-09
I chmod'ed a file to 111 (which should let anyone execute the file), but it can't be executed. It says permission denied. Why?

---

### Post by jemate18 on 2008-09-09
> **Znupi said:**
> I chmod'ed a file to 111 (which should let anyone execute the file), but it can't be executed. It says permission denied. Why?

the file might be owned by root
 try
> sudo chmod 111 yourfile

---

### Post by vishzilla on 2008-09-09
The right way to set permission will be ```
sudo chmod 777 OR 555 *filename*

``` with 111 you wont be able to read or write the file (if needed)

---

### Post by iaculallad on 2008-09-09
Or:

```
sudo chmod a+x filename
```

---

### Post by pansz on 2008-09-09
you should chmod 555

since anyone must be able to read the file in order to execute it.

---

### Post by Znupi on 2008-09-09
No, the file is owned by my user. Also, the chmod functions does not give any errors as it would give if I didn't have permission to change permissions on the file. Also, if I ls -l, the file's permissions look like this: ---x--x--x which means any user can execute it, right? Well, I can't execute it, it says permission denied. :confused:

---

### Post by jemate18 on 2008-09-09
> **Znupi said:**
> No, the file is owned by my user. Also, the chmod functions does not give any errors as it would give if I didn't have permission to change permissions on the file. Also, if I ls -l, the file's permissions look like this: ---x--x--x which means any user can execute it, right? Well, I can't execute it, it says permission denied. :confused:

> chmod 777 yourfile it will give -rwxrwxrwx

---

### Post by Flimm on 2008-09-09
Why would you give it execute permissions without read permissions? Give it both. (chmod 555)

---

### Post by jemate18 on 2008-09-09
I think to be able to execute you must also have a read access.

rwxrwxrwx by 777
or
r-xr-xr-x by 555

---

### Post by Znupi on 2008-09-09
> **pansz said:**
> you should chmod 555

since anyone must be able to read the file in order to execute it.
That works indeed, and I have thought of it, too. But my question is how do I make a file which upon double-click in nautilus doesn't bring up the "Do you want to run "xxx", or display its contents?" but instead executes it directly. With my rational sense, setting its permission to 111 should do the trick, but it doesn't.

---

### Post by Cadmus on 2008-09-09
It's because you've got to be able to read a file in order to execute it.

I agree it's not obvious, but you can see a situation where you would want read but not execute, such as a text file.

---

### Post by jemate18 on 2008-09-09
> **Znupi said:**
> That works indeed, and I have thought of it, too. But my question is how do I make a file which upon double-click in nautilus doesn't bring up the "Do you want to run "xxx", or display its contents?" but instead executes it directly. With my rational sense, setting its permission to 111 should do the trick, but it doesn't.

what type of file is it?

1. right click on the file
2. Click properties
3. Select Open With tab
4. If what you intend can be opened by the application on the list, click it.
5. If not, then click the add button and find what software/app you need to open your file.

---

### Post by iaculallad on 2008-09-09
You could just create a launcher for that script.

---

### Post by Vivaldi Gloria on 2008-09-09
> **Znupi said:**
> I chmod'ed a file to 111 (which should let anyone execute the file), but it can't be executed. It says permission denied. Why?

It must first read it to execute it. But you didn't give read permissions. Hence the result you get.

Need at least 5 digit to execute.

---

### Post by vishzilla on 2008-09-09
Create a launcher if you do not want to display the dialog box

---

### Post by Znupi on 2008-09-09
It's a shell script which launches a python program. How can I create a launcher for it? What exactly is a launcher? Is it a regular file or some special type of file? Can I place it in the same directory as the script? Thanks :)

---

### Post by Znupi on 2008-09-09
> **Znupi said:**
> It's a shell script which launches a python program. How can I create a launcher for it? What exactly is a launcher? Is it a regular file or some special type of file? Can I place it in the same directory as the script? Thanks :)
Nevermind, I got it. Thanks!

---

### Post by DezSP on 2008-09-09
> **Znupi said:**
> It's a shell script which launches a python program. How can I create a launcher for it? What exactly is a launcher? Is it a regular file or some special type of file? Can I place it in the same directory as the script? Thanks :)

Can't you just launch the python script directly? You only need to put

#/usr/env/python

As the first line of the file and make it executable.

---

### Post by Flimm on 2008-09-09
> **DezSP said:**
> Can't you just launch the python script directly? You only need to put

#/usr/env/python

As the first line of the file and make it executable.

You forgot the exclamation mark:
#!/usr/env/python

And the recommended line to add is actually:
#!/usr/bin/env python

---

### Post by Trail on 2008-09-09
On another note, Nautilus used to have an option somewhere where it asked whether to execute, edit or ask whenever it encountered a script file. Maybe you should change that setting.

---

### Post by DezSP on 2008-09-09
> **Flimm said:**
> You forgot the exclamation mark:
#!/usr/env/python

And the recommended line to add is actually:
#!/usr/bin/env python

Whoopsie. :D

---

