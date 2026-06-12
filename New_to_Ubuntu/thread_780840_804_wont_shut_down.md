---
title: "804 wont shut down"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by lost4now on 2008-05-03
Running version 804 for the last couple weeks and everything was fine. 

Out of the clear blue I can't shut down. The system seems to operate untill time to shut down. The icon has no effect. After that the whole system is locked up. Then the only wat to quit is hold the power button for a few seconds.  Any suggestions?  Please

---

### Post by Joeb454 on 2008-05-03
Can you try running the following from a terminal ```
sudo shutdown -P now
```

After asking for your password (and not showing you type it ;)) it **should** immediately shutdown your PC :)

---

### Post by Oldsoldier2003 on 2008-05-03
> **Joeb454 said:**
> Can you try running the following from a terminal ```
sudo shutdown -P now
```

After asking for your password (and not showing you type it ;)) it **should** immediately shutdown your PC :)

And for future reference, if Ubuntu just seems to hang at a black screen when using the shutdown button- Ctrl+Alt +F1 and do what Joe recommended.

---

### Post by sam_delta on 2008-05-03
this happened to me on xubuntu 7.10 a while back, and it got fixed when i shuted down preperly

so shut down with the command joeb proposed or you could also use 

to shut down
```
sudo init 0
```

to restart
```
sudo init 6
```

shut down properly using one of the commands from above and when you turn the pc back on check if the shutdown button now works

tell us how it goes
sam

---

### Post by lost4now on 2008-05-03
I tried the 
sudo shutdown -p now

It says -p option invalid see shutdown --help   I did but it is greek to me.

Next I tried sudo init 0  but the machine is locked up and the only option is to hold the power button in.

any more ideas  Please....

---

### Post by lost4now on 2008-05-06
bump

---

### Post by Oldsoldier2003 on 2008-05-06
> **lost4now said:**
> I tried the 
sudo shutdown -p now

It says -p option invalid see shutdown --help   I did but it is greek to me.

Next I tried sudo init 0  but the machine is locked up and the only option is to hold the power button in.

any more ideas  Please....

its a capitol P, case matters.

```
sudo shutdown -P
```

---

### Post by lost4now on 2008-05-06
Thanks.  That worked with a cap P

Any suggestions on how to correct the shut down or log out icon not doing its thing? Kind of a pain to have to use the term everytime to quit.

---

### Post by mapes12 on 2008-05-06
Looks that way for your configuration.

Call up a terminal window then type: man shutdown

then the enter key for the various extensions to the command to find out which one is best for you.:lolflag:

---

### Post by RJARRRPCGP on 2008-05-06
> **lost4now said:**
> Running version 804 for the last couple weeks and everything was fine. 

Out of the clear blue I can't shut down. The system seems to operate untill time to shut down. The icon has no effect. After that the whole system is locked up. Then the only wat to quit is hold the power button for a few seconds.  Any suggestions?  Please

I'm sorry, I never had this problem with Ubuntu. 

(I can't help it, everytime I hear about this type of problem, I'm reminded of Microsoft.) (It reminds me of the shutdown bug of Windows 98, because Microsoft rushed it)

---

### Post by lost4now on 2008-05-06
Huh!!!

---

### Post by paranoid_humanoid on 2008-05-06
i had the same problem a while back, did you disable the power manager process?
if so, re-enable by:
```
sudo gnome-power-manager
```

and set it to run on startup from system->preferences->sessions..

---

### Post by lost4now on 2008-05-06
Thanks paranoid. That did the trick. I never considered power manager would get involved in a manual function.   Thanks again.

---

### Post by kevb8ll on 2008-05-06
I've had this problem too. I'll check these suggestions.

---

