---
title: "Have messed up sudo..."
date: 2013-05-15
forum: New to Ubuntu
---

### Post by TheRealJimShady on 2013-05-15
Hi there,

I was trying to install some software and every now and again I got error saying that I didn't have permission to write to a specific folder. I was getting bored of doing this command all the time:

> sudo chown -R james /usr/lib/postgres/etc..etc...

So I thought that I would just do this:

> sudo chown -R james /usr/

However I think that I've majorly messed something up by doing this. Now when I try to do this command:

> sudo su postgres

I get an error of:

> sudo: must be setuid root

Reading a forum elsewhere I ran a command and got this, which I gather isn't correct:

> james@Ubuntu01:~$ ll /usr/bin/sudo
-rwxr-xr-x 2 james root 69708 Feb 27 20:32 /usr/bin/sudo*

Could someone please help me sort this mess out? If it helps, then I AM able to get the root/main user of the machine to help me. But I'll need to tell them what to do.

Thanks

James

---

### Post by Kopkins on 2013-05-15
That last output you posted looks correct to me. You just chown'd everything, but you didn't change the group, so the owner is you and the group is root. 

Try undoing it, there shouldn't be anything in /usr NORMALLY owned by your user. To check I checked ownership of all files 4 directories deep in /usr and everything is owned by root on my computer. You could do the opposite of what you did. ```
sudo chown -R root /usr/
```

Also, changing ownership of system files, like in /usr, can be a security risk. Linux is secure because of the way the files are owned and managed. Changing that, chips away at your security.

Good Luck

Kopkins

---

### Post by steeldriver on 2013-05-15
*Most *things in /usr are owned by root - but there are exceptions, basically anything in /usr/local *may* be owned by other people (depending on your sysadmin) and *some* system things are owned by other system accounts e.g.

```

$ find /usr -path '/usr/local' -prune -o ! -user 'root' -ls
653098   44 -rwsr-sr-x   1 daemon   daemon      42800 Oct 25  2011 /usr/bin/at
661405   20 -rwsr-sr-x   1 libuuid  libuuid     17976 Mar 30  2012 /usr/sbin/uuidd

```

Unfortunately neither you nor the other main user will be able to use sudo commands to fix this - you will need to fix sudo first from the recovery console

[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by ajgreeny on 2013-05-15
To avoid having to keep using the sudo prefix in a terminal for a long string of commands you can start with ```
sudo -i
``` which gives you a root terminal and avoids repeating sudo.

Use with care!! You can do great damage to your system if you don't think what you're about before you do something.

---

### Post by TheRealJimShady on 2013-05-15
> **steeldriver said:**
> *Most *things in /usr are owned by root - but there are exceptions, basically anything in /usr/local *may* be owned by other people (depending on your sysadmin) and *some* system things are owned by other system accounts e.g.

```

$ find /usr -path '/usr/local' -prune -o ! -user 'root' -ls
653098   44 -rwsr-sr-x   1 daemon   daemon      42800 Oct 25  2011 /usr/bin/at
661405   20 -rwsr-sr-x   1 libuuid  libuuid     17976 Mar 30  2012 /usr/sbin/uuidd

```

Unfortunately neither you nor the other main user will be able to use sudo commands to fix this - you will need to fix sudo first from the recovery console

[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

Thanks for this. Useful. We have tried to get to the recovery console, however we are using Ubuntu on a virtual machine, and as such we can't seem to get to it. We've been trying for an hour or so now. When we hit SHIFT to get to it, the screen just goes black and stays there until we reboot (power switch).

I think we are going to start afresh by reinstalling the whole virtual machine. Sigh. Thanks for your efforts though.

---

