---
title: "wxPython question."
date: 2011-02-04
forum: Programming Talk
---

### Post by GunnDawg on 2011-02-04
Hey folks I am trying my hand at wxPython and have everything working 99% and need just a little help on my last stride.

I am basically making a GUI based package installer and uninstaller. You click install or uninstall then type the name of the package you wanna remove then it runs the sudo apt-get...etc command. That works perfect.

The problem is if I launch my program without using terminal then the program never launches a terminal it self to run the code. So basically the only way for it to work is if you run my program via terminal, which I dont wanna do.

Somewhere in this code is where I need to add something to do the trick, just not sure what. I think it might have something to do with --command

```
subprocess.Popen(['gnome-terminal  sudo apt-get remove %s' % self.upname.GetValue(),], shell=True)
```

---

### Post by cgroza on 2011-02-04
I use os.system("command here") and it works.

---

### Post by GunnDawg on 2011-02-04
> **cgroza said:**
> I use os.system("command here") and it works.

yeah but if you launch the .py file as an executable and not from a terminal, then that wont work. It wont even launch a terminal window.

---

