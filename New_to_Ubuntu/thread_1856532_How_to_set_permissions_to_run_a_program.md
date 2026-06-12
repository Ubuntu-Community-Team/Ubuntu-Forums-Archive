---
title: "How to set permissions to run a program?"
date: 2011-10-08
forum: New to Ubuntu
---

### Post by jacklz on 2011-10-08
Hi,
I've tried out Xubuntu - I like it. I like the Xfce desktop environment, but the only problem is that I can't run any programs because I have no idea how to give it permissions to run. For example, I've installed a .jar file and have Java 6 Runtime installed, and set that to run it with but with Ubuntu you can just check the checkbox to give it permission to run under the permissions for the file but I don't know how to on Xubuntu.
I'm new to Xfce.

---

### Post by zhogan85 on 2011-10-08
You'll have to use chmod from the terminal (slide man chmod first). 

The code would be something like

```
sudo chmod 777 /path/to/file 
```

Read the man page, the 7s go in order owner, group, user I think and will make it readable, writable, and executable.

---

### Post by MG&amp;TL on 2011-10-08
Or another way, this works for me:

```
chmod +x program
```

-x will do the opposite.

---

### Post by MG&amp;TL on 2011-10-08
Incidentally, if you prefer the GUI,

```
sudo apt-get install nautilus
```

will give you nautilus, the ubuntu file manager.

---

### Post by Morbius1 on 2011-10-08
In the particular example you mentioned you have a third option as well:

Right click the *.jar file > Open with other application > Use a custom command > enter:
```
java -jar
```And make sure "Use as default for this kind of file" is checked.

It turns out that a jar ( or an exe file ) doesn't have to be tagged as executable to run as Java and Wine don't care and don't check for it. THe reason you get error messages is because of something called cautious-launcher.

---

