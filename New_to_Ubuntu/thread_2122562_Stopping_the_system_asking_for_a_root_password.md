---
title: "Stopping the system asking for a root password?"
date: 2013-03-05
forum: New to Ubuntu
---

### Post by GeordieJedi on 2013-03-05
Hi all.

OK, I'd like to stop my system from asking for the root password whenever I try
to run apps or elevate privaliges.
(I realise that this is normal and how things "should" be done,
however I've got really bad RSI and every little bit helps).

I also understand the security implications this involves too.


And was asked to edit the sudoers file using visudo and alter
the line in question to =
```
	
%admin ALL=(ALL) NOPASSWD: ALL

```

However even though I've done this
(And I'm pretty sure it was done properly - I went in and checked the
file running Gedit as root. However I only viewed the file I didn't edit it using Gedit).


At the moment I still get the request come up if I do any of the following -
I run Gparted.
I run a terminal session (and then ask for a root session).
I run GUFW.
Run Ubuntu software centre.


Is there anything I've done incorrectly, or anything else that I need to do ?

Useful information =

OS = Ubuntu 12.04
DE = KDE


TIA for any help or advice.

---

### Post by steeldriver on 2013-03-05
Without getting into the rights and wrongs of what you want to do, you would need to change the line for the 'sudo' group rather than for the 'admin' group I think

The 'admin' group is only there for backward compatibility afaik - since 12.04 any new sudoers will belong to sudo

You can check which groups your user belongs to with the 'groups' or 'id' commands - you will probably find you are not in 'admin'

You could also consider just changing the timeout - so it still asks for your password (btw it's NOT the root password), but less often

---

### Post by GeordieJedi on 2013-03-05
Hi there.

Right here are the results of a couple of commands that I've just ran  -

Command =
```

id	

```

Answer =
```

uid=1000(myname)
gid=1000(myname)
groups=1000(myname)
4(adm), 24(cdrom), 27(sudo), 30(dip), 46(plugdev),
109(lpadmin),124(sambashare)

```

Command =
```
	
groups	

```

Answer =
```

(myname) adm cdrom sudo dip plugdev lpadmin sambashare

```



Thanks for the help so-far

---

### Post by snowpine on 2013-03-05
Just an observation: you have typed 1,360 characters so far in your quest to make your system significantly less secure and save a few keystrokes. Assuming an 8-character password, this is equivalent to typing your password 170 times! 

Rather, I recommend:

```
sudo -i
```

This will open a root terminal where you can conduct all of your day's sys admin tasks without typing your password multiple times. All of this is explained here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Please carefully consider this advice from a long-time forum member before you aggravate your RSI further by replying to tell me "it's my computer, I can be as insecure as I like" as all of us old-timers have heard a thousand times, usually followed a week or two later by "help, I lost all my data!" ;)

---

