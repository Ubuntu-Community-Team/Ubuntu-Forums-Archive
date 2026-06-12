---
title: "Help with init.d script needed please"
date: 2010-02-19
forum: Programming Talk
---

### Post by love to learn on 2010-02-19
Hi Guys...and sorry admin this is a double-post as i picked the wrong category to post my initial request to.:roll:

I have a program which i wrote using sdl and i am trying to start it on boot using init.d.
The prog runs fine if run from the terminal but i cant get it to run on startup.

I first created a file in init.d called myprog which looks like this:

```

#! /bin/sh

su myuser -c /home/myuser/myprogs/./myprog

exit 0

```

Then i did      sudo update-rc.d -f myprog defaults
followed by sudo shutdown -r now
and myprog doesnt start after startup.

file permissions on the myprog file in init.d is 755.

The program does require the x server to be running.

Please help!

---

### Post by Zugzwang on 2010-02-19
I would like to propose the following. Check if you get any error when running the program on startup. Modify your starting script as follows:
```

#! /bin/sh

su myuser -c /home/myuser/myprogs/./myprog > /home/myuser/runlog.txt 2>&1

exit 0

```

Then examine the content of that runlog file after startup.

Probably it doesn't work because it is run too early in the booting process.

---

### Post by love to learn on 2010-02-19
Yes you are correct.
The log reports that sdl directfb could not initialise so i assume this means it is trying to run the prog before x is running?

How do i make my program run only after the x server is running?

btw what does that 2>&1 do?  where can i read up about those options?

And thanks for the prompt response.  I have been fighting with this for 2 days now :D

---

### Post by ajgreeny on 2010-02-19
Add a sleep command to the command in the script file that gives time for the GUI to appear, ie
```
sleep 60; su myuser -c /home/myuser/myprogs/./myprog > /home/myuser/runlog.txt 2>&1
```I don't know for certain what the last bit of the command means, but I think it is just a logging system to show you what is happening on running that script so you can try to put it right if it does not work.

---

### Post by dwhitney67 on 2010-02-19
> **love to learn said:**
> 
How do i make my program run only after the x server is running?

Step one is to define (that is, place) your script in /etc/init.d.  Step two is to create a symbolic link to it within /etc/rc5.d, using some name similar to 'S99myscript'.
```

cd /etc/rc5.d
ln -s ../init.d/myscript S99myscript

```
You are probably pondering the question of why the rc5.d directory?  Well, init level 5 is where X11 is started, and rc5.d not only contains the necessary scripts to launch X11, but all other scripts necessary to bring your system to "life".

P.S.  If your system will always boot with X11 running, then you might want to consider calling your script from within the file /etc/rc.local.  If your system will boot, but without X11 support, then it will probably be using init level 3, which summons the scripts in /etc/rc3.d.

--------

EDIT:  Upon examining my own system, I can't see any differences between /etc/rc3.d and /etc/rc5.d.  Perhaps my knowledge of how the init levels are done is dated, including when X11 is started.

---

### Post by love to learn on 2010-02-19
Thanks for all the prompt response.

dwhitney i did update-rc.d -f myprog remove to remove all the symbolic links created from my first attempt and installed a symbolic link in rc5.d the way you suggested.
It works... however the log now says :

su: must be run from a terminal

If i remove the su i will be running the program as root ,correct?

Can a program be run as a normal user from the init scripts?

Much appreciated
Deon

---

### Post by dwhitney67 on 2010-02-19
> **love to learn said:**
> 
If i remove the su i will be running the program as root ,correct?

Yes, remove the 'su' because those scripts are always run as 'root'.

> 
Can a program be run as a normal user from the init scripts?

No.  Regular users should place their scripts in their home directory (folder) and launch it using ummm... I forgot.  I think it should be placed in ~/.bash_profile or something like that.

---

### Post by love to learn on 2010-02-19
oops  this is the point where i start feeling a bit stupid :frown:

Because the log was complaining about the 'su' command i removed it as suggested.

The new script looks like this now:

```

#! /bin/sh

/home/myuser/myprogs/./myprog > /home/myuser/runlog.txt 2>&1

exit 0


```

Now ,  when i reboot , it doesnt even write the logfile.

Is there something i am omitting in my script perhaps?

---

### Post by dwhitney67 on 2010-02-19
Manually run the script, in /etc/rc5.d, using sudo.  What are the results?

From looking at the script you posted, there's nothing wrong with it.

Btw, what is the compelling reason for running this user-owned script as root during the start up of your computer??  Could it not be run once the user has logged in?

P.S.  I just read your original post.  Does this script start an SDL application?  I'm not 100% familiar with the requisites for X applications, but I believe you need an open X11 session, which you won't have until you log in.

---

### Post by love to learn on 2010-02-19
I am attempting to make a gamebox which will boot up to a menu (which i wrote using SDL) where one selects the game.

Running it from a terminal with sudo /etc/rc5.d/S99myprog works, so at least the script and symlink are operating ok.

I am busy reading [http://www.debian.org/doc/debian-policy/ch-opersys.html#s-sysvinit](http://www.debian.org/doc/debian-policy/ch-opersys.html#s-sysvinit) at the moment.Im sure i will find some clues in that doc too.

Yes it looks like i need to be logged on. sheesh.

Thanks dwhitney you have been of great assistance.

---

### Post by dwhitney67 on 2010-02-19
> **love to learn said:**
> 
Yes it looks like i need to be logged on. sheesh.

Call your script from within ~/.bash_profile.  Make sure you run it in the background.  For example:
```

~/myprogs/myprog &

```

---

### Post by love to learn on 2010-02-19
Thanks again dwhitney.

I do however have one last question for you...
How do i mark this question as solved ;)

---

### Post by dwhitney67 on 2010-02-19
Look for the pull-down menu at the top; I rarely ever post a new thread on this forum, so I don't quite remember.

---

