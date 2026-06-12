---
title: "Autostart programs"
date: 2012-04-05
forum: New to Ubuntu
---

### Post by cheatos on 2012-04-05
Hi to all,

I had to switch browsers from Opera to Firefox and now I can't get FF to start up at login automatically...

I have already looked for ~/.cache/session like said here [http://www.ubuntuforums.org/showthread.php?t=1953028&highlight=startup](http://www.ubuntuforums.org/showthread.php?t=1953028&highlight=startup) but I couldn't find the sessions folder.

I made a ~/.config/autostart directory on my own but this also didn'T have the desired effect, only that lubuntu automatically added a opera.desktop config file to my directory...

I also tried unmarking it in the desktopsettings tab but it always gets remarked when I close the window.

How can I fix this?

Thanks to all input!

---

### Post by dodo3773 on 2012-04-05
Lubuntu is openbox I believe. Openbox does not use "~/.config/autostart". It uses 

"~/.config/openbox/autostart.sh"

or sometimes

"~/.config/openbox/autostart"


The autostart file is bash. So all you need to do is put 

applicationname &

in it. Here is an example:


```

# This shell script is run before Openbox launches.
# Environment variables set here are passed to the Openbox session.

# Set a background color
#BG="000000"
#if which hsetroot >/dev/null 2>&1; then
#    BG=hsetroot
#else
#    if which esetroot >/dev/null 2>&1; then
#	BG=esetroot
#    else
#	if which xsetroot >/dev/null 2>&1; then
#	    BG=xsetroot
#	fi
#    fi
#fi
#test -z $BG || $BG -solid "#303030"

# D-bus
if which dbus-launch >/dev/null 2>&1 && test -z "$DBUS_SESSION_BUS_ADDRESS"; then
       eval `dbus-launch --sh-syntax --exit-with-session`
fi

# Make GTK apps look and behave how they were set up in the gnome config tools

#if test -x /usr/libexec/gnome-settings-daemon >/dev/null; then
#  /usr/libexec/gnome-settings-daemon &
#elif which gnome-settings-daemon >/dev/null 2>&1; then
#  gnome-settings-daemon &
# Make GTK apps look and behave how they were set up in the XFCE config tools
#elif which xfce-mcs-manager >/dev/null 2>&1; then
#  xfce-mcs-manager n &
#fi

# Preload stuff for KDE apps

#if which start_kdeinit >/dev/null 2>&1; then
#  LD_BIND_NOW=true start_kdeinit --new-startup +kcminit_startup &
#fi

# Run XDG autostart things.  By default don't run anything desktop-specific
# See xdg-autostart --help more info

#DESKTOP_ENV="OPENBOX"
#if which /usr/lib/openbox/xdg-autostart >/dev/null 2>&1; then
#  /usr/lib/openbox/xdg-autostart $DESKTOP_ENV
#fi
nitrogen --restore &
#qtpanel &
#tint2 &
xfce4-panel &
pytyle &
#cairo-dock -ciS 0 &
#sleep 10;
#xcompmgr -cC &
#xset -dpms s off &
numlockx &
#avant-window-navigator &
sleep 10 && wbar &
keepassx -lock &
kupfer --no-splash &

#sleep 5;
thunar --daemon &
#~/Documents/Scripts/matekeyring.sh &
~/Documents/Scripts/startupopen.sh &
~/Documents/Scripts/conky.sh &



```



Edit: "~/.config/openbox/autostart" is a file not a directory.

---

### Post by cheatos on 2012-04-05
Ok, thank you very much, somehow my Firefox now just started, don't ask me why ;) Still I'll have a llok to that file.

---

### Post by dodo3773 on 2012-04-05
> 
I made a ~/.config/autostart directory



You should probably get rid of that directory. There is a possibility that openbox will not boot if that directory is full of .desktop files that do not have "OnlyShowIn" line appended to them pointed to something else.

---

### Post by cheatos on 2012-04-05
Well, after posting this I went looking for that directory and i couldn't find it...
I think I really screwed up my OS now...

The only file inside my /.config/openbox folder is a lubuntu-rc.xml which I already edited for changing my keyboard shortcuts

---

### Post by dodo3773 on 2012-04-05
Does this file exist?:

```

.config/lxsession/lubuntu/autostart

```

I run plain openbox so it may be a little different.

---

### Post by dodo3773 on 2012-04-05
Please see this thread:

[http://ubuntuforums.org/showthread.php?t=1518818](http://ubuntuforums.org/showthread.php?t=1518818)

---

### Post by cheatos on 2012-04-06
The file /.config/lxsession/Lubuntu/autostart doesn't exist, too. Only file in Lubuntu folder is desktop.conf

The folder specified in you link exists but I don't really understand how I can edit it to make it start Firefox...

---

### Post by dodo3773 on 2012-04-06
> **cheatos said:**
> 
The folder specified in you link exists but I don't really understand how I can edit it to make it start Firefox...

What folder exists from the link?

---

### Post by cheatos on 2012-04-08
This one: /etc/xdg/lxsession/Lubuntu/autostart

---

### Post by dodo3773 on 2012-04-08
> **cheatos said:**
> This one: /etc/xdg/lxsession/Lubuntu/autostart

So add your autostart stuff in there and reboot or logout and back in. Should be as simple as that.

---

### Post by cheatos on 2012-04-09
Thank you very much, I added the line
@firefox -%u
to the autostart file and now it works :D

---

### Post by dodo3773 on 2012-04-09
> **cheatos said:**
> Thank you very much, I added the line
@firefox -%u
to the autostart file and now it works :D

I am not sure how different the lxde autostart file is from openbox. If it is the same syntax then it should just be 

```

firefox &

```

One of the reasons I pointed you to that other post was that I was hoping you would pick up on what they were saying about just pointing to one external script though. That's what I do now and it is much simpler I think.

---

### Post by cheatos on 2012-04-09
Well, I didn'T quite understand what they were doing there...
I haven't written anything like a script or whatever yet, so I just used this option, because that's how it worked with opera...

---

### Post by dodo3773 on 2012-04-09
> **cheatos said:**
> Well, I didn'T quite understand what they were doing there...
I haven't written anything like a script or whatever yet, so I just used this option, because that's how it worked with opera...

Okay. Well if you start needing to put multiple start up items in that file just don't forget the "&".

---

### Post by cheatos on 2012-04-09
Okay, I'll think of it ;)

Thanks for your very good and fast help!

---

