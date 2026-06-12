---
title: "can't delete from trash can"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by HunkieChan on 2008-05-10
hey guys, i can't delete this folder from trash .. i tried this command "sudo rm -fr $HOME/.Trash/*" but it still doesnt work.. can anyone help me ?

---

### Post by Xiong Chiamiov on 2008-05-10
When you say it doesn't work, what happens?  Do you get an error, or does it just not delete?

---

### Post by gn2 on 2008-05-10
Various options here: [http://ubuntuforums.org/showthread.php?t=788450](http://ubuntuforums.org/showthread.php?t=788450)

---

### Post by HunkieChan on 2008-05-10
nothing, i dont get any error whatsoever. the folder remains there. there is only one folder that doesnt get deleted but any other does.

---

### Post by terazen on 2008-05-22
Oddly enough I just had the same problem.  It said couldn't delete this one file so I found it in ~/.local/share/Trash (I use Hardy) and `chown myusername.myusername file` and then it let me delete it.

I initially tried to delete by right clicking the trash icon and selecting empty trash...I'd think it should ask me for a password to raise privileges in instances where I'm trying to delete a file root owns.

---

### Post by shifty_powers on 2008-05-22
> **terazen said:**
> Oddly enough I just had the same problem.  It said couldn't delete this one file so I found it in ~/.local/share/Trash (I use Hardy) and `chown myusername.myusername file` and then it let me delete it.

I initially tried to delete by right clicking the trash icon and selecting empty trash...I'd think it should ask me for a password to raise privileges in instances where I'm trying to delete a file root owns.

don't need to use chown. just gksudo nautilus and navigate to that folder.

and yes, had that problem myself occassionally...

---

### Post by HunkieChan on 2008-05-24
how do i find that file ?

---

### Post by sayakb on 2008-05-24
Open a terminal and do:
```
gksudo nautilus
```
And then open your home folder and press Ctrl+H and navigate to the .Trash folder.

---

### Post by iaculallad on 2008-05-24
If you're on Hardy, use this:

**sudo rm -rf ~/.local/share/Trash**

or cd ~/.local/share/Trash

then issue the command sudo rm -rf *.* inside the Trash directory

**sudo rm -rf ~/.local/share/Trash**

that should do it.

**~/.local/share/Trash** is you Trash directory

---

### Post by sayakb on 2008-05-24
Wow.. didn't notice this change from Gutsy (just been 1 day anyway).. The trash files are in ~/.local/share/Trash/files

---

### Post by iaculallad on 2008-05-24
> **LinuxIsInnovation said:**
> Wow.. didn't notice this change from Gutsy (just been 1 day anyway).. The trash files are in ~/.local/share/Trash/files

Yap, me too. I was in this situation before and tried locating the Trash folder and led me finding this (~/.local/share/Trash) :-)

---

### Post by jrharvey on 2008-05-24
Ok so I tried this because i too had a file that was stuck in the trash forever that i couldnt delete. I kinda figured it would happen but once i deleted the file as root it didnt really delete it. It only moved it to the root trash. Emptying the root trash did not work, just like my home trash. I believe the file is one that i put on my ubuntu desktop from my windows partition. It might have something to do with the fact that it is a shared file maybe????

---

### Post by iaculallad on 2008-05-24
> **jrharvey said:**
> Ok so I tried this because i too had a file that was stuck in the trash forever that i couldnt delete. I kinda figured it would happen but once i deleted the file as root it didnt really delete it. It only moved it to the root trash. Emptying the root trash did not work, just like my home trash. I believe the file is one that i put on my ubuntu desktop from my windows partition. It might have something to do with the fact that it is a shared file maybe????

Did you try this command instead?

**sudo rm -rf ~/.local/share/Trash/files/***

or try this if there's a file in the Trash that is not currently owned by you.

**sudo chown username -R ~/.local/share/Trash/files/***

---

### Post by Bubba64 on 2008-05-24
Right click on file to highlight then hold down shift and hit delete on the keyboard, I believe this will delete anything.

---

### Post by bugsy2 on 2008-07-18
Thank you. I couldn't perform this fix without your explicit explanation!

---

