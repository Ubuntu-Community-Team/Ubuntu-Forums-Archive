---
title: "[Bash] Finding Current Desktop Environment"
date: 2010-04-15
forum: Programming Talk
---

### Post by dodle on 2010-04-15
I'm trying to write a script that will find out which desktop is being used and launch the corresponding "gksu" or "kdesu".  According to what I have been able to find, i can use [color=green]$DESKTOP_SESSION[/color], but this variable is set by GDM.  So if someone logs in without using GDM then it won't work.  

Is there an environment variable that is specific to each desktop?  That way I can do something like this:
[php]#! /bin/bash

if [ -n "${KDE_VARIABLE+x}" ]; then
  echo The current session is KDE

elif [ -n "${GNOME_VARIABLE+x}" ]; then
  echo The current session is Gnome

elif [ -n "${XFCE_VARIABLE+x}" ]; then
  echo The current session is XFCE
fi[/php]
**Also:** I've heard people talking about a command "xdg-su" that is supposed to replace "kdesu" and "gksu", but it isn't installed on my system and does not seem to be included with xdg-utils.

**Edit:** Or is it a better idea to run through the processes and find desktop specific processes like "gnome-session" and "kde-session"?  I don't know how to do this yet, so any advice is welcome.  Also, what would a process look like for other DEs like XFCE, "xfce-session"?

---

### Post by soltanis on 2010-04-15
I would run through the processes, when it comes down to it, that's your most reliable indicator. You can use awk or grep to find the process you are looking for, e.g.

```

ps -e | awk '/gnome/ { print "gksu" } /kde/ { print "kdesu" }'

```

---

### Post by nvteighen on 2010-04-15
During LaRoza's sysres days, what we did was to:

1) Check if Kicker was running. If true, then it was KDE.
```

ps -ef | grep "[k]icker" >/dev/null 2>&1

```

2) If (1) was false, we checked if X was running by testing if DISPLAY was defined. If it was, we assumed that a GTK+ based/capable DE was running.

3) If everything failed, we defaulted to CLI.

I know it was a quite risky approach, but it worked in the cases we needed. Maybe you can elaborate this a bit more and adapt it to your needs.

---

### Post by Reiger on 2010-04-15
KDE sets the following variables:
```

KDE_FULL_SESSION
KDE_MULTIHEAD
KDE_SESSION_UID
KDE_SESSION_VERSION

```

---

### Post by diesch on 2010-04-15
From *xdg-open*:

```
detectDE()
{
    if [ x"$KDE_FULL_SESSION" = x"true" ]; then DE=kde;
    elif [ x"$GNOME_DESKTOP_SESSION_ID" != x"" ]; then DE=gnome;
    elif xprop -root _DT_SAVE_MODE | grep ' = \"xfce4\"$' >/dev/null 2>&1; then DE=xfce;
    fi
}

```

---

