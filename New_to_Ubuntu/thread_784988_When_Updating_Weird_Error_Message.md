---
title: "When Updating Weird Error Message"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by Spiritcrisis on 2008-05-07
Ubuntu 8.04 - the Hardy Heron



Question: What should I do?


Error Message:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

More Info:
The problem was created due to a freeze up during install of new updates. I was forced to restart the computer the old fashioned way... hold the power button. When I restarted I tried to resume the update or check to see if everything has been installed. When the updater began downloading the information for the new updates this error occurred.

---

### Post by llamakc on 2008-05-07
That's not a weird message. It is an informative one.

Open the Terminal program. Run the following:

```

sudo apt-get -f install

```

And after that:

```

sudo dpkg --configure -a

```

Post back any other error messages. If you have to post back more errors please give further details (what you were using before, what you're upgrading to, what the contents of the file /etc/apt/sources.list contains) please.

---

### Post by Xiong Chiamiov on 2008-05-07
Well, do what it says:
```

sudo dpkg --configure -a

```

---

### Post by lsmobrian on 2008-05-07
goto Applications -> accessories -> terminal

and type

```
sudo dpkg --configure -a
```

---

