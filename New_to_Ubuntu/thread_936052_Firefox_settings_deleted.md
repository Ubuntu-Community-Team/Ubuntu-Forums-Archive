---
title: "Firefox settings deleted"
date: 2008-10-02
forum: New to Ubuntu
---

### Post by silenthunter747 on 2008-10-02
My firefox installation seems to be entirely screwed. I started it today and my bookmarks were gone, history blank, passwords gone, and even the "stop" button is grayed out. The strange thing is they continue to stay blank. Sites I visit aren't being recorded, and even the back/forward buttons stay blank.

This all happened around the time I was installing Vmware Server 2.0. I've tried reinstalling FireFox, but that was no help. The only thing I can think of is that since the new vmware runs in Firefox, that it now has permissions Firefox instead of me. Any ideas on what's going on and how to fix it?

---

### Post by mrtomservo on 2008-10-02
This happened to me a couple of weeks ago... in my case, something I was running ate up all the remaining hard drive space.  It resulting in all my bookmarks being gone, no arrows, stop button, etc.  After removing the stuff that sucked up my hd space everything went back to normal.  I then preceded to make a backup of my bookmarks. :)

---

### Post by silenthunter747 on 2008-10-02
I got pretty low while installing vmware, but I don't think I ran out and now I have 2.2gb free, 1.7gb available. Did you have to do anything else or did it just fix itself after you freed up some space?

---

### Post by mrtomservo on 2008-10-02
In my case it just resolved itself after freeing up space, and rebooting.  However, you might want to try renaming your ~/.mozilla directory to another name, say ~/.mozillabackup or something.  That way you can rename it back if this step doesn't work.  Then try restarting FF.  Lemme know what happens!

EDIT: You should also try disabling any plugins you may have running in Firefox.

---

### Post by silenthunter747 on 2008-10-02
well I think the problems started when I used:

```
sudo vmware
```

to run the server like I had to in the old vmware. So firefox runs normally if I run that command again and just navigate away from the vmware page, or if I do:

```
sudo firefox
```

So I guess I lost permissions. I assume I can get those back, right? (I don't know which files were altered though :-?)

---

### Post by LastWho on 2008-10-02
Hi
i m a newbee/noob here, but since you re talking about permissions, why don't you check these and post the results:[INDENT]
```
ls -Flarth .mozilla
```


```
cd .mozilla
ls -Flarth

```


```
cd firefox
ls - Flarth

```[/INDENT]

---

### Post by silenthunter747 on 2008-10-02
.mozilla
```
total 20K
drwx------  3 gavin gavin 4.0K 2008-07-29 03:17 firefox/
drwx------  3 gavin gavin 4.0K 2008-07-29 03:17 extensions/
-rw-r--r--  1 gavin gavin  335 2008-08-26 11:53 appreg
drwx------  4 gavin gavin 4.0K 2008-08-26 11:53 ./
drwxr-xr-x 89 gavin gavin 4.0K 2008-10-02 11:02 ../

```

firefox
```

total 16K
-rw-r--r-- 1 gavin gavin   94 2008-07-29 03:17 profiles.ini
drwx------ 3 gavin gavin 4.0K 2008-07-29 03:17 ./
drwx------ 4 gavin gavin 4.0K 2008-08-26 11:53 ../
drwx------ 8 gavin gavin 4.0K 2008-10-02 12:52 kigqs8w9.default/

```

---

### Post by mrtomservo on 2008-10-02
I could be wrong, but those permissions look ok to me.  Unfortunately i'm not very familiar with VMware, so i'm not sure what else to suggest! :(

---

### Post by silenthunter747 on 2008-10-02
I can't really explain, but the problem seems to have fixed itself. I didn't restart or anything, it just works now. Thanks for your help though.:-?

so in review:
-Firefox was broken
-used sudo to run firefox
-looked at the permissions of firefox
-firefox works without sudo

---

### Post by aysiu on 2008-10-02
Just for the future, you shouldn't run Firefox with the command *sudo firefox*

If you ever need to run Firefox as root (and the only case I can think of is if you're trying to install updates for the Mozilla--not Ubuntu--version of Firefox), you should use the command ```
gksudo firefox
```

---

### Post by LastWho on 2008-10-02
> **aysiu said:**
> Just for the future, you shouldn't run Firefox with the command *sudo firefox*

If you ever need to run Firefox as root (and the only case I can think of is if you're trying to install updates for the Mozilla--not Ubuntu--version of Firefox), you should use the command ```
gksudo firefox
```

here is what i found on wiki:
> 
#** su** is a command line tool for Unix. It allows users to switch the terminal to a different account by entering the username and password of that account. If no user name is given, the operating system's superuser account (known as "root") is used, thus providing a fast method to obtain a login shell with full privileges to the system. Issuing an exit command returns the user to their own account.

# **sudo**, created around 1980, is a Unix command line tool similar to su, but it allows certain users to run programs with root privileges instead of having to switch to the root account.

# **gksudo **is a graphical frontend to sudo included with Ubuntu. It comes up automatically when a supported application needs to perform an action requiring root privileges.
[IMG]http://upload.wikimedia.org/wikipedia/en/9/9d/Gksudo.png[/IMG]



# **kdesu** is a graphical front-end to the su command.
[IMG]http://upload.wikimedia.org/wikipedia/en/9/9e/Kdesu_proper.png[/IMG]

# **kdesudo** is a graphical front-end to sudo that has replaced kdesu in Kubuntu, starting with the Gutsy Gibbon Tribe 5 pre-release version.

but still don't understand why gksudo and not sudo?
and what "gk" stand (s) for?

can u please explain to us, thx

---

### Post by aysiu on 2008-10-02
> **LastWho said:**
> here is what i found on wiki:


but still don't understand why gksudo and not sudo?
and what "gk" stand (s) for?

can u please explain to us, thx
Read this:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by LastWho on 2008-10-02
> **aysiu said:**
> Read this:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

i feel like i m less --stupid, oops i mean more --stupid, noooo, w/e.. thank u so much aysiu :p :KS

---

