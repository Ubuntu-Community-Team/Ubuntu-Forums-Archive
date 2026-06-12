---
title: "Another Tor help"
date: 2013-10-26
forum: New to Ubuntu
---

### Post by billathome65 on 2013-10-26
Hi I've been using Lubuntu for a while but had issues getting Tor to run and a mate of mine was saying that ubuntu has Tor now and sure enought I install Ubuntu and it does so I install Vilida and click run only to be told Tor  was unable to start then asks me to ensure the correct name and location of the Tor Executable is Specified I open settings and see this ( /usr/sbin/tor ) 
 
I have no idea how to get Tor / Vilida to run any hints would be good I don't think my ISP blocks however I tried the bridge thing but there are no bridges 

Please help 

Thanks Bill

---

### Post by verymadpip on 2013-10-26
Hi there.
Have you tried downloading the Tor Browser Bundle?

[https://www.torproject.org/](https://www.torproject.org/)

---

### Post by billathome65 on 2013-10-26
Yes Since posting this Ubuntu was freezing and dragging on my system so I have reinstalled Lubuntu so the question is the same for Lubuntu how to install and run on Lubuntu?

---

### Post by billathome65 on 2013-10-26
When I try to run the browser If I click to run in terminal the terminal opens giving a command line for tor but thats it and when I try to just open all I get is a text file?

Terminal

```
bill@bill-Aspire-5630:~/Desktop$ tor
The program 'tor' is currently not installed. You can install it by typing:
sudo apt-get install tor
bill@bill-Aspire-5630:~/Desktop$ sudo apt-get install tor
[sudo] password for bill: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
bill@bill-Aspire-5630:~/Desktop$

open tick box gives me this.

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
if [ "$#" -eq 1 -a \( "x$1" = "x--debug" -o "x$1" = "x-debug" \) ]; then
    debug=1
    printf "\nDebug enabled.\n\n"
elif [ "$#" -eq 1 -a \( "x$1" = "x--help" -o "x$1" = "x-help" \) ]; then
    echo "$usage_message"
    exit 0
fi

# If the user hasn't requested 'debug mode', close whichever of stdout
# and stderr are not ttys, to keep Vidalia and the stuff loaded by/for
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

if ldd ./App/Firefox/firefox-bin | grep -q "libz\.so\.1.*not found"; then
    LD_LIBRARY_PATH="${HOME}/Lib:${HOME}/Lib/libz"
else
    LD_LIBRARY_PATH="${HOME}/Lib"
fi

LDPATH="${HOME}/Lib/"
export LDPATH
export LD_LIBRARY_PATH

if [ "$debug" -eq 1 ]; then
    printf "\nStarting Vidalia now\n"
    cd "${HOME}"
    printf "\nLaunching Vidalia from: `pwd`\n"
    # XXX Someday we should pass whatever command-line arguments we got
    # (probably filenames or URLs) to Firefox.
    ./App/vidalia --loglevel debug --logfile vidalia-debug-log \
    --datadir Data/Vidalia/ -style Cleanlooks
    printf "\nVidalia exited with the following return code: $?\n"
    exit
fi

# not in debug mode, run proceed normally
printf "\nLaunching Tor Browser Bundle for Linux in ${HOME}\n"
cd "${HOME}"
# XXX Someday we should pass whatever command-line arguments we got
# (probably filenames or URLs) to Firefox.
./App/vidalia --datadir Data/Vidalia/ -style Cleanlooks
exitcode="$?"
if [ "$exitcode" -ne 0 ]; then
    complain "Vidalia exited abnormally.  Exit code: $exitcode"
    exit "$exitcode"
else
    printf '\nVidalia exited cleanly.\n'
fi
```

---

### Post by verymadpip on 2013-10-26
Hi Bill, try this:

Download the correct bundle for your machine - 32 or 64 bit.  That'll be a .tar.gz file.
Go to the folder that has been downloaded to.
Right click & select *extract here*.
When that's done, open the shiny new tor browser blah blah folder that has been created.
Right click the *start-tor-browser* file & select properties.
Go to the *permissions* tab & tick the *allow this file to run as a program* box & close the window.
Double click the *start-tor-browser* file thingummy.

A Vidalia window should open &, eventually, connect you to the Tor network &  then, eventually again, a Tor browser (modified Firefox) window should open & you're away.
(When I say eventually I don't mean hours by the way, but it may take a minute or two - a little patience is handy at this point).

Good luck.

---

### Post by billathome65 on 2013-10-26
Ok thanks will try this. Tried that it didn't have a tab allow this file to run it has 

Owner 
Group
Access control
View content
Change content
Execute


The General tab has 

Start tor browser

Says its a shell script

and open with leafpad which i'm assuming is similar to notepad in windows?

Bill




Execute

---

### Post by verymadpip on 2013-10-26
Hi Bill, 
My bad.  I'm on Xubuntu at the moment, forgot that Lubuntu has a different file manager, sorry about that.
I've had a look at a Lubuntu live environment & I think you need to check out the options available under *Execute*.
At worst set it to *anybody*.  If that works we can set about not letting any other user accounts from executing the file.

Yes, Leafpad is akin to Wordpad more so than notepad I think.  Personally I prefer Wordpad as it seems to keep formatting correctly.

---

### Post by billathome65 on 2013-10-26
Cheers that worked a treat 

Us windows freeks comming over to Linux must do your heads in even though lots like Lubuntu are GUI based it is still difficult navigating around and finding things

Thanks for the help.

By the way can I run this from my desktop as an icon like the onion you normally see?

Bill

---

### Post by billathome65 on 2013-10-26
Ok I got Tor running now but i'm getting a hell of a lot of problem loading page or time outs What is the most likely cause ( My ISP Blocking?? ) or bad luck?? whats all this about bridging I saw I can allow my pc to be a bridge but i'm warry about that this is so frustrating :)

---

### Post by verymadpip on 2013-10-26
Hi Bill.
Tor pages inevitably (IMO) load slower than pages in a regular browser.  It's the trade off for the anonymity.
Personally I have had issues with page loading & lost functionality due to No Script running - but No Script stops flash & java vulnerabilities from being exploited, I *think*.  (Someone else may be able to clarify for both of us here).  Of course, that could have nothing to do with what you're experiencing.
Depending on the sites you're visiting you may be able to give temporary permissions to some scripts, but you need to be cautious as we don't want to defeat the object of running Tor in the first place.

Are you in a place where your ISP would try to block you?

Regards bridging;  I have no idea what that is, so I'm not going to suggest anything.

I have to duck out for a couple of hours, but I'll check back later to see where we're up to.

Good Luck.

---

### Post by bapoumba on 2013-10-26
@billathome65 : I edited your post #4 to add [code] tags to your large terminal output. Please see here : [http://ubuntuforums.org/misc.php?do=bbcode]("http://ubuntuforums.org/misc.php?do=bbcode")

---

### Post by billathome65 on 2013-10-26
cheers which bb code did you use to box it if you know what I mean for future referance

---

### Post by billathome65 on 2013-10-26
> **verymadpip said:**
> Hi Bill.
Tor pages inevitably (IMO) load slower than pages in a regular browser.  It's the trade off for the anonymity.
Personally I have had issues with page loading & lost functionality due to No Script running - but No Script stops flash & java vulnerabilities from being exploited, I *think*.  (Someone else may be able to clarify for both of us here).  Of course, that could have nothing to do with what you're experiencing.
Depending on the sites you're visiting you may be able to give temporary permissions to some scripts, but you need to be cautious as we don't want to defeat the object of running Tor in the first place.

Are you in a place where your ISP would try to block you?

Regards bridging;  I have no idea what that is, so I'm not going to suggest anything.

I have to duck out for a couple of hours, but I'll check back later to see where we're up to.

Good Luck.

Your right about speed Ive used tor on and of for some time so expect slow speed. the timing out is a new one on me though as it never happened in windows but hey thats how the cookie crumbles.

Cheers for the help getting it running now how to run a torrent client like Bittorrent, Azuse also had problems installing them in the past.

:p

---

### Post by bapoumba on 2013-10-26
> **billathome65 said:**
> cheers which bb code did you use to box it if you know what I mean for future referance

I used the code one. By hand : [.code]blabla[./code] without the dots within the brackets, for you to see how to write it. Will show as :
```
blabla
```

You can also use the # button in the editor panel, see the screenshot.

---

### Post by verymadpip on 2013-10-27
Hi again Bill.
I tried Tor on a netbook I have running Lubuntu 13.10 32 bit & it all went swimmingly well.  Maybe I've just touched lucky.
How's Tor behaving for you at the moment?

As for launching from its own icon; I'm not sure that can be done from the extracted tarball executable.  There's a little discussion about that in this thread:
[http://ubuntuforums.org/showthread.php?t=2182827&page=2](http://ubuntuforums.org/showthread.php?t=2182827&page=2)

I don't think there was any joy though :(

I'm assuming your internet connection is generally okay with Lubuntu so we can rule out a hardware problem.  Wired or wireless by the way?

---

### Post by billathome65 on 2013-10-27
Seems to be behaving itself. 

I tried saving the Tor script to desktop and running execute from there but just got an error code so just running from it's own file instead.

Cheers mate and thanks for the help

Bill

---

### Post by verymadpip on 2013-10-28
No probs Bill, glad that's working for you :D

If you're happy with the outcome you can mark this thread solved from thread tools in the top right of the first post.

P.S.  We've all had to start somewhere mate, no head-doing-in at all ;)

---

### Post by jefferydavidiverse on 2013-11-02
Hi guys Im having the same issue as previously stated in this thread so I tried installing the tor browser bundle and when I select the start-tor-browser file and allow it to run as a program nothing happens at all. I cant figure out what im doing wrong but im very new to ubuntu. Any help or ideas would be appreciated. Thanks

---

