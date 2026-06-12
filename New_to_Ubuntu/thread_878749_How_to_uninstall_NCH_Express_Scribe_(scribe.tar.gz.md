---
title: "How to uninstall NCH Express Scribe (scribe.tar.gz)"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by swarup on 2008-08-03
Express Scribe is great software and it works great on the other two computers I have in my house. But on the third (any newest) computer, it is not working. So I'd like to try uninstalling and reinstalling it. Can someone tell me the uninstall command for a program like this?

It downloaded as scribe.tar.gz, then upon unarchiving it with Archive Manager, it yielded the file scribe.sh, which is a shell script. Upon running the shell script via terminal window, the program installs without a hitch.

If anyone wants to see their website with program and download info:

[http://www.nch.com.au/scribe/](http://www.nch.com.au/scribe/)

---

### Post by chuckyp on 2008-08-03
I would check the readme and see if they have an uninstall switch for their script ex:
```

$run scribe.sh --uninstall

```

---

### Post by swarup on 2008-08-03
Here is the output for that code:

```
swarup@swarup-laptop:~$ run scribe.sh --uninstall
bash: run: command not found
```

The program did not come with a readme file, unfortunately. Any further thoughts?

---

### Post by T-Boo on 2009-07-17
In the folder /opt/nch/scribe/bin there's a script called uninstall.sh. Run that using the command:

sudo ./uninstall.sh

---

