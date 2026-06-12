---
title: "Could not save the file “/etc/network/interfaces"
date: 2017-09-14
forum: New to Ubuntu
---

### Post by re3s on 2017-09-14
so im having this problem.. i want to host a server on ubuntu but i need a static ip..
the problem is that i cant save the Interfaces file... i have tried the solutions given [https://ubuntuforums.org/showthread.php?t=1148572](https://ubuntuforums.org/showthread.php?t=1148572) but i still cant save the the file
:confused: :confused::confused:
can anyone help me in this?

---

### Post by Bucky Ball on 2017-09-14
Welcome. How are you opening the file? As root?

```
sudo nano /etc/network/interfaces
```

And how are you trying to save the file? (Ctl+X, 'Y' from memory; follow instructions at bottom of terminal screen.)

Be aware that if you are running a regular Ubuntu, you are also running the Network Manager app. Whatever you set in /etc/network/interfaces will be ignored and the settings in Network Manager used in preference (last I looked). That file and Network Manager do not play well together.

PS: _Strongly_ advise you not follow advice from nearly ten years ago (as per your link). So much has changed in that time it is barely the same OS. ;)

That said, the command given on that link is for opening a gedit GUI as root. Nothing to do with what you are trying to do; save a file edited in a terminal (although, the instructions there are perfectly sound and will still work to open gedit as root, if you happen to have gedit installed which may have been default at the time; not sure about now).

---

### Post by &amp;KyT$0P# on 2017-09-14
Do you really need to touch that file at all?  I give my local server a static IP through NetworkManager ([FONT=Courier New]nmtui[/FONT]).

---

### Post by Bucky Ball on 2017-09-15
> **halogen2 said:**
> Do you really need to touch that file at all?  I give my local server a static IP through NetworkManager ([FONT=Courier New]nmtui[/FONT]).

+1. Same here. I have four machines, all set with static IPs this way. I never touch the /etc/network/interfaces anymore and haven't in ages. ;)

---

### Post by re3s on 2017-09-19
Yes i open it as root and use the same code u have shown here. I am following the instructions bellow the terminal screen.
I am running ubuntu gnome as recommended by my fellows. 
Also THANKS FOR THE ADVICE that that thread is over ten years old.. i did not know how old it was because im new to this forum :D
I have gedit installed and i installed it manually by that i mean i installed it myself.....

---

