---
title: "Where is my login script and how do i change it"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by päikese on 2008-08-08
I am trying to remap my keyboard using xkeymaps and to make the changes permanent I need to change my login script,
Whats that, where is it and how do I change it?
Please!

---

### Post by The Cog on 2008-08-08
Either /etc/profile if the change is for everyone, or ~/.bashrc if it is for a particular user.

---

### Post by päikese on 2008-08-08
ok found it, now how to change it.
I know i have to start at the terminal by opening /etc/profile with mousepad but can't remember how. and where would I put the line "xmodmap ~/.xmodmap- eric -n" which is what xkeycaps is telling me to add.

---

### Post by okey666 on 2008-08-08
To open "/etc/profile" using gedit (on gnome) I do:
```
sudo gedit /etc/profile
```

so if mousepad is the equivalent simply do
```
sudo mousepad /etc/profile
```

---

### Post by päikese on 2008-08-08
thanks, I opened both but decided not to do anything as /profile was full of stuff and bash.bashrc was empty.
I dont take clocks apart either!

---

### Post by okey666 on 2008-08-08
You could try using this howto:
[http://ubuntuforums.org/showthread.php?t=82500](http://ubuntuforums.org/showthread.php?t=82500)

Or, back up the file (by saving it somewhere accessible) try putting the line in a couple of places. (although that could cause problems)

Sorry I can't really help.

---

### Post by st33med on 2008-08-08
Add the line "xmodmap ~/.xmodmap- eric -n" at the bottom of your /etc/profile file. Reboot, and all should be cool :).

---

### Post by päikese on 2008-08-09
For anyone else who wants to use xkeycaps and needs to change their login script in xubuntu, open up the terminal program and type

"sudo mousepad /etc/profile"

When the file opens in mousepad before the unmask line right at the bottom add this

"xmodmap~/.xmodmap-YOURUSERNAME-desktop"

then click close and save changes.

and YOURUSERNAME means the name you type to login.
and when you see writing between " " DONT include the quotes!

 I know I'm not the only numpty on this planet so my instructions are numpty proof!

Thanks for all the help above and thanks (NOT) to the xkeycaps message that wasn't particularly accurate!

Now all I have to do is get my scroll lock button to make it's pretty little light come on. Not that I've ever used it for locking scrolls but sometimes in the lonely dark hours I like to tap it and watch the pretty little light flash.

---

