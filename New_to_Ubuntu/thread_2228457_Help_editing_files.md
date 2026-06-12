---
title: "Help editing files"
date: 2014-06-07
forum: New to Ubuntu
---

### Post by Ryles on 2014-06-07
Hi
I'm brand new to Linux and I'm trying to setup a HTPC using XMBCBuntu.
 
Anyway I'm trying to get an iMON LCD working and I have to edit the file below but I have zero experience with the Xterm thingy
 
**/etc/LCDd.conf** 
 
I've tried entering the above into xterm but I'm just getting invalid operation error,
I'm obviously missing something but I don't understand how the file hierarchy works in Linux.
 
  what do I need to put before this?
 
Many thanks
Ryles

---

### Post by LastDino on 2014-06-07
Try
```
gksu leafpad /etc/LCDd.conf
```

leafpad is your simple text editor (like notepad on windows). You might have something else installed as I've no idea about XMBCDBuntu. But you can check that easily.

You can also install ''dconf editor'' from software centre, that is about as easy as it gets.

---

### Post by MartyBuntu on 2014-06-07
Try:

**gksudo gedit /etc/LCDd.conf**

You'll be prompted for a password.

You can use **Kate** or **leafpad** in place of **gedit**...whatever editor you have installed you wish to use.

---

### Post by Ryles on 2014-06-07
Thanks for the reply
I think XBMCBuntu comes with something called nano but when I try that command it just launches into a new file, does that mean one doesn't exist yet?
 
Also if nano or leafpad is the editor I want to use and /etc/ denotes I wish to edit the file and LCDd.conf is the file name, what does sudo mean?

thanks

---

### Post by LastDino on 2014-06-07
sudo or gksu means giving temporary root privillages to user using the command.

Note: My initial command with ''sudo'' was wrong as you should always launch graphical/gui software/tools from ''gksu'' instead of ''sudo'' which is used for CLI operations.  I edited the post though, so I hope you got it right.

Yes, launch of empty file means that there is not any file named that, mind you, Commands are case sensitive, so please type path and file name as it is.

Also, /etc/ is path to folder called ''etc'' in your file system, you can also manually find and launch the file with leafpad/nano but you will need to do that with root as your normal account doesn't have enough permissions to access those files and edit them.  (That's why sudo and gksu are used.)

Path is same as the address you see in your file managers address bar.  You can check in terminal which directory you're currenly in by simply entering ''pwd''. By default, it is ''/home/username''

---

### Post by Ryles on 2014-06-07
ahhhh it's case sensitive!  this all makes sense now, lol who knew.  Seems alien coming from DOS.
 
thanks again :)

---

### Post by LastDino on 2014-06-07
No worries.

When you have some free time, give this a quick read.

[http://linuxcommand.org/learning_the_shell.php](http://linuxcommand.org/learning_the_shell.php)

Also, if your query is satisfied, please mark the thread as ''solved'' from thread tools above the thread.

---

