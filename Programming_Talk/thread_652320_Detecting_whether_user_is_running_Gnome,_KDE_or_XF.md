---
title: "Detecting whether user is running Gnome, KDE or XFCE?"
date: 2007-12-28
forum: Programming Talk
---

### Post by altonbr on 2007-12-28
I'm writing a program that will deal with a conditional dependant on which WM the user is running.

The problem with using
```
GNOME=`nautilus --version`
XFCE=`thunar --version`
KDE=`konqueror --version`
```

Is that the user could have multiple WM installed.

I was hoping to make the script as un-interactive as possible just for (1) less annoyance for the user (2) faster running -- should be able to run via CLI quickly and effectively.

Is Python now in order as Bash has reached its limits?

---

### Post by Majorix on 2007-12-28
You could try somehow hacking your way into the config file for gdm or kdm (or xdm, but since you want your script to run fast, I left this out) and from there learn whichever session is the default, then act accordingly in your application.

---

### Post by Airr on 2007-12-28
I think that if you're using a graphical logon manager (gdm,kdm, etc) that the $DESKTOP_SESSION variable gets set with the name of the current window manager....

AIR.

---

### Post by LaRoza on 2007-12-28
> **Airr said:**
> I think that if you're using a graphical logon manager (gdm,kdm, etc) that the $DESKTOP_SESSION variable gets set with the name of the current window manager....

AIR.

Yeah, "default", unless you are not using your default.

Perhaps you can do this with exceptions do determine what works.

I would just write more than one GUI for each and have them separate.

---

### Post by Peyton on 2007-12-28
Check what processes are running. KDE will run ksmserver, GNOME will run gnome-session, and Xfce will run xfce-mcs-manage.

---

### Post by ghostdog74 on 2007-12-28
```

lsof | awk '/ksmserver|gnome-session|xfce-mcs-manage/{
 processes[$3]=$1
}END{
 for ( p in processes ) print p, processes[p]
}'

```

---

### Post by altonbr on 2007-12-28
> **ghostdog74 said:**
> ```

lsof | awk '/ksmserver|gnome-session|xfce-mcs-manage/{
 processes[$3]=$1
}END{
 for ( p in processes ) print p, processes[p]
}'

```

What does this do? Will all the recent warnings about malicious code, I'm supposed to ask.

---

### Post by ghostdog74 on 2007-12-28
> **altonbr said:**
> What does this do? Will all the recent warnings about malicious code, I'm supposed to ask.

[meaning of lsof. ]("http://en.wikipedia.org/wiki/Lsof"). Please run it on the command line and see for yourself how the output is like. If you don't have lsof, then the ps command will also do it.
```

# ps -eo user,args|egrep "kcmserver|gnome-session|xfce-mcs-manage"

```

---

### Post by p_quarles on 2007-12-28
> **altonbr said:**
> What does this do? Will all the recent warnings about malicious code, I'm supposed to ask.
Nothing malicious there. lsof lists open files and the apps running them, and awk is a text-processing shell.

---

### Post by Peyton on 2007-12-28
Here:
```
if [ "$(pidof ksmserver)" ]; then
   echo "KDE running."
   # KDE-specific stuff here
elif [ "$(pidof gnome-session)" ]; then
   echo "GNOME running."
   # GNOME-specific stuff here
elif [ "$(pidof xfce-mcs-manage)" ]; then
   echo "Xfce running."
   # Xfce-specific stuff here
fi
```

---

### Post by odiseo77 on 2007-12-28
I had a similar situation and I made a simple post-install script for a program by targeting the login manager (I'm not a programmer; I can barely write small bash scripts). Here's a sample:

```
#!/bin/bash
if [ "`ps -e | grep gdm`" ]; then
           echo "You're running Gnome"
           elif [ "`ps -e | grep kdm`" ]; then
           echo "You're running KDE"
           else
                exit 0
fi
```

(You obviously have to change the ***echo*** command to whatever command you want executed for Gnome or KDE -and XFCE, in your case).

By the way, I didn't know about the *$DESKTOP_SESSION* variable; gonna play with it.

:)

---

### Post by p_quarles on 2007-12-28
@odiseo: Just FYI, that script would tell me that I'm running KDE, where in fact I'm running KDM and Fluxbox. If that matters to you, it would be pretty easy to fix by running options for the various window managers.

---

### Post by odiseo77 on 2007-12-28
> **p_quarles said:**
> @odiseo: Just FYI, that script would tell me that I'm running KDE, where in fact I'm running KDM and Fluxbox. If that matters to you, it would be pretty easy to fix by running options for the various window managers.

Thank you p_quarles! I have to play a bit more with it. I thought about targeting the window manager (for example kwin for KDE or nautilus (I believe) for Gnome), but if the person is running compiz for instance, I think there will be no kwin or nautilus in the list of processes. I have to do a little of research :)

---

### Post by ghostdog74 on 2007-12-28
> **Peyton said:**
> Here:
```
if [ "$(pidof ksmserver)" ]; then
   echo "KDE running."
   # KDE-specific stuff here
elif [ "$(pidof gnome-session)" ]; then
   echo "GNOME running."
   # GNOME-specific stuff here
elif [ "$(pidof xfce-mcs-manage)" ]; then
   echo "Xfce running."
   # Xfce-specific stuff here
fi
```

will there be a chance for one user to use 2 or more WM? I don't play with WMs, so.... 
If yes, then maybe elif would not be appropriate? If there cannot be a chance for 2 or more WM running for one user, then forget that i mentioned this.

---

### Post by altonbr on 2007-12-29
Hey, thanks you all! I was expecting such a response.

> **ghostdog74 said:**
> [meaning of lsof. ]("http://en.wikipedia.org/wiki/Lsof"). Please run it on the command line and see for yourself how the output is like. If you don't have lsof, then the ps command will also do it.
```

# ps -eo user,args|egrep "kcmserver|gnome-session|xfce-mcs-manage"

```

This just returns the actual grep statement:
> brett    grep -E kcmserver|gnome-session|xfce-mcs-manage

> **Peyton said:**
> Here:
```
if [ "$(pidof ksmserver)" ]; then
   echo "KDE running."
   # KDE-specific stuff here
elif [ "$(pidof gnome-session)" ]; then
   echo "GNOME running."
   # GNOME-specific stuff here
elif [ "$(pidof xfce-mcs-manage)" ]; then
   echo "Xfce running."
   # Xfce-specific stuff here
fi
```

Thanks, I'll try this...

> **ghostdog74 said:**
> will there be a chance for one user to use 2 or more WM? I don't play with WMs, so.... 
If yes, then maybe elif would not be appropriate? If there cannot be a chance for 2 or more WM running for one user, then forget that i mentioned this.

Hmm, I'm trying to figure out whether the user is running Ubuntu, Kubuntu or Xubuntu simply for program install choices (example: ubuntu-restricted-extras, kubuntu-restricted-extra, xubuntu-restricted-extras, plus more). So if people have multiple WMs installed AND running, then I'll have to figure out another way.

I just it may be best just to ask the user, but that takes away from the automated task of this script...

---

### Post by winch on 2007-12-29
You could check which *-desktop meta packages are installed.

```

dpkg -l xubuntu-desktop
dpkg -l kubuntu-desktop
dpkg -l ubuntu-desktop

or look for all in one go
dpkg -l "*untu-desktop"

```

Of course you can remove them or install more than one which might be a problem.

---

### Post by ghostdog74 on 2007-12-29
> **altonbr said:**
> 
This just returns the actual grep statement:

and i was expected you to try and do the rest.

---

### Post by altonbr on 2007-12-30
> **Peyton said:**
> Here:
```
if [ "$(pidof ksmserver)" ]; then
   echo "KDE running."
   # KDE-specific stuff here
elif [ "$(pidof gnome-session)" ]; then
   echo "GNOME running."
   # GNOME-specific stuff here
elif [ "$(pidof xfce-mcs-manage)" ]; then
   echo "Xfce running."
   # Xfce-specific stuff here
fi
```

When I add a else in your code, I always get the else to run it's echo.

I'm in a fresh install of Ubuntu (Gnome) so is there something I'm missing?

---

### Post by stroyan on 2007-12-30
It is possible for one user to have multiple window managers running on one system.
The rule of thumb is one window manager per X server.
But a user can actually run multiple X servers in multiple linux virtual terminals.
The most reliable way I know to find the current window manager is to use
the xprop command to read properties that window managers are supposed
to put on the X server root window and their own window.
That is spelled out in the window manager specification at [http://standards.freedesktop.org/wm-spec/wm-spec-latest.html](http://standards.freedesktop.org/wm-spec/wm-spec-latest.html)

Here is an example script that uses xprop```
WM_WINDOW=$(xprop -root _NET_SUPPORTING_WM_CHECK);
WM_WINDOW=${WM_WINDOW##* };
WM_NAME=$(xprop -id $WM_WINDOW 8s _NET_WM_NAME)
WM_NAME=${WM_NAME##* };
echo $WM_NAME
```
The first use of xprop gets the window ID of a window created by the window manager.
The second use of xprop gets the name of the window manager from the WM_NAME property on the window.
If there is no window manager running, or some non-compliant window manager is running, then the xprop commands might return "not found" or
get a BadWindow error.

---

### Post by altonbr on 2007-12-30
> **stroyan said:**
> It is possible for one user to have multiple window managers running on one system.
The rule of thumb is one window manager per X server.
But a user can actually run multiple X servers in multiple linux virtual terminals.
The most reliable way I know to find the current window manager is to use
the xprop command to read properties that window managers are supposed
to put on the X server root window and their own window.
That is spelled out in the window manager specification at [http://standards.freedesktop.org/wm-spec/wm-spec-latest.html](http://standards.freedesktop.org/wm-spec/wm-spec-latest.html)

Here is an example script that uses xprop```
WM_WINDOW=$(xprop -root _NET_SUPPORTING_WM_CHECK);
WM_WINDOW=${WM_WINDOW##* };
WM_NAME=$(xprop -id $WM_WINDOW 8s _NET_WM_NAME)
WM_NAME=${WM_NAME##* };
echo $WM_NAME
```
The first use of xprop gets the window ID of a window created by the window manager.
The second use of xprop gets the name of the window manager from the WM_NAME property on the window.
If there is no window manager running, or some non-compliant window manager is running, then the xprop commands might return "not found" or
get a BadWindow error.

Wow, works well, thanks!

The only problem with that is, for me, it returns "compiz". This means that I'm probably going to have to ask the user if they're running Kubuntu, Xubuntu or Ubuntu as there is no reliable way to tell which is which...
Or I guess, write an if statement asking what they're running if "compiz" is returned.

It also properly returns "Metacity" when I turn it off. Thank you, thank you, thank you!

---

### Post by odiseo77 on 2007-12-31
> **altonbr said:**
> Or I guess, write an if statement asking what they're running if "compiz" is returned.

I have the same problem with compiz since it replaces the window manager, but I've noticed that, if you're running kde with compiz, you'll find ***kde-window-decorator*** in the list of processes and if you're running gnome with compiz, you'll find ***gtk-window-decorator***, so maybe you can try to automate it without the need of prompting the user? (I will try to do it with my script as well, and now that I think about it, I believe it will be pretty easy to do it) :)

EDIT: oh, well, I think it will be more troublesome in case the user us running emerald :-? I will install emerald to see what's the difference.

---

### Post by altonbr on 2008-01-21
I found here: [https://wiki.ubuntu.com/DesktopTeam/Specs/AboutThisComputer#head-4698a94d7bc56e16178528636d8e66cb04637ee6](https://wiki.ubuntu.com/DesktopTeam/Specs/AboutThisComputer#head-4698a94d7bc56e16178528636d8e66cb04637ee6) that detecting KDE can be done via the 'KDE_FULL_SESSION' variable...

---

### Post by Paul Miller on 2008-01-22
Why not just let the user specify on the command line or in a .config file which option he'd like?  That seems a lot simpler than trying to probe the environment automatically and guess.

---

### Post by altonbr on 2008-01-22
> **Paul Miller said:**
> Why not just let the user specify on the command line or in a .config file which option he'd like?  That seems a lot simpler than trying to probe the environment automatically and guess.

Very true, but my father, my sisters, my grandmother, my grandfather, my neighbours, my clients and my co-workers would all look at me cock-eyed if I asked them if they're using GNOME, KDE or XFCE...

It's a usability feature...

---

