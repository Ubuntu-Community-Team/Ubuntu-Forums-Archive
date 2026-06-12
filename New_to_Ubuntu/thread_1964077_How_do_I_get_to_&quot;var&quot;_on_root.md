---
title: "How do I get to &quot;var&quot; on root"
date: 2012-04-23
forum: New to Ubuntu
---

### Post by Rich42 on 2012-04-23
I am using Ubuntu 11.10

Q 1/I would like to look into "var" folder to look for something

How is this done please.


Q 2/ How do I post "New Threads" on this forum


Thanks


Rich42

---

### Post by haqking on 2012-04-23
> **Rich42 said:**
> I am using Ubuntu 11.10

Q 1/I would like to look into "var" folder to look for something

How is this done please.


Q 2/ How do I post "New Threads" on this forum


Thanks


Rich42

```
cd /var
```

Though i cant imagine why you need to go in there if you dont know how to look in there ;)

and you just have posted a new thread.

Peace

---

### Post by roger_1960 on 2012-04-23
Hi

You can look at the contents of filesystem/var in the file manager Nautilus.

---

### Post by donkyhotay on 2012-04-23
> **haqking said:**
> ```
cd /var
```

Though i cant imagine why you need to go in there if you dont know how to look in there ;)

+1
the var folder is one of your system folders. As a general rule it's not a good idea to go poking around in there if you don't know what you're doing. If you want more information here is a [rundown of what the var directory is for](http://www.linfo.org/var.html).

---

### Post by raja.genupula on 2012-04-23
as you mentioned here in the title as root , just do as  **sudo -i** before doing what Haqking suggested  . then you will be in var as root .


if you want to be as root with nautilus then do as
```
sudo nautilus
```

---

### Post by haqking on 2012-04-23
> **raja.genupula said:**
> as you mentioned here in the title as root , just do as  **sudo -i** before doing what Haqking suggested  . then you will be in var as root .


if you want to be as root with nautilus then do as
```
**gk**sudo nautilus
```

that should be gksudo and not sudo.

Graphical apps should be gksudo 

Peace

---

### Post by Rich42 on 2012-04-23
Thanks all for your posts.

Sorry I have forgotten why I was looking into "var" I think it was to do with get_iplayer.

---

### Post by raja.genupula on 2012-04-24
> **haqking said:**
> that should be gksudo and not sudo.

Graphical apps should be gksudo 

Peace

But my friend , i usually do the things with sudo only and they are good with that . so i suggested my friend .

But i agree with you in the Debian case , to run GUI applications we must use gksu

---

### Post by haqking on 2012-04-24
> **raja.genupula said:**
> But my friend , i usually do the things with sudo only and they are good with that . so i suggested my friend .

But i agree with you in the Debian case , to run GUI applications we must use gksu



gksu/gksudo should be used for graphical apps (assuming gnome of course, or kdesudo etc depending on DE)

here for more information [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by raja.genupula on 2012-04-24
> **haqking said:**
> gksu/gksudo should be used for graphical apps

here for more information [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Interesting my friend , thanks for this

---

