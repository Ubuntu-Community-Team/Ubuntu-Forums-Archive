---
title: "how can I echo output of ls in a bash script"
date: 2007-07-16
forum: Programming Talk
---

### Post by syxbit on 2007-07-16
I've written a bash script that will do a backup, but it's written to deploy on many computers

how can i echo the output of "ls /Volumes/"  so that I can print it before I ask for the volume name 
thanks

---

### Post by Mr. C. on 2007-07-16
I don't understand - ls already echo's its output to the screen.

What aren't you telling us ?

MrC

---

### Post by jmazzarelli on 2007-07-17
Is this what you are looking for?
```
#!/bin/bash
ls /Volumes/
echo -n "Choose a volume: "
read volume
echo $volume

```

---

### Post by Motoxrdude on 2007-07-17
> **syxbit said:**
> I've written a bash script that will do a backup, but it's written to deploy on many computers

how can i echo the output of "ls /Volumes/"  so that I can print it before I ask for the volume name 
thanks

Idk, this is a kinda round-about-way of doing this, but ill give it a shot.

```
#!/bin/bash
volumes='ls /Volumes/
echo $volumes
```

---

### Post by ghostdog74 on 2007-07-17
> **Motoxrdude said:**
> Idk, this is a kinda round-about-way of doing this, but ill give it a shot.

```
#!/bin/bash
volumes='ls /Volumes/
echo $volumes
```

huh?

---

### Post by syxbit on 2007-07-17
yea, sorry I wasn't clear
your comments all helped too
thanks

---

### Post by Motoxrdude on 2007-07-17
> **ghostdog74 said:**
> huh?

It sets volume as the output of 'ls volume' then echos it.

---

