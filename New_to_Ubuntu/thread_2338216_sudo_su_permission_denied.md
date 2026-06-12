---
title: "sudo su permission denied"
date: 2016-09-25
forum: New to Ubuntu
---

### Post by luckystar3 on 2016-09-25
Hello All,
ive tried to install and run a few programs that need sudo access how ever upon typing sudo su and the pass word I get
a permission denied message.

Does anyone have any ideas as to what I can do? Failing this how would I edit 

/etc/apt/sources.list for reference im trying to install docker.

---

### Post by &amp;KyT$0P# on 2016-09-25
> **luckystar3 said:**
>  upon typing sudo su and the pass word I get
a permission denied message.
What "permission denied message"?
Can you please post the full message here?

---

### Post by kc1di on 2016-09-25
you do not have to use su in the commad sudo will do try it with just sudo

---

### Post by luckystar3 on 2016-09-25
[ATTACH=CONFIG]271354[/ATTACH]

---

### Post by Herber on 2016-09-25
I believe you need to use sudo -s.

---

### Post by steeldriver on 2016-09-25
```
/etc/apt/sources.list
```

is a file - not an executable command. If you're trying to *edit *it, try

```
nano /etc/apt/sources.list
```

---

### Post by &amp;KyT$0P# on 2016-09-25
That is not typing [FONT=Courier New]sudo su[/FONT], that is pasting the entire content of /etc/apt/sources.list in the Terminal and then pasting in literally [FONT=Courier New]/etc/apt/sources.list[/FONT].

> how would I edit

/etc/apt/sources.list
Not sure that's the best approach.  First try to create an extra file in [FONT=Courier New]/etc/apt/sources.list.d[/FONT].  Name it whatever you want but give it a .list extension.
Then, run
```
sudo nano /etc/apt/sources.list.d/<yourfile.list>
```
replacing <yourfile.list> with the actual filename, and make your desired edits.  It should be picked up on the next [FONT=Courier New]sudo apt-get update[/FONT].

For more information, run this command in a Terminal -
```
man sources.list
```

---

### Post by oldos2er on 2016-09-25
You need to let the system know what editor you want to open the file in. Exit your root shell, and type ```
sudo nano /etc/apt/sources.list
``` Once you've made your changes, press Ctrl-o to save and Ctrl-x to exit the editor.

Best to make a backup copy before making any changes though: ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
```

---

### Post by luckystar3 on 2016-09-25
That solved it. Thanks for the help.

---

### Post by &amp;KyT$0P# on 2016-09-25
You're welcome :)

---

