---
title: "Starting firefox from terminal"
date: 2014-08-21
forum: Programming Talk
---

### Post by bizhat on 2014-08-21
I have a bash script to start Firefox in different profile.

```

$ cat ~/bin/ff22 
#!/bin/bash


firefox -P ff22 &
$ 

```

This works fine.

But problem is the terminal i run this program keep showing error message from firefox.

How i hide error messages from firefox showing in terminal ?

---

### Post by ofnuts on 2014-08-21
Redirect stdout/sterr to /dev/null: 

```

firefox -P ff22 > /dev/null 2>&1 &

```

---

### Post by ajgreeny on 2014-08-21
Why not simply write another firefoxff22.desktop file to use as a launcher for that other profile?

Use command ```
gedit /usr/share/applications/firefox.desktop
``` to open the original, look for the line
 **Exec=firefox %u**
 and edit that to
 **Exec=firefox -P ff22**
 then save the edited file to your /home as firefoxff22.desktop.

You could then move that new launcher to /usr/share/applications if you want to and you should then have the two versions of firefox showing in your menu or dash.

---

### Post by bizhat on 2014-08-21
Thanks for the help. Got it working.

---

### Post by bizhat on 2014-08-21
[FONT=Verdana]> **ofnuts said:**
> Redirect stdout/sterr to /dev/null: [/FONT]

[FONT=Verdana]```
[/FONT]
[FONT=Verdana]firefox -P ff22 > /dev/null 2>&1 &[/FONT]
[FONT=Verdana]
```[/FONT]

[FONT=Verdana]Thanks, this is what i was looking for [/FONT]:)

[FONT=Verdana]Edit: sorry for double post, i don't see option to delete/merge posts.[/FONT]

---

### Post by vasa1 on 2014-08-21
> **ofnuts said:**
> Redirect stdout/sterr to /dev/null: 

```

firefox -P ff22 > /dev/null 2>&1 &

```
I use just **2>/dev/null**
@ofnuts, please explain why you have **> /dev/null 2>&1 &**? And, why is there **&** at the end in this specific case?

---

### Post by bizhat on 2014-08-21
& at the end because we need firefox run in background. If not, firefox won't release command prompt.

**> /dev/null 2>&1**

This, @ofnuts will explain :)

---

### Post by tgalati4 on 2014-08-21
It's bash magical shorthand for pushing Error Output (channel 2) into Standard Output (channel 1) and sending both of those into the bit bucket (/dev/null).  It's used in a lot of bootup scripts to hide things when starting up services.

```
grep null /etc/init.d/*
```

---

### Post by bizhat on 2014-08-21
> **tgalati4 said:**
> It's bash magical shorthand for pushing Error Output (channel 2) into Standard Output (channel 1) and sending both of those into the bit bucket (/dev/null).  It's used in a lot of bootup scripts to hide things when starting up services.

```
grep null /etc/init.d/*
```

Thanks,

```

firefox -P PROFILE_NAME 2>/dev/null &

```

Also worked with out any error message in terminal.

---

### Post by vasa1 on 2014-08-21
> **bizhat said:**
> & at the end because we need firefox run in background. If not, firefox won't release command prompt.

**> /dev/null 2>&1**

This, @ofnuts will explain :)

Got it. But you are running a script aren't you? From your original post:```
$ cat ~/bin/ff22 
#!/bin/bash


firefox -P ff22 &
$
```So just assign a keyboard shortcut to ~/bin/ff22 and you won't even need the terminal and **&** at the end won't be an issue. That's why I haven't found the need for & in my script.

---

### Post by bizhat on 2014-08-22
> **vasa1 said:**
> So just assign a keyboard shortcut to ~/bin/ff22 and you won't even need the terminal and **&** at the end won't be an issue. That's why I haven't found the need for & in my script.

Thanks, done that. Works much better now. Just switched from Windows, so still need to learn ubuntu tricks :)

---

