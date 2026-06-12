---
title: "Execute compiled C++ without &quot;./&quot; ?"
date: 2007-02-25
forum: Programming Talk
---

### Post by Gray Fox on 2007-02-25
Hi I think I have a simple question, I was wondering how to set up the terminal so that when I can execute my compiled C++ programs by simply typing in the program name instead of preceding them with "./" ?
ie "me@compy:~$ foo"
instead of "me@compy:~$ ./foo"

Any help would be appreciated, thank you!

---

### Post by scxtt on 2007-02-25
the directory you're running the program from needs to be in $PATH ...

so if you generally compile in ~/bin, make sure the output of **echo $PATH** includes <current PATH items>:~/bin ... i'm pretty sure ~/.bash_profile does this by default ... so if you create a ~/bin directory it should "just work" ... assuming you use bash ...

---

### Post by Stemp on 2007-02-25
Put your program into /usr/bin, /usr/local/bin etc... in your PATH (echo $PATH)

---

### Post by WW on 2007-02-25
You can add the "current directory" to your path with
> $ export PATH=$PATH:.
Add this command to **.bashrc** in your home directory if you always want **.** to be in your path.

---

### Post by Gray Fox on 2007-02-25
> **WW said:**
> You can add the "current directory" to your path with

Add this command to **.bashrc** in your home directory if you always want **.** to be in your path.

Ok that worked!  I put "export PATH=$PATH:/home/user/bin" in there and now its working.
Do I have to do this for any sub-directories I may create in the future in this new bin dir?

---

### Post by yabbadabbadont on 2007-02-25
> **Gray Fox said:**
> Ok that worked!  I put "export PATH=$PATH:/home/user/bin" in there and now its working.
Do I have to do this for any sub-directories I may create in the future in this new bin dir?

Yes.  Just like you would have to do in DOS, Windows, OS/2, ...  :D

---

### Post by Gray Fox on 2007-02-25
> **yabbadabbadont said:**
> Yes.  Just like you would have to do in DOS, Windows, OS/2, ...  :D
Heh I wasn't sure, my schools servers seem to automatically allow the ./-less running of compiled programs by default.

Anyway thanks for all the helps guys!

---

### Post by yabbadabbadont on 2007-02-25
> **Gray Fox said:**
> Heh I wasn't sure, my schools servers seem to automatically allow the ./-less running of compiled programs by default.

Anyway thanks for all the helps guys!
That just means that they include the current directory '.' in your PATH by default.  That used to be normal for all non-root users until just a few years ago.  Apparently it is considered a security risk, so the various Linux distributions started dropping '.' from the default non-root user PATH.

---

### Post by skeeterbug on 2007-02-26
So much work for two extra characters you have to type (that happen to be located right next to each other on the keyboard). :P

---

### Post by lloyd mcclendon on 2007-02-26
> **WW said:**
> You can add the "current directory" to your path with

Add this command to **.bashrc** in your home directory if you always want **.** to be in your path.

NO that is a bad idea.  i'm surprised you haven't heard of this from unix 101.

what if i come on there and do $ echo "rm -rf /*" > ls ; chmod 755 ls 

then you stumble into the current directory and type $ ls .. what do you think happens?  you never put the current directory in the path, just type the ./ it's only 2 f'ing keystrokes!

---

### Post by Gray Fox on 2007-04-28
> **lloyd mcclendon said:**
> NO that is a bad idea.  i'm surprised you haven't heard of this from unix 101.

what if i come on there and do $ echo "rm -rf /*" > ls ; chmod 755 ls 

then you stumble into the current directory and type $ ls .. what do you think happens?  you never put the current directory in the path, just type the ./ it's only 2 f'ing keystrokes!
Yes it may only be two keystrokes but on QWERTY keyboards they are some of the most awkward keys to hit, especially one after the other.  At least for me.  I dunno.

I just ended up adding making a /home/user/bin dir and adding that to path, restricting it to one directory instead of making it a catch all.

---

