---
title: "Remote desktop help"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by doctorbighands on 2008-11-27
Hi there,

I'm trying to administer my server via Remote Desktop, but I believe Gnome has crashed/frozen on the server. I have a console open on the server through SSH, and I'd like to know if there's a command for restarting Gnome via the SSH prompt. Obviously I can't use any of the traditional tricks like CTRL+ALT+BACKSPACE, because that would restart it on my local machine, and not on the server.

Thank you!

---

### Post by poebae on 2008-11-27
A couple of ways from [this link](http://forums11.itrc.hp.com/service/forums/questionanswer.do?admit=109447626+1227844236878+28353475&threadId=1115188), though admittely I'm not even sure if it's applicable.

Find the X server process ID:

```
ps -e | grep /usr/bin/X11/X | grep -v grep
```

Then:

```
kill -HUP <X_server_pid>
```

Repeat the "ps" command for a new X server process ID.

Another way to restart X server as root:

```
#/sbin/rc3.d/S95xlogin stop
#/sbin/rc3.d/S95xlogin start
```

---

### Post by doctorbighands on 2008-11-27
I tried the second method (because it looked slightly simpler), and the console gave this reply:

```

bash: /sbin/rc3.d/S95xlogin: No such file or directory

```

EDIT

I tried the first method, entering...
```
ps -e | grep /usr/bin/X11/X | grep -v grep
```
...and it didn't tell me anything. It just gave me a new prompt.

---

### Post by doctorbighands on 2008-11-28
...bump

---

