---
title: "how to turn on universe software source using terminal command"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by t-molli on 2008-05-02
I know I can turn on "Community Maintained Open Source Software (Universe)" by going to 

System -> Administration -> Software Source

However, I'd like to know how you would go about turning on that source using a terminal command.

Thanks!

---

### Post by PeterJS on 2008-05-02
You can use:
```

sudo nano /etc/apt/sources.list

```
and then uncomment the universe lines by deleting the # from the beginning of the line.

---

### Post by unutbu on 2008-05-02
Do you want a command you could, say, put in a script?
Or do you just wish to know how to edit the underlying file, say, with gedit, so that the universe repo is enabled?

---

### Post by t-molli on 2008-05-02
> **unutbu said:**
> Do you want a command you could, say, put in a script?
Or do you just wish to know how to edit the underlying file, say, with gedit, so that the universe repo is enabled?

Yes, a script. Glad you responded 'cause I was just about to reply that I knew about the sources.list, but I wanted a single command that would use Universe and not a command to update/edit the list.

thanks

---

### Post by unutbu on 2008-05-02
Run as root:

```
#!/bin/bash
echo "deb http://archive.ubuntu.com/ubuntu gutsy universe" | tee -a /etc/apt/sources.list 
apt-get update
```

Change gutsy to hardy if that's how you roll.

---

### Post by mlentink on 2008-05-02
> **t-molli said:**
> but I wanted a single command that would use Universe and not a command to update/edit the list.


Just curious, would you mind explaining why you would want that? The sudo-nano-etc-route is pretty straightforward, I would guess.

---

### Post by unutbu on 2008-05-02
Of course, the next question is probably, how to turn off universe? :)

In that case, it is probably better to make two versions of the sources.lst. Call them something like sources.lst-universe sources.list-nouniverse. (Blechy names, sorry).

Then you just use two scripts: 
universe-on:
```

#!/bin/bash
cp /etc/apt/sources.list-universe /etc/apt/sources.list 
apt-get update
```

universe-off:
```
#!/bin/bash
cp /etc/apt/sources.list-nouniverse /etc/apt/sources.list 
apt-get update

```

---

