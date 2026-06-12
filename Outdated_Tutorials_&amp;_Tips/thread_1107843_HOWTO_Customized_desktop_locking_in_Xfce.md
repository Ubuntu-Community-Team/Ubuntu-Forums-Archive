---
title: "HOWTO: Customized desktop locking in Xfce"
date: 2009-03-27
forum: Outdated Tutorials &amp; Tips
---

### Post by jis on 2009-03-27
In this howto I tell how you can set which utility is used for locking desktop in Xfce that is the desktop environment used in Xubuntu. You can launch the lock by <Crtl><Alt><Del> in Xubuntu, by default. The keyboard shortcut runs a Bourne shell script named xflock4. It is located at /usr/bin/. You can make a customized version and save it to /usr/local/bin/xflock4. That will be used instead of the default one, since /usr/local/bin/ directory is searched before /usr/bin/ for commands. (That is set in PATH environment variable.)

Here is the customized xflock4 I wrote:
```

#!/bin/sh

case "$DESKTOP_LOCK_UTILITY" in
    xscreensaver )
	if xscreensaver-command -lock 2>/dev/null; then
	  exit 0
        fi
    ;;   
    gnome-screensaver )
	if gnome-screensaver-command --lock 2>/dev/null; then
	  exit 0
        fi
    ;;
    xtrlock )
	# xtrlock leaves desktop visible
        if test -n "`which xtrlock 2>/dev/null`"; then
	  xtrlock &
          exit 0
        fi
   ;;

esac

# Try xlock by default and if nothing else works
if test -n "`which xlock 2>/dev/null`"; then
  xlock -mode blank $* &
  exit 0
fi

exit 1

```

You can save it as /usr/local/bin/xflock4 and make it executable by command
```
sudo chmod a+x /usr/local/bin/xflock4
``` in terminal.

You can choose the preferred locking utility by setting an environment variable named DESKTOP_LOCK_UTILITY. The current options are xscreensaver, gnome-screensaver, xtrlock and xlock. Of course, you have to install the utility of your preference before you use it. In case your preference is xscreensaver or gnome-screensaver, you have to start a respective screensaver daemon in xinitrc. (There are instructions for that in another howto that I authored. I link it here once I know its url; the howto has to be accepted by moderators first.) UPDATE: See [here]("http://ubuntuforums.org/showpost.php?p=6965233&postcount=1") for a hint on how to edit xinitrc script.

xtrlock is a special kind of desktop locking utility that does not hide screen. Once you have installed it, I recommend reading its short manual by ```
man xtrlock
``` in terminal.
NOTE 2009-04-01: I found that xtrlock does not work always, so you may consider not using it for now.

[Here]("https://help.ubuntu.com/community/EnvironmentVariables") it is told how to use environment variables in Ubuntu distributions.

---

### Post by Lampi on 2009-04-23
Hi jis

Thanks for the Howto, how to use it if I'm logged in Xserver as user root?
Xscreensaver daemon refuses to work with root, so no locking is possible.

---

### Post by jis on 2009-04-23
Are you sure xscreensaver daemon is running then? It is not started in Xfce's xinitrc, if you run it as root. I don't know why. You could make a customized xinitrc in which you remove string "$UID -gt 0 -a" in the if test around screensaver daemon startup to try to start xscreensaver anyway. Why do you log in Xserver as root?

---

### Post by Lampi on 2009-05-09
Hello jis, sorry for the long delay

No, the daemon does not run in X with root logged in and it refuses to start/restart in the Xscreensaver GUI.

I'll try the code modification you suggested. About beeing logged in as root: I no longer use sudo privileges, so it sometimes comes in handy to use the root account for configuration purposes (mostly to rule out permission problems)

---

### Post by jis on 2009-05-12
> **Lampi said:**
> Hello jis, sorry for the long delay

No, the daemon does not run in X with root logged in and it refuses to start/restart in the Xscreensaver GUI.

I'll try the code modification you suggested. About beeing logged in as root: I no longer use sudo privileges, so it sometimes comes in handy to use the root account for configuration purposes (mostly to rule out permission problems)

Hello Lampi. I guess Xscreensaver is not meant to work when you are logged in as root, so the modification in xinitrc will not work. You can use e.g. xlock then; just install xlockmore package.

---

