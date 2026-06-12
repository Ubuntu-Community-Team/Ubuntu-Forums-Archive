---
title: "Bash Script Ping Google"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by DBrocks on 2008-04-28
Hey guys,
I am writing a script to detect when my internet goes down. How can I make a script that, when a ping request to google fails, it does something, and if it succeeds, it just exits? Thanks in advance!!

~Dan

---

### Post by LaRoza on 2008-04-28
> **DBrocks said:**
> Hey guys,
I am writing a script to detect when my internet goes down. How can I make a script that, when a ping request to google fails, it does something, and if it succeeds, it just exits? Thanks in advance!!

~Dan

You can add it to cron. (Google for it, as I am not familiar with that.)

You can have a popup.

```

#!/bin/bash
ping -c 1 64.233.161.99
if [ $? -eq 1 ]
then
    zenity --info --text "Failed to reach google, panic!"
fi

```

---

### Post by DBrocks on 2008-04-28
Perfect! I know how to do cron, it was just the script aspect of it.:lolflag: Thanks alot man! Now, What happened to Thread Tools -> Mark Thread as Solved?

---

### Post by LaRoza on 2008-04-28
> **DBrocks said:**
> Perfect! I know how to do cron, it was just the script aspect of it. Thanks alot man!

Do you want it to do anything else? 

I am not sure if zenity is installed by default, but I think it is. Check by typing "zenity --version" in the terminal.

---

### Post by DBrocks on 2008-04-28
Yea. I know this is REALLY off topic. But, is there a way to back up my programs I got via apt-get on a CD from CLI? (I am running Ubuntu SE), so no GUI. I know Apt on CD is for GUIs only...:( Sorry, I know that question is really off topic!

---

### Post by PinkFloyd102489 on 2008-04-28
```
dpkg --get-selections > installed-software
```

Then open installed-software in your favorite editor to view packages.

---

### Post by DBrocks on 2008-04-28
Awesome!

---

### Post by PinkFloyd102489 on 2008-04-28
Oh I forgot to put this. If you want to use the list to reinstall the packages, just do this:

```
dpkg --set-selections < installed-software
```

---

