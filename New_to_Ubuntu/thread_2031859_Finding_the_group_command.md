---
title: "Finding the group command"
date: 2012-07-22
forum: New to Ubuntu
---

### Post by dimension123 on 2012-07-22
What command do I use in order to find my group/username text file ? I've been told its "sudo vim /etc/passwd" but my terminal says command not found. ? Does anyone know the command? Thank you!

---

### Post by texpat on 2012-07-22
If your terminal says command not found then it seems to me that vim is not installed.

But vim is a text editor and the command you cite "sudo vim..." opens the file /etc/passwd in super user mode which allows you to edit it and write it back to the disk with any changes you make. You want to be really careful with that!

Try cat /etc/passwd first. That'll list the file's contents to the screen. Its not a file that the normal user should directly edit, though. I apologise if I underestimate your skills, but making changes to users/groups should be done via the appropriate tools. There's a GUI program in System-Administration-Users and Groups that you can use for this.

---

### Post by papibe on 2012-07-22
Hi dimension123.

Editing and modifying that file manually can seriously affect your system.

Could you tell us what are you trying to accomplish?

In any case, I would recommend open it without sudo, so it became 'read only'.

This would just type the file on the terminal (no editor):
```
more /etc/passwd
```
This would open it on a terminal editor:
```
nano /etc/passwd
```
And this would open it in the GUI editor:
```
gedit /etc/passwd
```
Regards.

---

### Post by dimension123 on 2012-07-23
Thanks for the advice guys but the reason I want to see that file is because I am currently reading a book about Linux for beginners and they are teaching some commands but I am not going to edit or modify anything on it, I am just wanting to practice with it. But it seems to me that my etc command does not exist? because I just typed in "man etc" and it says no manual entry found. So do you think that is the problem?? Thanks again guys!

---

### Post by oldos2er on 2012-07-24
/etc is not a command, it's a location in the file system. vim is not installed by default, which is why you're seeing the "command not found" message. If you want to install vim, run ```
sudo apt-get install vim
```

---

### Post by codemaniac on 2012-07-24
The view command starts vim in read-only mode. You will be protected from writing the files.

You are allowed to do all vim commands but barred to save anything .

```
view /etc/passwd
```

---

### Post by HermanAB on 2012-07-24
Uhmmm, not much substance in this thread.

Just type 'groups' on the command line to see what groups you belong to, then use groupmod or usermod to change things.  Details are in the fine man pages...

---

