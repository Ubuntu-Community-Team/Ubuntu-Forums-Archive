---
title: "reach &quot;all applications&quot; from command prompt"
date: 2015-06-15
forum: New to Ubuntu
---

### Post by huff2 on 2015-06-15
Hi all,

In the application launcher there is a tab called "all applications." How can I reach the items in this tab through command prompt and then run one. I'm new and just trying to learn.

---

### Post by cariboo on 2015-06-15
Most executables are located in /usr/bin, you see if the application is there by using the following command:

```
ls -l <program name>
```

if you don't know what an application does try:

```
man <application name>
```

where <application-name> = for example:

```
man gnome-session-properties
```

---

### Post by tgalati4 on 2015-06-15
Alt-F2 will bring up a run box in some desktop environments.  Then you just type in what you want to run.  What happens when you press the "meta" (Windows symbol) key to the left of the spacebar?

Some Unity shortcuts information:  [http://askubuntu.com/questions/28086/what-are-unitys-keyboard-and-mouse-shortcuts](http://askubuntu.com/questions/28086/what-are-unitys-keyboard-and-mouse-shortcuts)

---

