---
title: "Bash command help"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by jayz_sg on 2008-05-21
Hi I need some help on bash commands in terminal.

Ok i want to setup another user called bart

so i go to terminal and type:

```
useradd -m bart -g root -p password
```

after this i dunno why i cannot log in so i have to do this

[HTML]passwd bart[/HTML]

after this i can log in but in terminal i just see a $ when i'm logged in as bart. 
so i did this:

```
sudo -s /bin/bash bart
```

now i see bart@ubuntu or something like that,

the problem is under system > admin > user and groups
login name is shown as bart but name is empty. 

Is there anyway to do this in terminal? I know I can just change it there but I need to know how to do it with bash commands as I have another proj on another system that has this issue.

The other thing is when i do the groups cmd on bart I only see root but when i do it on another user that I created on the GUI user and groups I see more groups like root adm dialout fax cdrom floppy tape. Will this result in any errors in the future?

And lastly can anyone point me to a link or something that teaches the way to create users in bash with proper instructions. All the cmds I quote I found from diff sites and have to trial and error to find out which ones works. THanks alots guys.

---

### Post by quelx on 2008-05-21
Try adduser instead of useradd

adduser is a script to generate all the things (home driectory, group, whatever) just like your initial user.

you can then use useradd for groups

```
useradd -G admin bart
```

would add bart to the admin group

if you want bart to access floppy tape cdrom drives add him to those groups

---

