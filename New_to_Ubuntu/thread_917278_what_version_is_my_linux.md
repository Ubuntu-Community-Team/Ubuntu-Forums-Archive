---
title: "what version is my linux?"
date: 2008-09-11
forum: New to Ubuntu
---

### Post by kaykav on 2008-09-11
Hi people,
           Simple request,and yet I cant find the command ,if any, to display 
             the distro version of my ubuntu. Im almost sure its 'Feisty 
             Fawn'. Nontheless I looked everywhere online for that command,
             to no avail. Keeping with that thought, where would one look to    
             find a command if you know what its supposed to do?...Thanks
                         Rich

---

### Post by KillerSponge on 2008-09-11
In system -> About Ubuntu, and then under "versionnumbers", you can see what version you have. There probably is a faster/better method, but this works ;)

---

### Post by Tatty on 2008-09-11
```
lsb_release -a
```

or "System->About Ubuntu" should also tell you

---

### Post by forger on 2008-09-11
Also:
```
cat /etc/issue
```

---

### Post by kaykav on 2008-09-11
thank you ..all...Rich

---

### Post by ad_267 on 2008-09-11
System - Administration - System Monitor should tell you and will also give the kernel version, GNOME version and details on your ram and processor.

---

### Post by Iowan on 2008-09-11
Really quick/dirty: switch to a terminal (CTRL-ALT-F1) the version is usually there.  Use CTRL-ALT-F7 to get back to Desktop.

---

