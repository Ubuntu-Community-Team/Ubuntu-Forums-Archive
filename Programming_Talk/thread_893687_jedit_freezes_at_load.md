---
title: "jedit freezes at load"
date: 2008-08-18
forum: Programming Talk
---

### Post by Skofo on 2008-08-18
Can anyone help me out with this? It just stops at the splash screen.

Here's what it says in terminal:
```
sko@art:~$ jedit
Warning: $JAVA_HOME environment variable not set! Consider setting it.
          Attempting to locate java...
Found a virtual machine at: /usr/bin/java...
sko@art:~$ /home/sko/.themes/Shiki-Brave/gtk-2.0/gtkrc:201: error: unexpected identifier `lightborder_ratio', expected character `}'

```

EDIT: I changed the theme to Glider and it still freezes, saying this:
```
sko@art:~$ jedit
Warning: $JAVA_HOME environment variable not set! Consider setting it.
          Attempting to locate java...
Found a virtual machine at: /usr/bin/java...
sko@art:~$ 

```

---

### Post by fifth on 2008-08-18
The console output is normal when starting jEdit. As it found the vm it should continue to start as normal.

When you say it freezes, does it freeze at the commandline or do you see any of the gui?

---

### Post by Skofo on 2008-08-18
> **fifth said:**
> The console output is normal when starting jEdit. As it found the vm it should continue to start as normal.

When you say it freezes, does it freeze at the commandline or do you see any of the gui?
It always freezes before the thing loads (at the splash), and pretty randomly. It'll freeze before the splash screen image even loads up, at the beginning when it's just a solid gray box, or when it says that it's loading things. The splash screen also spawns on either the top left or the middle of my screen, seemingly randomly as well.

Examples of where it freezes:
[[IMG]http://img292.imageshack.us/img292/1059/screenshot1qu2.th.jpg[/IMG]](http://img292.imageshack.us/my.php?image=screenshot1qu2.jpg) [[IMG]http://img143.imageshack.us/img143/922/screenshot2cy2.th.jpg[/IMG]](http://img143.imageshack.us/my.php?image=screenshot2cy2.jpg) [[IMG]http://img292.imageshack.us/img292/3180/screenshot3zn5.th.jpg[/IMG]](http://img292.imageshack.us/my.php?image=screenshot3zn5.jpg)

I'm also getting quirky errors while compiling in Flex, which needs the Java Runtime Environment, so I'm guessing something is wrong with the JRE on my comp. I'ma try reinstalling it and stuff.

Any other ideas would be very much appreciated.

EDIT: Reinstalling didn't work. =( Help?

EDIT2: Fixed it! Mostly by replacing the gcj java value things with sun java after running this:
```
sudo /usr/bin/java-alt-setup
```
Thanks for your help!

---

