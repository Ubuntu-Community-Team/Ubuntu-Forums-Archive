---
title: "Unable to update snap store"
date: 2023-02-18
forum: New to Ubuntu
---

### Post by taknikigyan on 2023-02-18
Hi,

I am new to Ubuntu and just now installed it in VirtualBox. After installation, when trying to update then it is showing an error only for Snap Store. It is showing below error:

[IMG]https://i.imgur.com/dI3MBQX.jpg[/IMG]

Help me to fix this error.

---

### Post by Holger_Gehrke on 2023-02-18
"gnome-software" / "ubuntu-software" / "snap-store" has the ugly habit of staying running and in memory even after you close it's window (no, it's not a bug; it's a design decision meant to make it faster to start the next time you need it; in my opinion questionable since you're not likely to run it all that often). You can't update a program that is currently running. So you need to close down that process. Either use some graphical process manager to stop that process or open a terminal and either run 'ubuntu-software --quit' or use the command 'kill' with the **p**rocess **id** the error message gives you (example: 'kill 2141' for the situation in your screenshot).

Holger

---

### Post by taknikigyan on 2023-02-18
Hi @[[COLOR=#000000]Holger_Gehrke[/COLOR]]("https://ubuntuforums.org/member.php?u=1961578")

Can you please tell me complete step by step how can I update it?

---

### Post by Holger_Gehrke on 2023-02-18
[LIST=1]
[*]open a terminal (keyboard shortcut ctrl-alt-t should work on all the desktop environments for the various flavours of *buntu; depending on your DE how you open a terminal from the menu or application overview or whatever is slightly different and often there's more than one way to do it ...) 
[*]enter 'snap-store --quit' (no, the double dash is not a typo; it's the way to give long 'gnu-style' options on the command line) 
[*]enter 'snap refresh' (you will be asked for your password; this will update all the snap packages including the 'Snap Store') 
[*]enter 'exit' to close the terminal 
[/LIST]

Optionally you could do an update of the .deb packages while you're still in the terminal with a quick 'pkexec apt update' (this will update the lists of available packages) followed by 'pkexec apt upgrade' (this will update any packages for which new versions are available). 

Holger

---

### Post by poorguy on 2023-02-18
> **taknikigyan said:**
> Hi @[[COLOR=#000000]Holger_Gehrke[/COLOR]]("https://ubuntuforums.org/member.php?u=1961578")

Can you please tell me complete step by step how can I update it?

[https://superuser.com/questions/1723668/how-to-update-snap-store-linux-how-to-update-this](https://superuser.com/questions/1723668/how-to-update-snap-store-linux-how-to-update-this)

---

### Post by send2 on 2023-02-18
Another way of resolving the "unable to refresh snap store" problem is to in terminal do:

sudo pkill snap-store && sudo snap refresh snap-store

This is in Ubuntu. 

Hope this helps...

This did it for me on getting rid of the problem.

---

### Post by grahammechanical on 2023-02-19
From the early days of Linux it has always been possible to carry out an action using more than one method. In Ubuntu we can update/upgrade the OS and applications by using Ubuntu Software; Software Updater or commands in a terminal. When we run Software Updater snap packaged apps will be automatically refreshed/updated. To do the same thing in a terminal run these commands:

```
sudo apt update
sudo apt upgrade
sudo snap refresh
```

I have also noticed that Ubuntu Software will inform that there are snap apps that can be updated but be unable to do the update because the updated packages are not yet available in the repository. Try again later. Ubuntu Software is also a snap packaged app. It might be true that Ubuntu Software cannot update itself. I do not know. Use one of the alternative methods.

Regards

---

