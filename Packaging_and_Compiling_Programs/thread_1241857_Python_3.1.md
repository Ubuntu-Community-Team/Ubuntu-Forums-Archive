---
title: "Python 3.1"
date: 2009-08-16
forum: Packaging and Compiling Programs
---

### Post by seelk on 2009-08-16
Is there a guide that shows how to go by compiling and updating Python to the latest 3.1?  Currently Python 2.6.2 is installed in Jaunty but I would like to update it to 3.1.  Is this possible?  Maybe there's a repository?

---

### Post by DirtDawg on 2009-08-16
> **seelk said:**
> Is there a guide that shows how to go by compiling and updating Python to the latest 3.1?  Currently Python 2.6.2 is installed in Jaunty but I would like to update it to 3.1.  Is this possible?  Maybe there's a repository?

Python 3.0 is in the repositories:
```
sudo apt-get install python3.0
```

I believe Python 3.0 will be installed along side, rather than replace, Python 2.6.

If you really need 3.1, you will probably need to compile it from source.

---

### Post by trilobite on 2009-08-17
> **DirtDawg said:**
> Python 3.0 is in the repositories:
```
sudo apt-get install python3.0
```

I believe Python 3.0 will be installed along side, rather than replace, Python 2.6.

If you really need 3.1, you will probably need to compile it from source.

Agreed, DirtDawg. Actually, 3.1.1 is coming out soon, so that may be worth waiting for. 
Anyway, it's very easy to compile it from source. 

Just grab the tar.bz2 or tar.gz file from python.org, download it to your home directory and do the following on the command-line - 

a) tar -zxvf Python-3.1.tar.gz2 
( or tar -xjvf Python-3.1.tar.bz2 if you get that one ) 
b) cd Python-3.1
c) ./configure
d) make 
e) su make install 
f) make clean ( to clean out all of the unneeded bits after the compile). 

 The compile *can* take a while, iirc (I think it took me between 45 min to an hour or so).  

 Then, all you have to remember is to call it by typing "python3.1" (without the quotes) on the command-line.  Just typing "python" starts the default version (2.6.2 in my Jaunty install). 
- Hope this helps..... :)  
- trilobite

---

### Post by seelk on 2009-08-17
Thank you guys for your help.  Question, does the "make install" of the 3.1 source install IDLE 3.1?  If so, I'll take this route.

---

### Post by trilobite on 2009-08-18
> **seelk said:**
> Thank you guys for your help.  Question, does the "make install" of the 3.1 source install IDLE 3.1?  If so, I'll take this route. 

Hi - 
 
 No, IDLE is a separate package, I'm afraid, so you'll need to install that separately. 

 If you're interested in a general IDE (not just for Python), I recommend Geany ([http://www.geany.org](http://www.geany.org)).  It's very easy to use and is really well-designed - not cluttered at all, unlike some other IDEs.  
- trilobite

---

### Post by HorstJENS on 2009-09-26
> **trilobite said:**
> 
e) su make install 


had to type:

```
sudo make install
```

because ```
su
``` was not working.
-Horst

---

### Post by Wink2tall on 2010-02-04
Thanks trilobite! A major help, specially for people new to Ubuntu like me.

---

### Post by MikeyDL on 2010-03-11
Hi, I tried this and was able to compile and install Python 3.1.2.  But when I ran "Python" from the terminal I still got the old 2.6 version.  Do you have to uninstall 2.6 first?  I did a "sudo dpkg -l | grep Python" but came up with allot of packages and didn't want to uninstall on all the different ones that popped up. 

Also was following the readme file and didn't do the clean optioned mentioned above.  Would that have cleaned out the older version?

Thanks!

---

### Post by MikeyDL on 2010-03-11
Actually did a bit more reading on the forums.  There were allot of warnings not to uninstall Python 2.6 because of it's links to other apps and that you could have multiple versions running.  I was reading about just linking the python link in /usr/bin/ to the new 3.1.2 version.  

So i downloaded the latest 3 version from python.org ran through the readme instructions and installed.  But there wasn't a python executible for 3 in /usr/bin like there is for 2.6.  running "Python" from the terminal just seems to run the 2.6 version.  

If you can have multiple versions running how do you run the 3.1 version?  Is there an executible that should be put into /usr/bin?  

Also I extracted the tar into ~/Downloads directory.  Do you need to run the make and config from a specific location to install when you run a compile?  Maybe I just installed it wrong.

---

### Post by Bachstelze on 2010-03-11
> **MikeyDL said:**
> 
If you can have multiple versions running how do you run the 3.1 version?  Is there an executible that should be put into /usr/bin? 

You run Python 3.1 by typing [font=monospace]python3.1[/font] or [font=monospace]python3[/font]. The executable is in [font=monospace]/usr/local/bin[/font].

> **MikeyDL said:**
> Also I extracted the tar into ~/Downloads directory.  Do you need to run the make and config from a specific location to install when you run a compile?  Maybe I just installed it wrong.

No, what you did is fine. And by the way, yes, it did install IDLE 3.

---

### Post by MikeyDL on 2010-03-11
Thanks!  That worked!:p

---

