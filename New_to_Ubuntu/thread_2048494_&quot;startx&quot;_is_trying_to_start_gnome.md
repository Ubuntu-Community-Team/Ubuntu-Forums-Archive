---
title: "&quot;startx&quot; is trying to start gnome"
date: 2012-08-26
forum: New to Ubuntu
---

### Post by sithpigeon on 2012-08-26
Hi, I have been working with a minimal install using only xserver and fluxbox. I was fairly happy with logging in from the terminal and then typing "startx" to get into my fluxbox session, but I tried installing lightdm for the heck of it. After that, everything stopped working... so I booted into recovery mode and removed lightdm and the other stuff it installed. Now however, when I type "startx" it won't load fluxbox, but rather tries to load gnome and says "failed to load gnome". I can create a .xinitrc file in my home directory and enter exec startfluxbox and that seems to help, but I'm wondering if installing lightdm edited another x file which is trying to start gnome when I type startx. Or will having a .xinitrc file in my home directory prevent that? I don't have gnome installed and I'm trying to go for the speediest system I can, so I'd rather not have X trying to load gnome everytime it starts. Not to mention if I create a new user and it tries to load gnome as the default. So basically, which files do I need to check to make sure fluxbox is the default and not gnome. 

Thanks in advance!

---

### Post by Cheesemill on 2012-08-26
The startx command simply runs your ~/.xinitrc file, you just need to edit it to launch the relevant WM/DE (as you have already done).

---

### Post by sithpigeon on 2012-08-27
Alright, so I edited my ~/.xinitrc file to contain just```
exec startfluxbox
```

but I noticed that the settings I had specified for aterm in .Xresources weren't remaining active after rebooting, even after running ```
xrdb ~/.Xresources
``` to reapply them. 

I looked in my default .xinitrc at /etc/X11/xinit/xinitrc and it had


```
#!/bin/sh

# /etc/X11/xinit/xinitrc
#
# global xinitrc file, used by all X sessions started by xinit (startx)

# invoke global X session script
. /etc/X11/Xsession
exec xfe
```

So I added```
/etc/X11/Xsession
```

to my user .xinitrc file, which now looks like

```
/etc/X11/Xsession
exec startfluxbox
```

Now when I run startx, my resource settings are loaded but it says "Failed to start gnome", and then it starts fluxbox. I'm guessing I need to edit my Xsession file, but I can't make heads or tails of that one. Mine looks like:


```
#!/bin/sh
#
# /etc/X11/Xsession
#
# global Xsession file -- used by display managers and xinit (startx)

# $Id: Xsession 967 2005-12-27 07:20:55Z dnusinow $

set -e

PROGNAME=Xsession

message () {
  # pretty-print messages of arbitrary length; use xmessage if it
  # is available and $DISPLAY is set
  MESSAGE="$PROGNAME: $*"
  echo "$MESSAGE" | fold -s -w ${COLUMNS:-80} >&2
  if [ -n "$DISPLAY" ] && which xmessage > /dev/null 2>&1; then
    echo "$MESSAGE" | fold -s -w ${COLUMNS:-80} | xmessage -center -file -
  fi
}

message_nonl () {
  # pretty-print messages of arbitrary length (no trailing newline); use
  # xmessage if it is available and $DISPLAY is set
  MESSAGE="$PROGNAME: $*"
  echo -n "$MESSAGE" | fold -s -w ${COLUMNS:-80} >&2;
  if [ -n "$DISPLAY" ] && which xmessage > /dev/null 2>&1; then
    echo -n "$MESSAGE" | fold -s -w ${COLUMNS:-80} | xmessage -center -file -
  fi
}

errormsg () {
  # exit script with error
  message "$*"
  exit 1
}

internal_errormsg () {
  # exit script with error; essentially a "THIS SHOULD NEVER HAPPEN" message
  # One big call to message() for the sake of xmessage; if we had two then
  # the user would have dismissed the error we want reported before seeing the
  # request to report it.
  errormsg "$*" \
           "Please report the installed version of the \"x11-common\"" \
           "package and the complete text of this error message to" \
           "<debian-x@lists.debian.org>."
}

# initialize variables for use by all session scripts

OPTIONFILE=/etc/X11/Xsession.options

SYSRESOURCES=/etc/X11/Xresources
USRRESOURCES=$HOME/.Xresources

SYSSESSIONDIR=/etc/X11/Xsession.d
USERXSESSION=$HOME/.xsession
USERXSESSIONRC=$HOME/.xsessionrc
ALTUSERXSESSION=$HOME/.Xsession
ERRFILE=$HOME/.xsession-errors

# attempt to create an error file; abort if we cannot
if (umask 077 && touch "$ERRFILE") 2> /dev/null && [ -w "$ERRFILE" ] &&
  [ ! -L "$ERRFILE" ]; then
  chmod 600 "$ERRFILE"
elif ERRFILE=$(tempfile 2> /dev/null); then
  if ! ln -sf "$ERRFILE" "${TMPDIR:=/tmp}/xsession-$USER"; then
    message "warning: unable to symlink \"$TMPDIR/xsession-$USER\" to" \
             "\"$ERRFILE\"; look for session log/errors in" \
             "\"$TMPDIR/xsession-$USER\"."
  fi
else
  errormsg "unable to create X session log/error file; aborting."
fi

# truncate ERRFILE if it is too big to avoid disk usage DoS
if [ "`stat -c%s \"$ERRFILE\"`" -gt 500000 ]; then
  T=`mktemp -p "$HOME"`
  tail -c 500000 "$ERRFILE" > "$T" && mv -f "$T" "$ERRFILE" || rm -f "$T"
fi

exec >>"$ERRFILE" 2>&1

echo "$PROGNAME: X session started for $LOGNAME at $(date)"

# sanity check; is our session script directory present?
if [ ! -d "$SYSSESSIONDIR" ]; then
  errormsg "no \"$SYSSESSIONDIR\" directory found; aborting."
fi

# Attempt to create a file of non-zero length in /tmp; a full filesystem can
# cause mysterious X session failures.  We do not use touch, :, or test -w
# because they won't actually create a file with contents.  We also let standard
# error from tempfile and echo go to the error file to aid the user in
# determining what went wrong.
WRITE_TEST=$(tempfile)
if ! echo "*" >>"$WRITE_TEST"; then
  message "warning: unable to write to ${WRITE_TEST%/*}; X session may exit" \
          "with an error"
fi
rm -f "$WRITE_TEST"

# use run-parts to source every file in the session directory; we source
# instead of executing so that the variables and functions defined above
# are available to the scripts, and so that they can pass variables to each
# other
SESSIONFILES=$(run-parts --list $SYSSESSIONDIR)
if [ -n "$SESSIONFILES" ]; then
  set +e
  for SESSIONFILE in $SESSIONFILES; do
    . $SESSIONFILE
  done
  set -e
fi

exit 0

# vim:set ai et sts=2 sw=2 tw=80:
```

I am currently reading through "man Xsession" and there is some promising information, but any assistance is appreciated.

---

### Post by sithpigeon on 2012-08-27
Just noticing a few things:

I ran ```
ps -e
``` and saw that wicd was running. I thought I uninstalled that, so I tried doing so again with ```
sudo apt-get purge wicd
``` and it says it isn't installed... (I have network-manager installed because it seems to run much more smoothly).

This leads me to wonder about something I did after I installed lightdm. In recovery mode, I initiated networking and then dropped to a root terminal. From there I used apt-get to remove wicd and lightdm. Would that have messed anything up? Removing packages as root that is? I thought they were universally installed and it wouldn't matter, but perhaps it didn't remove the configuration correctly??

Also, in searching through the Xsession file and the files in Xsession.d, I see that it appears to start "x-session-manager" first if no startup program is specified by the calling script, (in this case, my typing "startx" if I'm not mistaken). Curious as to whether this is the solution to my problem, I wanted to view the manual for "x-session-manager" so I type ```
man x-session-manager
``` and it spat out the manual for "gnome-session". So, I ran

```
x-session-manager
```

just to see what would happen, and I get the same error as when I start up, "Failed to load session "gnome"".

So then, the new question is, for what is x-session-manager used? Can I just comment out that line in the Xsession file? If it's a virtual package, as apt-get says, what does that mean? Can I change x-session-manager in some way to use a different session manager?? (Would that be a display manager?)

---

### Post by sithpigeon on 2012-08-27
Alright, so I figured out that x-session-manager is "configured" using a symlink in the /usr/bin/ directory. I renamed /usr/bin/x-session-manager to x-session-manager-backup and it stopped trying to start gnome. 

Is this an appropriate fix? Should I have a session manager installed? Xsm perhaps? Not entirely sure what that is but it seems like a simple form of the program.

---

### Post by xhiko on 2013-05-01
I was having the same issue that started happening after upgrading from Xubuntu 12.04 to Xubuntu 13.10 and [found this]("http://www.linux-archive.org/xubuntu-user/328714-new-xubuntu-but-im-startx-user-how-do-i-ditch-gui-login.html"):
**sudo update-alternatives --config x-session-manager**

It gave me the following output:

```
  Selection    Path                    Priority   Status
------------------------------------------------------------
* 0            /usr/bin/gnome-session   50        auto mode
  1            /usr/bin/gnome-session   50        manual mode
  2            /usr/bin/xfce4-session   40        manual mode

Press enter to keep the current choice
[*], or type selection number: 
```

Then I could change my default session from gnome-session to xfce4-session.

---

