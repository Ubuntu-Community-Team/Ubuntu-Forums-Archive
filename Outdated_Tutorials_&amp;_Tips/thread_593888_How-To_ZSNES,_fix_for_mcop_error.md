---
title: "How-To: ZSNES, fix for mcop error"
date: 2007-10-27
forum: Outdated Tutorials &amp; Tips
---

### Post by FranMichaels on 2007-10-27
Alright, so you had ZSNES working fine, then upgraded to Gutsy, suddenly no go...

So you go to terminal and type zsnes, and you see some arcane message about mcop and being unable to create a link.

This takes care of it:
*Just cut and paste this line into terminal, and hit enter.*

```
mkdir -p $HOME/.kde/socket-$HOSTNAME && chown -hR $USER $HOME/.kde && chmod 755 -R $HOME/.kde
```
Special thanks to mastahkillah666 for more readable terminal commands

it will make the directory zsnes looks for, then makes sure it's owned by your username, and that its permissions match those of the home folder.

Another fix (probably the *TRUE* fix, but it requires superuser privilege)
Big thanks to Fibonacci for posting it, and mastahkillah666 for a great lesson in bash scripting.

```
sudo sh -c 'echo "default_driver=alsa" > /etc/libao.conf'
```

This one makes the single variable in libao.conf set to alsa, not that mysterious alsa9

How about that? :razz:

Happy emulating! :KS

FYI: I've used both fixes in regard to testing, so you can use either fix or both without worry. :)

---

### Post by rainontin on 2007-11-02
Thanks, worked like a charm

---

### Post by Fibonacci on 2007-11-12
There is another way which has worked for me.
Search for the following line in /etc/libao.conf:
```
default_driver=*something*
```
And change it to:
```
default_driver=alsa
```
(make sure it says exactly "alsa" and not "alsa09" or something else). It appears that libAO tries to use aRts for sound (which, by the way, it shouldn't), causing strange errors when the aRts daemon is not running - that's the reason ZSNES works fine when a KDE application is running at the same time. This will force libAO to use ALSA instead.

---

### Post by nuir on 2007-11-14
It worked for me, thanx! :D

---

### Post by Gatesuka on 2007-12-19
Thank you very much Fran and Fibo :)

---

### Post by libertas on 2007-12-23
thanks a bunch

---

### Post by VegaOmega on 2008-01-16
I love this community... I don't think I've spent more than 15 minutes on any problem I've had since discarding the precious MS OS.
Thanks so much... SNES9X wasn't playing .smc files

---

### Post by h-town on 2008-01-26
Ok I have the exact same problem with zsnes, I entered sudo zsnes and got the same mcop directory thing that he had. Can someone explain to me how to do what fibbonaci says:

> There is another way which has worked for me.
Search for the following line in /etc/libao.conf:
Code:

default_driver=something

And change it to:
Code:

default_driver=alsa

(make sure it says exactly "alsa" and not "alsa09" or something else). It appears that libAO tries to use aRts for sound (which, by the way, it shouldn't), causing strange errors when the aRts daemon is not running - that's the reason ZSNES works fine when a KDE application is running at the same time. This will force libAO to use ALSA instead.

any help would be greatly appreciated. :)

---

### Post by |Jasp| on 2008-01-30
Thanks for the fix!!

h-town:
     I do not know about the method you are asking.  However, I may be able to help clarify the original fix.  After all, it did take me a few tries to get it right.

After you open Terminal and type "zsnes" and get the error, notice the message you receive says something like: "not able to create directory.../home/"something"/.kde/socket-"something"

Well, after the error shows up, type: mkdir /home/"something"/.kde/socket-"something"

Notice - you mkdir the exact same file path that terminal could not create.  

Then copy the other two lines character for character and space for space.  

Hope this helps!

---

### Post by mastahkillah666 on 2008-02-10
There is a more 'elegant' solution to the problem  8)  :

Instead of creating a directory, we will create a link of the socket to the /tmp directory and pointing it to null by typing in a terminal : 

```
lnusertemp socket >/dev/null
```You can also create such "links" not only for kde resource sockets, but also for its resource cache (lnusertemp cache >/dev/null) and its tmp (lnusertemp tmp >/dev/null).

Hope it 'helps' (even if the problem is indeed resolved with mkdir)  ;)  .

---

### Post by erginemr on 2008-02-14
Alternatively, you may consider installing the zsnes version from [www.getdeb.net](www.getdeb.net), which should work without any problems. 

The following thread is also focused on ZSnes:
[http://ubuntuforums.org/showthread.php?t=605199&page=2](http://ubuntuforums.org/showthread.php?t=605199&page=2)
where I have explained how to install the getdeb.net version of ZSnes. 

The funny thing is, that thread links here in return. So I think I have just created an infinite loop; a fracture in the time-space continuum... :popcorn:

---

### Post by couzin2000 on 2008-02-14
I know this sounds redundant, but I was stumped many times before the problems were fixed -- that's right, there were many.

So I did find what I needed to do from this thread, so thanks to both of you. However, because I had a hard time doing what was supposed to be done, I want to write it down so that everyone understands.

Here is the code as I got it:
```
sebastien@sebastien-desktop:~$ zsnes
ZSNES v1.51, (c) 1997-2007, ZSNES Team
Be sure to check http://www.zsnes.com/ for the latest version.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE.TXT' thoroughly before doing so.

Use ZSNES -? for command line definitions.

Starting Mouse detection.
Unable to poll /dev/input/event5. Make sure you have read permissions to it.
Unable to poll /dev/input/event6. Make sure you have read permissions to it.
Unable to poll /dev/input/event4. Make sure you have read permissions to it.
Unable to poll /dev/input/event2. Make sure you have read permissions to it.
Unable to poll /dev/input/event3. Make sure you have read permissions to it.
Unable to poll /dev/input/event1. Make sure you have read permissions to it.
Unable to poll /dev/input/event0. Make sure you have read permissions to it.
ManyMouse: 0 mice detected.
Creating link /home/sebastien/.kde/socket-sebastien-desktop.
can't create mcop directory
sebastien@sebastien-desktop:~$ mkdir ~/.kde/socket-sebastien-desktop
sebastien@sebastien-desktop:~$ sudo chown -hR `id -n -g` ~/.kde
sebastien@sebastien-desktop:~$ sudo chmod 755 -R ~/.kde
sebastien@sebastien-desktop:~$

```

At this point, it still didn't work. So I went in and wrote this:
```

sebastien@sebastien-desktop:~$ sudo gedit /etc/libao.conf

```
and changed the contents of the opening .conf file to this:
```
default_driver=alsa
```
I then saved the text file and went back to terminal. Wrote ```
zsnes
``` and it worked fine.

There you have it! Thanks to everyone!

---

### Post by rzrgenesys187 on 2008-02-16
The debian package worked for me.  Compiling from source also worked

---

### Post by mastahkillah666 on 2008-02-16
Has anyone tried my fix (links instead of creating directories)?  If you didn't, you could give it a try - fix in previous post.

See you around the forums...

---

### Post by erginemr on 2008-02-16
> **mastahkillah666 said:**
> Has anyone tried my fix (links instead of creating directories)?  If you didn't, you could give it a try - fix in previous post.

See you around the forums...

I think your suggestion turned out to be too **"elegant"** for us mortals. :wink:

Could you please explain this socket thing and how it works?

---

### Post by mastahkillah666 on 2008-02-16
First things first :

*lnusertemp* is an **application** mostly used by KDE and can be commonly found in the /usr/bin directory.

What *lnusertemp* does is that it creates **temporary resource directories** in your /tmp (in case you are creating temporary files or temporary sockets) or in your /var/tmp (in case you have created temporary cache) and then **links** or symlinks to them by creating the approriate symlinks (symbolic links) in the .kde of your home directory.

I hope that this information is clear enough for you.  If not, feel free to ask me... ;)

See ya all...

---

### Post by mastahkillah666 on 2008-02-16
**About sockets :**

As you should know, every single server application communicates with its clients (and your kernel) via communication sockets.

Sockets are in fact links between the application (commonly "server" applications) and a "hardware" port on your computer (i.e. port 6881 for your bitorrent client, 80 and 8080 for http and its cache, 20 to 22 for ftp...).  In order to see the sockets used by your kernel and applications in real time, please use the following code :
```
sudo netstat -veepN
```

options : v - verbose, ee - super extended mode, p - show PID and name attached to a socket, N - resolve hardware names.

Hope this helps too.

---

### Post by couzin2000 on 2008-02-16
> **rzrgenesys187 said:**
> The debian package worked for me.  Compiling from source also worked

Not to start any debate, but I for one come from a Windows XP background. So my knowledge of compiling from source is quite low - so I do prefer package installation. Problem is, the deb package got updraded and didn't work right.

The fix that handles permissions is definitely what needs to be done with a newer version, because you'll be using the latest version. I don't quite understand what the problem within the latest version is - is it that it requires the proper permissions which weren't there before, or that is screws with the existing ones during install - but that doesn't really matter. The point is to get the latest version which fixes previous bugs, and now we know of the NEW bug, so we can get it fixed.

But thanks for the pointer.:)

---

### Post by erginemr on 2008-02-17
> **mastahkillah666 said:**
> About sockets :

As you should know, every single server application communicates with its clients (and your kernel) via communication sockets.

Sockets are in fact links between the application (commonly "server" applications) and a "hardware" port on your computer (i.e. port 6881 for your bitorrent client, 80 and 8080 for http and its cache, 20 to 22 for ftp...).

Hope this helps too.

Thank you very much for your time to explain the logic behind sockets. 

However, the problem is, as a Gnome user, I don't have "lnusertemp" in my system. And the the method
```
mkdir ~/.kde/socket-`hostname`
chown -hR `id -n -g` ~/.kde
chmod 755 -R ~/.kde
```
proposed by the OP is towards KDE users. So, I doubt these two tricks will work on a Gnome system, leaving 
```
default_driver=alsa
```
as the only feasible solution.

---

### Post by mastahkillah666 on 2008-02-17
> **erginemr said:**
> Thank you very much for your time to explain the logic behind sockets. 

However, the problem is, as a Gnome user, I don't have "lnusertemp" in my system. And the the method
```
mkdir ~/.kde/socket-`hostname`
chown -hR `id -n -g` ~/.kde
chmod 755 -R ~/.kde
```
proposed by the OP is towards KDE users. So, I doubt these two tricks will work on a Gnome system, leaving 
```
default_driver=alsa
```
as the only feasible solution.

In order to get the lnusertemp application, would you please check via synaptic that the kdelibs4c2a and the kdelibs-data packages are installed on your system.

Please note that these are only some of the **libraries, commands, classes and interfaces** for KDE and that the packages **do not** install KDE desktop environment.

For maximum application compatibility, I strongly suggest to anyone to install these packages. I am under Gnome too ;) .

See ya around...

---

### Post by FranMichaels on 2008-02-17
I made this solution for Gnome users, as I'm a Gnome user, and so is my sister. who ran into the issue (I guess it's towards gnome users that have used a KDE app... I'm honestly not sure what triggers the error.)

I assure you it works, I wouldn't have posted it here if it didn't ;). It is a simple matter of cutting pasting my solution. 
Here is a nice cut n' paste one liner version.

```

mkdir ~/.kde/socket-`hostname` && chown -hR `id -n -g` ~/.kde && chmod 755 -R ~/.kde

```

The reason I put it line by line, was just illustrate what it was doing.
Also, there is no need to replace `hostname' with your computer's hostname, it's a variable. In a terminal type
echo `hostname`
and it will return the name of your computer. 
I hope I've made this painless as possible. :KS

---

### Post by mastahkillah666 on 2008-02-17
> **FranMichaels said:**
> I made this solution for Gnome users, as I'm a Gnome user, and so is my sister. who ran into the issue (I guess it's towards gnome users that have used a KDE app... I'm honestly not sure what triggers the error.)

I assure you it works, I wouldn't have posted it here if it didn't ;). It is a simple matter of cutting pasting my solution. 
Here is a nice cut n' paste one liner version.

```

mkdir ~/.kde/socket-`hostname` && chown -hR `id -n -g` ~/.kde && chmod 755 -R ~/.kde

```

The reason I put it line by line, was just illustrate what it was doing.
Also, there is no need to replace `hostname' with your computer's hostname, it's a variable. In a terminal type
echo `hostname`
and it will return the name of your computer. 
I hope I've made this painless as possible. :KS

You should replace **`hostname`** by **$HOSTNAME**, because it is somewhat confusing.  In fact, I first thought that hostname was between quotes, which it is not ; it is between the ASCII character 96 (in Decimal).

You should change the code, for a better legibility, to :

```
mkdir -p $HOME/.kde/socket-$HOSTNAME && chown -hR $USER $HOME/.kde && chmod 755 -R $HOME/.kde
```

Don't forget the parameter **"-p"**, because if you don't have a .kde directory, it won't create it and the command line will fail.
See ya all around.

P.S. : Indeed, your fix **does** work, but is less **'elegant'** than mine (LOL) :-\" .
P.P.S. : You should also edit your first post and make the appropriate corrections (or not).

---

### Post by mastahkillah666 on 2008-02-18
**About MCOP :**

MCOP is in fact a series of scripts that handles heavy multimedia streaming.  These scripts form a communication protocol (**Multimedia COmmunication Protocol**).  It is this communication protocol that ZSNES calls.  MCOP is mostly used by aRts, the KDE sound framework and its server aRtsd.

My guess is, ZSNES reads the /etc/libao.conf in search of an Audio Driver, finds the wrong one (Alsa09) and tries to call MCOP to handle the audio streaming (aRts implementation) instead of your ALSA driver.

Since aRts is a layer implementation on top of ALSA, the best solution - in my opinion - is the edition of the **/etc/libao.conf** file (better than mine :cry: ) in order for ZSNES to use your **default ALSA driver** (better hardware implementation) for the emulation instead of **aRtsd** (more CPU consumption for nothing).  We should also report the bug in the call to the Alsa09 driver or maybe it is the driver that's faulty, who knows?

Hope it helps.

---

### Post by FranMichaels on 2008-02-18
I did update the post. 

Thank you for the better legibility, mine was more hackish, as I just looked up the commands to try and get the values... 

As for the libao.conf fix, since you are well versed in bash...
Is this okay?
```
sudo echo "default_driver=alsa" > /etc/libao.conf
```

Anyway, thanks again. :KS

---

### Post by mastahkillah666 on 2008-02-18
> **FranMichaels said:**
> I did update the post. 

Thank you for the better legibility, mine was more hackish, as I just looked up the commands to try and get the values... 

As for the libao.conf fix, since you are well versed in bash...
Is this okay?
```
sudo echo "default_driver=alsa" > /etc/libao.conf
```

Anyway, thanks again. :KS

You are very welcome friend, no need to thank me ;) .  As for your code, I suggest you use :

```
sudo sh -c 'echo "default_driver=alsa" > /etc/libao.conf'
```

Feel free to use the code I've sent you (but, in that particular case, using sed is a waste of time, since there is only one line in libao.conf).

See you around the forums...

---

### Post by newagelink on 2008-04-14
[COLOR="Indigo"]Thanks a lot. Used the second fix -- although I wish I knew precisely what was wrong and what I've just done -- and zsnes now works. It's staying open, anyway.[/COLOR] :)

---

### Post by AstroLlama on 2008-09-29
sweeet... thanks for the clear, concise solutions. I like the explanations too. The beauty of simplicity. Now I can get my ToP fix (hands twitching)

---

