---
title: "lxterminal history -c does not work"
date: 2012-10-22
forum: New to Ubuntu
---

### Post by ginmardo84 on 2012-10-22
hi guys, 

installed and ran lubuntu 12.10 successfully. back in lubuntu 12.04 i was able to clear lxterminal input history with

history -c 

now it only wipes the current input history, but when i close lxterminal and open it anew, arrowing up displays the previous inputs since i installed lubuntu 12.10 and ran updates and installs in lxterminal. 

is this a bug or has there been changes made?

---

### Post by ajgreeny on 2012-10-22
This is exactly the same as gnome-terminal in Ubuntu 10.04.4, Lucid, so I think you are wrong in your assumption that that command removes the ~/.bash_history contents; it seems to just hide it from that terminal session.

---

### Post by SlugSlug on 2012-10-22
Thats does seem odd

you can delete all the history by deleting the file

```
rm  ~/.bash_history
```
but history -c  should clear it **all**

---

### Post by ginmardo84 on 2012-10-22
> **SlugSlug said:**
> Thats does seem odd

you can delete all the history by deleting the file

```
rm  ~/.bash_history
```but history -c  should clear it **all**

yo slugslug, 

i found out that the actual command to run in order to wipe the lxterminal history is 

rm -f ~./bash_history

altho the last input viewable remains the input itself, but that does not seem to post a problem. well that's solved now. running 

history -c 

should have done the job but just did not. thanks for the help guys.

---

### Post by JKyleOKC on 2012-10-22
Actually, the history feature in bash doesn't work the way most of us think it does. When you log in, bash copies the content of the .bash_history file into RAM, then closes the file and for the rest of that session does not touch the file at all. Instead, it adds the commands to the RAM copy of history. When you log out, bash adds the new entries of the RAM copy to the file, if any exist, but leaves it alone if nothing changed.

The "history -c" command just erases the RAM copy, without affecting the file itself in any way. To remove the full history completely, a simple "rm .bash_history" will do the trick, since bash does not keep the file open during the session.

I've created an alias by adding "alias zz=history -c;exit" to my .bashrc file. By placing the two commands in a single line, the "exit" command does not get added to history. Now after doing a batch of experimenting that I do not want to clutter up my history, I can just type "zz" and hit enter, to quit the terminal without updating the history file.

---

### Post by amjjawad on 2012-10-28
Lubuntu 12.04 here and 
```
history -c

```
remove the whole thing.
Whether I close LXTerminal and open it again OR reboot, same, nothing is there.

The other command doesn't work for me. Again, this is 12.04 so maybe something has been changed with 12.10? not sure.

---

