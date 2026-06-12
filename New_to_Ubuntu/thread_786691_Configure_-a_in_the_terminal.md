---
title: "Configure -a in the terminal"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by spa21788 on 2008-05-08
Can't install anything because I get an error in add/remove that says I have to dpkg configure -a, that's no problem it's that the download only goes a certain amount and then stops and times out so I can't install anything. Help!

---

### Post by Joeb454 on 2008-05-08
How do you mean the download only goes a certain way. Also that command needs to be run as root (not sure if you know that or not :)) To do this you would run ```
sudo dpkg configure -a
```

It would then ask for your password :)

---

### Post by bumanie on 2008-05-08
That is indicating that a package download has been interrupted. Put the code in terminal (as above post) and it will continue from where it was interrupted. If it is happening often, you should think about finding a local server to download from. To do this go to System --> Software Sources and at the 'download from' menu, choose other and let the system scan for the best server.

---

### Post by spa21788 on 2008-05-08
Actually I tried it again it just worked, thanks for your input I'm sure I'll have plenty more problems for you!

---

### Post by Joeb454 on 2008-05-08
Well...lets hope not, but breaking things is how I learnt, so just post here if you have issues :)

---

