---
title: "sudo chmod -x *"
date: 2013-10-22
forum: New to Ubuntu
---

### Post by f100114 on 2013-10-22
I went into a folder using cd in terminal
then I did sudo chmod -x *
now all the files in folders are empty (0 bytes)

What can I do to retrieve them, my heart sunk it's my work I just seem to have deleted

can I just do sudo chmod -x *?

or is there a way to retrieve my files?

please please help

---

### Post by f100114 on 2013-10-22
I'm sorry I fixed it

sorry guys, I just panicked so I didn't want to screw anything more up

sudo chmod +x * worked for me

edit: god that was scary, I thought I had lost EVERYTHING

---

### Post by newb85 on 2013-10-22
If you take execute permissions off a directory, you can't enter the directory or access its contents.

---

### Post by oldos2er on 2013-10-22
> **f100114 said:**
> I'm sorry I fixed it

sorry guys, I just panicked so I didn't want to screw anything more up

sudo chmod +x * worked for me

edit: god that was scary, I thought I had lost EVERYTHING

Please read [http://ubuntuforums.org/announcement.php?f=326](http://ubuntuforums.org/announcement.php?f=326)

---

### Post by oldfred on 2013-10-22
I think you originally turned off the execute on everything. So obviously nothing worked. But now you have turned on execute on everything. That may work for a while is is not how system is intended to be configured.

You may be able to do this and then reupgrade to get back to where you are.
 Over install without formatting to reuse same home data. "Dirty Install"
System settings or anything in / may be overwritten with defaults. Good backups still important
[https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation)
[http://ubuntuforums.org/showthread.php?t=1941872](http://ubuntuforums.org/showthread.php?t=1941872)

---

