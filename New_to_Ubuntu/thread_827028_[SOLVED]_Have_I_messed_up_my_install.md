---
title: "[SOLVED] Have I messed up my install?"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by Twizzle on 2008-06-12
I have been messing around trying to backup some of my files onto a server over the last few days and had a few problems so was running scripts as sudo and as me to try and solve the problem. The script was using rsync and trying to preserve permissions. (It should not have done anything to the source and I have nit tried to restore anything)

When I turned on my PC today I got an error as I logged into Gnome saying something about ignoring $/HOME/.dmrc and that it should have permissions set as 644.

I though 'no probs' logged in and opened a terminal and ran:

```
sudo chmod -R 644 /home/john
```

I rebooted and had all sorts of problems - I kept getting dropped back to the login screen with an error saying my X session lasted less than 10 seconds, and things about owners and permissions.

I opened a terminal from the login screen and ran:

```
sudo chmod -R 777 /home/john
```

and

```
sudo chown -R john /home/john
```

I logged out and in and now I can get into Gnome but I get the error about .dmrc being ignored and an error about permissions again - something along the lines of /home should not be writeable by everyone.

Before I mess thing up even more, should I just find this .dmrc file and chmod it to 644 and then chmod my /home to 755? I remember reading something a while back about there being all sorts of different permissions in /home and that if you changed anything it could really screw things up! (I can't remember where I read it though!)

---

### Post by hyper_ch on 2008-06-12
just chmod that file to 0644 and /home and /home/USER to 0755

---

### Post by Sinkingships7 on 2008-06-12
This should fix it:
```
sudo chmod -R 700 /home/john && sudo chown -R john /home/john
```

---

### Post by Twizzle on 2008-06-12
I went with the 755 option first and it seems to have worked. Thanks :)

---

