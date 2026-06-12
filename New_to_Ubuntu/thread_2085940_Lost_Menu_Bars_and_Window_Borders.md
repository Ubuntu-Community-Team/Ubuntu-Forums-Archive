---
title: "Lost Menu Bars and Window Borders"
date: 2012-11-19
forum: New to Ubuntu
---

### Post by dwdarkstar on 2012-11-19
[LIST]
[*]10.04 LST
[*]No mouse at login
[*]No menu bars top or bottom in desktop
[*]No max/min border around windows
[*]Logging in Guest account displays same symptoms
[/LIST]

Not sure whats going on.  Can't access System Prefs to check resolution or create new user.  Any help?

---

### Post by dannyboy79 on 2012-11-19
try alt-F2 and type in 
```
metacity --replace
```

---

### Post by dwdarkstar on 2012-11-19
```
farstar@go-bot:~$ metacity --replace
metacity: error while loading shared libraries: libvorbis.so.0: cannot dynamically load executable
```

---

### Post by dwdarkstar on 2012-11-19
Any other thoughts?

---

### Post by dannyboy79 on 2012-11-20
Where did you enter that command? Are you able to login to the ubuntu desktop manager or are you only able to login to a tty terminal session?

Are you using compiz?

---

### Post by dwdarkstar on 2012-11-20
The command was issued in terminal.  Yes I can login to my desktop, although there is no mouse I can TAB between users and hit ENTER to type my psswd.  Once in I created a dummy launcher to get to terminal.  I don't believe I'm running compiz as before I posted this thread I searched the forums and tried multiple solutions including this:
```

cd /usr/bin
sudo ln -s compiz compiz.real
gnome-session-save --logout

```
There were no errors, however upon logging back in nothing had changed, still no menu bars, no window borders.  What else can I try for you?

---

### Post by dannyboy79 on 2012-11-20
i'm at a loss. I am not sure as this is way over my head. sorry I couldn't help.

you even created a new user and the same problems exist makes me believe your whole OS is screwed to be honest. Normally things like this can be solved by created a new user because these settings are stored within the users home directory but apparently these problems are elsewhere.

---

### Post by dwdarkstar on 2012-11-20
I haven't tried new user creation yet because I don't know how to do it with out the GUI in System-Administration-Users, which I can't access.  Is there a way to do it in terminal?

---

### Post by dannyboy79 on 2012-11-20
here'a a guide for how to do it from a terminal
[http://www.dscripts.net/2010/08/14/how-to-add-users-and-usergroup-in-ubuntu-using-terminal/](http://www.dscripts.net/2010/08/14/how-to-add-users-and-usergroup-in-ubuntu-using-terminal/)

---

### Post by dwdarkstar on 2012-11-20
I created a new user but upon logging in under that account the same symptoms persisted unchanged.

I am hesitant to accept the diagnosis of irreversible OS damage as many GUI functions remain.  However it does not seem to be a hardware issue as the Vista partition functions normally, again suggesting a corruption of 10.04.  In the absence of further suggestions my next thought is whether or not I can upgrade my 10.04 to the latest LST version via bootable disk and maintain all of the data presently held in the 10.04 OS.  Any thoughts on this?

---

### Post by squakie on 2012-11-20
I'm wondering if you"lost" unity.  I had similar symptoms last week when trying to install a game in crossover.  It installed fine, but gave an error at run time about unable to reset device - and it appeared to be the display.  At that time I did the metacity --replace to see what would happen without compiz.  I was able to use the mouse yet, but all the bars, menus, etc., were gone and I had force a restart with the physical power button on the PC.

Perhaps you should try opening a terminal and entering:

compiz --replace

and see what happens.

---

### Post by monkeybrain2012 on 2012-11-20
> **squakie said:**
> I'm wondering if you"lost" unity.  I had similar symptoms last week when trying to install a game in crossover.  It installed fine, but gave an error at run time about unable to reset device - and it appeared to be the display.  At that time I did the metacity --replace to see what would happen without compiz.  I was able to use the mouse yet, but all the bars, menus, etc., were gone and I had force a restart with the physical power button on the PC.

Perhaps you should try opening a terminal and entering:

compiz --replace

and see what happens.

Op is using 10.04, there is no unity. Moreover by the look of it he has not installed compiz.

---

### Post by squakie on 2012-11-20
> **monkeybrain2012 said:**
> Op is using 10.04, there is no unity. Moreover by the look of it he has not installed compiz.

Missed that, and to top it off the compiz --replace doesn't seem to be a good idea when running unity.

---

### Post by squakie on 2012-11-20
If you have created a xorg config file, please post it here.  In addition, please post the output of lsmod (since it seems at least one module isn't loading with metacity and it doesn't say it's aleady loaded).

---

