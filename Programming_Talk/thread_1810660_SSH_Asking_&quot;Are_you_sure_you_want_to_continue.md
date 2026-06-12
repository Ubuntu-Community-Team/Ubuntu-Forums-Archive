---
title: "SSH: Asking &quot;Are you sure you want to continue connecting (yes/no)?&quot; Every Time?"
date: 2011-07-23
forum: Programming Talk
---

### Post by tdrusk on 2011-07-23
Is there a way, after running the ssh XXX.XXX.XXX.XXX command to ask "Are you sure you want to continue connecting (yes/no)?" every time that it is ran?

---

### Post by dwhitney67 on 2011-07-23
That particular ssh question should only be asked once.  If you acknowledge the question with a "yes", then an entry is placed within your ~/.ssh/known_hosts file.

Make sure that your ~/.ssh directory has the following permission mode set:  700.
```

chmod 700 ~/.ssh

```

Then make sure that your ~/.ssh/known_hosts has the following permission mode:  600
```

chmod 600 ~/.ssh/known_hosts

```

If you have entries within your ~/.ssh/known_hosts that conflict with an entry you are trying to add, then remove the offending entry.

P.S.  If you do not have a ~/.ssh directory, then create it before make the chmod changes noted above.

---

### Post by tdrusk on 2011-07-23
> **dwhitney67 said:**
> That particular ssh question should only be asked once.  If you acknowledge the question with a "yes", then an entry is placed within your ~/.ssh/known_hosts file.

Make sure that your ~/.ssh directory has the following permission mode set:  700.
```

chmod 700 ~/.ssh

```Then make sure that your ~/.ssh/known_hosts has the following permission mode:  600
```

chmod 600 ~/.ssh/known_hosts

```If you have entries within your ~/.ssh/known_hosts that conflict with an entry you are trying to add, then remove the offending entry.

P.S.  If you do not have a ~/.ssh directory, then create it before make the chmod changes noted above.
Thanks, but I still have some problems.

See, I have a script that connects with ssh. If the user has never connected to that host before they will be prompted. If they have, however, they won't be. I am using an expect script to answer the questions, and I can't find a way to account for both situations without simply asking every time.

---

### Post by stylishpants on 2011-07-25
You can disable strict checking of host keys.  With this setting, ssh will connect even if the host key is not found in the known_hosts file.

You can do it on the command line this way:
```
ssh -o "StrictHostKeyChecking no" XXX.XXX.XXX.XXX

```
Or you can update your ~/.ssh/config to include this setting.

For more information: 
```
man ssh_config | less -p StrictHostKeyChecking
```

---

### Post by slavik on 2011-07-25
> **stylishpants said:**
> You can disable strict checking of host keys.  With this setting, ssh will connect even if the host key is not found in the known_hosts file.

You can do it on the command line this way:
```
ssh -o "StrictHostKeyChecking no" XXX.XXX.XXX.XXX

```
Or you can update your ~/.ssh/config to include this setting.

For more information: 
```
man ssh_config | less -p StrictHostKeyChecking
```
at one point I had an expect script to roll through 90 servers via ssh, the quoted post is the method I used. I have come to memorize that option. ;)

---

### Post by mikejonesey on 2011-07-26
> Is there a way, after running the ssh XXX.XXX.XXX.XXX command to ask  "Are you sure you want to continue connecting (yes/no)?" every time that  it is ran?

there are three ways to ensure that you are asked the permissions every time...

1. permissions as noted above, although i would have gone with 400 on the known hosts, so no-one can write to the file? rather than 600?

2. a wrapper script to remove the line from the known_hosts

3. a wrapper script to replace ssh command (update-alternatives, mv ssh, call ssh from new script), new script can have custom read from user...

---

