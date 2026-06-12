---
title: "Pc linux os internet question"
date: 2008-02-18
forum: Other OS Talk
---

### Post by linux phreak on 2008-02-18
Hi i recently downloaded pclinux os and booted off the cd.I find that the sudo command is not recognised.Also how can i initiate the DSL connection like in ubuntu( sudo pon dsl-provider)

---

### Post by linux phreak on 2008-02-18
please guide me in this

---

### Post by Dennis on 2008-02-18
Pclinuxos uses su not sudo

---

### Post by linux phreak on 2008-02-18
ok so how can i initiate the connection in pclinux OS?Please explain the command

---

### Post by tdrusk on 2008-02-18
Go to the "configure your computer" icon on the taskbar and go to network&internet. Add a new network interface and pick what you want.

OR 

if you want to use the CLI like you originally wanted to, you have to type
```
su
```
then your password when it asks for it.
then run 
```
pon dsl-provider
```

I'm not sure about that last command, I was just going by what you to me.


I would imagine the graphical way would be easier though.

---

