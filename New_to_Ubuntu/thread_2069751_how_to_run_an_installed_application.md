---
title: "how to run an installed application"
date: 2012-10-11
forum: New to Ubuntu
---

### Post by sudoninja on 2012-10-11
1. I'm trying to run mwbuttons to fix the deliberate mistake in ubuntu server 11.10's window layout.
 
 
2. I believe metacity 'contains' mwbuttons.
 
3. I think metacity is installed - the software center says so.
 
So. How do you run an installed application? Linux doesn't tell you where anything is. It doesn't highlight the most recently installed apps. It's not giving much away and not being very helpful.
 
Please no linux fanboys - telling me to press Alt-F2 and type in the name - what name?
 
How do I call mwbuttons.
 
I press ALT-F2 and type mwbuttons and press Enter. I type metacity and press enter. Same response - nothing happens. The search icon spins a bit then stops. I really mean N O T H I N G H A P P E N S. This is just wrong - surely an operating system should tell you something like - "File not found"? But no. I get absolutely nothing.
 
Please no smug answers from linux fanboys - just talk to me like a grown-up please.

---

### Post by sandyd on 2012-10-11
> **sudoninja said:**
> 1. I'm trying to run mwbuttons to fix the deliberate mistake in ubuntu server 11.10's window layout.
 
 
2. I believe metacity 'contains' mwbuttons.
 
3. I think metacity is installed - the software center says so.
 
So. How do you run an installed application? Linux doesn't tell you where anything is. It doesn't highlight the most recently installed apps. It's not giving much away and not being very helpful.
 
Please no linux fanboys - telling me to press Alt-F2 and type in the name - what name?
 
How do I call mwbuttons.
 
I press ALT-F2 and type mwbuttons and press Enter. I type metacity and press enter. Same response - nothing happens. The search icon spins a bit then stops. I really mean N O T H I N G H A P P E N S. This is just wrong - surely an operating system should tell you something like - "File not found"? But no. I get absolutely nothing.
 
Please no smug answers from linux fanboys - just talk to me like a grown-up please.
mwbuttons is seperate I think.

You can run mwbuttons by running this in a terminal though
```

wget http://launchpad.net/mwbuttons/trunk/v0.2/+download/mwbuttons
chmod +x mwbuttons
./mwbuttons

```

---

### Post by shaktiman1234 on 2012-10-11
@sudoninja:
you did not tell how did you install the mwbuttons application.
1. If you installed using .deb package or using Ubuntu software center then you can search in the Ubuntu software center itself. If it is installed properly then you will find it listed.
2. If you downloaded the source code and did yourself the make and install then you it should be present in your working directory while installing.

---

### Post by sudoninja on 2012-10-11
how do i run a terminal window?

- Got it "Ctrl + Alt + T" - very 1980's

---

### Post by sudoninja on 2012-10-11
Metacity is listed as an installed application in the software center. Green tick. Installed via the software center.

---

### Post by sudoninja on 2012-10-11
I'm trying to run it in a terminal window.

I'm getting this...

```
(mwbuttons:13926): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
```

four times, followed by 

```
Traceback (most recent call last):
  File "./mwbuttons", line 25, in <module>
    import gconf

```

---

### Post by sudoninja on 2012-10-11
> **sudoninja said:**
> I'm trying to run it in a terminal window.

I'm getting this...

```
(mwbuttons:13926): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
```

four times, followed by 

```
Traceback (most recent call last):
  File "./mwbuttons", line 25, in <module>
    import gconf

```
thought i'd type in "sudo apt-get install pixmap" just to see what would  happen.

---

### Post by sudoninja on 2012-10-11
> **sudoninja said:**
> thought i'd type in "sudo apt-get install pixmap" just to see what would  happen.
thought i'd try "sudo apt-get install gconf"...

---

### Post by sudoninja on 2012-10-11
> **sudoninja said:**
> thought i'd try "sudo apt-get install gconf"...
no that didn't work. guess i'll keep on guessing.

---

### Post by sudoninja on 2012-10-11
> **sudoninja said:**
> thought i'd type in "sudo apt-get install pixmap" just to see what would  happen.
what does "
mwbuttons:13926" mean?

---

### Post by sudoninja on 2012-10-11
> **sudoninja said:**
> what does "
mwbuttons:13926" mean?
what does "
Gtk-WARNING" mean?

---

### Post by sandyd on 2012-10-11
fixed commands in earlier post - c&p failure :|

---

### Post by sudoninja on 2012-10-11
It took some guessing but I found this.

gconftool-2 --type string --set /apps/metacity/general/button_layout 
"menu:minimize,maximize,close"

Windows is better than Linux - deal with it.

---

