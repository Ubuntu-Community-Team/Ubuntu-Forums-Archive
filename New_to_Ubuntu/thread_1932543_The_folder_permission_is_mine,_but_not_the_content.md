---
title: "The folder permission is mine, but not the contents"
date: 2012-02-27
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2012-02-27
Honestly! I've netsearched for: change permission directory file.

I found lots of hits.

My problem is I copied a folder onto a cd-rom. When I next needed it, I copied it back to the desktop. There, it's folder or directory permission are that of me the user. BUT the folders and filed within it are all show with a lock icon on each file and folder.

the folder sits as follows:

/home/mark/first-last-name

from the command line, how do I recursively change the permission so that the user (me) is the owner/modifier?

---

### Post by mikewhatever on 2012-02-27
```
sudo chown -R $USER:$USER /home/mark/first-last-name
```

Hope that works. ;)

---

### Post by Mark_in_Hollywood on 2012-02-27
Some days it doesn't pay to get out of bed. 

I tried it. To no avail.

If you are reading this, please do not post further. I wish I could fix this, but as I can read all the files, but not edit or 'own' them, it's enough and I don't wish to take more posters time.

Thank you, Ubuntu Community.

---

### Post by forrestcupp on 2012-02-27
But someone else may search through here and need an answer. 

Try this:
```
sudo chmod ugo+rw -R /home/mark/first-last-name
```

---

### Post by Mark_in_Hollywood on 2012-02-27
Thank, that fixed it. I'll look up the 'ugo' part to learn the distinction from chown and chmod.

---

### Post by audiomick on 2012-02-27
> **Mark_in_Hollywood said:**
> ... I'll look up the 'ugo' part ....

try

```
man chown
```

and 

```
man chmod
```
to look at the man pages. They are sometimes a bit cryptic, but should list the options and help you understand the difference.

---

### Post by forrestcupp on 2012-02-27
> **Mark_in_Hollywood said:**
> Thank, that fixed it. I'll look up the 'ugo' part to learn the distinction from chown and chmod.
ugo means user, group, and other. ugo+rw means you gave read/write permission to everyone. chmod is the command that modifies the permissions on files. The -R is for recursion on all of the folders and files within that folder.

---

### Post by 1clue on 2012-02-27
That's really not a very good permission to give on a directory.

What you've done is give global write to that directory and the files in it to anyone who can get CPU time on the system.  Which could be you or your family, or somebody from who knows where.  They don't need to even log in if they can leverage some security hole.

Try **chown go-rw -R /home/mark/first-last-name**

That takes away everything done with the prior 'ugo' command, except it leaves what happened for the owner.

---

### Post by Miljet on 2012-02-27
@ 1clue

```
chown go-rw -R /home/mark/first-last-name
```

That certainly won't work. I'll leave it to you to figure out why.

---

### Post by forrestcupp on 2012-02-28
> **1clue said:**
> That's really not a very good permission to give on a directory.

What you've done is give global write to that directory and the files in it to anyone who can get CPU time on the system.  Which could be you or your family, or somebody from who knows where.  They don't need to even log in if they can leverage some security hole.

Try **chown go-rw -R /home/mark/first-last-name**

That takes away everything done with the prior 'ugo' command, except it leaves what happened for the owner.

So it would have been better to just do a **chmod u+rw** instead of a ugo+rw?

You could probably take the group and other off and leave only user permission with this, couldn't you?
```
sudo chmod go-rw -R /home/mark/first-last-name
```

---

### Post by 1clue on 2012-02-28
Exactly.  You would also need to **chown -R you:yourgroup** or **chown -R you** to make sure of ownership.

There is a shorthand numeric way of changing permissions as well.  It can be pretty confusing for a new user, but it works better than most operating systems in my opinion.  The ones with more precise control seem to require a lot more forethought in that sort of thing.

---

