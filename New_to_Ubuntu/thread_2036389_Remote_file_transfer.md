---
title: "Remote file transfer?"
date: 2012-08-01
forum: New to Ubuntu
---

### Post by joco1500 on 2012-08-01
Hello Ubuntu forums!

i am 14 and allowed to use my laptop in school.
 thats great but i have files on my desktop at home and i need them for what in trying to do at school.

is there any way to remotely transfer the files from my desktop to my laptop?
I'm running Ubuntu 12.04 on the laptop and windows xp on my desktop.

i would prefer a method that would be through the command line, has a fast transfer, and nothing would pop up on my desktop at home because my mom uses it for work.

if it doesn't meet those criteria, say it anyway because i would still use it.

---

### Post by papibe on 2012-08-01
Hi.

A few ideas:

Install openssh-server on your Ubuntu laptop, and you can use ether Filezilla, WinSCP or Firefox's FireFTP plugin on the Windows desktop. For protocol use 'sftp' and 22 for the port.

For the other way: share a directory on Windows XP. In your Ubuntu machine open Nautilus (file manager) and then
```
Go -> Network
```
Then browse for your windows share.

I hope that helps, and tell us how it goes.
Regards.

---

### Post by whitethorn on 2012-08-01
I can't think of an easy of doing this. It depends a lot on how your network is setup at home. You'll need to open a port on your router or two pointing at your winXP machine. Then you'll need to share the folder in XP and then connect using your external IP. Here's some reading material :)

[http://ecross.mvps.org/howto/share.htm](http://ecross.mvps.org/howto/share.htm)

---

### Post by levlaz on 2012-08-01
This isn't an answer to your question per se... but rather than opening ports and whatnot why not just use dropbox or Ubuntu one? Both work with windows and Ubuntu and that way you can keep all of your files synced.

---

### Post by audiomick on 2012-08-01
I think that is a good idea. If you keep all your files in a folder that is set to synch to Ubuntu one or Dropbox, you can access that from your second machine.

---

