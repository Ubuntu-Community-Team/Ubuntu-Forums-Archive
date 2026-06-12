---
title: "nano and .nano_history"
date: 2012-12-24
forum: New to Ubuntu
---

### Post by vasa1 on 2012-12-24
I've been using sudo nano to edit my Privoxy user.action file and can't remember ever using nano without sudo.
Today, for the first time, I used nano on a file that I own and so didn't prefix sudo.
I saw this:
```
Error reading /home/vasa1/.nano_history: Permission denied

Press Enter to continue starting nano.

```
I pressed Enter and could then edit the file without issue.
I then ran ls -al on my home directory and saw that .nano_history is owned by root.
```
-rw-------  1 root    root       55 Dec 21 17:57 .nano_history
```

/etc/nanorc has this:
```

## Enable ~/.nano_history for saving and reading search/replace strings.
set historylog
```
It's not really a big deal, I just have to press enter to proceed, but I thought it strange that a file, .nano_history, in my home folder should be owned by root.

Edit: I commented out "set historylog" in /etc/nanorc and then renamed .nano_history to something else and now I can use plain nano without the "Permission denied" error.

---

