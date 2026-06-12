---
title: "[SOLVED] how to enable emerald"
date: 2008-07-21
forum: New to Ubuntu
---

### Post by rixtr66 on 2008-07-21
i have emerald and some themes but i cant enable them,i used to have compiz icon but idont remember how to get it.
rick

---

### Post by dje on 2008-07-21
press Alt + F2 and run:
```
emerald --replace
```

hope that helps,
dje

---

### Post by Joeb454 on 2008-07-21
I think you may need compiz enabled for some themes to use emerald as well. I've never really used it much so I can't say for sure.

The above command should work just fine though, you can then add it to your startup too

---

### Post by overdrank on 2008-07-21
> **rixtr66 said:**
> i have emerald and some themes but i cant enable them,i used to have compiz icon but idont remember how to get it.
rick

Hi and you can have a look at the link in my signature.
VVV

---

### Post by m_ad on 2008-07-21
To enable emerald, navigate to /home/username/.config/compiz

if there isn't a file called "compiz-manager," create one. Open it with a text editor, and add this to it:

```
USE_EMERALD="yes"
```

Now, restart X (Ctrl+Alt+Backspace).

If you ever want to switch back to Metacity, replace yes with no.


Alternatively, you could install "Compiz Fusion Icon" via Add/Remove.. launch it and play with the settings. It's really self explanatory from there :)

---

### Post by wolfdog_1987 on 2009-04-30
Or you could just go into the compiz config manager, and to the selection marked "window decoration". Where it says "command: /usr/bin/whatever" replace it with "/usr/bin/emerald"

Edit: im sorry apparently that didnt work on my laptop. It worked on my desktop so i guess each one is different

---

### Post by 6205 on 2009-07-22
> **wolfdog_1987 said:**
> Or you could just go into the compiz config manager, and to the selection marked "window decoration". Where it says "command: /usr/bin/whatever" replace it with "/usr/bin/emerald" 

Thanks.. That did the trick on my Jaunty :)

---

### Post by KashuBeanBrew on 2010-11-17
> **dje said:**
> press Alt + F2 and run:
```
emerald --replace
```hope that helps,
dje
THIS is exactly what worked for me INSTANTLY. 

Thank you!

---

