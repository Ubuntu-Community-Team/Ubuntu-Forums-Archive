---
title: "Installing TOR on Ubuntu 14.04"
date: 2014-06-15
forum: New to Ubuntu
---

### Post by kelly4 on 2014-06-15
Hi, I am new to linux with intermediate knowledge of Windows

I would like some help with installing TOR on ubuntu 14.04

Thank you kindly,

:popcorn:

---

### Post by texpat on 2014-06-15
This [https://www.torproject.org/docs/debian.html.en](https://www.torproject.org/docs/debian.html.en) any help?

I have no experience with tor myself (and no ambition to gain it ;-)) but it *looks* pretty straight forward.

---

### Post by Vladlenin5000 on 2014-06-15
You don't actually have to install it to use it. Keeping it in a USB pen allows you to run without leaving traces* in the host computer. 

* The use of third-party apps, namely download managers, can leave a trace.

---

### Post by kelly4 on 2014-06-16
> **texpat said:**
> This [https://www.torproject.org/docs/debian.html.en](https://www.torproject.org/docs/debian.html.en) any help?

I have no experience with tor myself (and no ambition to gain it ;-)) but it *looks* pretty straight forward.

Thank you, I will try that and report back with my results

:popcorn:

> **Vladlenin5000 said:**
> You don't actually have to install it to use it. Keeping it in a USB pen allows you to run without leaving traces* in the host computer. 

* The use of third-party apps, namely download managers, can leave a trace.

Yes, I always get a message when I DL something when using TOR

I like the idea of an USB pen

Thank you, I'll get back with my results

:popcorn:

---

### Post by Nobody Nessie on 2014-06-18
Personnally, I just click [this link](https://www.torproject.org/dist/torbrowser/3.6.2/tor-browser-linux32-3.6.2_en-US.tar.xz) (_warning_ : this is the real Linux TBB package download link !)   I download it in my /home/ directory and extract it in my /home/ directory. Then just click on "start-tor-browser" in the /tor-browser_en-US/ directory and that's it !       _Another warning_ : I personnaly do not worry at all of using Tor as, firstly, I do nothing illegal and, secondly, I am used to avoid Tor exit nodes (and Tor hidden services).  When TorProject update their TBB, I delete the old one and install the new one in the same place !

---

### Post by kelly4 on 2014-06-18
On this [page]("https://www.torproject.org/docs/debian.html.en"), I attempted to run this in terminal

> deb     [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) **Trusty Tahr** main

and got this error

> No command 'deb' found, did you mean:
 Command 'deb3' from package 'quilt' (main)
 Command 'dab' from package 'bsdgames' (universe)
 Command 'debc' from package 'devscripts' (main)
 Command 'derb' from package 'icu-devtools' (main)
 Command 'xdeb' from package 'xdeb' (universe)
 Command 'debi' from package 'devscripts' (main)
 Command 'dwb' from package 'dwb' (universe)
deb: command not found

so didn't get to add the gpg key used to sign the packages by running the following commands at your command prompt:

> gpg --keyserver keys.gnupg.net --recv 886DDD89
gpg --export A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89 | sudo apt-key add

nor refresh your sources, running the following command (as root) at your
command prompt:

> apt-get update

If there are no errors you're good to continue.

We provide a Debian package to help you keep our signing key current. It is
recommended you use it. Install it using

> apt-get install deb.torproject.org-keyring    To finally install Tor just run: 
apt-get install tor


Thanks for any help

---

### Post by Nobody Nessie on 2014-06-18
I have already tried to install the Tor daemon alone with "sudo apt-get install tor", then Vidalia. I removed both of them. The first thing, it did not work and I did not want to waste my time. The second thing, the TorProject themselves recommand to use direcly the TBB as it is often updated for vulnerabilities and bugs issues.  I even do not know if you can easily be able to connect to obfs3 bridges with Tor/Vidalia daemon. If it still does not work, you can try to download the TBB and redirect all your application to socks5, 127.0.0.1:9150, or with Privoxy to http, 127.0.0.1:8118, allowing it to forward socks5 to port 9150. I have a privoxy apparmor profile somewhere in my folders, if you need !

---

### Post by kelly4 on 2014-06-19
Dropped the start-tor-browser file into terminal and it worked but gave terminal failed msg

It opened but am getting error msg

```
(process:13533): GLib-CRITICAL **: g_slice_set_config: assertion 'sys_page_size == 0' failed
```

and this msg

> Your Firefox profile cannot be loaded. It may be missing or inaccessible

:popcorn:

---

### Post by kelly4 on 2014-06-20
Tor works now on 14.04, but would like to turn this code

```
#!/bin/sh
#
# GNU/Linux does not really require something like RelativeLink.c
# However, we do want to have the same look and feel with similar features.
#
# To run in debug mode simply pass --debug
#
# Copyright 2011 The Tor Project.  See LICENSE for licensing information.

complain_dialog_title="Tor Browser Bundle"

# First, make sure DISPLAY is set.  If it isn't, we're hosed; scream
# at stderr and die.
if [ "x$DISPLAY" = "x" ]; then
    echo "$complain_dialog_title must be run within the X Window System." >&2
    echo "Exiting." >&2
    exit 1
fi

# Do not (try to) connect to the session manager 
unset SESSION_MANAGER 

# Determine whether we are running in a terminal.  If we are, we
# should send our error messages to stderr...
ARE_WE_RUNNING_IN_A_TERMINAL=0
if [ -t 1 -o -t 2 ]; then
    ARE_WE_RUNNING_IN_A_TERMINAL=1
fi

# ...unless we're running in the same terminal as startx or xinit.  In
# that case, the user is probably running us from a GUI file manager
# in an X session started by typing startx at the console.
#
# Hopefully, the local ps command supports BSD-style options.  (The ps
# commands usually used on Linux and FreeBSD do; do any other OSes
# support running Linux binaries?)
ps T 2>/dev/null |grep startx 2>/dev/null |grep -v grep 2>&1 >/dev/null
not_running_in_same_terminal_as_startx="$?"
ps T 2>/dev/null |grep xinit 2>/dev/null |grep -v grep 2>&1 >/dev/null
not_running_in_same_terminal_as_xinit="$?"

# not_running_in_same_terminal_as_foo has the value 1 if we are *not*
# running in the same terminal as foo.
if [ "$not_running_in_same_terminal_as_startx" -eq 0 -o \
     "$not_running_in_same_terminal_as_xinit" -eq 0 ]; then
    ARE_WE_RUNNING_IN_A_TERMINAL=0
fi

# Complain about an error, by any means necessary.
# Usage: complain message
# message must not begin with a dash.
complain () {
    # Trim leading newlines, to avoid breaking formatting in some dialogs.
    complain_message="`echo "$1" | sed '/./,$!d'`"

    # If we're being run in a terminal, complain there.
    if [ "$ARE_WE_RUNNING_IN_A_TERMINAL" -ne 0 ]; then
        echo "$complain_message" >&2
        return
    fi

    # Otherwise, we're being run by a GUI program of some sort;
    # try to pop up a message in the GUI in the nicest way
    # possible.
    #
    # In mksh, non-existent commands return 127; I'll assume all
    # other shells set the same exit code if they can't run a
    # command.  (xmessage returns 1 if the user clicks the WM
    # close button, so we do need to look at the exact exit code,
    # not just assume the command failed to display a message if
    # it returns non-zero.)

    # First, try zenity.
    zenity --error \
        --title="$complain_dialog_title" \
        --text="$complain_message"
    if [ "$?" -ne 127 ]; then
        return
    fi

    # Try kdialog.
    kdialog --title "$complain_dialog_title" \
        --error "$complain_message"
    if [ "$?" -ne 127 ]; then
        return
    fi

    # Try xmessage.
    xmessage -title "$complain_dialog_title" \
        -center \
        -buttons OK \
        -default OK \
        -xrm '*message.scrollVertical: Never' \
        "$complain_message"
    if [ "$?" -ne 127 ]; then
        return
    fi

    # Try gxmessage.  This one isn't installed by default on
    # Debian with the default GNOME installation, so it seems to
    # be the least likely program to have available, but it might
    # be used by one of the 'lightweight' Gtk-based desktop
    # environments.
    gxmessage -title "$complain_dialog_title" \
        -center \
        -buttons GTK_STOCK_OK \
        -default OK \
        "$complain_message"
    if [ "$?" -ne 127 ]; then
        return
    fi
}

if [ "`id -u`" -eq 0 ]; then
    complain "The Tor Browser Bundle should not be run as root.  Exiting."
    exit 1
fi

debug=0
usage_message="usage: $0 [--debug]"
# !!! We may have more than one argument, changed -eq to -ge in if & elif clauses below
if [ "$#" -ge 1 -a \( "x$1" = "x--debug" -o "x$1" = "x-debug" \) ]; then
    debug=1
    shift # pop the debug argument
    printf "\nDebug enabled.\n\n"
elif [ "$#" -ge 1 -a \( "x$1" = "x--help" -o "x$1" = "x-help" \) ]; then
    echo "$usage_message"
    exit 0
fi

# If the user hasn't requested 'debug mode', close whichever of stdout
# and stderr are not ttys, to keep Firefox and the stuff loaded by/for
# it (including the system's shared-library loader) from printing
# messages to $HOME/.xsession-errors .  (Users wouldn't have seen
# messages there anyway.)
#
# If the user has requested 'debug mode', don't muck with the FDs.
if [ "$debug" -ne 1 ]; then
  if [ '!' -t 1 ]; then
    # stdout is not a tty
    exec >/dev/null
  fi
  if [ '!' -t 2 ]; then
    # stderr is not a tty
    exec 2>/dev/null
  fi
fi

# If XAUTHORITY is unset, set it to its default value of $HOME/.Xauthority
# before we change HOME below.  (See xauth(1) and #1945.)  XDM and KDM rely
# on applications using this default value.
if [ -z "$XAUTHORITY" ]; then
    XAUTHORITY=~/.Xauthority
    export XAUTHORITY
fi

# If this script is being run through a symlink, we need to know where
# in the filesystem the script itself is, not where the symlink is.
myname="$0"
if [ -L "$myname" ]; then
    # XXX readlink is not POSIX, but is present in GNU coreutils
    # and on FreeBSD.  Unfortunately, the -f option (which follows
    # a whole chain of symlinks until it reaches a non-symlink
    # path name) is a GNUism, so we have to have a fallback for
    # FreeBSD.  Fortunately, FreeBSD has realpath instead;
    # unfortunately, that's also non-POSIX and is not present in
    # GNU coreutils.
    #
    # If this launcher were a C program, we could just use the
    # realpath function, which *is* POSIX.  Too bad POSIX didn't
    # make that function accessible to shell scripts.

    # If realpath is available, use it; it Does The Right Thing.
    possibly_my_real_name="`realpath "$myname" 2>/dev/null`"
    if [ "$?" -eq 0 ]; then
        myname="$possibly_my_real_name"
    else
        # realpath is not available; hopefully readlink -f works.
        myname="`readlink -f "$myname" 2>/dev/null`"
        if [ "$?" -ne 0 ]; then
            # Ugh.
            complain "start-tor-browser cannot be run using a symlink on this operating system."
        fi
    fi
fi

# Try to be agnostic to where we're being started from, chdir to where
# the script is.
mydir="`dirname "$myname"`"
test -d "$mydir" && cd "$mydir"

# This is a fix for an ibus issue on some Linux systems. See #9353 for more
# details. The symlink needs to be created before we change HOME.
if [ ! -d ".config/ibus" ]; then
  mkdir -p .config/ibus
  ln -nsf ~/.config/ibus/bus .config/ibus
fi

# If ${PWD} results in a zero length HOME, we can try something else...
if [ ! "${PWD}" ]; then
    # "hacking around some braindamage"
    HOME="`pwd`"
    export HOME
    surveysays="This system has a messed up shell.\n"
else
    HOME="${PWD}"
    export HOME
fi

SYSARCHITECTURE=$(getconf LONG_BIT)
TORARCHITECTURE=$(expr "$(file Tor/tor)" : '.*ELF \([[:digit:]]*\)')

if [ $SYSARCHITECTURE -ne $TORARCHITECTURE ]; then
   complain "Wrong architecture? 32-bit vs. 64-bit."
   exit 1
fi

LD_LIBRARY_PATH="${HOME}/Tor/"
export LD_LIBRARY_PATH

# XXX: Debug mode for Firefox??

# not in debug mode, run proceed normally
printf "\nLaunching Tor Browser Bundle for Linux in ${HOME}\n"
cd "${HOME}"
# XXX Someday we should pass whatever command-line arguments we got
# (probably filenames or URLs) to Firefox.
# !!! Dash above comment! Now we pass command-line arguments we got (except --debug) to Firefox.
# !!! Use at your own risk!
./Browser/firefox -no-remote -profile Data/Browser/profile.default "${@}"
exitcode="$?"
if [ "$exitcode" -ne 0 ]; then
    complain "Tor Browser exited abnormally.  Exit code: $exitcode"
    exit "$exitcode"
else
    printf '\nTor Browser exited cleanly.\n'
fi
```

 into a file that executes autmatically when clicked like a batch file in windows so that I don't have to open it up terminal :O

Also I can't set it as a file that opens with terminal :/

Thanks for any help out there

:KS

---

