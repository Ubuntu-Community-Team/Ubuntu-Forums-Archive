---
title: "Enabling root in desktop temporarily"
date: 2014-12-20
forum: Programming Talk
---

### Post by dfriedberg on 2014-12-20
I use my Ubuntu machine for web dev so I run nginx, PHP and MySQL on my box. Is there a way to temporarily be root in desktop to drag and drop files or its easier just to sudo in command line?

---

### Post by kpatz on 2014-12-20
You can use **gksudo** to run a GUI program as root.  So, for example, **gksudo nautilus** or whatever file manager you're using.

If you don't have gksudo, install the package: **sudo apt-get install gksu**

---

### Post by Bashing-om on 2014-12-20
dfriedberg; Hello;

You do not say what release you are running, and as well if there is a GUI (Desktop Environment ) instaled.
I guess there is something:
> 
 root in desktop to drag and drop files or its easier 

Depending on the DE is the file manager that is installed ( or one you have installed ) .
Say for instance there is the unity desktop, by default the file manager is 'nautilus'. You can start the file manager with the elevated privileges of administration:
```

gksudo nautilis

```
Be aware, in the latter releases: - the times they are achange'n -
Gksudo and others are deprecated now and not recommended any more. Pkexec is the new boy but it is not straightforward either.
Discussion here:
[http://ubuntuforums.org/showthread.php?t=2225832](http://ubuntuforums.org/showthread.php?t=2225832)

Confused enough. we will work through it .

[INDENT][INDENT][INDENT]no step for a stepper
[/INDENT][/INDENT][/INDENT]

---

### Post by ajgreeny on 2014-12-20
If you want to try it, and I make no claims for its safety in all cases, you can try using pkexec with the rather complicated command prefix ```
pkexec env DISPLAY=$DISPLAY XAUTHORITY=$XAUTHORITY
``` so for unity or gnome DEs it would be ```
pkexec env DISPLAY=$DISPLAY XAUTHORITY=$XAUTHORITY nautilus
``` **pkexec <command>** does not work like gksudo; if you look at the command used for GUI apps such as synaptic you will see it is reversed to **synaptic-pkexec** but using **nautilus-pkexec** does not work as an extra policy file is needed for it to take effect.

I have set up an alias of pkx for the prefix part of this command to make it easier to use, but I have to admit that I usually forget it, and use gksu as I have been using that since 2005.

EDIT:
I didn't look at the link ventrical supplied in the post above from Bashing-om [http://ubuntuforums.org/showthread.php?t=2225832](http://ubuntuforums.org/showthread.php?t=2225832) which gives the same info as I have just given here; probably where I found it myself.
Never mind; it works fine as far as I can make out, though I am not sure why it is better than gksu.

---

### Post by Bashing-om on 2014-12-20
@ajgreeny; Hey, hey.

As to the why fore of pkexe; 
> 
Never mind; it works fine as far as I can make out, though I am not sure why it is better than gksu.

I am under advisement:
> 
Bashing-om: The reason they(gksudo) are no longer installed by default is that there are no GUI apps in the default install with launchers using gksudo/gksu. All default GUI apps that need elevated privileges most of the time now use PolicyKit to ask for specific privileges rather that having to run the whole app as root.(Jordan_U)


[INDENT][INDENT]as we live and learn
[/INDENT][/INDENT]

---

### Post by dfriedberg on 2014-12-21
I"m using Unity that comes with 14.10. I''ll check it out thank you.

---

