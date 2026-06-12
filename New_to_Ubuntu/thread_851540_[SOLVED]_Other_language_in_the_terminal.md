---
title: "[SOLVED] Other language in the terminal"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by Vossibear on 2008-07-06
How do I change the language in the terminal?

I want to have German as the standardt language in my system, but the terminal should be in English, because I want to youse the prints of it in this forum

THX

Vossibear

---

### Post by ChameleonDave on 2008-07-07
Hmm, I don't know of any standard way to do that.

Even if your terminal program is in German, most of the command-line stuff will still be in English, won't it?  I'm sure it won't be too much of a problem getting support on these forums.

---

### Post by ladr0n on 2008-07-07
A lot of the GNU apps use the system locale to display printout in the local language.  The commands will be the same, but the readout would be (in this case) in German.  It's great for people who want to use their native language on their computer, but it does make support in the forums slightly more difficult. 
There is probably a way to acheive what you're trying to do (probably by messing with the locale settings), but I can't think of it off the top of my head.

---

### Post by sdennie on 2008-07-07
If you want your terminal to be in English but the rest of your system in another language, you could try adding the following to ~/.bashrc:

```

if [ ! -z "$PS1" ]; then
    LANG=en_US.UTF-8
fi

```

---

### Post by ChameleonDave on 2008-07-07
> **vor said:**
> If you want your terminal to be in English but the rest of your system in another language, you could try adding the following to ~/.bashrc:

```

if [ ! -z "$PS1" ]; then
    LANG=en_US.UTF-8
fi

```

...except that the code for English is en_GB.  ;-)

---

### Post by sdennie on 2008-07-07
> **ChameleonDave said:**
> ...except that the code for English is en_GB.  ;-)

Haha.  :)

---

### Post by Vossibear on 2008-07-07
I'm sry for my stupid question, but where I must add the Code for my favourite English ;)

---

### Post by ChameleonDave on 2008-07-07
> **Vossibear said:**
> I'm sry for my stupid question, but where I must add the Code for my favourite English ;)

You can type a command like these to open the file for editing:

(to edit entirely from the command line)
```

sudo nano ~/.bashrc

```

(to edit on GNOME/Ubuntu)
```

gksudo gedit ~/.bashrc

```

(to edit on KDE/Kubuntu)
```

kdesudo kwrite ~/.bashrc

```

(to edit on Xfce/Xubuntu)
```

gksudo mousepad ~/.bashrc

```


The tilde or swung dash (~) means "the home directory for this user".

---

### Post by Vossibear on 2008-07-07
Thanks I think it's solved

---

### Post by ChameleonDave on 2008-07-07
> **Vossibear said:**
> Thanks I think it's solved

Perhaps you could use the "Thread Tools" menu to mark this thread as solved.

---

