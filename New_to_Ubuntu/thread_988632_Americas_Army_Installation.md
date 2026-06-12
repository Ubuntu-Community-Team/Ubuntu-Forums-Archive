---
title: "Americas Army Installation"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by JumpForJoy on 2008-11-20
I installed the linux version of Americas Army.  I then ran the program I downloaded, and it created the dir.  But when I try to run armyops, it show the below error.  Why is this?  How can I fix it?
Thanks.

```
./armyops-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
```

---

### Post by ibuclaw on 2008-11-20
What arch are you running? 32 or 64bit?
run:
```
uname -m
```

For 64bit, I know stdc++.so.5 is in the **ia32libs** packages.

You could also try this here:
[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

It's called getlibs, it scans the libs that the binary needs (as found out by running **ldd armyops-bin**) and downloads/installs the missing dependencies for you.

Also, to memory AA uses openAL, so make sure that these dsp and mixer devices exist.
```

/dev/dsp
/dev/mixer

```
else, create a softlink to them.

And make sure that no software is using the sound devices either, else you won't get any sound.
running:
```

lsof /dev/dsp

```
will tell you that.

If you get any problems, or are unsure about anything, just reply back on what you aren't sure about.


Regards
Iain

---

### Post by JumpForJoy on 2008-11-21
I ran:
```
uname -m
```
and got:
```
i686
```

I ran:
```
ldd /usr/local/games/armyops/armyops
```
and got:
```
not a dynamic executable
```

As for how to run getlibs:
I ran:
```
getlibs /usr/local/games/armyops/armyops
```
and got:
```

Cannot determine the dependencies required by this program, it may be a script:
If this program needs a 32-bit library use:
getlibs -l i386librarytoinstall.so
If this program needs a 64-bit library use:
getlibs -64l amd64librarytoinstall.so

```

I then ran:
```
getlibs -l i386librarytoinstall
```
and got:
```
No match for i386librarytoinstall
```

How can I run getlibs.
As for the other stuff.  I'm not sure how to do it.
thanks.

---

### Post by ibuclaw on 2008-11-21
OK, one step at a time ;)

The file **armyops** is a shell script:

```
file armyops 
armyops: POSIX shell script text executable

```

cd into the **System** directory and run getlibs on armyops-bin


```
cd /usr/local/games/armyops/System
sudo getlibs armyops-bin

```

Regards
Iain

---

### Post by JumpForJoy on 2008-11-24
Ok.  Thanks.  So I ran the program and
```
This application isn't missing any dependencies
```

Thanks.  What's next?

Sorry I was away for a few days...

---

### Post by ibuclaw on 2008-11-24
No probs... and just out of sheer luck, I happened to review this page again at the exact same time ;)

OK, since you are running 64bit Ubuntu, I suggest that you should check that ia32libs is installed.

```
sudo apt-get install ia32libs
```
As that is where the libstdc++.so.5 file is.

Give me a minute or two, I'll just boot up the machine with AA installed. And I'll check for any amendments that I may have made.

Regards
Iain

---

### Post by ibuclaw on 2008-11-24
OK, what does this output?
```
ls -l /usr/lib32/libstdc++.so.5
```

Regards
Iain

---

### Post by JumpForJoy on 2008-11-24
Ok, as for the first of your 2 post.  I couldn't run that line.
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package i32libs
```
that happend
this kept me from doing #2
thanks

sry I didn't expect such a quick return.  :-)  thanks

---

### Post by ibuclaw on 2008-11-24
Yeah, I always try to reply swiftly :D

As for replying to your post; it's not i32libs... it's **ia32libs**.

To paste what I post into a terminal, use **Ctrl+Shift+V**.
[EDIT]
Sorry, my bad ... there is a hifen in it too :P
```
sudo apt-get install ia32-libs
```
Try again ;)

Regards
Iain

---

### Post by JumpForJoy on 2008-11-24
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ia32libs
```

nope...  I also belive that I chose 32 bit not 64 when I downloaded and installed ubuntu, but I'm not sure...

I apriciate your help.  And how quick you are

---

### Post by JumpForJoy on 2008-11-24
AWSOME.  I was looking at AA webpage and
[http://forum.americasarmy.com/viewtopic.php?t=139483](http://forum.americasarmy.com/viewtopic.php?t=139483)
I don't know if it will help.  I'm looking at it now....
thought you might want to know to,
Your so fast.  I apreiciate it so much..
thx

---

### Post by ibuclaw on 2008-11-24
> **JumpForJoy said:**
> 
nope...  I also belive that I chose 32 bit not 64 when I downloaded and installed ubuntu, but I'm not sure...

I apriciate your help.  And how quick you are

Ah, sorry about that... I don't know where that confusion came from.

Yes, I had a look at what you posted a few days ago and indeed you are running the 32bit Ubuntu.

ok, then you just need to check that the libstdc++5 libraries are installed.
```
sudo apt-get install libstdc++5
```
Again, sorry about that.

Hopefully that confusion is now behind us.

Regards
Iain

---

### Post by JumpForJoy on 2008-11-24
AHHH it worked.  that website kinda helped but not much.  Thank you.  so I have the program now.  What's next.  And I don't mind the confusion.  As long as you can help me work things out in the end:-)

---

### Post by ibuclaw on 2008-11-24
Does the application start ?

Is there any sound ?

If it starts, run **armyops** in the terminal and quit it once it loads, then post any output that it may print out.

What I found with my setup was that I had to kill all applications that were using my soundcard before I could hear sound from AA.

Regards
Iain

---

### Post by JumpForJoy on 2008-11-24
no nothing started after I installed it.  How do I run it?  no sound eiter.

---

### Post by ibuclaw on 2008-11-24
Did you run
```
armyops
```
In the term? Does it give out any errors?

Regards
Iain

---

### Post by JumpForJoy on 2008-11-29
THANK YOU.  I got it running.
After I ran it then exited I got:
```
Cheat protection disabled
WARNING: ALC_EXT_capture is subject to change!
Xlib:  extension "XiG-SUNDRY-NONSTANDARD" missing on display ":0.0".
```
I didn't have a problem with my sound.  I heard all the noise.  Also is their any way to add aa in my applications->games file?

Thanks,
JFJ

PS  Sry I was away for Thanksgiving(grandma's)

---

### Post by ibuclaw on 2008-11-29
Cools, that message looks fine, as long as it starts and is usable. That should be all things good to go :)

To create a desktop menu item, create a file in ~/.local/applications/share called **armyops.desktop**

```

mkdir -p ~/.local/share/applications
gedit ~/.local/share/applications/armyops.desktop
```

And put in something like this:
```

[Desktop Entry]
Name=AArmy
Comment=First Person Army Ops Multiplayer
Exec=armyops
Terminal=false
Type=Application
Categories=Game;ArcadeGame
Encoding=UTF-8
Icon=/usr/local/games/armyops/ArmyOps.xpm

```
Save and quit.

Then check your applications menu again under "Games"

Regards
Iain

---

### Post by JumpForJoy on 2008-11-30
Great, thank you for all of your help!  I appreciate it greatly.
:guitar:
you rock!

---

### Post by dehyde on 2010-05-03
hi, this doesn't work for me.
i installed the .deb file but still get this error:

./armyops-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

any ideas? 

:confused:

---

