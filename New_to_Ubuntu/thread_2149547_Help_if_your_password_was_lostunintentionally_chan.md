---
title: "Help if your password was lost/unintentionally changed."
date: 2013-05-29
forum: New to Ubuntu
---

### Post by Redmouse on 2013-05-29
Note: this was tested on a machine running Ubuntu 11.10, an older release, so parts of this tutorial may not work with newer versions.
IMPORTANT: please do not mess with the recovery console while logged in as root. As you can do anything, you may** seriously** screw up your system.

Have you ever forgotten your password or did something to it? Probably yes.. But then, how can it be recovered, without resetting the system completely? Like this!
Ubuntu has help options to help you do this, but they may not work... When you don't remember AAANY of your passwords. :( But still, there is a solution! If you boot up your computer, and hold shift while doing so, you will launch into a menu, which will have some options. Select the option with '(recovery mode') at the end, using the arrow keys, and the Enter/Return key. Now, you are faced with yet another menu. Now, select the 'root' option, 
and make sure that you see a black line at the bottom of the screen, with some text. You won't be able to do much 
unless you can write in your computer's options, so we need to remount the computer's files and make them writable in. For this we type in a command(note, please read the man page of mount before using, as I might have gotten some syntax wrong. To do this, type in 'man mount') that does that: 'mount -o rw, remount /'.
Next, type in 'passwd (your account name)'. Your account name is probably your first name, and if it is not, you probably know what it is. Type in your new password, hit enter, and do it again. Yay! You have reset your password, and learned how to gain physical access to your machine, and immediately become administrator (aka root).
Please make this topic known, and I hope you learned some stuff other than the topic of this tutorial.
(p.s. Move this topic if I posted in the wrong place)

---

### Post by Cheesemill on 2013-05-29
Or with pictures...

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by newb85 on 2013-05-29
> **Redmouse said:**
> (note, please read the man page of mount before using, as I might have gotten some syntax wrong. To do this, type in 'man mount') that does that: 'mount -o rw, remount /'.

If you're going to post a tutorial, you should check the syntax of the commands yourself.  The command needs to be thus:
```
mount -o rw,remount /
```
(Notice there's no space before "remount".  I know from experience it won't work with the space there.)

Also, when including commands and code, you should enclose them in code tags, either by manually typing them, like this:
```
[noparse][code]mount -o rw,remount /
```[/noparse][/code]
or by highlighting them and clicking the "#" button above the composition frame on the forums website.
It makes it much easier to read.

---

