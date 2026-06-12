---
title: "Autostart Synergy w/ Sudo"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by wedgiey1 on 2008-04-30
Help!  I'm in BRAND new to Ubuntu.  I decided to try it out on my secondary machine because windows needed a format.  I used multiplicity before and saw that Synergy does the same thing.  There is a bug with Synergy and the newest Ubuntu (8.0.4?) that causes so much lag it renders Synergy un-usable.  The work-around to this is to run the synergy client (synergyc) with 'sudo'.

I follow the autostart directions exactly and it works (with lots of lag).  The instructions say to use this script (/etc/X11/Xsession.d/85synergyc):

/usr/bin/killall synergyc
sleep 1
/usr/bin/synergyc <HOST NAME>

This works, but with the lag as mentioned above.  I tried changing it to:

/usr/bin/killall synergyc
sleep 1
sudo /usr/bin/synergyc <HOST NAME>

&

/usr/bin/killall synergyc
sleep 1
/usr/bin/sudo synergyc <HOST NAME>

I'm sure these attempts are laughable because neither worked.  Any help would be greatly appreciated.

Signed,
Linux Newb,
Wedgiey1

---

### Post by swoll1980 on 2008-04-30
when I want to autostart I go to system>preferences>sessions then create new then add the program that I want to autostart for sudo add a gksu then a space then the program path

---

### Post by wedgiey1 on 2008-04-30
I looked into this too; is there a way to make it run as the root that way?

---

### Post by swoll1980 on 2008-04-30
gksu then a space then path to program

---

### Post by wedgiey1 on 2008-04-30
I'll try this; to make certain though, do I run the "85synergyc" that I created?  Or just the 'synergyc' command?  And can I add arguments to the end of it?  Lol, sorry for all the dumb questions, but this is all very new to me.

---

### Post by swoll1980 on 2008-04-30
if the script you created opens the program just point the path to the script if you need to run the script and then open the program I think you put one of these (>) in between them like /path/to/script>/path/to/program don't quote me on that though

---

### Post by wedgiey1 on 2008-04-30
So close!  I got a prompt to enter my password for administrative tasks, but before I could do anything it vanished!  The program is 'working' but it's still too laggy to do anything.  Why did the prompt go away so fast?

*Edit:  Seemed to almost work for a while, but now everything seems to be locked up.  I can move the mouse but can't click on anything.  I'm going to reboot and see what happens.

---

### Post by wedgiey1 on 2008-04-30
Ok, no luck so far.  I tried using preferences->session to run my script with gksu in front, I tried running the 'synergyc' command with gksu and sudo in front of it.  None of them worked.  I wonder if I need to 'killall' synergyc and then re-run it with 'sudo' or 'gksu' in front?  Do the startups under session execute in any particular order?

---

### Post by swoll1980 on 2008-04-30
You have surpassed any knowledge I have on this subject hopefully somebody else will have an answer for you. good luck!

---

### Post by wedgiey1 on 2008-04-30
Thanks for your help!  I was surprised somebody replied so quickly!  I'll look back in tomorrow.

---

### Post by wedgiey1 on 2008-04-30
I'm going to update to try and help anybody that wants to help me.  Another poster seems to have had the problem here:  [http://ubuntuforums.org/showthread.php?t=767236&highlight=synergy](http://ubuntuforums.org/showthread.php?t=767236&highlight=synergy)
but no info given on how to AutoStart as root, just that running as root fixes the problem.
Here is the bug report:  

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/194029/](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/194029/)

Can anybody please help?

Thanks

---

### Post by wedgiey1 on 2008-04-30
I read about something called a "crontab" I'm going to try when I get home.  Any ideas if this will work?

---

### Post by wedgiey1 on 2008-05-01
This is starting to get frustrating.  Crontab didn't help anything.

It's unclear as to how to edit crontab (crontab -e vs. sudo gedit /etc/crontab) and @reboot sudo /usr/bin/synergyc <SERVER> doesn't work; neither does @reboot root /usr/bin/synergyc <SERVER>.

I've read a little about rc.local in 'Init.d' but I don't understand what I'm supposed to do with it.  I know that my runlevel is '2' and that somehow I can put scripts (a one line command?) into it somehow so that they run at startup as root.

Help, please!

---

### Post by Jared Norris on 2008-05-01
I found this to be a real problem as well and I had spent ages looking around for a fix. I found an archived thread here on the forums I thought I would try purely out of desperation and to my surprise it has worked a charm. 

I'm no guru on anything linux related so I can't say if this is making it run as sudo user or working around the problem another way. All I know is that I have a smooth, responsive synergy client on my Hardy Heron install.

I have taken this all from:

[http://ubuntuforums.org/showthread.php?t=48196](http://ubuntuforums.org/showthread.php?t=48196)

Thanks to Insti!

> **Insti said:**
> I wanted to make the synergy server run from my ubuntu (5.10) box. 
Here is what you need to do:

Make a directory in /etc to store the configuration:

```
sudo mkdir /etc/synergy
```

Setup my synergy server configuration file:
```
sudo gedit /etc/synergy/synergy.conf
```

To make the server run when gdm runs, but before anyone has logged in:

edit /etc/gdm/Init/Default:
```
sudo gedit /etc/gdm/Init/Default
```

Added the following lines in the middle of the file **BEFORE** the "sysmodmap=/etc/X11/Xmodmap" line:

```

SYNERGYS=`gdmwhich synergys`
if [ x$SYNERGYS != x ] ; then
        $SYNERGYS --config /etc/synergy/synergy.conf
fi

```

The only problem with that is once you log in it kills off the server, so you need to make it start again for you.
 
edited /etc/gdm/Init/Default:
```
sudo gedit /etc/gdm/PreSession/Default
```

Added the following lines in the middle of the file **BEFORE** the "XSETROOT=`gdmwhich xsetroot`" line:
```

SYNERGYS=`gdmwhich synergys`
if [ x$SYNERGYS != x ] ; then
        $SYNERGYS --config /etc/synergy/synergy.conf
fi

```

Log out and back in again.

The synergy server should now startup and run whenever your gdm session does.

---

### Post by richbl on 2008-05-01
Have you looked at [http://synergy2.sourceforge.net/](http://synergy2.sourceforge.net/), under "Starting synergy automatically?"

This has consistently worked for me, no problems whatsoever. Or, perhaps I've misunderstand the issue.

Best of luck.

---

### Post by wedgiey1 on 2008-05-02
richbl, problem is with Ubuntu 8.04 you have to run it as root or it's so laggy it's un-usable.  

head_victim, thanks for your reply!  I actually solved my problem yesterday before I read this.  Here's what I did...

I edited '/etc/gdm/Init/Default' to include the command:
'/usr/bin/synergyc <Host IP>'
   This makes it so synergyc runs before login and you can use the srvr mouse & keyboard to login.

For whatever reason this process seems to die immediately after login, so I edited '/etc/gdm/PreSession/Default' to include the command:  '/usr/bin/synergyc <Host IP>'.  This made the command run as root to eliminate the lag problem.

Hope this might help somebody else!

*edit:  richbl, just noticed my solution looks a lot like what you provided!

---

### Post by neurostu on 2008-05-02
So you don't need the 
```

killall synergyc

```
B/c when you boot synergy hasn't been started yet.

---

### Post by dro0g on 2008-05-05
> **wedgiey1 said:**
> richbl, problem is with Ubuntu 8.04 you have to run it as root or it's so laggy it's un-usable. 

You can also renice the process so you don't need to run synergyc as root (per this thread: [http://ubuntuforums.org/showthread.php?t=767236&highlight=synergy](http://ubuntuforums.org/showthread.php?t=767236&highlight=synergy) )

---

### Post by rssvihla on 2008-05-11
Glad you got it working!

Other things that could have been a possible solution:

-run visudo

-add this to the bottom of the file

```
yourusername ALL=(root)NOPASSWD: /usr/bin/synergyc
```

then you can setup gnome to run the following at login:
```
gksu -u root /usr/bin/synergyc yourhost
```

Finally, the ultimate cheesy trick that isn't always the best as your password would be in the script is [http://wiki.tcl.tk/1865](http://wiki.tcl.tk/1865).

> **wedgiey1 said:**
> richbl, problem is with Ubuntu 8.04 you have to run it as root or it's so laggy it's un-usable.  

head_victim, thanks for your reply!  I actually solved my problem yesterday before I read this.  Here's what I did...

I edited '/etc/gdm/Init/Default' to include the command:
'/usr/bin/synergyc <Host IP>'
   This makes it so synergyc runs before login and you can use the srvr mouse & keyboard to login.

For whatever reason this process seems to die immediately after login, so I edited '/etc/gdm/PreSession/Default' to include the command:  '/usr/bin/synergyc <Host IP>'.  This made the command run as root to eliminate the lag problem.

Hope this might help somebody else!

*edit:  richbl, just noticed my solution looks a lot like what you provided!

---

