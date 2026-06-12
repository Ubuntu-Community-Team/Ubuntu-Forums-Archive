---
title: "rsync exclude/include and RSYNC_PASSWORD help"
date: 2014-02-25
forum: New to Ubuntu
---

### Post by s0mba on 2014-02-25
Considering the following directory structure:
```
/work/
|-- bak/
    |-- samples/
|-- int/
|-- samples/
|-- repos/
|-- release/
```

How to make sure that only the top level "samples" is excluded, and the bak/samples/ is there?..
Example script:

```
#!/bin/bash                                                                     
export PATH=$PATH:/bin:/usr/bin:/usr/local/bin
export RSYNC_PASSWORD=pass
SDIR=/work
DST=user@srv:/backup/work
OPTS="--force --delete --ignore-errors --archive -v -e ssh"
EXCLUDE="--exclude=samples --exclude=release --exclude=repos"
                                                                                
rsync $OPTS $EXCLUDE --dry-run $SDIR $DST
```

And another question. Looks like [COLOR=#b22222][FONT=arial]export RSYNC_PASSWORD=pass[/FONT][/COLOR] does not have an effect. The password prompt is still there. What am I missing here?

Thanks!

---

### Post by SeijiSensei on 2014-02-25
Won't excluding only work/samples solve this problem?

As for the password, I recommend using [shared SSH keys]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys") so you don't need to use any passwords at all.

---

### Post by s0mba on 2014-02-25
Thanks, looks like
[COLOR=#000000][FONT=Ubuntu Mono]EXCLUDE="--exclude=work/samples --exclude=release --exclude=repos"
[/FONT][/COLOR]did the trick.
I know about the SSH keys, but can only use the password protected keys.. Is there a way to somehow have the password in the script, so that I does not need to be entered manually?

---

### Post by Habitual on 2014-02-25
> **s0mba said:**
> Is there a way to somehow have the password in the script, so that I does not need to be entered manually? Yes, but NO.
Passwords in scripts is not recommended and **not secure.**

See [http://askubuntu.com/questions/46930/how-can-i-set-up-password-less-ssh-login](http://askubuntu.com/questions/46930/how-can-i-set-up-password-less-ssh-login)

---

