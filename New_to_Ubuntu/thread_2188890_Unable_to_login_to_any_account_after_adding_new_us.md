---
title: "Unable to login to any account after adding new user"
date: 2013-11-19
forum: New to Ubuntu
---

### Post by chrissie-c-l on 2013-11-19
So using the GUI interface, I added a new, second user with administrator access.  I'm pretty sure I didn't touch anything on my own administrator account.

Now, when I try to login to my account, I just get a black screen, nothing.  I wait a minute or so, nothing happens, so I force it to turn off and try something else.

When I try to login to the new account, I just got shot right back out to the login screen. One of the times I tried though, I just got a black screen with a blinking white cursor line.

I can login to the guest session fine.

I can ctl-alt-f1 into the terminal from the login screen, but don't know where to start searching for a problem from there.  I can login to both accounts fine from the terminal.

---

### Post by DuckHook on 2013-11-19
To avoid confusion, let's call the terminal within the GUI the 'terminal' and the console that you get with <Ctrl>+<Alt>+<Fx> the 'console'. Not trying to be nitpicky, but absent screenshots, accurate terminology keeps things clearer and easier for everyone.

In console, for each user with this problem, post back output of```
id
``````
la ~ | grep -i '\.x'
```If one of the outputs is .Xauthority, then for each user, rename the file with:```
mv ~/.Xauthority ~/.Xauthority.old
``````
sudo reboot
```**NOTE** *.Xauthority* must have both the dot and a capital "X". This trips up a lot of people.

Also, don't know what you mean by> ...force it to turn off...It is much better to switch into a console and power down elegantly with```
sudo poweroff
```or```
sudo shutdown -P now
```

---

### Post by chrissie-c-l on 2013-11-19
for the new user's response to id
```
uid=1001(tempuser) gid=1001(tempuser) groups=1001(tempuser),4(adm),27(sudo),108(lpadmin),124(sambashare)
```

tempuser's response to la ~ | grep -i '\.x'
```
.Xauthority
```

I did the move and reboot for tempuser, and still can't login to them.  

for albiero's reponse to id
```
uid=1000(albiero) gid=1000(albiero) groups=1000(albiero,4(adm),24(cdrom)27(sudo),30(dip),46(plugdev),108(lpadmin),124(sambdashare),127(vboxusers)
```

and albiero's response to la ~ | grep -i '\.x'
```
.Xauthority
.xsession-errors
.xsession-errors.old

```

I did mv and reboot for albiero, and I no longer get the black screen of nothingness when I try to login to albiero.  I just get kicked back to the login screen.  I guess that is an improvement...

the ownership on both albiero and tempuser's .Xauthority file's is -rw------- 1 user user, was before and is now.  

And thanks for telling me how to power off elegantly when everything else has decided to stop working.  I only learned about the "console" a few hours ago, and am very glad there is a better way than the last resort of holding down the power buton.

---

### Post by DuckHook on 2013-11-19
In albiero what does .xsession-errors tell you?

You can see the contents of this file in the console either with```
nano ~/.xsession-errors
```or```
less ~/.xsession-errors
```type <q> to get out of *less*, <Ctrl>+<x> to get out of *nano*. The file may be long, so please don't feel obligated to reproduce it to post here. Rather, just scan through it for any error messages that stand out. Anything that says "error" or "CRITICAL" should especially draw scrutiny.

---

### Post by chrissie-c-l on 2013-11-19
nothing in either .xsession-errors or .xsession-errors.old.  They actually both have size 0.

---

### Post by DuckHook on 2013-11-19
hmmm... stranger and stranger.

Is this a fresh install or do you have important data on your computer? You may need to back up any critical data before proceeding further.

We can walk you through this using command line. It's arcane to a new user but not really that bad.

Let's look at dmesg (your log from boot to now) by doing:```
dmesg | egrep -i 'error|warning|unity'
```dmesg is typically huge, so we are trying to cut down the output by limiting results only to lines containing the strings "error", "warning" or "unity". This obviously has the disadvantage of blinding us to any other messages that may be pertinent. Therefore, if you feel bold, you can scan through the full output by doing:```
dmesg | less
```Also, do similar with:```
cat /var/log/syslog | egrep -i 'error|warning|unity'
```syslog is even bigger and will sometimes overwhelm with warnings (which aren't that big a deal, actually). If so, you can see better by piping it through *less* like this:```
cat /var/log/syslog | egrep -i 'error|warning|unity' | less
```Again, if nothing stands out, then go through the whole darned thing with```
cat /var/log/syslog | less
```

---

### Post by chrissie-c-l on 2013-11-19
So dmesg doesn't have anything old enough since I have re-booted the computer since.  

My syslog is actually size 0 with nothing in it.  syslog.1 has error messages from a few days ago in it.   

I have everything backed up, so I think I will just do a reinstall now.

---

### Post by DuckHook on 2013-11-19
Sometimes, a fresh reinstall is the best way. By the time we figure out the problem, you'd be up and running with a fresh install. Takes me about 20 minutes from start to finish.

You may wish to consider 12.04 instead of the latest which often is not the greatest. 12.04 is designed to be stable and will remain supported until 2017. 13.10 will stop being supported in 8 month's time.

---

### Post by chrissie-c-l on 2013-11-22
Thanks for all your help. Hopefully in eight months time I'll know what I'm doing a bit more. Still learned quite a few lessons.

---

### Post by DuckHook on 2013-11-23
Regrettably, I didn't end up helping you very much, but you are very welcome. Hope you enjoy this new world that Ubuntu/Linux opens up.

---

