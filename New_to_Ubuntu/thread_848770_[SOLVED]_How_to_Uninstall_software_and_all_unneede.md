---
title: "[SOLVED] How to Uninstall software and all unneeded dependencies"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by KuroYoma on 2008-07-03
I was wondering what would be the best way to uninstall unneeded software if it is not on the synaptic Package Manager list?

---

### Post by Presto123 on 2008-07-03
Post the name of the program and someone may know the answer.

---

### Post by KuroYoma on 2008-07-03
vmplayer   i am trying to get ride of this and it is not in my Synaptic Package manager

---

### Post by skylinedna on 2008-07-03
Lol im tryin to uninstall frostwire. can anyone help? i wan to do a fresh install.

---

### Post by bodhi.zazen on 2008-07-03
How did you install it ? from source or from a 3rd party .deb or alien or ...

---

### Post by drs305 on 2008-07-03
You can do a search with aptitude even though synaptic and aptitude both are part of apt.
```
aptitude search vmplayer
```

If it's found:
```
sudo aptitude purge vmplayer
```

---

### Post by KuroYoma on 2008-07-03
I type in the search and just opens another command line. it does nothing else.  The program itself is located in /usr/bin/vmplayer

and the properties says it is opened with wine

---

### Post by drs305 on 2008-07-03
> **KuroYoma said:**
> I type in the search and just opens another command line. it does nothing else. 

Returning to the command line is the default if 'aptitude search' doesn't have the app 

'registered'. Guess it's to be expected since synaptic also didn't know about vmplayer.

Can you answer bodhi.zazen's question in post #5?

---

### Post by KuroYoma on 2008-07-03
honestly i can't remember, that is why i am having so much trouble.

---

### Post by drs305 on 2008-07-03
Do you have this file anywhere on your system - vmware-uninstall.pl :
```
sudo find / -type f -iname vmware-uninstall.pl
```

---

### Post by KuroYoma on 2008-07-03
thnx its working like a charm, thank you again.

---

