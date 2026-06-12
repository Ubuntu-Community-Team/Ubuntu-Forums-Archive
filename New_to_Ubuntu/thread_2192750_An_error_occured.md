---
title: "An error occured"
date: 2013-12-09
forum: New to Ubuntu
---

### Post by jon-h on 2013-12-09
I am a new user and now have a red no entry sign on the top bar. i t says an error occured, run package manager. i cant a package manager and i cant open the software centre and i cant update anytghing either. is this some kind of bug? HELP i am new to all this, i am trying to get away from microst and all of those problems...??  jon

---

### Post by bashiergui on 2013-12-09
Copy the entire error message and paste it here.

---

### Post by jon-h on 2013-12-20
I have no access to my software and I am not able to update.  The error flag says I should use a package manager, what is a package manager and where do I find it. I have changed from MS to get away from bugs and a constant battle wids virus packages, have made a mistake changing to Ubuntu?  Jon

---

### Post by ventrical on 2013-12-20
> **jon-h said:**
> I have no access to my software and I am not able to update.  The error flag says I should use a package manager, what is a package manager and where do I find it. I have changed from MS to get away from bugs and a constant battle wids virus packages, have made a mistake changing to Ubuntu?  Jon

 You are not barred.

Press the keys:

Ctrl+Alt+t and you will get a terminal.

At the prompt enter these codes.

```

sudo apt-get update <Enter>
sudo apt-get dist-upgrade <Enter>

```

Are you running the 14.04 'Trusty' version of Ubuntu?

---

### Post by Cavsfan on 2013-12-20
Also a good idea to get your updates is adding a few aliases to .bashrc.

**gedit ~/.bashrc**

and add these lines at about line 92:

```
# update aliases
alias **ud**='sudo apt-get update && sudo apt-get upgrade && sudo apt-get clean'
alias **ud2**='sudo apt-get dist-upgrade'
alias **ud3**='sudo apt-get autoremove'

```

Logout and back in. Open up terminal Ctrl+Alt+t if you cannot access it any other way.
Then just enter **ud** in terminal and your password and it will check for updates.

Then if there is an update held back because there is an additional file that is new enter **ud2**.

When it says you have unneeded packages and enter **apt-get autoremove** to remove them just enter **ud3**.

Although these help,  **ventrical** knows more about this stuff than I do.

---

### Post by sffvba[e0rt on 2013-12-20
My package manager just went all loopy on me as well... something with openjdk 7 went belly up.  I had to do a** sudo apt-get -f install** to get it all sorted again... I am on Xubuntu 13.10 (just saying ;) )

---

### Post by Cavsfan on 2013-12-20
> **not found said:**
> My package manager just went all loopy on me as well... something with openjdk 7 went belly up.  I had to do a** sudo apt-get -f install** to get it all sorted again... I am on Xubuntu 13.10 (just saying ;) )

If you know ranch hand, you'll recall he always called update manager "update mangler". :) He told me to always use the CLI method to get updates.

Someone in this forum told me how to put those into .bashrc but I cannot remember who it was.
I added the third one "ud3" myself to save typing. ;)

---

### Post by codemaniac on 2013-12-20
*Thread moved to **Absolute Beginners Section**.*

---

### Post by kansasnoob on 2013-12-20
Sounds like a broken icon??? Sometimes certain apps that are not compatible with various panels display a broken icon in the panel.

We don't even know which desktop environment you're using, or which flavor of Ubuntu you installed. I see you originally posted here:

[http://ubuntuforums.org/showthread.php?t=2192750](http://ubuntuforums.org/showthread.php?t=2192750)

We really need much more info.

---

### Post by holycow131415 on 2013-12-20
OP, you should probably take a screen shot.

---

### Post by kansasnoob on 2013-12-20
Just happened to think ............. try right-clicking on the borked icon and see if it shows an "about". If so clicking on About should provide some info ;)

---

### Post by oldos2er on 2013-12-20
Threads merged. Please don't create more than one thread for the same or similar questions; it's confusing and it dilutes community effort.

---

