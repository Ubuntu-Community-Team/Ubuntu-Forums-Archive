---
title: "Add Folder to Path"
date: 2012-03-06
forum: New to Ubuntu
---

### Post by dkinthehouse on 2012-03-06
I want to just be able to type type "python filename.py" and have it execute.  To do that I think i have to add it to the path ubuntu right?

Do I just need to add a directory to the path where I want to store the .py files?  If so, how do I do that?  Sorry, I'm new to this.

---

### Post by souravc83 on 2012-03-06
open up .bashrc and add the path.
To do this, open up the terminal.
then go to /home/user (replace user with whatever your username is)
[HTML]cd /home/user[/HTML] 

then open up .bashrc with gedit

[HTML]gedit .bashrc[/HTML]

then scroll down to the end of the file and add the following lines.

export PATH=$PATH:"path to directory which contains the binaries"

for example, for matlab, I have the following line

[HTML]export PATH=$PATH:/usr/local/MATLAB/R2010bSP1/bin[/HTML]

find the directory you have installed python in, and add this.
However, are you sure that your installation was okay, since most common programs do not require this step.
Try it, and if this does not work, then maybe try and reinstall.

---

### Post by dkinthehouse on 2012-03-07
Awesome.  Really appreciate your reply.   If I cd into the folder then it'll execute the .py files.  I kind of wanted to have the documents directory added to the PATH.  Is that a bad idea?  I tried following your instructions to add /home/dave/Documents to the path but it didn't work for some reason.

This is what I added to the end of the .bashrc file: export PATH=$PATH:/home/dave/Documents

I probably messed something up.

Thanks, really appreciate your help.


Dave

---

### Post by souravc83 on 2012-03-07
You need to add the directory where your python binaries are.
But I am little confused about what you mean.

lets say you have a file called hello.py in /home/Dave/Documents

So, in this case, you will have to cd to /home/Dave/Documents and then execute the file. Is this working?
If this is not working, then the binary is not in the path, and you need to add it, as I replied earlier.

Now, it seems from your previous post that you want to be in any other directory, lets say in home/Dave, and still want to execute the files which are in home/Dave/Documents. This might be possible, but I don't know how to do it.

---

### Post by Diametric on 2012-03-07
To find out what your current path is, just type:

```
echo $PATH
```

It should give something like:  /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

which is a colon delimited list of the directories bash searches when you run a command.  If you wish to add a directory follow the directions of dkinthehouse - but you might want to check with others about the soundness of adding you Document directory to your path.  I don't know if there are any security issues there.

Good luck!

---

### Post by dkinthehouse on 2012-03-07
Yes, when I cd into /home/dave/Documents and execute a .py file that is working now.  Thanks.  I eventually want to figure out how to execute a .py when I'm in a different folder but right now I'm good.  I appreciate the help a lot.

---

### Post by dkinthehouse on 2012-03-07
Thanks Diametric.  I checked out the PATH.  Like you said, souravc83's instructions worked perfectly and /home/dave/Documents is on the Path.  But when I type python filename.py from command line it says the file doesn't exist.  But it does.  Not a big deal.  Sounds like I should maybe remove it for security reasons anyways.

---

