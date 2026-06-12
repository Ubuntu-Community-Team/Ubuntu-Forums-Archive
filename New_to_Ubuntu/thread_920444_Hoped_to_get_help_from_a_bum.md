---
title: "Hoped to get help from a bum"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by Langstracht on 2008-09-15
I am having a problem getting cron to start from boot up.

I had thought that I could use bum to activate cron as a boot process.  To my regret (and surprise) cron seems not to be there to be activated.

So!  Can someone tell me either

how to get cron "available" to be activated in bum

or

what command I need to put where (i.e. in what directory or file) so as to have cron get started.

As you may have realized I am a bit of an idiot when it comes to understanding/handling scripts and ".sh" and links and such like.  So I really do need someone to be very pedantic in their reply.

Thanks in advance for that.

---

### Post by baruch60610 on 2008-09-15
Well, is cron installed?  IIRC (and I might not), cron isn't installed by default.  I vaguely recall having to install it myself, somewhat to my surprise.

---

### Post by Oldsoldier2003 on 2008-09-15
> **baruch60610 said:**
> Well, is cron installed?  IIRC (and I might not), cron isn't installed by default.  I vaguely recall having to install it myself, somewhat to my surprise.

```
which cron
``` is a fast way to tell if cron is installed.  A good basic cron tutorial is here:[http://ubuntuforums.org/showthread.php?t=102626](http://ubuntuforums.org/showthread.php?t=102626) There is more to cron than is shown in the tutorial but if you need further help there are plenty of folks on the forums that know how to use cron.

---

### Post by Langstracht on 2008-09-15
Yes cron is installed.  I can "manually" (i.e. command line) start it and it works just fine.

---

### Post by knix on 2008-09-15
If nothing else, you can add it to your /etc/rc.local

---

### Post by Langstracht on 2008-09-15
Thank you for that response.  But what does that mean?

Sorry but I don't even know what "/etc/rc.local" is.  Is it a file?  A directory?  A script?

And so, what do I add (the word "cron"?) and into where?

Sorry for being dumb ... but I come by it honestly ...

---

### Post by nowshining on 2008-09-15
/etc/rc.local is a script that allows one to run their own commands/scripts, etc.. upon login, it's a file, sudo gedit /etc/rc.local in terminal and add any info/command you want there or a path to another script..

example:

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

/etc/???/sysmods

exit 0
```

or

in a terminal apt-get install sysv-rc-conf

in the same terminal issue sudo sysv-rc-conf and find cron (press the page up/page down button to control and q to exit and if after you get a high cpu usage then sudo killall -9 sysv-rc-conf) now u'll see run levels at top #'s, etc.. again find cron on the left then move the move into one of the [] boxes then under 2, 3, 4. 5 make them look like this [x] then press q to quit.

---

### Post by Langstracht on 2008-09-15
O.K.   Thank you so much for that.

But ... just to be real sure (I hate to fiddle with stuff when I'm iffy about what I am doing) ... instead of entering "/etc/???/sysmods" as per your example, I can simply create a new line, enter "cron" (without any paths or directories or whatever) and that's it.  Yes?

---

### Post by shoot2kill on 2008-09-15
you enter the same command as you would to start cron from the terminal, whatever that may be.

---

### Post by Langstracht on 2008-09-15
Well I think I may have a problem then.

From the command line I've needed to enter

sudo cron

which then asks for my password ...

---

### Post by nowshining on 2008-09-15
the file was a script i made to run that helps even out the sytem with speed tweaks, etc.. & to run some command after login or when ever i run /etc/rc.local and it also re-seats the font cache, etc.. I can give u a copy if you'd like to take a look at it.

Alas for your Q:

no need for sudo, /etc/rc.local runs as root and anything in it goes thru root, etc.. :) you could put sudo but it won't ask for a pw just like if u sudo at a root prompt - the command will just fine..

edit: if ever you want to run a program easily as another you can install sux

sudo apt-get install sux

then

sux username program

---

### Post by Langstracht on 2008-09-15
Thanks for the re-assurance.  Sorry that I need it (the re-assurance) but I am really just a bit paranoid about bricking my machine.

I'll give it a go ... and hopefully let yourself and the other responders get on to bigger things.

Best.

---

### Post by nowshining on 2008-09-15
hehe it's okay...

Just be careful what u put and never link to a script from your home folder in there, put it in /etc/ or somewhere safe and only allow root to edit it for extra protection, 'cause someone can easily edit the script in your home folder and since rc.local is all root anything can go wrong...

:)

---

