---
title: "Confused by quotes in shell script"
date: 2010-12-28
forum: Programming Talk
---

### Post by websavages on 2010-12-28
Hi all,

I am trying to setup an automated rsync job between my server and client. The server ssh daemon listens to port 8888 (for security reasons) and as such I have to issue the following command to get rsync to work

```

rsync -avz --rsh='ssh -p 8888' user@server:/remote/dir /local/dir/

```

Hard coding this into a sh script works, however I would like to tidy things up and use variables. So I split everything up and have the following:

```

RSYNC=/usr/bin/rsync
RSYNC_OPTIONS="-avz  --rsh='/usr/bin/ssh -p 8888'"
RSYNC_REMOTE_HOST="user@server"

$RSYNC $RSYNC_OPTIONS $RSYNC_REMOTE_HOST:/remote/dir /local/dir/

```

But this results in rsync failing with the following messages:

```


building file list ... rsync: link_stat "/usr/local/bin/8888'" failed: No such file or directory (2)
rsync: link_stat "/usr/local/bin/user@servr:/remote/dir" failed: No such file or directory (2)


```

I'm guessing the single quotes are interfering in some way. Any ideas?

ws

---

### Post by MadCow108 on 2010-12-28
edit: nonsense, see later post

you need to quote the variables when using them too:
$RSYNC "$RSYNC_OPTIONS" $RSYNC_REMOTE_HOST:/remote/dir /local/dir/

the quotes in the assignment are not saved in the variable

---

### Post by websavages on 2010-12-28
MadCow,

Thanks for the info, however rsync now complains about:

```

rsync: -avz --rsh='ssh -p 8888': unknown option
rsync error: syntax or usage error (code 1) at main.c(1318) [client=2.6.9]

```

Any ideas?

ws

---

### Post by gmargo on 2010-12-28
One idea: you can eliminate the "-p 8888" by putting that info in your $HOME/.ssh/config file.  That will at least get rid of some spacing issues.

```

$ cat $HOME/.ssh/config
Host server.name.here
    Port 8888

```

---

### Post by websavages on 2010-12-28
Hi gmargo,

You beat me to it. I have just changed my ssh_config file to remove the need for -P 8888.

Thanks for everyones help none the less.

Cheers ws

---

### Post by MadCow108 on 2010-12-28
ups sorry I did not read your post properly, quoting is nonsense.

you have to force bash to reevaluate the expanded options with eval to get the quoting right:
eval "$RSYNC $RSYNC_OPTIONS $RSYNC_REMOTE_HOST:/remote/dir /local/dir/"

---

