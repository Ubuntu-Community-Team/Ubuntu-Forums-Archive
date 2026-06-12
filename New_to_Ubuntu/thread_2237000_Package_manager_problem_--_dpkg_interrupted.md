---
title: "Package manager problem -- dpkg interrupted"
date: 2014-07-30
forum: New to Ubuntu
---

### Post by jbh000911 on 2014-07-30
I appear to have partially installed 2 copies of Dropbox and its taken the package managers out of action, with dpkg being interrupted. The suggested fixes in Terminal haven´t fixed the problem.. Ist fix was to manually run sudo dpkg --configure -a   and the other run sudo apt-get install -f.
I can´t get updates, delete or install programs.
Some advise of other possible correction actions would be greatly appreciated.

:mad:

---

### Post by plucky on 2014-07-30
> **jbh000911 said:**
> I appear to have partially installed 2 copies of Dropbox and its taken the package managers out of action, with dpkg being interrupted. The suggested fixes in Terminal haven´t fixed the problem.. Ist fix was to manually run sudo dpkg --configure -a   and the other run sudo apt-get install -f.
I can´t get updates, delete or install programs.
Some advise of other possible correction actions would be greatly appreciated.

:mad:

You might get an answer if you posted the output of the two commands above.

It does help to actually see what the error is and which package is causing the error.

Good Luck

---

### Post by jbh000911 on 2014-07-31
More info:  Was installing Dropbox on Lubuntu 12.04.3 from repository. Internet connect was extremely slow, slower than diaup, which caused confusion as the install was ¨Waiting" ..... Gnome System Monitor Resources showed that both CPU were working at 100% - but nothing appeared to being achieved. A check of  Gnome System Monitor Processes showed Dropbox twice with %CPU each 50%!
Attempted to access Synaptic but received the message Software Index is broken. It is impossible to install or remove any software. Please use package manager ¨Synaptic¨ or run ¨sudo apt-get install -f¨ in terminal to fix the issue first. 
Running  ¨sudo apt-get install -f¨  resulted in Dropbox install recommencing running to 100% - then generating the message ¨dpkg was interrupted, you must manually run ¨dpkg -- configure -a¨ to correct the problem.
Running ¨dpkg -- configure -a¨  results in Dropbox install recommencing running to 100% - then generating the  message ¨dpkg was interrupted, you must manually run ¨dpkg -- configure  -a¨ to correct the problem.
Talk about going around in circles ...
Some help with Terminal code to remove Dropbox totally would be appreciated.

---

### Post by plucky on 2014-07-31
> Some help with Terminal code to remove Dropbox totally would be appreciated. 

Try ```
sudo dpkg -r dropbox
```

How did you add the dropbox repository?

I just tried it in 14.04 by adding a line into sources.list and somehow it also added the same line in /etc/apt/sources.list.d/dropbox.list.

This led to the error "duplicate entries in sources.list" when I ran "apt-get update".

After removing one entry,I was able to install "dropbox".

Good Luck

---

### Post by jbh000911 on 2014-07-31
I didn´t need to add the Dropbox repository, as Dropbox exists in the Lubuntu repository.
I suspect an earlier unsuccessful attempt was made to install Dropbox from the Dropbox site.

---

