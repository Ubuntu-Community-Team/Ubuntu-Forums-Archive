---
title: "Change desktop that x11vnc starts"
date: 2014-02-16
forum: New to Ubuntu
---

### Post by ccReynolds on 2014-02-16
My Ubuntu machine does not have a monitor connected.  I have it set to start to a command line log in.  I am starting x11vnc server via an ssh login remotely with the following:
```
x11vnc -create -usepw -geometry 1280x1023 -auth ~/.Xauthority
```

I log in using tightVNC.  Everything seems to work ok.  The only issue I have is this setup defaults to the unity desktop.  I wanted to use the gnome-fallback desktop.  Where do I go to setup the default desktop.  I'm a bit fuzzy on whether this is a generic x setting, or i should be going though x11vnc or xvfb.

---

### Post by jjk2 on 2014-02-16
hey Reynolds, 

I think it is a generic x setting, i have a bit of experience on running an x server in vnc.

the settings are in the file /home/(your username)/.xinitrc
you can edit it using the following command:
```
sudo nano /home/(your username)/.xinitrc 
```
when you're finished, hit ctrl+o to save, then ctrl + x to exit.

you need to change a line looking like:

exec unity

to 

exec gnome-session 

or something alike.

if you need help editing just post the output of 
```
cat /home/(your username)/.xinitrc
```

JJK

---

### Post by ccReynolds on 2014-02-16
The home seemed like a logical place for the configuration, but my home folder does not have that file.  My original install was Ubuntu Desktop 12.04 LTS.  Not sure if that is part of the problem.
```
$ ls ~ -A
.ICEauthority  .elc                   .mission-control      Documents
.Xauthority    .fontconfig            .mozilla              Downloads
.adobe         .gconf                 .nano_history         Music
.bash_history  .gnome2                .nv                   Pictures
.bash_logout   .goutputstream-6JG0AX  .profile              Public
.bashrc        .goutputstream-M8I5AX  .pulse                Templates
.cache         .gstreamer-0.10        .pulse-cookie         Videos
.compiz        .gtk-bookmarks         .thumbnails           el_linux
.compiz-1      .gvfs                  .vnc                  el_linux_193.zip
.config        .launchpadlib          .xsession-errors      examples.desktop
.dbus          .local                 .xsession-errors.old  nohup.out
.dmrc          .macromedia            Desktop
```

Other than adding the vnc server and support applications for it the only change to the original install was to uninstalled the unity greeter so I didn't have that running on startup.  This is the contents of my lightdm.conf file not sure if this still applies when you remove the greeter:

```
cat /etc/lightdm/lightdm.conf
[SeatDefaults]
greeter-session=
user-session=gnome-fallback
```

---

### Post by jjk2 on 2014-02-17
do
```
sudo nano /etc/rc.local
```

and add the line to start vnc (which you posted) just before exit 0

this will start vnc at boot, tell me what you see after you boot and connect to ,vnc

---

