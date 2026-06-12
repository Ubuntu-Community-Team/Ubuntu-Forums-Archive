---
title: "blank screen after running application"
date: 2008-10-05
forum: New to Ubuntu
---

### Post by belazir on 2008-10-05
hi all

scanned some threads and didnt find this specific issue...

installed ubuntu ultimate last night from winxp, installed as a 10gb without a partition (shows up in add/remove in windows)

boots fine, login in fine.... run an application and the screen switches off. any application at all. it's well annoying cause otherwise ubuntu looks and sounds gorgeous heh

any clues at all?

ps - yup, total n00b..... apologies for this, been a hard working ms techie for years but frankly everything since win and office 2k/xp has both sucked and blown.... time for fresh tech....

---

### Post by Michael.Godawski on 2008-10-06
>  installed ubuntu ultimate last night from winxp, installed as a 10gb without a partition (shows up in add/remove in windows)Did you use Wubi? What do you mean without a partition? Only as a virtualization?

What are your specs? Perhaps there is a conflict with your graphic card...

Post please the output of these terminal commands:
```
lspci
sudo lshw -short
```

---

