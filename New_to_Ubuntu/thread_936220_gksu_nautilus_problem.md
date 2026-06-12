---
title: "gksu nautilus problem?"
date: 2008-10-02
forum: New to Ubuntu
---

### Post by H.Callahan on 2008-10-02
I was using ```
gksu nautilus
``` to move some picture files to /etc/share/backgrounds.  When I exited Nautilus, this was on the terminal: ```
callahan@callahan-linux:~$ gksu nautilus
Initializing nautilus-open-terminal extension
Initializing nautilus-share extension

** (nautilus:19942): WARNING **: Unable to add monitor: Operation not supported
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSS
--- Hash table keys for warning below:
--> file:///

(nautilus:19942): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 1 element at quit time (keys above)

(nautilus:19942): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 1 element at quit time
seahorse nautilus module shutdown
Shutting down nautilus-open-terminal extension
callahan@callahan-linux:~$ 
```
Since I have JUST upgraded to 8.04 from 7.10 and had some problems with the process (in a different thread), I am concerned about any problems that might appear.

Is this a normal output?  (BTW, everything seems to have worked ok in the Nautilus session).

---

### Post by LowSky on 2008-10-02
It doesn't seem normal, but for curisoity sake, what happens if you start nautilus from terminal without gksu?

---

### Post by H.Callahan on 2008-10-02
> **LowSky said:**
> It doesn't seem normal, but for curisoity sake, what happens if you start nautilus from terminal without gksu?

Runs normally with no warning messages.

---

### Post by LowSky on 2008-10-02
do a reboot and if nothing is wrong I'd say your in the clear

---

### Post by fooman on 2008-10-02
since the error mentions nautilus-open-terminal, have you tried uninstalling nautilus-open-terminal ?...*then* try running gksu nautilus and see if the error still occurs.

if it works with no error...try reinstalling nautilus-open-terminal again and see if its fixed.

---

### Post by H.Callahan on 2008-10-02
First Run after reboot:
```

callahan@callahan-linux:~$ gksu nautilus
Initializing nautilus-open-terminal extension
Initializing nautilus-share extension

** (nautilus:5819): WARNING **: Unable to add monitor: Operation not supported
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSseahorse nautilus module shutdown
Shutting down nautilus-open-terminal extension

```
Second run after reboot since the output was a bit different
```

callahan@callahan-linux:~$ gksu nautilus
Initializing nautilus-open-terminal extension
Initializing nautilus-share extension

--- Hash table keys for warning below:
--> file:///
Shutting down nautilus-open-terminal extension

```
Third run since output is different still
```

callahan@callahan-linux:~$ gksu nautilus
Initializing nautilus-open-terminal extension
Initializing nautilus-share extension

--- Hash table keys for warning below:
--> file:///
Shutting down nautilus-open-terminal extension
callahan@callahan-linux:~$ 

```
Fourth run:
```

clifford@clifford-linux:~$ gksu nautilus
Initializing nautilus-open-terminal extension
Initializing nautilus-share extension
Shutting down nautilus-open-terminal extension
clifford@clifford-linux:~$ 

```
Now it seems to be running clean.  

That kinda makes me nervous.  What is going on?

---

