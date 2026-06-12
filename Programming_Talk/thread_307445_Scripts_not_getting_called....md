---
title: "Scripts not getting called..."
date: 2006-11-26
forum: Programming Talk
---

### Post by davebed on 2006-11-26
I am trying to have the following script excecuted automatically when the AC power is removed and the battery is called:
```
#!/bin/bash 

DISPLAY=:0 /usr/bin/aticonfig --set-powerstate=1
```

I put in in a file called **script.sh** (with execute permissions) and placed it in /etc/acpi/battery.d 

The problem is that it doesn't appear to get called.

How can I track this and see why it's not getting executed?

NOTES:
If I execute the code in the TERM it works fine.
```
DISPLAY=:0 /usr/bin/aticonfig --set-powerstate=1
```

If it execute it with sudo:
```
sudo DISPLAY=:0 /usr/bin/aticonfig --set-powerstate=1
```
 I get:
```
sudo: DISPLAY=:0: command not found

```

Perhaps that is useful in solving this little problem?

thank you.

---

### Post by po0f on 2006-11-26
davebed,

I don't know too much about handling ACPI events; are you sure that the script is associated with the correct event?  Also, the sudo command would be:
```
[FONT="Courier New"]$ DISPLAY=:0 sudo /usr/bin/aticonfig --set-powerstate=1[/FONT]
```
You have to declare variables *before* the command you run.

---

### Post by PilotJLR on 2006-11-26
Try removing the extension from the filename... so just "scripts"

Also make sure the executable bit is set.

---

### Post by pdietric on 2006-11-26
You can see what happens when the event occurs that should trigger your script by examining /var/log/acpid.
I bet your problem has something to do with root not being granted access to your X-session.

Bye

---

### Post by davebed on 2006-11-27
Thank you all for your replies. I will put them to work and report back soon.

Many thanks again.

---

### Post by davebed on 2006-11-27
> **pdietric said:**
> You can see what happens when the event occurs that should trigger your script by examining /var/log/acpid.
I bet your problem has something to do with root not being granted access to your X-session.

Bye

How could I grant X-session root access on an automatic basis?

Thanks.

---

### Post by scoon on 2006-11-27
Hey there, 

This is interesting.  I am having a similar problem.  

I have a script that should get called when I bring up my VPN, but it does not.  

I'll be curious to see how this plays out for you.

My gut tells me that it could pertain to having an inactive root account.  I will try to enable root and post back. 

-scoon

---

### Post by pdietric on 2006-11-27
Davebed,

the first thing to do would be to figure out how to grant root access to the user's X-Session at all. I myself have been trying to do this (also want to have some scripts executed at battery or ac event). All attempts unsuccessful so far.

What do you see in that acpid log. If it is a privilege issue there should be some entries saying "Connection to Display :0.0 refused. Can't open display " upon execution of power.sh .

If have read a lot of posts from people reporting some behavior similar to the just mentioned one. Some of these people claim they were able to solve it by doing a ```
xhost +localhost
``` or similar command.

What is for sure is that ```
xhost +
``` grants everybody access to the X-session in question and thus also root. The result is that power.sh does execute the scripts - it works. But this way one **[COLOR="Red"]substantially weakens system security[/COLOR]**.

Others recommend the use of xauth's cookie system to enable root access to the user's X-session. This is supposed to be much more secure than using xhost. I think (don't know for sure) there are several ways to go about this with xauth (try One of the following).

1. when root, set root's XAUTHORITY environment variable with path to user's .Xauthority file: ```
export XAUTHORITY=/home/user/.Xauthority
```

2. copy user's Xauthority file to root's directory: ```
cp /home/user/.Xauthority /root/
```

3. use xauth command when root (don't know the actual effect of this one): ```
xauth merge /home/user/.Xauthority
```

Trying all of the above I had no success with power.sh executing my scripts. But strangely the following worked after doing method 1 for example:

Go to virtual terminal: ```
Alt+Ctrl+F1
```

After loggin in as normal user become root: ```
sudo -i
```

Set DISPLAY env variable: ```
export DISPLAY=:0
```

execute a command affecting user's xsession, e.g.: ```
aticonfig --set-powerlevel=1
```

Switch back to your X-session: ```
ALT+Ctrl+F7
```

and check the powerlevel of your ati graphics chip: ```
aticonfig --lsp
```

It changed. But the I don't understand why executing the exact same command in a script by power.sh does not.

I hope I could make my point clear. Thanks for listening.

---

### Post by davebed on 2006-11-28
Hmmm...

Ya. I had to run a ```
xhost +localhost
``` script at session startup in order for my fglrxpowermode.sh (the ATI script called from power events that automatically scales the video card power up or down) script to execute the ```
aticonfig --set-powerlevel=X
``` automatically.

If i run ```
DISPLAY=:0 /usr/bin/aticonfig --set-powerstate=1
```  

or ```
DISPLAY=:0 sudo /usr/bin/aticonfig --set-powerstate=1
```  
from a terminal, i get
```
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

Error: Unable to open display `:0.0'.

```

but if i run a script with ```
#!/bin/bash 

DISPLAY=:0 /usr/bin/aticonfig --set-powerstate=1

```

It works fine. and so do my scripts in **ac.d** and **battery.d**

Come to think of it, all the scripts I've been tring to run from ac.d and battery.d have been display related. 

Is there a simple script you can think of that I could test with that is NOT diplay related?

Oh ya and, this means that we're no closer to solving this still, doesn't it?!

---

### Post by onaka_the_kaka on 2006-12-09
I also entered Gnome-Toolbar->System->Preferences->Sessions->Startup Programs-> and added

xhost +local:

If someone has figured out a better solution we might be able to put this on the wiki as many people seem to post about this!

---

### Post by stbaker on 2006-12-29
I have a very similar problem. Like everyone else, I'm having no success getting fgrlx-powermode.sh to run properly. However, I also have another script, ipw-powermode.sh in both ac.d and battery.d. its pretty simple, it just sets the powersaving mode of my wireless card:

#!/bin/bash 

iwpriv eth1 set_power 7

So basically when i (un)plug the power connector, the acpid log tells me power.sh gets called, but power.sh doesn't call the scripts in battery.d/ac.d. Any ideas?

Sean

---

### Post by twstokes on 2007-02-01
**My original post:** Add me to the list. I'm having the exact same problem trying to set my ATI card to a lower powerstate. I can run the script manually and it works fine.

**Follow up: **I found out how to fix my particular problem. All I had to do was remove the "#" from the beginning of "FGLRX_ACPI_SWITCH_POWERSTATES=true" in /etc/default/fglrx.

Now the script runs automatically when I run on battery or AC.

---

