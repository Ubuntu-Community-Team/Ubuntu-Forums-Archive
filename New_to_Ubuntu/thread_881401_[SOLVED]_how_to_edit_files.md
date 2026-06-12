---
title: "[SOLVED] how to edit files??"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by rixtr66 on 2008-08-06
how can i edit the  file,/etc/apt/sources.list.
any help would be great.
rick

---

### Post by OutOfReach on 2008-08-06
I think Kubuntu comes with kate as the default text editor (correct me if i am wrong) so I would imagine that you would need to type the following into the terminal:

```
kate /etc/apt/sources.list
```

if that doesn't work try this:

```
sudo kate /etc/apt/sources.list
```

---

### Post by tuxxy on 2008-08-06
Righ click file and open with?

---

### Post by SunnyRabbiera on 2008-08-06
Right, you need root privileges to edit files like that so you need to type in sudo and the command you need in a terminal.

---

### Post by tuxerman on 2008-08-06
If you're using Kubuntu, there's a way to do it from the Dolphin file manager itself.

Right click the file --> Actions --> Edit as Root.

The mouse pointer will display a bouncing icon all through the edit, but I guess this is just keep you aware that you're editing as root.

---

### Post by fuzzyk.k on 2008-08-06
as was said that is a "system file" or core file you need root rights

---

### Post by sujoy on 2008-08-06
sudo (choose any editor) /etc/apt/sources.list

---

### Post by ilrudie on 2008-08-06
> **sujoy said:**
> sudo (choose any editor) /etc/apt/sources.list

Not necessarily the best advice.  sudo should only be used with command line text editors like vi, emacs, nano etc...  Use gksudo (for gnome/ubuntu) or kdesu (for KDE/kubuntu) with any graphical text editors like gedit or kate.

Read the following for more information.  Its a good resource.
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by fatality_uk on 2008-08-06
Best way to edit in Ubuntu.
In a terminal USE gksudo gedit /etc/apt/sources.list

---

### Post by AdamWood on 2008-08-06
In kubuntu press ALT+F2 then type
```

kdesu kate /etc/apt/sources.list

```

---

### Post by rixtr66 on 2008-08-06
thanx fo all the input.
rick

---

