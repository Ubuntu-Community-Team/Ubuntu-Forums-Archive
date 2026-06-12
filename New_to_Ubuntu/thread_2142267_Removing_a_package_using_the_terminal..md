---
title: "Removing a package using the terminal."
date: 2013-05-05
forum: New to Ubuntu
---

### Post by techbuntu27 on 2013-05-05
I used this code on the terminal ```
sudo apt-get autoremove build-essential
``` which I installed recently and I just try this command, because it's my first time to use this method aside the ubuntu software center. But I'm confused, because it says that I don't have that package but then at the bottom it says the *linux-headers-3.2.0-29 linux-headers-3.2.0-29-generic-pae *will be remove. Which I don't understand what is *linux-headers-3.2.0-29 linux-headers-3.2.0-29-generic-pae* is all about, I hope you could give me insights what its purpose or so.

[IMG]http://i.imgur.com/nE0DJx9.jpg[/IMG]

---

### Post by Shadius on 2013-05-05
I think those are Linux kernels that are no longer needed so they will be removed if you run that command.

Helpful link:
[Apt-get]("https://help.ubuntu.com/community/AptGet/Howto")

---

### Post by fantab on 2013-05-05
Install Synaptic Package manager and use it to remove un-needed packages.

sudo apt-get install synaptic

---

### Post by galgalesh on 2013-05-05
the autoremove command also removes packages that are installed but no longer needed.

---

### Post by atm123 on 2013-05-05
1. type uname -a - this will give you info abt your kernel release. 
2. remove all other existing/installed kernels from your synaptic package manager.

---

### Post by Mopar1973Man on 2013-05-05
Anything that's not be use could be cleared out by.

```
sudo apt-get autoremove
```

This checks for other dependencies packages that are no longer being used and removes them.

---

### Post by codingman on 2013-05-05
The command *autoremove* removes unneeded packages from the system, as well as the package that is your argument. The command *remove* removes only the argument. The command *purge* removes the argument and all of its dependencies.

---

