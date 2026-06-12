---
title: "Sudo Password"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by expatCM on 2008-05-09
I just installed Hardy fresh.  Some things are a bit different.  I would like to loose the password prompt for sudo for example.

So I use the following command to open the sudoers file

 export EDITOR=gedit && sudo -E visudo

and edit to include a line 

# User privilege specification 
root	ALL=(ALL) ALL 
user1	ALL=(ALL) PASSWD: ALL 

But the trouble is that it does not have any effect.

Did something change or did I get it wrong?

---

### Post by kerry_s on 2008-05-09
?
you mean your trying to disable asking for a password? aka:NOPASSWD

that is very unsafe. you should make it application specific for gui programs only.
example:

user1 ALL=NOPASSWD: /usr/sbin/synaptic, /usr/bin/nautilus, etc...

using a open sudo, you might as well be running as root. :(

---

### Post by mlentink on 2008-05-09
I advise strongly against this.
The sudo mechanism is there to protect you against human failure, and because we are all human, we **_will_** fail.

If you would want to do work as superuser for a prolonged period of time, you could always do 
```
sudo su
```
and when ready
```
exit
```

---

### Post by expatCM on 2008-05-09
I cannot understand why people worry so about using sudo without a password.  Indeed having to use a password is a very negative measure since it uses the system password and if you have to enter this password say ten times in a session then the password needs to be set as a very simple password.  This means that the login password ends up being short and sweet which is very easy to crack. 

I wish to avoid that.  Have a good password to protect access but once in be free to work without interruption.

Sudo Su is not quite the solution.  This will work for one application only but often I have many different tasks to perform ... 

But it looks like I made a typo .....  I can see PASSWD instead of NOPASSWD.  I will check and post back .....

---

### Post by Dr Small on 2008-05-09
Try:
```
user	ALL=(ALL) NOPASSWD: ALL
```

Or you could specify only certain application that would not require a password like:
```
user	ALL=(ALL) NOPASSWD: /usr/sbin/visudo, /bin/kill, /bin/ls
```

---

### Post by expatCM on 2008-05-09
I appear to have something wrong since it does not work.  The following is what is in sudoers but I cannot see what is wrong.  Any idea?


```

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults	env_reset

# Uncomment to allow members of group sudo to not need a password
%sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL) ALL
user1	ALL=(ALL) NOPASSWD: ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
```

---

### Post by spiderbatdad on 2008-05-09
The syntax doesnt look right.
Try:

```
# User privilege specification
root	ALL=NOPASSWD: ALL
user1	ALL=NOPASSWD: ALL

# Members of the admin group may gain root privileges
%admin ALL=NOPASSWD: ALL
```

Though user1 should be unecessary if user1 is admin.

OR: ALL hostname=NOPASSWD: ALL

---

### Post by Xiong Chiamiov on 2008-05-09
Do what is says [here]("https://help.ubuntu.com/community/RootSudo#head-66c2db5bdb2734f0a66336d8d68499c47c82fff5").

That said, I have a fairly long and complicated password even though I sudo things all the time.  I believe sudo priviledges are remembered for 15 mins by default (you can change it), and I drop into a root shell for extended periods of time if I need to:
```

sudo -s

```

---

### Post by expatCM on 2008-05-10
I seem to have got this more or less under control.

What I have done is change 

user1	ALL=(ALL) NOPASSWD: ALL

to 

user1 ALL=NOPASSWD: ALL

Amazing how things work if you get the syntax right :)

---

### Post by Joeb454 on 2008-05-10
> **Xiong Chiamiov said:**
> I drop into a root shell for extended periods of time if I need to:
```

sudo -s

```

I'm not going to go into a lot of detail on this one, but usually it's preferred to do ```
sudo -i
``` in this case. As there is less of a risk of messing up your permissions in your /home (~/) directory :)

---

### Post by Dr Small on 2008-05-10
> **expatCM said:**
> I seem to have got this more or less under control.

What I have done is change 

user1	ALL=(ALL) NOPASSWD: ALL

to 

user1 ALL=NOPASSWD: ALL

Amazing how things work if you get the syntax right :)
Hmm, that is strange. It must be different in Arch then, because I copied that entry right out of my /etc/sudoers file that was generated when created.

---

### Post by spiderbatdad on 2008-05-10
> **Dr Small said:**
> Hmm, that is strange. It must be different in Arch then, because I copied that entry right out of my /etc/sudoers file that was generated when created.

Not sure what's up with that Doc. I just looked at my sudoers file in Hardy and it matches the syntax you posted. The syntax I suggested to the OP, that apparently worked, was from an article you wrote a year or so ago...LOL.

---

