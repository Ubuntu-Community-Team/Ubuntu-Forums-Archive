---
title: "How to make changes with manual commands"
date: 2014-06-22
forum: New to Ubuntu
---

### Post by conure on 2014-06-22
Hi all,

I am now using Ubuntu as my primary OS because it's so simple for Ruby development compared to W8, but I'm slightly confused about something. Ubuntu is making secondary files ending in ~ which I have learned are backups, and I have looked into the nano and gedit man pages to find that -B (--backup) is the variable that seems to control this. I don't actually want these backups as I'm using GIT and dropbox, but I'm unsure of how effect the change. Would it be possible for someone to explain it to me? I've read the man page but can't work it out!

---

### Post by m_duck on 2014-06-22
I don't use gedit very often but it looks as though you want the first answer [here]("http://askubuntu.com/questions/83026/prevent-gedit-from-creating-files-with-the-tilde-suffix").

EDIT: for completeness: *In gedit preferences, disable "Create a backup copy of file before saving*"

[s]As far as I can remember, nano doesn't create these temp files by default.[/s] I stand corrected [**[COLOR=#000000]ajgreeny[/COLOR]**]("http://ubuntuforums.org/member.php?u=27747") [post=13056170]below[/post].

---

### Post by ajgreeny on 2014-06-22
You can stop gedit from making backups automatically be going to Edit->Preferences and de-selecting the tick-box.  I am not sure about stopping nano from doing so as on my system it seems to backup by default when saving files and I can't find a way to stop it doing so.

However, don't be too hasty!  Once or twice in the past the backup file from both gedit and nano has saved my bacon when I've done something stupid and saved a file wrongly.

@ m_duck
> As far as I can remember, nano doesn't create these temp files by default.It does on my system (Xubuntu 12.04), and I am pretty sure I have not done anything to make it so, eg an alias in .bashrc or .bash_aliases.

A search suggests that for nano you can  look in /etc/nanorc for:
```
## Backup files to filename~. 
set backup
```     and change that to  
  ```
## Backup files to filename~.
# set backup
```
However the line in my nanorc is already commented out but I still get backups by default.

---

### Post by steeldriver on 2014-06-22
... have you tried

```

unset backup

```

in your ~/.nanorc

---

### Post by ajgreeny on 2014-06-22
I don't have a file ~/.nanorc at present; there is only the one in /etc.  Not that I want to stop nano making backups; it's far too potentially useful so I want it to continue

I will, however, copy the /etc/nanorc to my home and edit it as you suggest then try again, just to see if it works.

Well, I've just tried and even with **unset backup** in my home .nanorc I still get backups.

---

### Post by conure on 2014-06-22
guys, thanks so much for this - you've helped a tonne :)

---

