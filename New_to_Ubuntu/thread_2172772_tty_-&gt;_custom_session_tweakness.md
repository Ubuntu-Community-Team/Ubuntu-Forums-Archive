---
title: "tty -&gt; custom session tweakness"
date: 2013-09-06
forum: New to Ubuntu
---

### Post by whatisgoingon on 2013-09-06
hello all!

first off, my question concerns rather curiosity and experimentation with tty than anything else, i'm having a fully operational system, so this is not a distress call by any means, 
don't break yourself offering an accurate answer to the followings, i'd love you for you doing so, tho.
so here's the situation: i'm running xubuntu 13.04 upon which i recently have installed and currently am using lxde. just for the heck of it i edited grub to prevent x from starting at startup.

i tried to log in to an lxde session from tty, which resulted in the message below.
```
Gtk-WARNING **: cannot open display
```

and startx gives:

```
Failed to load session "gnome"
```
which kinda makes sense i guess as i never edited my xinitrc.

i suspect the mere fact of having a custom DE behind the problem instead of going with the default one 
(, which makes it a bit more specific of an issue than those i encountered during googling for a solution), but i'm not quite sure.
startxfce4 does what it is expected to, so maybe.

so the main question is: what file should i edit (and how) to get startlxde working?
and a side one: how could i replace the action for startx so that instead of trying to init gnome it gets me to the regular xfce login/session selection screen, or better yet, declare a new command for that matter?
[B]
/etc/xdg/xfce4/xinitrc[/B]

```
#!/bin/sh

# fix broken $UID on some system...
if test "x$UID" = "x"; then
  if test -x /usr/xpg4/bin/id; then
    UID=`/usr/xpg4/bin/id -u`;
  else
    UID=`id -u`;
  fi
fi

# set $XDG_MENU_PREFIX to "xfce-" so that "xfce-applications.menu" is picked
# over "applications.menu" in all Xfce applications.
if test "x$XDG_MENU_PREFIX" = "x"; then
  XDG_MENU_PREFIX="xfce-"
  export XDG_MENU_PREFIX
fi

# set DESKTOP_SESSION so that one can detect easily if an Xfce session is running
if test "x$DESKTOP_SESSION" = "x"; then
  DESKTOP_SESSION="xfce"
  export DESKTOP_SESSION
fi

# set XDG_CURRENT_DESKTOP for alacarte
if test "x$XDG_CURRENT_DESKTOP" = "x"; then
  XDG_CURRENT_DESKTOP="XFCE"
  export XDG_CURRENT_DESKTOP
fi

# $XDG_CONFIG_HOME defines the base directory relative to which user specific
# configuration files should be stored. If $XDG_CONFIG_HOME is either not set
# or empty, a default equal to $HOME/.config should be used.
if test "x$XDG_CONFIG_HOME" = "x" ; then
  XDG_CONFIG_HOME=$HOME/.config
fi
[ -d "$XDG_CONFIG_HOME" ] || mkdir "$XDG_CONFIG_HOME"

# $XDG_CACHE_HOME defines the base directory relative to which user specific
# non-essential data files should be stored. If $XDG_CACHE_HOME is either not
# set or empty, a default equal to $HOME/.cache should be used.
if test "x$XDG_CACHE_HOME" = "x" ; then
  XDG_CACHE_HOME=$HOME/.cache
fi
[ -d "$XDG_CACHE_HOME" ] || mkdir "$XDG_CACHE_HOME"

# set up XDG user directores.  see
# http://freedesktop.org/wiki/Software/xdg-user-dirs
if which xdg-user-dirs-update >/dev/null 2>&1; then
    xdg-user-dirs-update
fi

# Modify libglade and glade environment variables so that
# it will find the files installed by Xfce
GLADE_CATALOG_PATH="$GLADE_CATALOG_PATH:/usr/share/glade3/catalogs"
GLADE_PIXMAP_PATH="$GLADE_PIXMAP_PATH:/usr/lib/glade3/modules"
GLADE_MODULE_PATH="$GLADE_MODULE_PATH:/usr/share/glade3/pixmaps"
export GLADE_CATALOG_PATH
export GLADE_PIXMAP_PATH
export GLADE_MODULE_PATH

# For now, start with an empty list
XRESOURCES=""

# Has to go prior to merging Xft.xrdb, as its the "Defaults" file
test -r "/etc/xdg/xfce4/Xft.xrdb" && XRESOURCES="$XRESOURCES /etc/xdg/xfce4/Xft.xrdb"
test -r $HOME/.Xdefaults && XRESOURCES="$XRESOURCES $HOME/.Xdefaults"

BASEDIR=$XDG_CONFIG_HOME/xfce4
if test -r "$BASEDIR/Xft.xrdb"; then
  XRESOURCES="$XRESOURCES $BASEDIR/Xft.xrdb"
elif test -r "$XFCE4HOME/Xft.xrdb"; then
  mkdir -p "$BASEDIR"
  cp "$XFCE4HOME/Xft.xrdb" "$BASEDIR"/
  XRESOURCES="$XRESOURCES $BASEDIR/Xft.xrdb"
fi

# merge in X cursor settings
test -r "$BASEDIR/Xcursor.xrdb" && XRESOURCES="$XRESOURCES $BASEDIR/Xcursor.xrdb"

# ~/.Xresources contains overrides to the above
test -r "$HOME/.Xresources" && XRESOURCES="$XRESOURCES $HOME/.Xresources"

# load all X resources (adds /dev/null to avoid an empty list that would hang the process)
cat /dev/null $XRESOURCES | xrdb -nocpp -merge -

# load local modmap
test -r $HOME/.Xmodmap && xmodmap $HOME/.Xmodmap

# run xfce4-session if installed
if which xfce4-session >/dev/null 2>&1; then

  # check if we start xfce4-session with ck-launch-session. this is only
  # required for starting from a console, not a login manager
  if test "x$XFCE4_SESSION_WITH_CK" = "x1"; then
    if which ck-launch-session >/dev/null 2>&1; then
      ck-launch-session xfce4-session
    else
      echo
      echo "You have tried to start Xfce with consolekit support, but"
      echo "ck-launch-session is not installed."
      echo "Aborted startup..."
      echo

      exit 1
    fi
  else
    # start xfce4-session normally
    xfce4-session
  fi

  exit 0
fi

##################
# IMPORTANT NOTE #
##################

# Everything below here ONLY gets executed if you are NOT using xfce4-session
# (Xfce's session manager).  If you are using the session manager, everything
# below is handled by it, and the code below is not executed at all.  If you're
# not sure if you're using the session manager, type 'ps -e|grep xfce4-session'
# in a terminal while Xfce is running.

##################

# Use dbus-launch if installed.
if test x"$DBUS_SESSION_BUS_ADDRESS" = x""; then
  if which dbus-launch >/dev/null 2>&1; then
    eval `dbus-launch --sh-syntax --exit-with-session`
    # some older versions of dbus don't export the var properly
    export DBUS_SESSION_BUS_ADDRESS
  else
    echo "Could not find dbus-launch; Xfce will not work properly" >&2
    fi
fi

# this is only necessary when running w/o xfce4-session
xsetroot -solid black -cursor_name watch

# or use old-fashioned startup script otherwise

xfsettingsd &
xfwm4 --daemon

# start up stuff in $XDG_CONFIG_HOME/autostart/
if test -d "$XDG_CONFIG_HOME/autostart"; then
  for i in ${XDG_CONFIG_HOME}/autostart/*.desktop; do
    grep -q -E "^Hidden=true" "$i" && continue
    if grep -q -E "^OnlyShowIn=" "$i"; then
      # need to test twice, as lack of the line entirely means we still run it
      grep -E "^OnlyShowIn=" "$i" | grep -q 'XFCE;' || continue
    fi
    grep -E "^NotShowIn=" "$i" | grep -q 'XFCE;' && continue

    # check for TryExec
    trycmd=`grep -E "^TryExec=" "$i" | cut -d'=' -f2`
    if test "$trycmd"; then
      which "$trycmd" >/dev/null 2>&1 || continue
    fi

    cmd=`grep -E "^Exec=" "$i" | cut -d'=' -f2`
    if test "$cmd" && which "$cmd" >/dev/null 2>&1; then
      $cmd &
    fi
  done
fi

xfdesktop&
orage &

panel=`which xfce4-panel`
case "x$panel" in
    x|xno*)
        ;;
    *)
        $panel
        ret=$?
        while test $ret -ne 0; do
            xmessage -center -file - -timeout 20 -title Error <<EOF
A crash occured in the panel
Please report this to the xfce4-dev@xfce.org list
or on http://bugs.xfce.org
Meanwhile the panel will be restarted
EOF
            cat >&2 <<EOF
A crash occured in the panel
Please report this to the xfce4-dev@xfce.org list
or on http://bugs.xfce.org
Meanwhile the panel will be restarted
EOF
            $panel
            ret=$?
        done
        ;;
esac

xsetroot -bg white -fg red  -solid black -cursor_name watch
```

**/etc/X11/Xsession**
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

tx in advance
```

---

### Post by zero2xiii on 2013-09-06
Hay,

People will probably shoot me for this:
>  how could i replace the action for startx so that instead of trying to init gnome it gets me to the regular xfce login/session selection screen, or better yet, declare a new command for that matter?

The easiest and cleanest way in my mind would be to set an alias:
You will probably need to set it system wide for it to work properly so first check that you local ~/.bashrc contains the following(The user you use to log in with before "startx"):
```
if [ -f /etc/bashrc ]; then
        . /etc/bashrc
fi
```

You can try adding it to this file and log out and back in and see if it works:

 ```
alias startx='startxfce4'
```

If not, add it to: "/etc/bashrc" and retest, if still not, try adding to " /etc/profile". The reason for this is different files are read for different shell environments.

TIP:
You can define any alias to any command. I have a few nice ones set up for example when I change directory, the new directories content is automatically listed (colored, and sorted folders first).

I hope this gives you a starting direction at least.

Cheers

---

### Post by Bashing-om on 2013-09-06
whatisgoingon; Hi ! Welcome to the forum.

As you want to start YOUR user session, edit (create) " ~/.xinitrc".
The ~/.xinitrc file is a shell script read by xinit and startx. It is mainly used to execute desktop environments, window managers and other programs when starting the X server.
The file "/etc/xdg/xfce4/xinitrc" is to be edited only for a system wide effect. In this case you want to effect the single user session.
For reference ONLY here is mine, note I start "xfce4" desktop environment.
I also export the variable "XAUTHORITY" which should not be required in your install.
I am redirecting the errors to a file for examination !
An echo statement for a troubleshooting mark.

> 
sysop@1304mini:~$ cat ~/.xinitrc
#!/usr/bin/env bash
#started creation of this file 23may2013
#
#
echo "starting the X session, Billy" >&2
export XAUTHORITY=/home/sysop/.Xauthority
exec startxfce4 --with-ck-launch > /home/sysop/errors-boot.txt 2>&1
#end
sysop@1304mini:~$ 

Change the "exec" to start whichever environment you want.[that you have previously set up] The DE is fully/completely customize-able, once you know what files are where do what.

In response to your question to start the session.
In your current install, from CLI what results;
```

sudo service lxde start

```
To aid your quest of discovery:
Unity, GDM. or lxde or xfce ect ect ..(literally hundreds out there)  are merely different Desktop Environments (DE) that you may use ... be aware there are probable config conflicts when multiple DEs are installed and  One may install a desktop manager to load a desired DE to help manage them.

I hope this serves to answer some of your questions. And a welcome once again to our world.
And I hope this is a good start to ->
[INDENT][INDENT][INDENT]let the hacking begin[/INDENT][/INDENT][/INDENT]

---

