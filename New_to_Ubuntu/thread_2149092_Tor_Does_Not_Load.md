---
title: "Tor Does Not Load"
date: 2013-05-27
forum: New to Ubuntu
---

### Post by CJMacalister on 2013-05-27
I have installed Tor on my new Ubuntu laptop (first time user of Linux), and upon attempting to open it, only the Vidalia control panel will open. According to the control panel, it "successfully connects to the Tor network," but Tor Browser itself does not open. What do I do?

---

### Post by Paqman on 2013-05-27
What exactly have you installed? The TOR browser bundle?

Try running it through a terminal, it should spit out what actual errors it encounters.

---

### Post by CJMacalister on 2013-05-28
I followed your advice, and here's what I got:

May 28 08:21:05.759 [notice] Tor v0.2.3.25 (git-3fed5eb096d2d187) running on Linux.
May 28 08:21:05.759 [notice] Tor can't help you if you use it wrong! Learn how to be safe at [https://www.torproject.org/download/download#warning](https://www.torproject.org/download/download#warning)
May 28 08:21:05.759 [notice] Read configuration file "/etc/tor/torrc".
May 28 08:21:05.762 [notice] Initialized libevent version 2.0.19-stable using method epoll (with changelist). Good.
May 28 08:21:05.762 [notice] Opening Socks listener on 127.0.0.1:9050
May 28 08:21:05.763 [warn] Could not bind to 127.0.0.1:9050: Address already in use. Is Tor already running?
May 28 08:21:05.763 [warn] Failed to parse/validate config: Failed to bind one of the listener ports.
May 28 08:21:05.763 [err] Reading config failed--see warnings above.

Do you know what to do from here? Keep in mind that I fully recognize that I'm terribly inept at Linux still.

And yes, I have installed Tor Browser Bundle.

---

### Post by dino99 on 2013-05-28
[https://help.ubuntu.com/community/Tor](https://help.ubuntu.com/community/Tor)

maybe you need to check ufw to open the required port (and your router too if you have one)

---

### Post by Lars Noodén on 2013-05-28
It looks like something is already listening on port 9050.  Did you happen to install Tor first and then try to add the Tor Browser Bundle?  

```

sudo netstat -ntlp | grep :9050
dpkg --get-selections tor

```

If so, then uninstall Tor and just keep the Tor Browser Bundle.  The Bundle comes with its own version of Tor, and a graphical configurator, so it is not necessary to install Tor from the Software Center / Repository.

---

### Post by Paqman on 2013-05-28
> **dino99 said:**
> [https://help.ubuntu.com/community/Tor](https://help.ubuntu.com/community/Tor)

maybe you need to check ufw to open the required port (and your router too if you have one)

Er, that's an internal address dude. 127.0.0.1 is the local machine.

CJMacalister: Try giving your machine a reboot and starting from scratch, run it from a terminal again and see what you get. If you get the same error then you might already have some other service running on that port, either you'll have to figure out what that is, or look into running TOR on a different port.

---

### Post by dino99 on 2013-05-28
> **Paqman said:**
> Er, that's an internal address dude. 127.0.0.1 is the local machine.

CJMacalister: Try giving your machine a reboot and starting from scratch, run it from a terminal again and see what you get. If you get the same error then you might already have some other service running on that port, either you'll have to figure out what that is, or look into running TOR on a different port.

maybe you have not read or understood, dude.
May 28 08:21:05.763 [warn] Could not bind to 127.0.0.1:9050: Address already in use. Is Tor already running?

---

### Post by Paqman on 2013-05-28
> **dino99 said:**
> maybe you have not read or understood, dude.
May 28 08:21:05.763 [warn] Could not bind to 127.0.0.1:9050: Address already in use. Is Tor already running?

Yes, I saw that, and I suspect the OP had previously launched TOR and the service is in fact up and running, but the browser has not launched for some reason. I could have suggested using killall to stomp any TOR processes that were still running, but a reboot is probably quicker and easier for a noob. 

It may of course be that the TOR bundle doesn't launch the browser if it can't connect to the network (which could be due to a firewall as you say), but we don't know that for sure. Starting with a clean slate in a terminal will allow us to see the actual error message. Do you disagree with the logic of this course of action?

---

### Post by CJMacalister on 2013-05-30
In response to everyone generically in this thread after looking over the responses, I chose to instead resort, as someone have here suggested, to the Tor Browser Bundle without installation. This was actually my initial intention, in fact, as that is how I use Tor with both Mac as well as with Windows (when I still used Windows, that is). However, given my Linux illiteracy as of yet, I still don't know what to do with the downloaded Tor Browser Bundle content after downloading it. On Windows and Mac I merely unzipped the files and Tor Browser was already there ready for use. But on Linux, I see, it requires something more than merely unzipping, no? There's plenty of content in the unzipped folder but no icon to direct oneself to Tor Broswer. Do I type a command in the terminal of some sort to integrate the downloaded content into the system?

---

### Post by Lars Noodén on 2013-05-30
> **CJMacalister said:**
> In response to everyone generically in this thread after looking over the responses, I chose to instead resort, as someone have here suggested, to the Tor Browser Bundle without installation. This was actually my initial intention, in fact, as that is how I use Tor with both Mac as well as with Windows (when I still used Windows, that is). However, given my Linux illiteracy as of yet, I still don't know what to do with the downloaded Tor Browser Bundle content after downloading it. On Windows and Mac I merely unzipped the files and Tor Browser was already there ready for use. But on Linux, I see, it requires something more than merely unzipping, no? There's plenty of content in the unzipped folder but no icon to direct oneself to Tor Broswer. Do I type a command in the terminal of some sort to integrate the downloaded content into the system?

After you have downloaded the Tor Browser Bundle, untar/unzip it.  (That is also an option to combine with the download).  I recommend making a directory ~/bin and unpacking it there.  If you have it unpacked in ~/bin, then next time you use the shell, you can run it with tor-browser-*_en-US*/start-tor-browser.  Substitute *en-US* for what you actually have.  You can also make an icon for it and launch it that way.

The Bundle is the recommended way to run a browser with Tor because it helps present a standardized profile and the larger the herd of identical browsers, the better chance of anonymity.

---

### Post by ShadowVegan on 2013-05-30
> **CJMacalister said:**
> In response to everyone generically in this thread after looking over the responses, I chose to instead resort, as someone have here suggested, to the Tor Browser Bundle without installation. This was actually my initial intention, in fact, as that is how I use Tor with both Mac as well as with Windows (when I still used Windows, that is). However, given my Linux illiteracy as of yet, I still don't know what to do with the downloaded Tor Browser Bundle content after downloading it. On Windows and Mac I merely unzipped the files and Tor Browser was already there ready for use. But on Linux, I see, it requires something more than merely unzipping, no? There's plenty of content in the unzipped folder but no icon to direct oneself to Tor Broswer. Do I type a command in the terminal of some sort to integrate the downloaded content into the system?
No, there's nothing more to it. To unzip it, just right click on the downloaded .tar.gz file and click 'extract here'. When you do that, you should see a folder called something like 'tor-browser_en-US'. At this point you can delete the .tar.gz file. Wthin the 'tor-browser_en-US' folder there should be several other folders, as well as a file called 'start-tor-browser'. Open the file called 'start-tor-browser' and if it gives you options like 'open, execute, execute in terminal, exit' click on 'execute' (or perhaps 'run'). Then just wait about a minute and a Tor-enabled version of Firefox will open.

Although the default settings are pretty good there are some things you can do to make it more secure, such as enabling NoScript, disabling @font-face, disabling all cookies, etc. If you want more info on what settings to change send me a PM.

---

### Post by CJMacalister on 2013-06-01
> **ShadowVegan said:**
> No, there's nothing more to it. To unzip it, just right click on the downloaded .tar.gz file and click 'extract here'. When you do that, you should see a folder called something like 'tor-browser_en-US'. At this point you can delete the .tar.gz file. Wthin the 'tor-browser_en-US' folder there should be several other folders, as well as a file called 'start-tor-browser'. Open the file called 'start-tor-browser' and if it gives you options like 'open, execute, execute in terminal, exit' click on 'execute' (or perhaps 'run'). Then just wait about a minute and a Tor-enabled version of Firefox will open.

Although the default settings are pretty good there are some things you can do to make it more secure, such as enabling NoScript, disabling @font-face, disabling all cookies, etc. If you want more info on what settings to change send me a PM.

Okay, I have followed your instructions. However, when I open the "start-tor-browser" file, instead of receiving the options you listed, I am offered only a text file with the following text, which is incomprehensible to me:

> #!/bin/sh
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

Do you know why it does this instead, and what I should do about it?

---

### Post by Lars Noodén on 2013-06-01
The text is a shell script that should have been run but, due to a defect that you have found in Ubuntu's file manager, does not.  I'd say it's worth filing a bug over since it impairs use of the file manager to launch programs / scripts.  I notice there's not even a way to find the right application (/bin/sh) to open it with.

So, you'll have to launch Tor via the shell, I outlined the general process above.  Myself, I would enter the following in the shell (terminal) because that's where I put Tor.

```

~/tor-browser_en-US/start-tor-browser

```

Depending on where you unpacked the archive and the language you chose, yours should be similar.

---

### Post by verymadpip on 2013-06-01
Hi there.
This probably won't help, but have you made the "srart-tor-browser" file executable? [Right click > properties > permissions. Or some type of chmod in a terminal].

---

### Post by Lars Noodén on 2013-06-01
The script 'start-tor-browser' is already executable when it is unpacked.  The defect seems to be with Ubuntu's file manager which looks like it is unable to launch shell scripts in general.

---

### Post by CJMacalister on 2013-06-01
> **Lars Noodén said:**
> The text is a shell script that should have been run but, due to a defect that you have found in Ubuntu's file manager, does not.  I'd say it's worth filing a bug over since it impairs use of the file manager to launch programs / scripts.  I notice there's not even a way to find the right application (/bin/sh) to open it with.

So, you'll have to launch Tor via the shell, I outlined the general process above.  Myself, I would enter the following in the shell (terminal) because that's where I put Tor.

```

~/tor-browser_en-US/start-tor-browser

```

Depending on where you unpacked the archive and the language you chose, yours should be similar.

I finished filing a bug over just now, so that's settled for now. However, upon launching the Tor via shell, I now experience the same problem about which I initially began this thread in the first place, only this time with the Tor Browser Bundle instead of Tor installed via the Software Center: wherein the Vidalia control panel "successfully connects to the Tor network," but Tor Browser itself does not open. Know what that's about?

---

