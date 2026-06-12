---
title: "[SOLVED] Shell Scripting and FTP"
date: 2008-01-13
forum: Programming Talk
---

### Post by 71fnRVVm on 2008-01-13
Hi everyone,

I've been looking at some docs online regarding shell scripting and FTP usage, but am having some problems.

I can connect to the host, but not actually login.  I've tried:
```

ftp -n $conn_loc;
user $user $pass;

ftp -n $conn_loc;
user $user;
pass $pass;

ftp -n $conn_loc;
USER $user;
PASS $pass;

ftp -n $conn_loc;
quote user $user $pass;

ftp -n $conn_loc;
quote user $user;
quute pass $pass;

```

And always with the same result.  I can't find anything else on this topic that's helpful... any suggestions?

Thanks

---

### Post by yabbadabbadont on 2008-01-13
If the user and password don't change, put them in ${HOME}/.netrc and ftp will use them automatically.  It has been a very long time since I have worked with ftp scripts, but I seem to remember that you can specify different user/pass combinations in the .netrc for different servers.  Also, you have to redirect input to the ftp program in order to issue commands from a script.  Something like
```
ftp -n $conn_loc < script-with-ftp-commands
```
At least that is how we did it in my old Unix days.  :)

---

### Post by ghostdog74 on 2008-01-13
> **71fnRVVm said:**
> Hi everyone,

I've been looking at some docs online regarding shell scripting and FTP usage, but am having some problems.

I can connect to the host, but not actually login.  I've tried:
```

ftp -n $conn_loc;
user $user $pass;

ftp -n $conn_loc;
user $user;
pass $pass;

ftp -n $conn_loc;
USER $user;
PASS $pass;

ftp -n $conn_loc;
quote user $user $pass;

ftp -n $conn_loc;
quote user $user;
quute pass $pass;

```

And always with the same result.  I can't find anything else on this topic that's helpful... any suggestions?

Thanks

that is not the correct syntax. you use a HERE document to do auto ftp login

```

ftp  -n server.com <<_EOD
user $user $password
cd somewhere
bin
get file
bye
EOD



```

---

### Post by geirha on 2008-01-13
> **ghostdog74 said:**
> 
```

ftp  -n server.com <<[color=red]_[/color]EOD
...
EOD

```

A minor error has sneaked in here, there should be a space where that underscore is, so that the EOD matches the ending EOD ...

That's the way I would do the ftp too, btw.

---

### Post by 71fnRVVm on 2008-01-13
Hi,

Thanks for the help.

I did this:```

ftp -n $conn_loc << FTP_LOGIN
user $user $pass
cd $dir_loc1
ls
FTP_LOGIN

```

It manages to attempt to login, but then hangs for about 5 minutes... and then returns
```

Authentication failed, sorry.
Login failed.
You aren't logged in.
```

My username and password are exactly as they should be... did I do anything wrong?

Thanks again

---

### Post by geirha on 2008-01-13
Does the username or password contain any special characters, like spaces?

My guess is, it's either that, or you have some error in the code that sets those variables.

---

### Post by 71fnRVVm on 2008-01-13
Well, the domain name has a dash in it ("int-ind.com") and the username contains an at symbol ("@").  I can't login without doing [email]theuser@int-ind.com[/email] as the username, it's not setup to allow anything but that, and I can't change that.

As far as variables go, it looks like:
```

user="theuser@int-ind.com"
pass="thepassword"

```

Thanks

---

### Post by geirha on 2008-01-13
It all looks correct to me. If you run ftp manually, with ```
ftp -n *hostname*
``` and then type ```
user theuser@int-ind.com thepassword
``` at the ftp-prompt, it connects successfully?

---

### Post by 71fnRVVm on 2008-01-13
Yes, I get logged in within seconds.

---

### Post by geirha on 2008-01-13
That's odd. Try adding the following line just above the ftp-command:
```
echo -e "'$conn_loc'\n'$user'\n'$pass'\n'$dir_loc1'\n"
ftp -n $conn_loc << FTP_LOGIN
 ...

```
And check that all those four variables are printed correctly. If they are, I'm out of ideas, it should just work ...

---

### Post by 71fnRVVm on 2008-01-13
Yeah, they all print properly.  I checked that before I even posted here... I'm not very experienced in Shell Scripting, but have cut my teeth on many other languages over the years ;-)

I thought *maybe* that I was using the wrong password, but it turns out I wasn't.

I guess I'll have to contact MediaTemple (my host) and see why this isn't working when it should be.  Maybe it's a port issue or something.

Thanks for the help though!

---

### Post by yabbadabbadont on 2008-01-13
Read up on using .netrc for storing your username and password.

---

### Post by 71fnRVVm on 2008-01-13
I saw .netrc was an option, but prefer to keep this script self contained... which is why I didn't/don't use it.

I actually figured out what the problem was, after calling (mt).  They require:
```

ftp -np
```
or
```

pftp -n
```
instead of ```

ftp -n
```

Weird, the problem I was struggling with was passive mode.

Thanks again!

---

### Post by danielgroves on 2010-05-23
Hi,

I'm trying to connect via shell, like you were, to FTP, and failing dismally.  I'm also new to Shell scripting, and after reading this thread I have now been left rather confused.  I was wondering if you would mind posting the complete script that you used in order to connect to FTP after a shell script here?  It would be extremely helpful.  

Thanks in advance,
Dan.

---

