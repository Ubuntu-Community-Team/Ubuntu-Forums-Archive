---
title: "Execute script on ssh logout?"
date: 2009-07-16
forum: Programming Talk
---

### Post by stair314 on 2009-07-16
Is there anything like a .bashrc that executes when you log out?
I have one machine set up with a line in the .bashrc that turns the terminal background green when I log in. That is to make it extra clear which windows are for the machine I've ssh'ed into. (Bad things happen if I run the wrong command on the wrong machine) The only problem is, when I log out of this machine, the terminal remains green, so the color code isn't fully accurate.

---

### Post by leandromartinez98 on 2009-07-16
You could create a script called "logout", for instance, that
does the change in color and then exits.

---

### Post by stair314 on 2009-07-16
I gave my "logout" script execute permissions and put it in the first directory in my PATH variable, but the real "logout" still gets executed instead.

---

### Post by Dill on 2009-07-16
If you don't already have one, create a .bash_logout file:

[http://rcsg-gsir.imsb-dsgi.nrc-cnrc.gc.ca/documents/advanced/node125.html](http://rcsg-gsir.imsb-dsgi.nrc-cnrc.gc.ca/documents/advanced/node125.html)

Here are the contents of my default .bash_logout on an Ubuntu machine and Debian server:

```
# ~/.bash_logout: executed by bash(1) when login shell exits.

# when leaving the console clear the screen to increase privacy

if [ "$SHLVL" = 1 ]; then
    [ -x /usr/bin/clear_console ] && /usr/bin/clear_console -q
fi
```

---

### Post by leandromartinez98 on 2009-07-17
> **Dill said:**
> If you don't already have one, create a .bash_logout file:

[http://rcsg-gsir.imsb-dsgi.nrc-cnrc.gc.ca/documents/advanced/node125.html](http://rcsg-gsir.imsb-dsgi.nrc-cnrc.gc.ca/documents/advanced/node125.html)

Here are the contents of my default .bash_logout on an Ubuntu machine and Debian server:

```
# ~/.bash_logout: executed by bash(1) when login shell exits.

# when leaving the console clear the screen to increase privacy

if [ "$SHLVL" = 1 ]; then
    [ -x /usr/bin/clear_console ] && /usr/bin/clear_console -q
fi
```


Nice, I didn't know that files existed either. :-)

---

### Post by stair314 on 2009-07-17
That's very cool! Thanks!

Anybody have any guess why
export PS1=`echo -en '\033[40m\w\$ '`;
would have no effect in that file? I can get other commands to run successfully though.

---

