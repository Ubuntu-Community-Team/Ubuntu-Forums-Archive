---
title: "How do I enable/install software in the partner repository"
date: 2013-09-11
forum: New to Ubuntu
---

### Post by SpazCool on 2013-09-11
Do to a host of problems with this install of Ubuntu, the first of which I have since forgotten, I have been instructed to "enable partner repositories." A couple of hours of searching has led me to this well written and easy to follow website:  [HTML]http://askubuntu.com/questions/14629/how-do-i-enable-the-partner-repository[/HTML]  His first instruction is to click the "Ubuntu" button, I see no such button on my desktop but, I managed to find a similar set of options in the Ubuntu Software Center, I'm hoping that is my Ubuntu version's equivalent. Then the author's instructions read, simply click the available options of "canonical partners."   My problem is I have no such options to choose from. Googling "add/install canonical partners to software sources" brings up a whole new set of problems and terminology that a novice, such as myself, can't begin to decipher.   There is a whole mess of problems with this setup I have, but for the ease of this thread, I just want to add the canonical partners to the "Other Software" sources.  Any help would be appreciated.

---

### Post by deadflowr on 2013-09-11
Simplest way, if using precise(12.04) is to open the update manager and go to the settings button and click on it.
Then go to the "other software" tab when the software sources window opens.
Then check the listings for partner(I think there are two, but you only need one:click 'em both anyway)
It'll ask for a password, so give it your password.
Now close this window, and then click check in the update manager.
This will reload the package list for you.
When all done, any packages included with the partner repo will be available for you.

If you have installed synaptic, then this can all done with synaptic.
In synaptic, go to settings > repositories follow the advice above.
When you close the software sources window, click on reload.

---

### Post by SpazCool on 2013-09-13
Again, in my "partner" section I see no listings for canonical; which I have been lead to believe is the repository I need to allow.  I do have two listings, but I believe one is from a failed attempt to download Steam and the other, from another failed attempt to download, Chrome.  There are buttons to "add volumes", but I'm afraid of just clicking away and causing more problems for myself.

---

### Post by ibjsb4 on 2013-09-13
Please post the output of:

```
cat /etc/apt/sources.list
```

[https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal](https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal)

---

### Post by SpazCool on 2013-09-15
Alright guys & gals, I thank you all for your help and ideas. But, it has been more than a week on this install and I'm still drowning in problems; that is, it's time for a re-install. While such an action doesn't help me learn what was wrong to begin with, it has given me a chance to reconsider my views on and desires for Linux. I've installed Ubuntu to help familiarize myself with Linux but, I fear, it is too similar to Windows to really teach me anything about system's internal structure. 

Because of this I will be deleting Ubuntu and replacing it with a "harder" distro; slackware, arch and LFS have all been mentioned to me; and given my novice understanding of Linux I'm sure I'll be drowning in those as well. 

Again, thanks for the help, I'm sure I'll still be on here looking for help with the next distro...and possibly the one after that.

---

### Post by deadflowr on 2013-09-15
Ubuntu is nothing like Windows.
And you can learn as much about linux with Ubuntu as with any other distro.
The only real difference is in how distros manage their packaging and installation procedures.

But getting back to the finer points of this thread, what was the output for the command
```
cat /etc/apt/sources.list
```

It is of interest to see if you're list has the partner repos listed.

---

