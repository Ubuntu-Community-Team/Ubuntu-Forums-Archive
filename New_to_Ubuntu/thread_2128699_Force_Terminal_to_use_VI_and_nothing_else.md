---
title: "Force Terminal to use VI and nothing else"
date: 2013-03-23
forum: New to Ubuntu
---

### Post by rparge on 2013-03-23
Sorry if I am not precise, thus posting in this area. (:

In my work environment, I have to jump on a lot of AIX boxes, and the terminal on these are straight VI. No arrow / tab keys allowed.
I am practicing a lot on my home Ubuntu install, but I find myself using the arrow keys and the tab key a lot.

So to train myself to use only VI, I was wondering how to change bash to use VI only - including removing arrow keys, tab keys, and any other key that is not used in an AIX install.

I'm using 

bash -version
GNU bash, version 4.2.37(1)-release (i686-pc-linux-gnu)
Copyright (C) 2011 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>

TIA for any advice on this.

Rick

---

### Post by Impavidus on 2013-03-24
Try **vi -C**. This will start vim in compatibility mode, making it behave almost identical to vi. Not sure whether it will do everything you want.

---

### Post by schragge on 2013-03-24
Put *set -o vi* into file *~/.bashrc*

[SIZE=-1]@**Impavidus** I guess the OP means bash command-line editing mode.[/SIZE]

---

### Post by siddharth007 on 2013-03-25
Try this command
```
export EDITOR="vi"
```

Next try and open the crontab file by doing *crontab -e. *This will open the cron file in vi editor instead of the nano.In the above command if you specify *nano *(instead of vi) the cron file opens in the nano editor.

To choose vi/vim as the default editor permanently just put the above code in the **~/.bashrc** file and restart your system.

---

### Post by rparge on 2013-03-25
Thanks all, this seems to be working, the arrow keys and tab keys still work, but I'll keep off of them. :)

---

### Post by steeldriver on 2013-03-26
... maybe it's just a question of the shell you are using? iirc AIX used the Korn shell, there are a couple of Korn shell alternatives in the repos that you might want to play with

```
$ apt-cache search --names-only ksh
kshisen - Shisen-Sho solitaire game
[B]pdksh - Public domain version of the Korn shell
ksh - The real, AT&T version of the Korn shell
[/B]kshutdown - advanced shut down utility for KDE
mksh - MirBSD Korn Shell
```

---

### Post by schragge on 2013-03-26
Starting from quantal, pdksh is just a dummy package that installs mksh:
```

[COLOR=#008000]$[/COLOR] apt-cache -n search ksh$
[COLOR=#008000]ksh - Real, AT&T version of the Korn shell
mksh - MirBSD Korn Shell
pdksh - transitional dummy package to migrate from pdksh to mksh[/COLOR]

```

---

