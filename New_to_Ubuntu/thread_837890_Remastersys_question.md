---
title: "Remastersys question"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by dnns123 on 2008-06-22
If I install VMware Tools in Ubuntu 64-bit which is a guest OS in VMware, will remastersys keep it when making the LiveCD?

---

### Post by Oldsoldier2003 on 2008-06-22
> **dnns123 said:**
> If I install VMware Tools in Ubuntu 64-bit which is a guest OS in VMware, will remastersys keep it when making the LiveCD?

it should.

---

### Post by cariboo on 2008-06-23
I found this at:

[http://www.linuxmint.com/wiki/index.php/Remastersys](http://www.linuxmint.com/wiki/index.php/Remastersys)

> There are 3 options that can be passed to the script.


backup - backs up your system including your /home folder with your users on it.

dist - omits the /home folder thus making it a distributable cd that you can give to your friends.

clean - removes the temporary folder that was created, including the new iso so burn it and copy it elsewhere before you run "sudo remastersys clean" 

Hope this helps.

Jim

---

