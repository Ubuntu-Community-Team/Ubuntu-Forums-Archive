---
title: "Skip login prompt on Wvdial?"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by Jeeeep on 2008-09-07
Me again. I have a Verizon UM150 wireless card, and I'm trying to configure my desktop to let me simply click a panel icon instead of having to open a terminal and type in the command each time, and having an unused Terminal Window open the entire time I'm connected also annoys me. Simply using pppd won't let me use it without an annoying terminal window popping up (Yes I know I can just move it to an unused workspace, but getting rid of this added step every time I turn my laptop on is the entire point).

Wvdial will, however, but it gives me the line "Carrier detected. Waiting for prompt..." and it hangs there for about a minute until it says "Don't know what to do! Starting pppd and hoping for the best..."

But my card doesn't require a login username/password, and thus it never gives me this prompt. It's incredibly annoying to have to wait there for a minute until it skips it by itself (It takes me less time to just open up a terminal, type in 'pppd call verizon', and move the window to an unused workspace), is there any way to configure Wvdial to just skip this prompt altogether and move on with connecting? It'll be perfect if I can just do that.

---

### Post by niteshifter on 2008-09-07
Hi,

True enough, your card doesn't require login, but Verizon's network does. How you "login" depends upon what type of data plan you're using (QNC, Express).

This [web site]("http://www.poremsky.com/p/verizonwireless.htm") has some info on user name and passwords needed.

The easiest way to get all the info you need (sans password) is to use a Windows machine and Verizon's software. The software doesn't do anything "magical" - it just sets up Dial Up Networking for you. You pull what you need from the Window's DUN applet itself and from the Phones and Modems applet in Window's Control Panel (your phone must be connected to the computer).

Next best is to try Verizon's customer forums and ask for the setting. [howardforums.com]("http://www.howardforums.com/") is another handy resource.

No win machine handy? Then google (or the forums above) is your best hope - the odds of another 'buntu user, who uses Verizon, has the same or similar phone and uses this forum are smaller. I found the web site above with the search term "cell modem verizon". Sorry, I can't give you more specific help:
A) I use a different cell provider and phone.
B) The various providers all differ in number / user name / password.
C) phones vary in setup.
D) And then there's GPRS / EVDO / HSDPA differences.

Once you lay hands on all the info needed. I or somebody else will gladly lend a hand.

PS We (or I) can help you setup GNOME PPP (a GUI dialer) which will mitigate your terminal woes - but as that program just uses wvdial for you,  you have to get wvdial happy first.

---

### Post by lswb on 2008-09-07
I take it you have a working pppd/peers file named verizon. Can you just use the <Alt-F2> window and type pon verizon (or pppd call verizon) there instead of opening a full terminal window?

This is what I did on my system, substitute "verizon" where I have "vzw" below and substitue the device name for your UM150 where I have /dev/cdma. (it is probably something like /dev/ttyACM0. I have a udev rule to make a symlink to this device named /dev/cdma but that's for another thread)

```

#!/bin/bash

TITLE="PPP to VZW"
if ! [ -c /dev/cdma ] ; then
zenity --error --title="$TITLE" --text="Cannot find device\!\nCheck connections."
exit
fi

if pgrep -fl "pppd[[:space:]]call[[:space:]]vzw" >>/dev/null ; then
        if zenity --question --title="$TITLE" --text "Close connecton?" ; then
        poff vzw
        exit
        fi
else
        pon vzw updetach|zenity --progress --title="$TITLE" --text="Connecting..." --pulsate --auto-kill --auto-close
        exit
fi


```


Then make a launcher on the panel that points to this script. Not sure if zenity is installed by default on ubuntu but if you need it it's in the repositories. Or if you prefer remove all the zenity stuff and rewrite the script to your liking.

There is also a gnome-ppp program that can use a system tray icon and likely can do what you want, I don't use it myself so I can't provide details.

As for the terminal window staying open, pppd by default should detach from the terminal and run in the background after connection, unless the "nodetach" option is specified. Check your /etc/ppp/peers/verizon file and rmove that option if it is there.

---

### Post by Jeeeep on 2008-09-07
> **lswb said:**
> As for the terminal window staying open, pppd by default should detach from the terminal and run in the background after connection, unless the "nodetach" option is specified. Check your /etc/ppp/peers/verizon file and remove that option if it is there.

Worked perfectly; thanks. I had to make my pppd script with the help of some users on another forum (complete Linux newbie here), and I was told to put that option in.

---

### Post by PressingOnAlways on 2009-08-01
Hi, for future reference... to skip the login prompt on Wvdial, add "
stupid mode = 1 " to the configuration file...

Refer to the man wvdial.conf for more information...

[http://linux.die.net/man/5/wvdial.conf](http://linux.die.net/man/5/wvdial.conf)

---

