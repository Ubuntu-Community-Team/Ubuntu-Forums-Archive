---
title: "Really stupid processor speed question"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by simonbardell on 2008-05-18
Just installed ubuntu 7.10 on an old PC that has been sat in the cupboard at my mums house for ages. I am trying to find out the processor speed, and have managed to get as far as hardware info, but when I click on the AMD athalon it doesnt give me the speed. Even when I click the advanced tab it doesnt. Please help.

---

### Post by hyper_ch on 2008-05-18
```

cat /proc/cpuinfo

```

---

### Post by shifty_powers on 2008-05-18
```
sudo dmidecode | more
```

in a terminal.

Will give you a lot of info, but your processor speed will be in there somewhere ;)

---

### Post by shifty_powers on 2008-05-18
or what he said, probably a lot easier.

damn not quick enough ;)

---

### Post by simonbardell on 2008-05-18
Sorry, but I am brand new to linux and those codes dont mean anything to me. How do I get them to work?
Thanks

---

### Post by Malta paul on 2008-05-18
Hi, you could install 'Sysinfo' it rather good.
From Applications>Add/remove, select All applications and search.
Have fun:)

---

### Post by bmac on 2008-05-18
Open system/administration/system monitor
left click on the system tab.

Check out the resources tab and it provides a trend of your CPU history...


Hope this helps...

---

### Post by shifty_powers on 2008-05-18
> **simonbardell said:**
> Sorry, but I am brand new to linux and those codes dont mean anything to me. How do I get them to work?
Thanks

heh, go applications>accessories>terminal

and then type/copy and pastes those commands ;) (oh and press enter of course :D)

---

### Post by shifty_powers on 2008-05-18
course, just had a thought, could you not just go into the bios? it would tell you in there i would have thought.

just repeteadly pres f2 and delete when you turn it on ;) (it's usally one of those two to enter the bios)

---

