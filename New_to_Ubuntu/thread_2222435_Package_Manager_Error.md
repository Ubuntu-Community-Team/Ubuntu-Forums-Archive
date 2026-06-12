---
title: "Package Manager Error"
date: 2014-05-06
forum: New to Ubuntu
---

### Post by don62 on 2014-05-06
This error message has been indicated in notification area.

An error occurred, please run 
Package Manager from the right-
click menu or apt-get in a terminal
to see what is wrong.
The error message was. 'Error:
Opening the cache (E:Encountered 
a section with no Package:header,
E;Problem with MergeList/var/lib/
apt/lists/
gb.archive,ubuntu.com_ubuntu_dists_precise_multiverse_binary-
i386_Packages, E:The package lists 
or status file could not be parsed or
opened.)', This usually means that
your installed packages have
unmet dependencies.

I am completely at a loss. Can somebody please help this idiot through this problem.

---

### Post by papibe on 2014-05-06
Hi don62.

Open a termina, and run this commands:
```
sudo apt-get clean

sudo mv /var/lib/apt/lists /var/lib/apt/lists.old

sudo mkdir -p /var/lib/apt/lists/partial

sudo apt-get clean

sudo apt-get update
```
Let us know how it goes.
Regards.

---

### Post by don62 on 2014-05-06
Thank you for your quick response. Somehow my thread header got changed.
It should have been "ubuntu 12.04 LTS Error in notification area"
I've no idea how it got changed to "Mr"
sudo apt-get clean com   seemed to complete quickly
but
sudo mv /var/lib/apt/list /var/lib/apt/list.old
returned this
mv: cannot stat `/var/lib/apt/list': No such file or directory
    
so I didn't proceed further.
Any further advice will be greatly appreciated.

---

### Post by papibe on 2014-05-06
Please continue with the commands, the next one create the directory is missing.

Regards.

---

### Post by Bashing-om on 2014-05-06
don62; Hey,

Just in passing by:
There exist a slight typo in the command:
```

sudo mv /var/lib/apt/list /var/lib/apt/list.old

``` Indeed that file "list" does not exist.
correct by supplying the correct file name as list[color=green]s[/color]
Where an 's' is missing on lists.
To be:
```

sudo mv /var/lib/apt/lists /var/lib/apt/lists.old

```

And all should be hunky dory.

[INDENT][INDENT][INDENT]happens - even to the best -
[/INDENT][/INDENT][/INDENT][INDENT][INDENT]of us
[/INDENT][/INDENT]

---

### Post by papibe on 2014-05-06
Thanks Bashing-om.

---

### Post by Bashing-om on 2014-05-06
@papibe'
meh,
How many times have you pulled my much hotter taters out of the fire ! .. just thought ya might be a bit busy and I could address this little bitty thing. 

The little I can do 
[INDENT][INDENT]I help
[/INDENT][/INDENT]

---

### Post by don62 on 2014-05-06
Thanks  papibe & Bashing-om. Everything worked out fine. Looking good again.
I must try & learn how to do these things,
If you guys ever find yourselves in UK, look me up in North Yorkshire 'cos I owe you
one - well more than one actually. Thanks again guys.:D    
:guitar:

---

