---
title: "Help with permission denied executing a perl script from the command line"
date: 2011-07-14
forum: Programming Talk
---

### Post by tanoloco on 2011-07-14
Hello!

I was setting up a lamp, configuring the cgi-bin folder
but I was always getting a permission denied message in error.log
stopping me.

I changed everything I could think but still I can't browse
to my script.

Please can anyone help me?

Scenario:

I wrote the easiest perl script in the world
```
#!/usr/bin/perl

print "Content-type: text/plain; charset=iso-8859-1\n\n";
print "Hello"
```

I checked my path to interpreter
```
$ which perl
/usr/bin/perl

```

I saved my script under /media/data/www/cgi-bin
and chmodded 777 everything in the path I mean:
data www cgi-bin and script.pl
They are all 777!
(Of course they are NOT my normal permissions, I use them only now for debugging)

if I open a terminal I get correctly
```
$ cd to /media/data/www/cgi-bin
$ perl script.pl
Content-type: text/plain; charset=iso-8859-1

Hello
```
but if I use
```
$ ./script.pl
bash: ./script.pl: Permission denied
```

same if I use ```
$ sudo ./script.pl
bash: unable to execute ./script.pl: Permission denied
```

So now!
I moved the script on /tmp and chmodded it 777
tried ./script.pl and it worked!

Then I suppose **it's something about the way I mount** the drive data.
Maybe I loose some **permissions of execute** something.
I mount it at start-up using fstab
```
/dev/sdb5	/media/data	ext4	defaults,users,errors=remount-ro	0	1
```

Is there a way to tell it to execute everything?
Does anyone know how to solve it? I'm puzzled !!!

Many thanks in advance

---

### Post by fdrake on 2011-07-14
what does this command says?

```
ls -al script.pl
```

---

### Post by tanoloco on 2011-07-14
```
$ ls -al script.pl
-rwxrwxrwx 1 root root 88 2011-07-15 02:28 script.pl

```

---

### Post by fdrake on 2011-07-14
on fstab try adding umask=000 this should make all file executable.like this:

```
/dev/sdb5	/media/data	ext4	defaults,users,umask=000,errors=remount-ro	0	1
```

link [fstab otions]("https://help.ubuntu.com/community/Fstab#Options")

---

### Post by tanoloco on 2011-07-14
Hey!

I found the solution thanks to this thread
[http://www.linuxquestions.org/questions/programming-9/cant-execute-c-binaries-permission-denied-even-though-permission-is-777-a-102959/]("http://www.linuxquestions.org/questions/programming-9/cant-execute-c-binaries-permission-denied-even-though-permission-is-777-a-102959/")

For me the solution was to change the fstab entry in
```
/dev/sdb5	/media/data	ext4	defaults,exec,errors=remount-ro	1	1
```

I added exec, but it didn't work until I removed users, which is a group. I always thought defaults already contains exec, in fact it works even without exec.

I don't remember why I added this group name, now I have to check if this will cause me other problems somewhere ... 

Anyhow this seems to be solved! :)

---

### Post by cgroza on 2011-07-14
> **tanoloco said:**
> 

Anyhow this seems to be solved! :)
Then mark the thread as such.:)

---

### Post by tanoloco on 2011-07-14
> **fdrake said:**
> on fstab try adding umask=000 this should make all file executable.like this:

```
/dev/sdb5	/media/data	ext4	defaults,users,umask=000,errors=remount-ro	0	1
```

link [fstab otions]("https://help.ubuntu.com/community/Fstab#Options")

I tried it, but:
changed fstab into
```
/dev/sdb5	/media/data	ext4	defaults,users,umask=000,errors=remount-ro	1	1
``` 
and
```
$ sudo mount -o remount /media/data
mount: /media/data not mounted already, or bad option"
```

---

### Post by tanoloco on 2011-07-14
> **cgroza said:**
> Then mark the thread as such.:)

Done! :)

Thank you all!
I hope this could help someone else ...

---

### Post by tanoloco on 2011-07-14
> 

I don't remember why I added this group name, now I have to check if this will cause me other problems somewhere ... 



Now I remember! It was for acl support!
As per my old thread
[http://ubuntuforums.org/showthread.php?t=1414003]("http://ubuntuforums.org/showthread.php?t=1414003")

So now I installed again acl and I changed fstab into
```
/dev/sdb5	/media/data	ext4	users,exec,acl,errors=remount-ro	0	1
```
did some test and everything is woking perfectly!!

Both acl and cgi-bin issues!

Thanks again

PD: Why putting defaults and a group name stuck?

---

