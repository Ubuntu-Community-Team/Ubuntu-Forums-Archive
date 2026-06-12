---
title: "made shell script needs sudo rights"
date: 2008-04-28
forum: Programming Talk
---

### Post by Erik. on 2008-04-28
Hi all,

I made a startup script for my wireless driver.
When i run the script i need to type my password because i need to use sudo.
For the command i type sudo -i
how to make the script whit sudo rights but i do not enter my password?

Hope you can help me

Erik

---

### Post by pedro_orange on 2008-04-28
Hmmm, I'm certainly not the best BASH programmer/scripter.

Solutions I can think of: (But have a distinct security problem if people get into your machine)
- Hard code the root pw in your script
- Have the root pw in a file you retrieve from your script
- Edit your /etc/sudoers to have %sudo ALL=NOPASSWD: ALL

But these are terrible options you should only choose in a worst case scenario. I'm sure the BASH legends will come up with something spiffy later on.

---

### Post by Erik. on 2008-04-28
Not all good options, when someone comes into my computer.
I only need sudo for that script...
Its for my wireless internet connection to make it work.

---

### Post by heikaman on 2008-04-28
hi...
make sure the owner of the script is root and 

sudo chmod +s /path/to/script/script_name

try it.

---

### Post by Erik. on 2008-04-28
I added it, next time i reboot i will take a look
Thanks for helping me :)
Hope it works

---

### Post by ivze on 2008-04-28
Why don't you run the whole script as root? Sudo, obviously, allows root to do anything. May be, it's even better completely without sudo.

See /etc/rc.local. 
It is satrted at OS startup and has root priveleges.

---

### Post by heikaman on 2008-04-28
If it makes no difference just give all permissions to every one + setuid bit like this

[PHP]
sudo chmod ugo+wrxs script
[/PHP]

now the permission bits will look like this:

[PHP]
-rwsrwsrwx 1 root root 0 2008-04-28 19:16 script
[/PHP]

:)

---

