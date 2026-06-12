---
title: "new to python trying to fix file copy issue"
date: 2010-03-17
forum: Programming Talk
---

### Post by DouglasAWh on 2010-03-17
I have been fighting with ssh/sftp/ftp/scp and found this python module called paramiko.  Info is at [http://www.lag.net/paramiko/](http://www.lag.net/paramiko/) and it's in the repos as python-paramiko.

I installed and was trying to modify the script at [http://lists.webjunction.org/wjlists/web4lib/2006-July/041030.html](http://lists.webjunction.org/wjlists/web4lib/2006-July/041030.html) to my needs.

Here's my script [http://pastebin.org/116471](http://pastebin.org/116471) , which I am running with python script.py so I don't need the ! in the first line.

I get the following error:

```

Traceback (most recent call last):
  File "sftp.py", line 10, in <module>
    myhostkey = paramiko.RSAKey(data=base64.decodestring('AAIAv8CabCRjhl7cnU='))
NameError: name 'base64' is not defined

```

Any ideas how I would go about defining this?

In the end, I just want to copy a file and I want the password to be in the command.  I cannot do write access with anonymous ftp.  We've made the decision that we are not concerned about this user password not being secure.  The user doesn't have permission to do anything other than access this one directory.  If the password got out, we would still have the same problem as anonymous ftp, but in comparison to the rest of the company servers, this server is of little importance and would not be a target for hackery.  While it is a production server in some sense of the word, only two admins will be using the information in this folder, so if someone deleted the files, no big deal, plus the files should be auto-populating every 15 minutes.  The files will contain no sensitive information.  If we had to reformat the server it really would not be a big deal. In fact, I'm pretty sick of CentOS's old packages and an excuse to move it to the Ubuntu LTS would actually be a blessing only partially in disguise.  The machine is not open to the outside world and smtp is turned off, so it shouldn't be becoming a mail relay.  Basically, all of this is to say I do not want to get a lecture on the security risks of putting a password in a cron job.  

I don't care if this is done in python, bash, C or binary, as long as I can get what I need from the Lucid repos for the client end and the CentOS repos for the server end.

There's a suggestion in that thread about taring and then untaring a file.  I haven't tried that yet.  It seems like unnecessary overhead, but if it works...

---

### Post by geirha on 2010-03-17
To get rid of that error:
```
import base64
```

As for the rest, I don't really see any description of the problem. What's the issue with sftp/scp? and why not put the ftp password in a netrc file?

---

### Post by DouglasAWh on 2010-03-17
> **geirha said:**
> To get rid of that error:
```
import base64
```

As for the rest, I don't really see any description of the problem. What's the issue with sftp/scp? and why not put the ftp password in a netrc file?

Now it's throwing an error in /usr/lib/python2.6/base64.py but I'm assuming I can figure out how to get my known host into that part of the script.

The issue I want to be able to do something like

```

sftp user@server -p sUpErSecurePassword put file

```

but I can't do that, as far as I can tell.

Don't know anything about netrc files.  I'll look into it.

---

### Post by DouglasAWh on 2010-03-17
.netrc files get me logged in, but when I try to run my macro it seg faults.  I'm looking at [http://www.mavetju.org/unix/netrc.php](http://www.mavetju.org/unix/netrc.php) for instructions.

---

### Post by geirha on 2010-03-17
> **DouglasAWh said:**
> 
The issue I want to be able to do something like

```

sftp user@server -p sUpErSecurePassword put file

```

but I can't do that, as far as I can tell.


No, because that would defeat the purpose of a secure protocol. For ssh/scp/sftp, you'll want to use public key authentication or host-based authentication.


A segfault indicates a serious bug in the application you're using. You might want to file a bug report on that.

---

### Post by DouglasAWh on 2010-03-17
> **geirha said:**
> No, because that would defeat the purpose of a secure protocol. For ssh/scp/sftp, you'll want to use public key authentication or host-based authentication.


A segfault indicates a serious bug in the application you're using. You might want to file a bug report on that.

yeah, I know it defeats the purpose...could have just done ftp. .netrc is working.  The login info apparently can all be in one line, but the macros need a spaced out syntax.  It'll make a little harder to maintain the scripts doing it that way, but certainly doable.

Right now what I need to do is pipe a text file I've created to the ftp command. this file is based off the host name, so it's not something I can hard code.

I suppose I could just mount the drive and do a cp.  That's what we do for our other files, but I've never had need to actually mount this particular server, so I didn't think of that.  That probably would have saved me a lot of time.  Might look into that when I get into work tomorrow.

---

