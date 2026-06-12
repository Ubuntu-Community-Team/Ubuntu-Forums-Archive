---
title: "[SOLVED] 10gb System Full !!? help..."
date: 2008-07-29
forum: New to Ubuntu
---

### Post by hopelessone on 2008-07-29
Hi,

I just noticed that my Ubuntu install is absolutely full!!

how can i check where is all the unneccesary files..logs...i'm sure theres something weird going on..

thanks..

---

### Post by lisati on 2008-07-29
If you've used package manages a fair bit, the following might help:
```
sudo apt-get clean
```
(There are a couple of others along similar lines)

---

### Post by mevets on 2008-07-29
Baobab is a good utility to determine where the bloat is on your system.

---

### Post by hopelessone on 2008-07-29
thanks for the apt cleaned about 250mb...running Baobab now..

---

### Post by El Conquistador on 2008-07-29
also something else to help in your cleaning process:

sudo apt-get install gtkorphan

A graphical tool to find and remove orphaned libraries

---

### Post by hopelessone on 2008-07-29
the logs are taking up 2.5GB and the 2.6.25 kernel...

heres the screens...

what can i do?

thanks

---

### Post by picpak on 2008-07-29
My solution to this problem was to buy a new computer. :lolflag: Some commands like
```
sudo apt-get autoclean
sudo apt-get clean
```

should help.

---

### Post by hopelessone on 2008-07-29
Why is kernel 2.6.25 there when i'm using 2.6.24-19?

---

### Post by hopelessone on 2008-07-29
how can i delete these log files?

---

### Post by hansdown on 2008-07-29
> **hopelessone said:**
> how can i delete these log files?

Hi hopelessone. You should read this , and point it to someone who understands it more than I do. [http://www.google.ca/search?q=+2.6.25+&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.ca/search?q=+2.6.25+&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by hopelessone on 2008-07-30
Heeeeeaaaalp..

I used sudo nautilus to delete the log files and it made no difference to the unused space???? there is nothing in trash....

What can i do??????

thnaks...

---

### Post by hopelessone on 2008-07-30
```

** (nautilus:31196): WARNING **: Unable to add monitor: Operation not supported

--- Hash table keys for warning below:
--> file:///usr/src
--> file:///

(nautilus:31196): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 2 elements at quit time (keys above)

(nautilus:31196): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 2 elements at quit time
seahorse nautilus module shutdown
redox@redox-pc:~$ 

```

---

### Post by Oldsoldier2003 on 2008-07-30
> **hopelessone said:**
> Heeeeeaaaalp..

I used sudo nautilus to delete the log files and it made no difference to the unused space???? there is nothing in trash....

What can i do??????

thnaks...

you need to empty roots trash either by command line or gui. If you use gui you'll have to CTRL+H in Nautilus to see the hidden folders.

/root/.local/share/Trash/files

---

### Post by hopelessone on 2008-07-30
```
redox@redox-pc:~$ Baobab
bash: Baobab: command not found

```

now what? weird... Baobab crashed the computer last time i ran it? reinstalled in synaptic...

thanks..

---

### Post by hopelessone on 2008-07-30
> you need to empty roots trash either by command line or gui. If you use gui you'll have to CTRL+H in Nautilus to see the hidden folders.

/root/.local/share/Trash/files

Ahhh...see all the files i deleted....how can i delete them... if i delete them they reappear...?

thanks

---

### Post by hopelessone on 2008-07-30
```
 sudo rm -rf /root/.local/share/Trash/files
```

sweet...

3.2GB back !! Woooohoooo...

---

### Post by hopelessone on 2008-07-30
hansdown > Hi hopelessone. You should read this , and point it to someone who understands it more than I do. [http://www.google.ca/search?q=+2.6.2...ient=firefox-a](http://www.google.ca/search?q=+2.6.2...ient=firefox-a)

Haa haa... wouldn't a better one beeee.. [http://www.google.ca/search?hl=en&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aunofficial&q=ubuntu&btnG=Search&meta=](http://www.google.ca/search?hl=en&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aunofficial&q=ubuntu&btnG=Search&meta=)

:popcorn:

---

