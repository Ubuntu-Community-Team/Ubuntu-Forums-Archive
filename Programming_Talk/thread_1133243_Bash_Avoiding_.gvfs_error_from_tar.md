---
title: "Bash: Avoiding .gvfs error from tar"
date: 2009-04-22
forum: Programming Talk
---

### Post by Jesdisciple on 2009-04-22
I've Googled around for this and found lots of cases, at least one of which has been solved, but the solution is somehow evading me.

I'm trying to back up /home because I finally have a Live CD.  The errors are always hidden by filenames, so I redirect stdout to a file to get it out of the way.
```
$ sudo tar -cvzf --exclude /home/chris/.gvfs ~/backup.tar.gz /home > /tmp/output
[sudo] password for chris: 
tar: Removing leading `/' from member names
tar: /home/chris/.gvfs: Cannot stat: Permission denied
tar: /home/chris/backup.tar.gz: Cannot stat: No such file or directory
tar: Removing leading `/' from hard link targets
tar: /home/chris/--exclude: Cannot stat: No such file or directory
```

```
$ sudo tar -cvzf - --exclude /home/chris/.gvfs ~/backup.tar.gz /home > /tmp/output
[stdout prints to the terminal; errors are lost.]
```
I built that command based on [this]("http://www.linuxsa.org.au/pipermail/linuxsa/2005-August/080724.html").

Help, please...

---

### Post by Arndt on 2009-04-23
> **Jesdisciple said:**
> I've Googled around for this and found lots of cases, at least one of which has been solved, but the solution is somehow evading me.

I'm trying to back up /home because I finally have a Live CD.  The errors are always hidden by filenames, so I redirect stdout to a file to get it out of the way.
```
$ sudo tar -cvzf --exclude /home/chris/.gvfs ~/backup.tar.gz /home > /tmp/output
[sudo] password for chris: 
tar: Removing leading `/' from member names
tar: /home/chris/.gvfs: Cannot stat: Permission denied
tar: /home/chris/backup.tar.gz: Cannot stat: No such file or directory
tar: Removing leading `/' from hard link targets
tar: /home/chris/--exclude: Cannot stat: No such file or directory
```

```
$ sudo tar -cvzf - --exclude /home/chris/.gvfs ~/backup.tar.gz /home > /tmp/output
[stdout prints to the terminal; errors are lost.]
```
I built that command based on [this]("http://www.linuxsa.org.au/pipermail/linuxsa/2005-August/080724.html").

Help, please...

I'm not sure exactly what you want solved, but we can begin with some of the error messages: the f option wants the output file as the very next argument, but you have --exclude there. This ought to be a better order:

```
$ sudo tar -cvzf ~/backup.tar.gz --exclude /home/chris/.gvfs /home > /tmp/output

```

You can pipe stderr separately instead of getting it on the terminal (and it won't interfere with sudo's prompt - I guess sudo opens /dev/tty or something):

```
$ sudo tar -cvzf ~/backup.tar.gz --exclude /home/chris/.gvfs /home > /tmp/output 2> /tmp/errors

```

---

### Post by Jesdisciple on 2009-04-23
I also moved the archive so it's not put inside itself, and finally...```
$ sudo tar -cvzf /tmp/backup.tar.gz --exclude /home/chris/.gvfs /home > /tmp/output
[sudo] password for chris: 
tar: Removing leading `/' from member names
tar: Removing leading `/' from hard link targets
```

Thanks!!

---

### Post by Penguin Guy on 2009-04-28
You can get rid of:
[COLOR="Green"]tar: Removing leading `/' from member names[/COLOR]
By adding the [COLOR="Green"]-P[/COLOR] parameter to your command.
Which may also fix your other error:
[COLOR="Green"]tar: Removing leading `/' from hard link targets[/COLOR]

The correct syntax is [COLOR="Green"]--exclude=file[/COLOR] **not** [COLOR="Green"]--exclude file[/COLOR]

* I'm not sure of your Linux knowledge so I would like to point out that parameters **are** case-sensitive (so [COLOR="Green"]-p[/COLOR] and [COLOR="Green"]-P[/COLOR] are two different parameters)

So the new command would be:
[COLOR="Green"]sudo tar -cv**P**zf /tmp/backup.tar.gz --exclude**=**/home/chris/.gvfs /home > /tmp/output[/COLOR]


However I would advise changing some other things:
[LIST]
[*]Add [COLOR="Green"]-p[/COLOR] to retain file permissions
[*]Backup at [COLOR="Green"]/[/COLOR] instead of [COLOR="Green"]/tmp[/COLOR] (unless you actually *want* a temporary backup)
[*]Make it work with usernames other than chris
[*]Name it [COLOR="Green"].tgz[/COLOR] instead of [COLOR="Green"].tar.gz[/COLOR]
[/LIST]

**This is the command that I would most advise using:**
[COLOR="Green"]sudo tar -cv**p**Pzf **/**backup.**tgz** --exclude=/home/*****/.gvfs /home > /tmp/output[/COLOR]

---

### Post by Jesdisciple on 2009-04-29
> **Penguin Guy said:**
> You can get rid of:
[COLOR="Green"]tar: Removing leading `/' from member names[/COLOR]
By adding the [COLOR="Green"]-P[/COLOR] parameter to your command.
Which may also fix your other error:
[COLOR="Green"]tar: Removing leading `/' from hard link targets[/COLOR]Do you happen to know what the practical difference is?

> **Penguin Guy said:**
> The correct syntax is [COLOR="Green"]--exclude=file[/COLOR] **not** [COLOR="Green"]--exclude file[/COLOR]The manpage from our repos seemed to have been lying; see [this thread]("http://www.linuxsa.org.au/pipermail/linuxsa/2005-August/080700.html").  However, it worked with the = this time.

> **Penguin Guy said:**
> * I'm not sure of your Linux knowledge so I would like to point out that parameters **are** case-sensitive (so [COLOR="Green"]-p[/COLOR] and [COLOR="Green"]-P[/COLOR] are two different parameters)Hmm...  I'm actually uncertain whether I would have caught that myself!  :P

> **Penguin Guy said:**
> However I would advise changing some other things:
[LIST]
[*]Add [COLOR="Green"]-p[/COLOR] to retain file permissions
[/LIST]Oh, good idea...  I'm almost certain that matters for some of my stuff.

> **Penguin Guy said:**
> [LIST]
[*]Backup at [COLOR="Green"]/[/COLOR] instead of [COLOR="Green"]/tmp[/COLOR] (unless you actually *want* a temporary backup)
[/LIST]I think I chose /tmp when I wasn't sudoing the command, and the folder needed to be owned by 'chris' but outside of /home.

> **Penguin Guy said:**
> [LIST]
[*]Name it [COLOR="Green"].tgz[/COLOR] instead of [COLOR="Green"].tar.gz[/COLOR]
[/LIST]Is there any practical difference?

> **Penguin Guy said:**
> 
**This is the command that I would most advise using:**
[COLOR="Green"]sudo tar -cv**p**Pzf **/**backup.**tgz** --exclude=/home/*****/.gvfs /home > /tmp/output[/COLOR]OK, thanks!

---

### Post by Penguin Guy on 2009-04-29
> Do you happen to know what the practical difference is?
With [COLOR="Green"]-P[/COLOR] means; backup the folder [COLOR="Green"]/home/music[/COLOR].
Without [COLOR="Green"]-P[/COLOR] means; backup the folder [COLOR="Green"]**.**/home/music[/COLOR].

* Type [COLOR="Green"]pwd[/COLOR] - this will give you the current value of [COLOR="Green"]**.**[/COLOR]


> The manpage from our repos seemed to have been lying; see [this thread]("http://www.linuxsa.org.au/pipermail/linuxsa/2005-August/080700.html"). However, it worked with the = this time.
That's odd, maybe it has something to do with the [COLOR="Green"]-P[/COLOR] option...


> Oh, good idea... I'm almost certain that matters for some of my stuff.
Yes, if you don't use [COLOR="Green"]-p[/COLOR] then it will cause a pain in the *** later when you try to backup (depending on which folders you're backing up).


> Is there any practical difference?
Yes; it looks nicer.
:lolflag:

---

### Post by Arndt on 2009-04-29
> **Penguin Guy said:**
> 

Yes, if you don't use [COLOR="Green"]-p[/COLOR] then it will cause a pain in the *** later when you try to backup (depending on which folders you're backing up).



Isn't it the case that -p is only relevant when extracting from an archive, not when creating it?

---

### Post by Penguin Guy on 2009-04-30
> **Arndt said:**
> Isn't it the case that -p is only relevant when extracting from an archive, not when creating it?
Ah, yes you're right; in that case - remember to use [COLOR="Green"]-p[/COLOR] if and when you extract it.

---

### Post by geirha on 2009-04-30
> **Jesdisciple said:**
> 
Is there any practical difference?


.tgz makes the file easier to use on ancient DOS versions which limited filenames to 8 chars + 3 char extension. .tar.gz is the extension most commonly used, so I'd stick with that.

---

### Post by Jesdisciple on 2009-04-30
OK, thanks!  My laptop won't boot on my DVD-RW, so I have to wait for the Live CD mailed by Canonical to continue...  *checks calendar nervously*

---

