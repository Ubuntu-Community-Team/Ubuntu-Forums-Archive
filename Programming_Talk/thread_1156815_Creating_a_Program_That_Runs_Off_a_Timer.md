---
title: "Creating a Program That Runs Off a Timer"
date: 2009-05-12
forum: Programming Talk
---

### Post by adun153 on 2009-05-12
I wanted to make a program that runs in the background, and closes the active window if the computer hasn't been touched for a certain amount of time.

Can anybody point me to a starting point? 

I'm thinking of how the system screen saver does the 'counting' of time; the program should be a bit similar to the screensaver in the sense that it triggers something after a certain period of inactivity. Thanks!

---

### Post by Dill on 2009-05-12
You can get a user's idle time from the 'w' command (see "IDLE" column):

```
satherdy@lamp:~$ w
 04:46:04 up 40 min,  3 users,  load average: 0.10, 0.19, 0.17
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
satherdy tty7     :0               04:06   40:42   1:21   0.15s x-session-manag
satherdy pts/0    :0.0             04:31    4:19   0.15s  0.15s bash
satherdy pts/1    :0.0             04:41    0.00s  0.15s  0.00s w
```

And, if you install a program called 'wmctrl'...

```
sudo apt-get install wmctrl
```

... and run the following command:

```
wmctrl -c :ACTIVE:
```

It will close the active window.

I imagine you could write a script to take advantage of both of these commands to accomplish what you want.

_EDIT_: I also found this article on a C program that takes advantage of the Xscreensaver idle time info that may be helpful: [http://coderrr.wordpress.com/2008/04/20/getting-idle-time-in-unix/](http://coderrr.wordpress.com/2008/04/20/getting-idle-time-in-unix/)

Cheers,
Dill

---

