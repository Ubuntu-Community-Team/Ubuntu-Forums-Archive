---
title: "K3b errors"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by philk949 on 2008-08-07
Hi,
I've posted on this topic before, but the issue remains unresolved.
I find the K3b burning tool to be just about useless, as all I get from it are error messages and announcements re the shortcomings of my CD writer (when it deigns to even recognise my writer). I don't know of any other  tool for burning .iso images, which is what I'm trying to do.
Have attached screenshots to illustrate.
Can anyone help me with this, please?

Phil

---

### Post by rokytnji on 2008-08-07
Have you tried using Braserio instead of k3b? Its in synaptic package manager and add/remove/.

---

### Post by LowSky on 2008-08-07
seems odd that you dont have permission to your cd-r drive. hmmmm

try running k3b with sudo access for the time being until someone smarter knows a fix,
 hit Alt+F2
```

sudo k3b
```

---

### Post by philk949 on 2008-08-07
Have tried Brasero - equally useless, and does not burn .iso images.
Ran the sudo k3b command and tried again - no result, except for the OS strongly disapproving of root command. 
Is my problem with the unsupported buffer underrun (burnfree) perhaps? (not that I know what that is).

Phil

---

### Post by oldos2er on 2008-08-07
Sounds like your user doesn't have CD-ROM access. Look in System, Administration, Users and Groups, check your user properties.

---

### Post by philk949 on 2008-08-08
User has full privileges, so don't understand that particular error message.

Phil

---

### Post by eightmillion on 2008-08-08
Phil, could you paste the output of the command **groups** please?

---

### Post by philk949 on 2008-08-08
For your viewing pleasure, 8 mill.

Phil

---

### Post by philk949 on 2008-08-08
And another thing.... since running K3b as root, I can no longer open it from outside the terminal.

Phil

---

### Post by eightmillion on 2008-08-08
It seems that there can be a conflict between nautilus-cd-burner and wodim. You might try checking if an instance of nautilus-cd-burner is running and killing it and trying the burn again.

---

### Post by philk949 on 2008-08-08
> You might try checking if an instance of nautilus-cd-burner is running and killing it and trying the burn again. 

How might this absolute beginner do that, pray tell?

Phil

---

### Post by eightmillion on 2008-08-08
> pgrep nautilus-cd-burner
If that process is running, it will output a number, the process's PID. To kill it:
> sudo pkill -9 nautilus-cd-burner

---

### Post by philk949 on 2008-08-08
No output from running "pgrep nautilus-cd-burner", so I guess there's no other burner running, 8 mill.

Phil

---

