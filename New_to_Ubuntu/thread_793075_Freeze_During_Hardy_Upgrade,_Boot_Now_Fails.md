---
title: "Freeze During Hardy Upgrade, Boot Now Fails"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by McMagic on 2008-05-13
Was upgrading from Gutsy to Hardy this morning when the upgrade froze. I checked the terminal for the process and it was just sitting there. I did a soft restart after ending the process, and now boot is insane. Crazy, pixelated colored rows flash on screen before login, login is Lo-res, and after entering username and pass, i get the orange screen w/ cursor, and thats it! Please tell me i don't have to reinstall and start from scratch!

Im on liveCD right now, and i can access the partition containing the Half Gutsy/Half Hardy system files. Is there a command i can run to rebuild and rehabilitate this poor install? PLEASE HELP!

---

### Post by Inxsible on 2008-05-13
Have you tried restarting in recovery mode? You can update your machine in text mode and then try and log back in the normal way.

---

### Post by Het Irv on 2008-05-13
If you have a way to backup your files, I would suggest getting all your personal files and any special configuration files (xserver configs, net share if you have them) off the computer and do a fresh install.

---

### Post by McMagic on 2008-05-13
What command would i use in recovery mode to update?

---

### Post by Inxsible on 2008-05-13
> **McMagic said:**
> What command would i use in recovery mode to update?```
sudo aptitude update && sudo aptitude dist-upgrade
```

---

### Post by McMagic on 2008-05-13
> sudo aptitude update && sudo aptitude dist-upgrade

tried this in recovery console to no avail... anyone have any ideas?? please!

---

### Post by Het Irv on 2008-05-13
try the commands separately
```
sudo aptitude update
```
```
sudo aptitude dist-upgrade
```

---

### Post by Inxsible on 2008-05-13
> **Het Irv said:**
> try the commands separately
```
sudo aptitude update
``````
sudo aptitude dist-upgrade
```If it didn't work previously, it wouldn't work when you separate the commands. The && actually performs the first command and then executes the second and then the third and so on...

---

### Post by Het Irv on 2008-05-13
I only suggested that because I just joined ..... oh wait nvm, I know what happend.

Your right, and I forgot something.

---

