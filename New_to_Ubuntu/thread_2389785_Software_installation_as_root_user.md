---
title: "Software installation as root user"
date: 2018-04-21
forum: New to Ubuntu
---

### Post by ragpach2 on 2018-04-21
I am new to Ubuntu.I have installed an sdk on my vm but as a root user.During the installations I might have installed many other softwares like curl python etc pertaining to it too.
Now I realize I should have rather used sudo to be safe.I want access to all the software installed when I was root.I could change permissions maybe but I am not sure about what other programs did I install as root user.How do I know which all did I install as root? Kindly help me.Also once I figure out is re installation the only safe option?
Thank you.

---

### Post by oldrocker99 on 2018-04-21
You shouldn't create a root account, as you've probably figured out. A user account still has **temporary** "Super User" access, and running as root is *dangerous*.

---

### Post by ajgreeny on 2018-04-21
The only way to install any software in Ubuntu is as root, either in the non-recommended manner you used, ie, creating a root user, or by temporarily raising your user privileges using sudo.

I do not think it will make any difference to your ability to find out what was installed, and if you run command ```
grep -i " install " /var/log/dpkg.log.1 /var/log/dpkg.log
``` you should get a list of everything installed (after the OS was installed) in date order; which user installed things should not make a scrap of difference to that output.

There should be absolutely no need to reinstall the complete OS, but in future do please use the **sudo apt install** command, or the software applications already available, the only one of which I can talk about being **synaptic** as that is the one I use if I want a GUI application.

---

