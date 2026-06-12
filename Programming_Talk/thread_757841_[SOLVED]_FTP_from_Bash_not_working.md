---
title: "[SOLVED] FTP from Bash not working?"
date: 2008-04-17
forum: Programming Talk
---

### Post by EvilMarshmallow on 2008-04-17
Hey all,

I've read about 15 posts on half a dozen different forums and I can't find a solution to my problem.

I'm trying to write a bash script that will FTP into a computer, download all of the file*.dat files, and then delete the files from the FTP server.

Everyone seems to be using something like this:

> 
ftp << _EOF_
open xxx.xxx.xxx.xxx
user ID pword
mget file*.dat
mdelete file*.dat
quit
_EOF_


When I run this, it tells me that the login failed, access denied.  The weird part is that if I run the lines of the script individually, it works fine!

What am I missing?

---

### Post by WW on 2008-04-17
Trying adding the **-n** option to the ftp command, to disable auto-login.  It may be that ftp is prompting for a login immediately after the **open** command, before processing the **user** command.

EDIT: Wait--you said it works fine when you run the lines from the script individually.  When you do this, does it prompt you for a login name and password when you do the open command?

---

### Post by EvilMarshmallow on 2008-04-17
Nope, you're right, I needed -n.  I also needed -i to prevent the system from prompting me for each file.

Works like a charm... thanks for getting me started!

---

