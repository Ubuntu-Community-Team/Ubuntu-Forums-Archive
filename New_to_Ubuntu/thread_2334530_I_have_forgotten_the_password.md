---
title: "I have forgotten the password"
date: 2016-08-20
forum: New to Ubuntu
---

### Post by dave6 on 2016-08-20
I set up lubuntu LTS on a computer 2 - 3 years back, in the back room to be used by others for web checking their email or what ever, the wife has been doing a bit of her family tree research on it as well rather than her chrome book, and it has got to the point of asking for an update on the 2 web browsers fire and chrome, BUT ! as admin I have no idea what I set the pass as, so, I am unable to update the 2 browsers.

Any suggestions as how to update without having to re-install the entire OS :confused:

Thanks in advance 

Dave

---

### Post by sudodus on 2016-08-20
If the system is not encrypted, it should work according to the following link:

[http://psychocats.net/ubuntu/resetpassword](http://psychocats.net/ubuntu/resetpassword)

---

### Post by dave6 on 2016-08-21
Thanks sudodus for the reply, none of the commands worked after I got into the shell prompt, "mount -o rw, remount /" remount is not a command, "password username"is not a command, so I did a few of my own, "show passwd" got the message back "show" is not installed blah blah blah, type "apt -get show", done that then and got "apt" is not blah blah blah.   I finally give up.
But any one else trying to get into the prompt shell, boot up first then restart when you hear beep, then press the [shift key]


Dave

I will just reinstall lubuntu lts some time in the future

---

### Post by Bucky Ball on 2016-08-21
You drop into the recovery kernel. Boot the machine> choose 'Advanced options' from the grub list> choose the recovery kernel option. Should be second on the list. When you get to the list of recovery options, choose to drop to a root shell and perform the commands given on the psychocats page.

```
mount -o rw,remount /
ls /home
passwd <username>
exit
```

Where it says <username> you must replace with your username. Hope that helps.

Not sure where you're currently trying to give those commands, but doesn't sound like you are following the instructions on the psychocats page and dropping to a root shell from recovery by your description.

---

### Post by dave6 on 2016-08-21
Bucky Ball
I re-ran the code again one line at a time
when I type
{ mount -o rw, remount / }
I get back
[ mount: special device remount does not exist ]

when I type
{ ls /home }
I get back the name of the computer
[ homeuser ]

when I type
{ passwd username }
I get back
[ passwd: user 'username' does not exist ]_ followed by_
A device can be given by name, say /dev/hda1 or /dev/cdrom, or by label, using -L label or by uuid, using -U uuid, 
Other options: [ -nf Frsuw]  [ -o options]  [ -p passwdfd]  
For many more details, say man 8 mount.

But when I type in
{ passwd }
I get back

Enter new UNIX password   (which I do)
Retype new UNIX password ( as above)
passwd: Authentication token manipulation error
passwd: password unchanged

Funny thing is when I type in the code you have in the box, I do it as a line, the computer runs for about 3 seconds, hundreds of lines of code shoot up the screen

So, that's why I have given up
Some day, maybe next year or the year after I might just redo the computer software, full re-install

until then ??
Dave

---

### Post by steeldriver on 2016-08-21
Copy the commands carefully - in particular note the **lack **of space between the rw, and the remount:

```

mount -o rw,remount /

```

If you add a space, the shell interprets 'remount' as a separate (non-existent) command

If 
```

ls /home

```

says 

```

homeuser

```

then use **that **as your username for the password command i.e.

```

passwd homeuser

```

---

### Post by dave6 on 2016-08-21
still getting

```
passwd: Authentication token manipulation error
passwd: password unchanged
```

Dave

rebooted the computer and done that again

It worked ? :confused:

Any way, update chrome browser, it is now asking for command line ? 
Thats it, I quite : no more command line stuff, chromium is at ver 24.0.13 and firefox is running ver 16 


Thanks to all that replied, hopefully others out there have learned more than I have

Dave
:P](*,)

---

### Post by Bucky Ball on 2016-08-21
Please mark the thread as solved using Thread Tools at top right or see second line in my signature. Don't hesitate to post a new thread for any further issues.

---

