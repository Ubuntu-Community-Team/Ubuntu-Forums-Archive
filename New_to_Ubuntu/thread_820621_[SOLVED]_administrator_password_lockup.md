---
title: "[SOLVED] administrator password lockup"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by Mike Atnip on 2008-06-06
Hi.  I just started having problems with Hardy 8.04 that whenever I need to do something that requires an administrator password, it either locks up what I am trying to do (like run the update manager or unlock after putting the system into hibernation) or just simply wont open something (like trying to change the login window).  Hardy was working fine, and I ran the update manager several times with no problem for several weeks.  I have narrowed the problem down to the administrative password but have no idea on how to go about correcting whatever went wrong.
Help!? :confused:
 Thanks, Mike

---

### Post by melrom on 2008-06-06
Mike-

What happens when you try to use the command "sudo" from the terminal? Does this cause the system to freeze as well?

-MelRom

---

### Post by rraj.be on 2008-06-06
could you be a bit specific what you ran and how long it took for freezing [i.e soon after executing the command or after a while]

---

### Post by Mike Atnip on 2008-06-06
Here is what I get
 "unable to resolve host Mike"
Looks like it is a problem in "host Mike"?

---

### Post by Mike Atnip on 2008-06-06
> **rraj.be said:**
> could you be a bit specific what you ran and how long it took for freezing [i.e soon after executing the command or after a while]

When I run the update manager, it just "freezes" immediately, waiting, I assume, on the administrator password which never shows up on the screen.
THanks!

---

### Post by Mike Atnip on 2008-06-06
> **Mike Atnip said:**
> When I run the update manager, it just "freezes" immediately, waiting, I assume, on the administrator password which never shows up on the screen.
THanks!

I should add that only the update manager freezes until I kill it.  Everything else (Firefox browser etc.) works fine meanwhile .

---

### Post by rraj.be on 2008-06-06
I think that you had terminated some instalation in the middle.

the sync lock may be the problem.

Just try  update along with sudo

---

### Post by Mike Atnip on 2008-06-06
s

---

### Post by Mike Atnip on 2008-06-06
so what do I type into the terminal? 
I tried the following.
michael@Mike:~$ sudo update
sudo: unable to resolve host Mike
sudo: update: command not found
michael@Mike:~$

---

### Post by rraj.be on 2008-06-06
Try this

Turns out  the localhost setting in /etc/hosts was.


Go to System--> 'Administration--> 'Network'. 

Select the tab Hosts, enter password in dialog box, then change the localhost name:

127.0.0.1 <something>

to

127.0.0.1 <pcname> (For example say localhost)

and save it.

I hope this helps you.

---

### Post by Mike Atnip on 2008-06-06
The 127.0.0.1 is already at "localhost" so I did not change it.  Any other suggestions?

---

### Post by rraj.be on 2008-06-06
is it just localhost or something like



localhost.networkname.

if so it should work fine.

---

### Post by Mike Atnip on 2008-06-06
Just "localhost".

---

### Post by cariboo on 2008-06-06
Just add the following to /etc/hosts:

```
127.0.0.1     Mike
```

That will fix your problem.

Jim

---

### Post by rraj.be on 2008-06-06
q

---

### Post by Mike Atnip on 2008-06-06
> **cariboo907 said:**
> Just add the following to /etc/hosts:

```
127.0.0.1     Mike
```

That will fix your problem.

Jim

Hey, you guys are great!
:popcorn:

Thanks!!!

---

### Post by rraj.be on 2008-06-06
```
Mark your thread as solved if its solved.
```

To mark it as solved  

go to ```
Thread tools at the top and select Mark this thread as solved.
```

because some others will be helped by seeing this.


See my signature for more info.

Good night. [sorry Good morning. already 12:10 in my [COLOR="Red"]INDIA[/COLOR]]

---

### Post by SteveHillier on 2008-06-10
> **rraj.be said:**
> 

Turns out  the localhost setting in /etc/hosts was.


Go to System--> 'Administration--> 'Network'. 

Select the tab Hosts, enter password in dialog box, then change the localhost name:

127.0.0.1 <something>

to

127.0.0.1 <pcname> (For example say localhost)

and save it.

I hope this helps you.

It did.  You are quite wonderful.
Cheers
Steve

---

