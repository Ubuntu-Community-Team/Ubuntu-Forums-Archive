---
title: "Firefox tabs not transferring from sudo -&gt; normal"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by linkmaster03 on 2008-06-14
I opened Firefox with sudo once for one reason or another, now I can not open it normally and still have my tabs from last time and bookmarks. I'm on FF3.

---

### Post by sdennie on 2008-06-14
I would try the following:

```

cd
sudo chown -R your_username:your_username .mozilla

```

Replace the two your_username options with your actual user name.  That should make you owner of all the firefox files in your home directory again.

---

### Post by joshsmith on 2008-06-14
looks like the firefox running over as root has taken some files to be own by root (as might be expected) meaning firefox running as the user cant access them

you can take permissions back by running:
sudo chmod -R 755 ~/.mozilla
sudo chown yourusername:yourusernme -R ~/.mozilla
-R sets the permissions recursively

or you could just make a new firefox profile:
run 
gksudo nautilus 
in terminal, and rename the hidden folder .mozilla to .mozilla1

edit: appears i was beaten

---

### Post by aysiu on 2008-06-14
Never run Firefox as *sudo*

If you run the Firefox from Mozilla (as opposed to the one from the Ubuntu repositories), you can run it with the command ```
gksudo firefox
``` in order to install updates, but **never** run the command *sudo firefox*, as you will then run into the problem you've run into.

More details [here](http://www.psychocats.net/ubuntu/graphicalsudo).

---

