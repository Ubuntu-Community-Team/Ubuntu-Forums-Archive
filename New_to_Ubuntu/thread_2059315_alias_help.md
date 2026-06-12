---
title: "alias help"
date: 2012-09-17
forum: New to Ubuntu
---

### Post by cmcanulty on 2012-09-17
I made an alias to logout and it works fine for gnome classic but not for lxde or xfce. Here is the script which I put in ~./bash.rc
```
alias logout='echo password | sudo pkill -u cmcanulty'
```
How can I do this for xfce and lxde. I am experimenting with both and so am logging out a lot.

---

### Post by Cheesemill on 2012-09-17
I'm not sure what alias command you should use.

What I am sure of, however, is that storing your password in plain-text in your home folder is a [COLOR=Red]**[SIZE=3]VERY BAD IDEA !!![/SIZE]**[/COLOR]
There are much better ways to achieve the same effect (editing sudoers).


Edit - To log out of XFCE you can use the command 'xfce4-session-logout --logout'.
For Gnome you can use 'gnome-session-quit --logout'

You may be better off writing a function rather that an alias that checks for the running DE and calls the specific command for each.
Also is there actually any need to use sudo in your alias? You should already have permission to kill your own processes without it (neither of the commands I posted above need root permissions).

---

### Post by cmcanulty on 2012-09-17
OK I will try that although I have no idea how to write a function. Is there a command for logging out of lxde and kde?

---

### Post by Cheesemill on 2012-09-17
Add something like this to your ~/.bashrc
```
function logout {
   if (pgrep -x gnome-shell) then `gnome-session-quit --logout`
   elif (pgrep -x xfce4-session) then `xfce4-session-logout --logout`
   elif (pgrep -x ksmserver) then `qdbus org.kde.ksmserver /KSMServer org.kde.KSMServerInterface.logout -1 -1 -1`
   fi
}
```Basically the expression in brackets evaluates to TRUE if the specified process is running (to detect the current session). This will then run the logout command for that session.

I haven't tested this as I only have Gnome Shell installed, you may have to check the session process names I've given are correct using ps (I'm going from memory).
Also I've just pulled the logout commands from the net, they may need double checking as well (especially the KDE one).

---

### Post by cmcanulty on 2012-09-17
OK I will try though I don't understand it. What about lxde? and thank you very much. I got stuck in kde and couldn't get it to logout at all. It worked in gnome classsic but not xfce

---

