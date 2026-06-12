---
title: "How to get Komodo working"
date: 2008-03-26
forum: Programming Talk
---

### Post by brijith on 2008-03-26
hai friends,

       I am a python professional. In my company we are using Dedian. But I am a UBUNTU fan and I personally use Ubuntu in my home. I succeeded in setting up all those packages and software that I use in my office except my favourite editor Komodo. Actually Komodo does not come along with Debain I have Downloaded it. And installed using an install script given with it. But When I tried to install it in Ubuntu it resulted in Error. Some how I installed Komodo by changing the install script that they given. But when took komodo it says some files missing.
       
       Can any body suggest me how to install these kinds of packages which are not included in UBUNTU. Or can anyone suggest a Good editor that will do what Komodo does for me. (Komodo has very effective code completion)
       
[COLOR="Sienna"]**Thanks In Advance**[/COLOR]

---

### Post by stevescripts on 2008-03-26
Have you tried support on Activesate?

[http://www.activestate.com/Products/komodo_ide/index.mhtml](http://www.activestate.com/Products/komodo_ide/index.mhtml)

Steve

---

### Post by scruff on 2008-03-31
Do you know what the error was? I use Komodo and I only had to run the install script to get it up and running.

---

### Post by brijith on 2008-03-31
When I tried to Run the install script it was saying a file can not be found. Sorry I can't remember the name of file. I can not check it right now because I am away from my home. only during weekend I used to go home. Any why it is not even starting installation. But the thing is I can locate the file in the then path specified in the error message. I will try to gather more info about the error and post it here. Hope you can help me.

[COLOR="Red"]**Thanks**[/COLOR]

---

### Post by scruff on 2008-03-31
No problem. Just post the error when you get time.

---

### Post by brijith on 2008-04-07
Hai When I run ./install.sh I got 

```
./INSTALLDIR/lib/python/bin/python: 4 ./INSTALLDIR/lib/python/bin/python2.5 not found
```

Any idea why it says like this ?


**[COLOR="Red"]Thanks[/COLOR]**

---

### Post by scruff on 2008-04-07
Well quick guess off the top of my head is there is a problem creating the INSTALLDIR during setup. Perhaps you are trying to put it somewhere that requires root privs?

Here is the directory structure of my install, which I just put under my home dir, since I am the only one using it. As you can see, that path does exist here:

```

sesulliv@sesulliv-laptop:~$ ls -l Komodo-IDE-4/lib/python/bin/python2.5
-rwxr-xr-x 1 sesulliv sesulliv 10990 2008-03-24 07:00 Komodo-IDE-4/lib/python/bin/python2.5

```

Those directories/files should be created during install. I'm at work right now, but if this doesn't help you attach the install script to this thread so I can take a quick look at it.

-Sean

edit - also, let me know what steps you take before getting to this point!

---

### Post by brijith on 2008-04-07
Hai,

Let me explain what i did.

[LIST=1]
Extracted the file I downloaded to my desktop[/LIST]
[LIST=2]
And became SU in the terminal[/LIST]
[LIST=3]
And then executed the install script ./install.sh[/LIST]

          then comes the message that I posted in my previous post

But there in Debian didn't find any difficulty in installing it with the same download

and the same procedure above

I used to Install komodo in /usr/shsre/komodo/


Please check the attachment. I am attaching the install script that I have

Sorry if am interrupting,

**[COLOR="Red"]Thanks[/COLOR]**

---

### Post by scruff on 2008-04-10
cd into the activestate directory that you had untarred and try listing that directory to see if it exists.

```

ls -l lib/python/bin/

```

All I can think of is an incomplete download, which incidentally just happened to me last week when installing Komodo. Firefox said it was complete, but the tarball was only like 14mb rather than 39mb...

---

### Post by brijith on 2008-04-10
I have navigated to the path given in the error message. I can find the files there.
but I can't under stand why it says it does not exist.

**[COLOR="Red"]Help me please[/COLOR]**

---

### Post by Sunon on 2008-06-25
I don't know if this will be valuable to the original poster since it was awhile ago, but I just had this issue with installing Komodo on 64 bit Ubuntu.

I resolved the issue by installing 2 packages

sudo apt-get install lib32stdc++6
sudo apt-get install ia32-libs

---

### Post by brijith on 2008-06-26
> **Sunon said:**
> I don't know if this will be valuable to the original poster since it was awhile ago, but I just had this issue with installing Komodo on 64 bit Ubuntu.

I resolved the issue by installing 2 packages

sudo apt-get install lib32stdc++6
sudo apt-get install ia32-libs


Thank You Very Much,

Me too is using 64 bit Ubuntu. Now I am from my office I will definitely try this when I go home..

---

### Post by ajjublr on 2010-03-16
Sunon,

I have the same problem, as u said I tried, but lib32stdc++6 & ia32-lib are not found, it says "E: Couldn't find package lib32stdc++6" & "E: Couldn't find package ia32-lib"

any help?

Thanks

---

