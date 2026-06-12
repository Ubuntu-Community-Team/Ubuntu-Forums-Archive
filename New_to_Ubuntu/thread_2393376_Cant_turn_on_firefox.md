---
title: "Cant turn on firefox"
date: 2018-06-02
forum: New to Ubuntu
---

### Post by peppek1993 on 2018-06-02
Hey

Today I bought my very first remote server and I configured it following this guide.

#!/bin/bash
set -xe

# Run this script as a user with sudo rights

# Password for the vnc server
PASSWORD="Passw0rd" # please change this password before you run
VNC_STATE_FOLDER="$HOME/.vnc"

# Install minimal desktop and tightvnc
sudo apt update
sudo apt install xorg lxde-core tightvncserver \
    firefox chromium-browser -y

mkdir -p "${VNC_STATE_FOLDER}"
echo $PASSWORD | vncpasswd -f > "${VNC_STATE_FOLDER}/passwd"
chmod 0600 "${VNC_STATE_FOLDER}/passwd"

cat << EOF >> ${VNC_STATE_FOLDER}/xstartup
#!/bin/sh

xrdb $HOME/.Xresources
xsetroot -solid grey
export XKL_XMODMAP_DISABLE=1
/etc/X11/Xsession

lxterminal &
/usr/bin/lxsession -s LXDE &
EOF

chmod 777 ${VNC_STATE_FOLDER}/xstartup

tightvncserver  :1





Now, lets make 1 thing clear. I'M EXTREMELY NEW to this, I don't know what any of it means or does.

Before doing steps above i logged in as root (i think?)


basically I logged in using Putty SSH then typed

su

and logged into root

then did the steps above.


After that I launched TightVNC Viewer, connected to my server and everything seemed okay.


However, when I tried to turn on firefox - literally nothing happens. I click it once, wait. Nothing.

I click it a milion times, nothing.


What am I doing wrong here?

For christ sake, all I want to do is access Firefox. I've been looking for a solution for 3 hours, losing my mind here. Help me, I beg you


@edit

Also, at this point im fairly certain i installed a milion useless things in there. Is there a way to basically wipe everything and start over?

---

